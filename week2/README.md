# 🌿 WiDS Week 2: The Shallow Baseline Challenge

![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange)
![Time](https://img.shields.io/badge/Time-4%20Hours-blue)
![Python](https://img.shields.io/badge/Python-3.8%2B-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

## 🎯 The Mission
Welcome to Week 2. Before we build massive Convolutional Neural Networks (CNNs) next week, we must establish a **Scientific Baseline**.

**The Golden Rule of ML:** *Never deploy a complex model if a simple one works just as well.*

Your goal this week is to find the "ceiling" of classical Machine Learning. You will build a system that classifies plant diseases using "Old School" methods (SVMs, Random Forests) on raw pixel data. This score will serve as the benchmark that our Deep Learning models must beat in Week 3.

---

## 📉 What is a "Baseline Approach"?

In Machine Learning, a baseline is a reference point used to compare performance. For this workshop, we are establishing **Two Levels of Baselines**:

### Level 1: The Dummy Baseline (The Floor)
This represents "Zero Skill." It answers: *What accuracy do I get if I just guess the most common label?*
* **Example:** If 70% of your dataset is "Healthy" and 30% is "Diseased", a model that blindly guesses "Healthy" for every image gets **70% accuracy**.
* **Requirement:** Your actual models **must** beat this score. If they don't, your code has a bug.

### Level 2: The Shallow Baseline (The Standard)
This represents the limit of traditional math without Neural Networks. We use algorithms like **Random Forest** or **Support Vector Machines (SVM)**.
* **The Constraint:** These models cannot "see" 2D shapes like a human does. We must **flatten** the images into long lists of numbers (vectors).
* **The Goal:** Push this score as high as possible. If you reach 75% here, our Deep Learning model needs to hit 90%+ to justify its cost.



---

## 🧩 The Algorithm (Pseudocode)

Don't just copy-paste code. Understand the logic. Here is the pseudocode for the system you need to build.

```text
ALGORITHM Shallow_Disease_Detection:

    1. DEFINE Constants:
       TARGET_SIZE = (64, 64)   // Resize images to keep feature vector small
    
    2. FUNCTION Load_Data(directory):
       Create empty lists X (features) and y (labels)
       FOR each folder in directory:
           label = folder_name
           FOR each image in folder:
               img = Read image
               img_resized = Resize img to TARGET_SIZE
               
               // CRITICAL STEP: Flatten 3D image to 1D vector
               // (64, 64, 3) becomes a vector of size 12,288
               vector = Flatten(img_resized)
               
               Append vector to X
               Append label to y
       RETURN X, y

    3. MAIN Execution:
       // Step A: Prepare Data
       X, y = Load_Data("plantvillage/color")
       Scale X using Standard Scaler (Crucial for SVM!)
       Split X, y into Train_Set (80%) and Test_Set (20%)

       // Step B: Level 1 Baseline (Sanity Check)
       Dummy_Model = Create Dummy Classifier (Strategy="Most Frequent")
       Train Dummy_Model on Train_Set
       Print "Dummy Accuracy" on Test_Set

       // Step C: Level 2 Baseline (The Real Work)
       My_Model = Create Random Forest OR SVM
       Train My_Model on Train_Set
       Predictions = My_Model predict on Test_Set
       
       // Step D: Evaluation
       Calculate Accuracy(Predictions, Real_Labels)
       Generate Confusion Matrix
