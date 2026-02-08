# 🚀 WiDS Extra Module: Production & Deployment

### Why docker? Well, _"It works on my machine" is not a valid excuse._

**Status Check:** By Week 5, you have a working Federated Learning model. But right now, it lives in a Python script or a Notebook.

**The Problem:** You can't ask a farmer to open a Terminal and run `python train.py`.

**The Solution:** You need to package your model into a **Microservice** that can run anywhere—on a cloud server, a laptop, or even a Raspberry Pi—without breaking.

This module was requested by many of you who asked: _"How do I actually ship this?"_

----------

## 📺 Prerequisite: The "Must Watch" Video

Before you touch a single line of code below, you **must** watch this. It is arguably the clearest 11 minutes on the internet regarding containers.

**The Only Docker Tutorial You Need To Get Started** (by The Coding Sloth)

[https://www.youtube.com/watch?v=DQdB7wFEygo](https://www.youtube.com/watch?v=DQdB7wFEygo)

----------

## 🛠️ The Stack (Industry Standard & Free)

We are dumping `flask` (too slow) and `pickle` (unsafe). We are using the modern standard:

1.  **FastAPI:** High-performance API framework (standard for ML).
    
2.  **Docker:** To containerize the application (Shipping the "computer" with the code).
    
3.  **Basic Logging:** Your first step into MLOps.
    

----------

## 📝 Step-by-Step Guide

### Step 1: Build the Inference Engine (`app.py`)

We need a server that accepts an image and returns a prediction. Create a file named `app.py`.

Python

```
# app.py
from fastapi import FastAPI, File, UploadFile
from PIL import Image
import io
import torch
import torchvision.transforms as transforms
import logging

# 1. Initialize API
app = FastAPI(title="Plant Disease Detector API")

# 2. Setup Logging (This is your minimal MLOps monitoring)
logging.basicConfig(filename='app.log', level=logging.INFO, 
                    format='%(asctime)s - %(message)s')

# 3. Load Your Model (From Week 5)
# Ensure you have your 'global_model.pth' in a folder named 'model'
MODEL_PATH = "model/global_model.pth" 
device = torch.device("cpu") # Docker containers usually run on CPU

# Load architecture (This must match your Week 3/4 definition exactly)
# For this example, we assume you saved the entire model
try:
    model = torch.load(MODEL_PATH, map_location=device)
    model.eval()
    print("✅ Model loaded successfully.")
except Exception as e:
    print(f"❌ Error loading model: {e}")

# 4. Define Preprocessing
transform = transforms.Compose([
    transforms.Resize((224, 224)),
    transforms.ToTensor(),
])

@app.get("/")
def home():
    return {"status": "Online", "message": "Send POST request to /predict 🌿"}

@app.post("/predict")
async def predict(file: UploadFile = File(...)):
    # Read Image
    image_data = await file.read()
    image = Image.open(io.BytesIO(image_data)).convert("RGB")
    
    # Preprocess
    tensor = transform(image).unsqueeze(0).to(device)
    
    # Inference
    with torch.no_grad():
        outputs = model(tensor)
        probabilities = torch.nn.functional.softmax(outputs[0], dim=0)
        confidence, predicted_class = torch.max(probabilities, 0)
    
    # Map index to class name (Edit these based on your dataset)
    class_names = ["Healthy", "Early Blight", "Late Blight"] 
    result = class_names[predicted_class.item()]
    
    # Log the prediction (Monitoring)
    logging.info(f"Pred: {result} | Conf: {confidence.item():.4f}")
    
    return {
        "class": result,
        "confidence": float(confidence.item())
    }

```

### Step 2: The Recipe (`Dockerfile`)

This file tells Docker how to build your "virtual computer." Create a file named `Dockerfile` (no extension).

Dockerfile

```
# 1. Base Image: Start with a lightweight Python version
FROM python:3.9-slim

# 2. Set Working Directory inside the container
WORKDIR /app

# 3. Copy Requirements first (optimizes build cache)
COPY requirements.txt .

# 4. Install Dependencies
# We use --no-cache-dir to keep the image small
RUN pip install --no-cache-dir -r requirements.txt

# 5. Copy the rest of the application code
COPY . .

# 6. Expose the port (FastAPI defaults to 8000)
EXPOSE 8000

# 7. Command to run the app
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]

```

### Step 3: Dependencies (`requirements.txt`)

Create this file so Docker knows what to install.

Plaintext

```
fastapi
uvicorn
python-multipart
torch --index-url https://download.pytorch.org/whl/cpu
torchvision --index-url https://download.pytorch.org/whl/cpu
pillow

```

_(Note: We use the CPU version of PyTorch to keep the Docker image size small, as most free cloud tiers don't offer GPUs)._

----------

## 🚀 Launch Time

### 1. Build the Container

Open your terminal in the folder containing these files and run:

Bash

```
docker build -t plant-doctor-v1 .

```

_(This will take a few minutes as it downloads Python and PyTorch. Watch the layers build—it's satisfying.)_

### 2. Run the Container

Bash

```
docker run -p 8000:8000 plant-doctor-v1

```

Your terminal is now locked to the container. The app is live inside the isolated environment.

### 3. Test It (The "Magic" Moment)

Open your browser to:

👉 **http://localhost:8000/docs**

FastAPI automatically generates a documentation UI (Swagger UI).

1.  Click **POST /predict**.
    
2.  Click **Try it out**.
    
3.  Upload a leaf image.
    
4.  Click **Execute**.
    

If you see a JSON response with `"class": "Late Blight"`, congratulations. You have just engineered a production-grade ML microservice.

----------

## 📊 Where to go from here? (Challenge)

Now that it's Dockerized, you can deploy this **anywhere**.

-   **Easy:** Deploy to **Render.com** (Free Tier supports Docker).
    
-   **Medium:** Deploy to **Hugging Face Spaces** (Select Docker SDK).
    
-   **Hard (Pro):** Deploy to AWS EC2 or Google Cloud Run.
    

**Final Deliverable for this Module:**

Take a screenshot of your **Swagger UI** successfully classifying a plant image and share it in the group.

**_Happy Shipping! 🚢_**
