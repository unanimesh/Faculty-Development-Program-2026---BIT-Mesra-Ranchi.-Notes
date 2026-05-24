#  Faculty Development Program 2026 - BIT Mesra
## Session 10: AI in Autonomous Vehicles and Smart Agriculture

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Sudhansu Kumar Mishra |
| **Designation** | **Head of Department**, Electrical & Electronics Engineering |
| **Institution** | Birla Institute of Technology (BIT) Mesra, Ranchi |
| **Email** | bitmesra.ac.in  |
| **Google Scholar Citations** | 2,002+ |
| **Research Areas** | Signal Processing, Control Systems, Bio-medical Image Processing, Soft Computing, Multi-Objective Optimization |

> **This is your own department head speaking!** Dr. Mishra is not just a faculty member — he is the **Head of EEE Department at BIT Mesra**, the same department hosting this FDP.

### Key Research Areas (Directly on Today's Topic)

1. **Autonomous Vehicles** — Lane detection, mid-lane estimation, path planning, obstacle avoidance, probabilistic vehicle localization
2. **Smart Agriculture** — Vision-based autonomous agricultural vehicles, satellite image processing for field monitoring, control techniques for agri-robots
3. **Signal Processing & Computer Vision** — Image processing, contour-based methods, sensor fusion
4. **Soft Computing** — ML-based path planning, adaptive algorithms, multi-objective optimization

### Key Publications 

| # | Paper | Key Contribution |
|---|---|---|
| 1 | **"LDCCAES: A Concomitant Perception Methodology for Real-Time Detection and Estimation of Median-Lane Positioning for Prototype Autonomous Vehicle"** | Novel contour-based mid-lane estimation for autonomous vehicle road navigation |
| 2 | **"Control Techniques for Vision-Based Autonomous Vehicles for Agricultural Applications: A Meta-Analytic Review"** | Comprehensive review of vision+control methods for autonomous agri-vehicles — directly today's topic |
| 3 | **"A Machine Learning Approach for Collision Avoidance and Path Planning of Mobile Robot under Dense and Cluttered Environments"** | ASGDLR algorithm (Adaptive Stochastic Gradient Descent Linear Regression) for robot path planning |
| 4 | **"State Estimation Obstacle Avoidance (SEOA) Algorithm for Autonomous Mobile Robot"** | Collision-free path planning while minimizing cost and time |
| 5 | **Probabilistic Models for Autonomous Ground Vehicle Position Estimation** | Bayesian state estimator for autonomous vehicle localization — position estimation under uncertainty |
| 6 | **Satellite Image Processing for Agricultural Field Monitoring** | Preprocessing and analysis of satellite imagery for crop monitoring, forest surveillance, field mapping |

---

##  Topic Deep Dive: AI in Autonomous Vehicles and Smart Agriculture

These two application domains — autonomous vehicles (AV) and smart agriculture — share the **same underlying AI stack**: computer vision, sensor fusion, path planning, and control. The agricultural robot is essentially an autonomous vehicle operating in a structured field environment.

---

### 1. AI in Autonomous Vehicles

#### The AV Perception Stack

An autonomous vehicle must understand its environment in real-time. The perception pipeline:

```
World
  ↓
[Sensors: Camera, LiDAR, RADAR, GPS, IMU]
  ↓
[Sensor Fusion — combines all sensor inputs]
  ↓
[Perception: Object Detection, Lane Detection, Depth Estimation]
  ↓
[Localization: Where am I? (SLAM, GPS, HD Maps)]
  ↓
[Prediction: What will other vehicles/pedestrians do?]
  ↓
[Planning: Path Planning + Trajectory Generation]
  ↓
[Control: Steering, Throttle, Brake]
  ↓
Vehicle actuators
```

#### A. Lane Detection — Dr. Mishra's Core Research

Lane detection answers: **"Where is the lane boundary and where is the center of my lane?"**

**Dr. Mishra's Contribution — LDCCAES:**
- Focuses on **mid-lane estimation** — finding the exact center of the driveable lane
- Uses **contour-based approach** — extracts lane boundaries as geometric contours from camera images
- Real-time capable — designed for prototype autonomous vehicle deployment
- Key challenge addressed: Robust performance under varied lighting, road markings, and occlusion

**Common Lane Detection Methods:**

| Method | Approach | Strength | Weakness |
|---|---|---|---|
| **Hough Transform** | Detects straight lines | Simple, fast | Fails on curves |
| **Contour-based (Dr. Mishra)** | Edge-contour extraction | Handles curves, real-time | Sensitive to noise |
| **CNN-based** | Deep learning (SCNN, UFLD) | Very accurate | Computationally heavy |
| **Polynomial fitting** | Fits lane to a curve equation | Smooth output | Needs good edge detection first |
| **Transformer-based** | Vision Transformer | State-of-art accuracy | Slow, needs GPU |

#### B. Vehicle Localization — Dr. Mishra's Probabilistic Work

**Problem**: GPS is inaccurate (±3–10 meters). AVs need centimeter-level accuracy.

**Dr. Mishra's approach — Bayesian State Estimation:**
- **Bayesian estimator** maintains a probability distribution over the vehicle's possible positions
- As new sensor data arrives, the distribution is updated (Bayes' theorem)
- Two probabilistic models applied to autonomous ground vehicles:
  - **Kalman Filter**: Optimal for linear systems with Gaussian noise
  - **Particle Filter**: Handles nonlinear systems and non-Gaussian distributions

**Localization methods compared:**

| Method | Accuracy | Compute Cost | Dr. Mishra's relevance |
|---|---|---|---|
| GPS only | ±3–10 m | Low | Insufficient for AV |
| GPS + IMU fusion | ±1–2 m | Medium | Common baseline |
| **Bayesian/Particle Filter** | ±0.1–0.5 m | Medium | Dr. Mishra's approach |
| SLAM (LiDAR) | ±0.05 m | High | State of art |
| HD Map + SLAM fusion | ±0.02 m | Very High | Production AVs |

#### C. Path Planning — ML-Based Obstacle Avoidance

**Dr. Mishra's ASGDLR Algorithm (Adaptive Stochastic Gradient Descent Linear Regression):**
- Applied to mobile robot path planning in **dense and cluttered environments**
- Combines ML (gradient descent optimization) with geometric path planning
- Goals: Collision-free path + minimize travel time + minimize computational cost
- The **SEOA (State Estimation Obstacle Avoidance)** algorithm extends this with real-time state estimation

**Classical vs ML-based Path Planning:**

| Method | Type | Best For |
|---|---|---|
| **Dijkstra's Algorithm** | Graph search | Known static maps |
| **A\*** | Heuristic graph search | Known maps with obstacles |
| **RRT / RRT\*** | Sampling-based | Unknown environments |
| **DWA (Dynamic Window Approach)** | Real-time | Moving obstacles |
| **ASGDLR (Dr. Mishra)** | ML + optimization | Dense, cluttered environments |
| **Deep RL** | Neural network | Complex dynamic environments |

#### D. AI Techniques Used in Modern AVs

| AI Method | AV Application |
|---|---|
| **CNN (YOLO, Faster R-CNN)** | Object detection — cars, pedestrians, signs |
| **Semantic Segmentation (DeepLab, SegNet)** | Pixel-level road/lane/obstacle classification |
| **LSTM / Transformer** | Trajectory prediction of other vehicles |
| **Kalman / Particle Filter** | State estimation + sensor fusion |
| **Reinforcement Learning** | End-to-end driving policy learning |
| **Graph Neural Networks** | Multi-agent interaction modeling |
| **PointNet** | 3D LiDAR point cloud processing |

---

### 2. AI in Smart Agriculture

#### Why Smart Agriculture?

- India is the world's second-largest food producer but faces major challenges: labor shortage, inefficient resource use, climate variability, crop disease
- Autonomous vehicles + AI can address: precision spraying, soil monitoring, crop health assessment, yield prediction, irrigation management
- **Dr. Mishra's meta-analytic review** specifically covers control techniques for vision-based autonomous agricultural vehicles

#### The Agricultural Autonomous Vehicle (AgAV)

An agricultural robot is an autonomous ground vehicle (UGV) adapted for farm environments:

```
Camera/LiDAR → Crop Row Detection
GPS/IMU      → Field Navigation
Soil Sensors → Soil Health Data
Drone Images → Crop Canopy Analysis
                    ↓
            AI Processing Unit
                    ↓
    Precise Spraying | Weeding | Harvesting | Monitoring
```

**Key difference from road AV**: Farm environment is **structured but unpredictable** — crop rows are regular, but terrain is uneven, lighting changes, crops grow and obscure paths.

#### Applications of AI in Smart Agriculture

| Application | AI Method | Impact |
|---|---|---|
| **Crop Disease Detection** | CNN, Transfer Learning (ResNet, VGG) | Early detection → 20–30% yield loss prevention |
| **Weed Detection & Precision Spraying** | YOLOv8, semantic segmentation | Reduces herbicide use by 90% |
| **Yield Prediction** | LSTM, Random Forest, satellite imagery | Better harvest planning |
| **Soil Health Monitoring** | IoT sensors + ML | Optimized fertilizer use |
| **Autonomous Tractor Navigation** | GPS + computer vision + path planning | Row tracking in fields |
| **Irrigation Management** | DRL, sensor fusion | Reduces water use by 30–50% |
| **Satellite Image Analysis** | CNN, image segmentation | Field-level crop monitoring at scale |

#### Dr. Mishra's Satellite Imagery Work

**Problem**: Deploying physical sensors everywhere in large agricultural fields is impossible.

**Dr. Mishra's Approach — Satellite Image Processing for Agriculture:**
- Raw satellite images need preprocessing before analysis (atmospheric correction, geometric correction)
- Applications: Monitoring crop health (NDVI — Normalized Difference Vegetation Index), detecting field boundaries, tracking irrigation patterns, forest surveillance
- Satellite imagery enables **field-scale monitoring** of thousands of hectares simultaneously
- Connects to: Government schemes like Fasal Bima (crop insurance), ISRO's agricultural remote sensing programs

#### Vision-Based Control for Agri-Robots

From Dr. Mishra's meta-analytic review — control techniques for autonomous agri-vehicles:

| Control Method | Description | Agricultural Use |
|---|---|---|
| **PID Control** | Error-based feedback | Row-following, heading control |
| **Fuzzy Logic** | Human-like rules | Terrain adaptation |
| **Model Predictive Control** | Receding horizon optimization | Trajectory tracking on uneven terrain |
| **Vision-based Servo Control** | Camera feedback drives actuators | Crop row centering |
| **Neural Network Control** | End-to-end learned controller | Complex field navigation |
| **SLAM-based** | Simultaneous mapping + navigation | Unknown field mapping |

---

### 3. Where AV and Smart Agriculture Converge

The key insight of this combined session:

| Technology | Road AV | Agricultural AV |
|---|---|---|
| **Perception** | Lane detection, traffic sign | Crop row detection, obstacle in field |
| **Localization** | GPS + HD Maps + SLAM | GPS + RTK + field maps |
| **Path Planning** | Road network graph | Field row path, headland turning |
| **Object Detection** | Cars, pedestrians, cyclists | Weeds, fruits, soil features |
| **Control** | Steering + throttle + brake | Tractor steering + implement control |
| **AI Core** | Same: CNN, LSTM, RL, Bayesian | Same: CNN, LSTM, RL, Bayesian |

> **Dr. Mishra's unique contribution**: Bridging the autonomous vehicle research domain and the agricultural robotics domain — both using the same AI foundation.

---

### 4. India-Specific Context

- **India's AV Policy**: NITI Aayog and Ministry of Road Transport are developing frameworks for autonomous and connected vehicles; Bharat NCAP safety ratings now active
- **Agriculture**: India has 1.4 billion people to feed; 58% of population depends on agriculture; average farm size is only 1.08 hectares — small farms need affordable, lightweight agri-robots
- **ISRO Support**: Satellite imagery from Resourcesat-2, RISAT — freely available for agricultural monitoring
- **BIT Mesra's Role**: Dr. Mishra's prototype autonomous vehicle research directly contributes to India's Make-in-India AV development ecosystem
- **PM-KISAN, Digital Agriculture Mission**: Government pushing AI-based precision agriculture as national priority

---

## Questions to Ask


1.
   > *"Your LDCCAES paper focuses on contour-based mid-lane estimation for prototype autonomous vehicles. In agricultural environments — where 'lanes' are crop rows, not painted road markings — how does the contour-based approach need to be modified to handle irregular row spacing, partial occlusion by crop canopy, and the absence of color contrast that road lane detection relies on?"*

2. > *"Your meta-analytic review covers control techniques for vision-based agricultural vehicles. Of all the control methods reviewed — PID, fuzzy, MPC, vision servo, neural — which do you believe is the most deployable for a smallholder Indian farmer's context (low cost, no cloud connectivity, simple maintenance), and what is the minimum viable sensor suite?"*

3. > *"In your probabilistic localization work using Bayesian state estimation — how does the position estimation accuracy degrade in a dense crop field where GPS signal is partially blocked by canopy and there are no visible landmarks for visual odometry? What is your practical fallback strategy?"*

4. > *"Your satellite image processing work for agricultural monitoring requires preprocessing raw satellite data. With ISRO's Resourcesat-2 freely available — what is the end-to-end pipeline a BIT Mesra research group could build today, using open-source tools, to deliver real-time crop health maps to farmers in Jharkhand?"*

5. > *"As Head of EEE at BIT Mesra — where do you see the most impactful intersection of this FDP's themes (power electronics, control, AI, cybersecurity) with autonomous agricultural vehicles? Is there a specific research problem that a multidisciplinary BIT Mesra team — combining your AV work with Dr. Sarode's power electronics and Dr. Subhojit Ghosh's digital control — could tackle together?"*

---

## 📚 Key Terms Glossary

| Term | Meaning |
|---|---|
| AV | Autonomous Vehicle — self-driving car/robot |
| UGV | Unmanned Ground Vehicle — autonomous robot on ground (includes agri-robots) |
| LDCCAES | Dr. Mishra's lane detection and mid-lane estimation methodology |
| SEOA | State Estimation Obstacle Avoidance — Dr. Mishra's path planning algorithm |
| ASGDLR | Adaptive Stochastic Gradient Descent Linear Regression — Dr. Mishra's ML path planning |
| Lane Detection | Identifying lane boundaries from camera image |
| Mid-lane Estimation | Finding exact center of the driveable lane |
| Contour-based | Image processing using geometric edge contours |
| Bayesian State Estimation | Probabilistic vehicle position tracking using sensor updates |
| Kalman Filter | Optimal state estimator for linear Gaussian systems |
| Particle Filter | Probabilistic state estimator for nonlinear/non-Gaussian systems |
| SLAM | Simultaneous Localization and Mapping |
| LiDAR | Light Detection and Ranging — laser-based 3D sensing |
| RADAR | Radio Detection and Ranging — velocity + distance sensing |
| IMU | Inertial Measurement Unit — acceleration + gyroscope |
| RTK GPS | Real-Time Kinematic GPS — centimeter-level accuracy |
| NDVI | Normalized Difference Vegetation Index — satellite-based crop health metric |
| Precision Agriculture | Data-driven, site-specific crop management |
| YOLOv8 | You Only Look Once version 8 — fast real-time object detection |
| Semantic Segmentation | Classifying every pixel in an image (road, crop, obstacle) |
| Meta-analytic Review | Systematic review + quantitative synthesis of existing research |
| HD Map | High-Definition Map — centimeter-accurate 3D road map for AVs |
| Vision Servo Control | Using camera feedback directly to control robot actuators |

---



## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
