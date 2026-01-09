# 🌺 WiDS Week 4: The Federated Privacy Challenge

## 🎯 The Mission

Status Check: In Week 3, you built a centralized CNN and achieved ~90% accuracy. Fantastic.

The Problem: You achieved this by "cheating", you hoarded all the data on one machine.

In the real world (healthcare, finance, competitive farming), you **cannot** centralize data.

-   **Privacy Laws (GDPR):** You can't move patient/farm data to a central cloud.
    
-   **Bandwidth:** You can't upload terabytes of video from rural cameras.
    

Your New Goal now becomes:

You must rebuild your training pipeline using Federated Learning.

-   **The Challenge:** Can you recover your **90% accuracy** if the data is split across 3 isolated clients?
    
-   **The Success Metric:** If your Federated model hits **85-88%**, you pass. If it drops below 80%, the "Privacy Tax" was too high, and you need to tune your training.
    

----------

## 📉 What is "Federated Learning"?

You are moving from a **Dictatorship** (One computer rules all data) to a **Democracy** (Voting on model updates).

### The Experiment Setup

We will simulate a "Data Silo" scenario:

1.  **The Centralized Run (Week 3):** 100% Data $\rightarrow$ 1 Model. (Result: ~90%)
    
2.  **The Federated Run (Week 4):** Data split into 3 isolated chunks $\rightarrow$ 3 Local Models $\rightarrow$ Averaged. (Result: **??%**)
    

**Why might accuracy drop?**

-   **fragmentation:** Each client sees less data, so their local gradients are "noisier."
    
-   **Non-IID Data:** If Farmer A only has potatoes and Farmer B only has tomatoes, averaging their models can get messy. (We will start with random shuffling to keep it easy).
    

----------

## 🧩 The Algorithm (Pseudocode)

We use **PyTorch** + **Flower (`flwr`)**. The logic is similar to Week 3, but wrapped in a communication layer.

Plaintext

```
ALGORITHM Federated_Recovery_Run:

    1. DEFINE Constants:
       NUM_CLIENTS = 3          // The 3 isolated Farmers
       NUM_ROUNDS = 5 to 10     // We might need more rounds to catch up to 90%
    
    2. FUNCTION Define_Client(net, local_data):
       // The "FlowerClient" is a wrapper around your Week 3 code
       CLASS FlowerClient(fl.client.NumPyClient):
           
           METHOD get_parameters():
               // Extract weights to send to the server
               RETURN net.get_weights()

           METHOD fit(global_weights):
               // Step A: Download the Global Brain
               Update local_net with global_weights
               
               // Step B: Train LOCALLY (The "Secret" Training)
               // IMPORTANT: Use the exact hyperparameters from Week 3
               Train local_net on local_data for 1-2 Epochs
               
               // Step C: Upload the improved weights
               RETURN local_net.get_weights()

           METHOD evaluate(global_weights):
               // Check accuracy on local test set
               Test local_net on local_test_data
               RETURN Accuracy

    3. MAIN Execution (The Simulation):
       // 1. Split your Week 3 dataset into 3 random parts.
       // 2. Start the Federation.
       
       Start_Simulation(
           client_fn = Client_Generator,
           num_clients = NUM_CLIENTS,
           strategy = FedAvg()  // The algorithm that averages the weights
       )

    4. FINAL COMPARISON:
       Print("Week 3 Centralized Accuracy: ~90%")
       Print("Week 4 Federated Accuracy:   " + Final_Round_Accuracy)
       
       IF (Week4_Acc > Week3_Acc - 5%):
           PRINT "System Robust. Deployment Ready."
       ELSE:
           PRINT "Drastic Drop Detected. Increase Rounds or Epochs."

```

----------

## 📚 Resources: The "Surrounding Things"

Since you have mastered basic CNNs, here is where the field is going next:

### 1. The "Must Read" (Practical)

-   **[Flower with PyTorch Tutorial](https://flower.ai/docs/framework/tutorial-series-get-started-with-flower-pytorch.html):** The exact code you need.
    
-   **[Federated Learning Comic](https://federated.withgoogle.com/):** A visual guide to why Google uses this for your phone's keyboard prediction.
    

### 2. The "Deep Dive" (Advanced Concepts)

-   **Non-IID Data:** What if Client 1 has _only_ healthy plants and Client 2 has _only_ diseased ones? (This breaks simple models). Read about **FedProx** if you are curious how we fix this.
    
-   **Privacy Attacks:** Can a hacker reverse-engineer the plant photos just by looking at the model updates? Yes! Look up **"Model Inversion Attacks"** to see why this is a cyber-security battleground.
    

### 3. "Surrounding" Tech

-   **Edge AI:** This code is designed to run on Raspberry Pis or NVidia Jetsons in the field.
    
-   **Homomorphic Encryption:** Performing math on encrypted data without decrypting it. (The "Holy Grail" of privacy).
    

----------

## ✅ Execution Checklist

-   [ ] **The Split:** Use `torch.utils.data.random_split` to divide your dataset into 3 equal parts.
    
-   [ ] **The Wrap:** Wrap your Week 3 training loop inside the `fit()` method.
    
-   [ ] **The Simulation:** Run for 5-10 rounds.
    
-   [ ] **The Benchmark:** Compare your final FL accuracy against your 90% baseline. Did you lose performance? How much?
