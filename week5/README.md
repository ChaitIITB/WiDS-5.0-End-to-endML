# 🚀 Week 5 — Saving, Visualizing, and Deploying a Federated Model (Beginner MLOps)

This week focuses on **what happens after training is complete**.

You already have a working Federated Learning model from Week 4.  
Now, you will treat it like a **real ML system**, not a one-time experiment.

The goal is **not** better accuracy — it is **usability, visibility, and reproducibility**.

---

## 🎯 Objectives
By the end of Week 5, you will be able to:

- Save the final **global federated model** to disk
- Persist training metrics for later inspection
- Visualize federated training behavior using **Streamlit**
- Understand how these steps relate to real-world MLOps

No retraining is required.

---

## 🧠 Why This Matters
In real deployments:

- Models are **saved**, not retrained every time
- Training and analysis are **separate steps**
- Engineers inspect results **after** training finishes

Federated Learning makes this even more important because:
- Clients are distributed
- Training behavior is harder to debug
- Observability is essential

---

## 🧩 What You Will Build

### 1️⃣ Model Persistence
You will save the **final global model** produced by federated training.

**Why**
- Enables reuse for inference
- Simulates shipping the model to edge devices
- Matches real deployment workflows

---

### 2️⃣ Metric Logging
You will store key training metrics per federated round, such as:
- Round number
- Global accuracy
- (Optional) Number of participating clients

**Why**
- Logs are the primary debugging tool in ML systems
- Results can be analyzed without rerunning training

---

### 3️⃣ Streamlit Visualization App
You will create a simple **Streamlit app** that:
- Loads saved metrics
- Plots global accuracy vs federated rounds
- Displays final model performance

**Why**
- Separates training from analysis
- Provides a human-readable interface
- Mimics lightweight model monitoring

---

## 🛠️ Step-by-Step Tasks

### Step 1: Save the Global Model
After the final federated round:
- Save the global model weights to disk (e.g., `.pth` file)
- Store it in a dedicated `models/` directory

---

### Step 2: Save Training Metrics
During or after training:
- Write metrics to a CSV or JSON file
- One entry per federated round

Suggested fields:
- `round`
- `global_accuracy`
- `num_clients` (optional)

---

### Step 3: Build the Streamlit App
Create a Streamlit app that:
- Loads the saved metrics file
- Plots accuracy vs rounds
- Displays a short summary of the final result

Keep it simple — static plots are enough.

---

### Visualization Resources
- Streamlit Documentation  
  https://docs.streamlit.io/

- Why Monitoring ML Models Matters  
  https://evidentlyai.com/ml-monitoring

---

## 🏁 Final Takeaway
Week 5 is about **thinking like an ML engineer**, not a researcher.

You move from:
- *Training a model*  
to  
- *Saving, inspecting, and reusing a model*

That mindset is what turns experiments into systems.
