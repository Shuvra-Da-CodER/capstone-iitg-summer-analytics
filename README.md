# 📅 Dynamic Pricing for Urban Parking Lots

**Capstone Project | Summer Analytics 2025**  
Hosted by *Consulting & Analytics Club × Pathway*

---

## 🔎 Overview

Urban parking spaces are limited and often inefficiently priced with static rates, leading to either underutilization or excessive congestion.

This project simulates a **real-time intelligent pricing engine** for 14 urban parking lots using real-world inspired streaming data, demand signals, and predictive modeling. The objective is to dynamically adjust parking prices in response to:

- Current demand  
- Traffic and queue conditions  
- Special events  
- Competitor pricing (optional)

All models are implemented from scratch using only **NumPy, Pandas, and Pathway** in **Google Colab**.

---

## 🛠️ Tech Stack

| Tool             | Purpose                                 |
| ---------------- | ---------------------------------------- |
| **Python**       | Core language                           |
| **Pandas**       | Data preprocessing                      |
| **NumPy**        | Numeric computations                    |
| **Pathway**      | Real-time stream processing & windowing |
| **Bokeh**        | Live interactive plotting               |
| **Panel**        | Visualization wrapper in Colab          |
| **Google Colab** | Development environment                 |
| **GitHub**       | Version control & sharing               |

---

## 🛁 Architecture Diagram
![WhatsApp Image 2025-07-07 at 18 19 53_d1492eec](https://github.com/user-attachments/assets/4a6116e8-1d25-482d-80d9-36b659625e2b)


---

## 🔄 Workflow & Architecture Details

### ✅ Step 1: Data Simulation & Replay

- Pathway's `replay_csv()` is used to simulate streaming input

### ✅ Step 2: Model Implementations

#### **Model 1: Baseline Linear Pricing**

Formula:
```
Price_{t+1} = Price_t + α × (Occupancy / Capacity)
```

- Simple cumulative update  
- Per-lot memory  
- Works well with small α (e.g., 0.05) to avoid runaway prices  

#### 📉 Plot:

![model1 2](https://github.com/user-attachments/assets/9036503f-de42-426a-8f69-4f74349eb367)
![model1 3](https://github.com/user-attachments/assets/e09dd0ce-3ee0-4365-b69e-39d8f87b98b3)


-This shows that for every parking lot, there is a linear increase in the price and the price predicted at next time stemp is always greater than the price at the current time step.

---

#### **Model 2: Demand-Based Dynamic Pricing**

Formula:
```
Demand = α(Occupancy/Capacity) + βQueue - γTraffic + δEvent + εVehicleWeight  
Price = Base × (1 + λ × NormalizedDemand)
```

- Vehicle type weighted  
- Traffic-sensitive  
- Uses sigmoid-style normalization to cap extremes  

#### 📉 Plot:

![model2 1](https://github.com/user-attachments/assets/3ad34c55-c7db-4aa9-9d5b-01b8ae553c75)
![model2 2](https://github.com/user-attachments/assets/22d587da-5f09-4846-8616-64683a127839)

- This shows that everyday there is a price hike from morning to abuot midday and thereafter as the day ends, the price again reduces.

---

### ✅ Step 3: Visualization

- Prices are plotted in real-time using **Bokeh**  

---


---

## 📈 Future Enhancements

- Model 3: Competitive-aware rerouting  
- Cost optimization per lot  
- Integration into a city-wide dashboard  

---

## 🚀 Run in Google Colab

https://colab.research.google.com/drive/1tI_JI6pyC_x3_CV7xsp832uedSBrOYVJ?authuser=1#scrollTo=HOXmJBsscPGg




