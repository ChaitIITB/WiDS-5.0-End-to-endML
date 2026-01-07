# 🌿 WiDS Week 3: Deep Learning — Let the Model Learn the Features

![Difficulty](https://img.shields.io/badge/Difficulty-Advanced-purple)
![Time](https://img.shields.io/badge/Time-4--5%20Hours-blue)
![Python](https://img.shields.io/badge/Python-3.8%2B-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

## 🎯 The Mission

Last week, you built “old school” ML models.

They worked — but they struggled.

This week, you will build something different:

> **A model that learns its own features directly from images.**

You will train your first **Convolutional Neural Network (CNN)** and then upgrade it using **Transfer Learning** to reach **85–90% accuracy**.

This is the point where Machine Learning stops being theory — and starts feeling powerful.

---

## 🧠 Why Do We Need Deep Learning?

Classical models require hand-crafted features.

CNNs do this automatically.

They learn patterns like:

- ✔ edges  
- ✔ textures  
- ✔ spots / lesions  
- ✔ disease shapes on leaves  

And they stack these patterns into understanding:

> “This leaf looks like late blight.”

CNNs don’t flatten the image — they **preserve spatial structure**.

---

## 🚀 Our Two-Stage Plan

### ⭐ Stage 1 — Build a Simple CNN (From Scratch)

You’ll train a small CNN to understand:

- Convolution  
- Pooling  
- Activation functions  
- Overfitting  

Expected accuracy: **70–80%**

---

### 🔥 Stage 2 — Transfer Learning (The Real Power Move)

Instead of starting from zero, we use a model trained on **millions of images**, such as:

- MobileNet  
- ResNet  
- EfficientNet  

We freeze most layers, replace the final classifier, and fine-tune.

Expected accuracy: **85–90%+**

---

## 🧩 The Algorithm (Pseudocode)

```text
ALGORITHM Deep_Disease_Detection:

    1. LOAD dataset (train + validation)

    2. PREPROCESS:
       - Resize images to 224x224
       - Normalize pixel values to [0,1]
       - Apply Data Augmentation (flip/rotate/zoom)

    3. MODEL A: Simple CNN
       - Conv -> ReLU -> MaxPool
       - Conv -> ReLU -> MaxPool
       - Flatten
       - Dense -> Softmax

       Train for ~10 epochs
       Record accuracy

    4. MODEL B: Transfer Learning
       - Load pretrained backbone (e.g., MobileNetV2)
       - Freeze backbone layers
       - Add new classification head:
           GlobalAveragePooling -> Dense -> Softmax

       Train only head (~5 epochs)
       Then optionally unfreeze last few layers and fine-tune.

    5. EVALUATE:
       - Accuracy
       - Confusion Matrix
       - Compare with Week 2 baseline

    6. REFLECT:
       - Why did transfer learning perform better?
       - Where does model still fail?
```

---

## 🧪 Your Tasks

### ✅ Task 1 — Train a Simple CNN
Goal: feel the limitations and understand overfitting.

### ✅ Task 2 — Apply Transfer Learning
Goal: boost accuracy with fewer parameters.

### ✅ Task 3 — Compare
Write down:

- Shallow Model Accuracy (Week 2)  
- CNN Accuracy  
- Transfer Learning Accuracy  

If your deep model doesn’t clearly beat Week 2:

> something is wrong — revisit preprocessing or labels.

---

## 📊 Evaluation Checklist

Before submitting, make sure you generated:

- ✔ accuracy score  
- ✔ confusion matrix  
- ✔ training vs validation curves  
- ✔ short reflection (2–3 lines)

---

## 📚 Resources (Curated + Short)

### 🎥 Concept explainers
- Neural Networks visually explained (3Blue1Brown):  
  https://www.youtube.com/watch?v=aircAruvnKk
- Convolutions explained simply:  
  https://poloclub.github.io/cnn-explainer/

### 🧭 Transfer Learning Guides
- Transfer Learning with TensorFlow (Keras):  
  https://www.tensorflow.org/tutorials/images/transfer_learning

### 🛠 Data Augmentation
- Torchvision transforms:  
  https://pytorch.org/vision/stable/transforms.html

---

## 🏁 What You’ve Learned

By the end of Week 3, you’ll understand:

- why flattening destroys spatial information  
- what convolutions actually do  
- why pretrained networks are game-changers  
- how deep models move beyond “guessing patterns”  

And most importantly:

> **You now have a real, working deep learning model.**

Week 4 will take this one step closer to production 😉
