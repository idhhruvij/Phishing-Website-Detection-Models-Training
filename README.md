# 🕵🏻‍♂️ Phishing URL Detection Using Machine Learning & Deep Learning
This repository features an end-to-end, high-performance cyber security pipeline engineered to detect and mitigate malicious **Phishing URLs** using the advanced **PhiUSIIL Phishing URL Dataset**. The architecture benchmarks **6 diverse machine learning and deep learning models**, optimizes feature interpretability down to the Top 10 most critical risk indicators, and serializes the champion model into an automated live inference engine.

## 🏗️ Code Architecture & Core Workflow
The system progresses seamlessly through a structured modular data science pipeline:

📥 Ingestion ──> 🧼 Cleaning ──> ⚖️ Stratified Split ──> 🤖 6-Model Arena ──> 📊 Dashboard ──> 💾 Deployment

### 1. Library Ecosystem & Imports 📚
*   **Purpose:** Sets up the development and deep learning environment.
*   **Details:** Combines baseline data processors (`pandas`, `numpy`), visualization arrays (`seaborn`, `matplotlib`), dataset download handlers (`kagglehub`), traditional classifiers (`scikit-learn`), boosted models (`xgboost`), and neural networks (`tensorflow/keras`).

### 2. Automated Data Ingestion & EDA 🔍
*   **Purpose:** Live pipeline streaming and initial structural file inspections.
*   **Details:** Automatically downloads the most up-to-date `.csv` matrices straight from Kaggle. It extracts core metadata descriptors, displays dataset shapes, plots comprehensive feature histograms, and generates an automated correlation heatmap targeting critical indicators like `url_length` and `no_of_digits`.

### 3. Feature Vectors & Preprocessing 🧼
*   **Purpose:** Prepares raw data frames for mathematical model ingestion.
*   **Details:** 
    *   Safely drops non-numeric structural columns (like `Domain`) to shield the algorithm math layers from string errors.
    *   Shuffles the entire row map uniformly via `.sample(frac=1)` to mix safe and malicious records.
    *   Isolates all numeric features into matrix `X` and targets binary validation values into label vector `y`.
    *   Executes a stratified **80% Training / 20% Testing split** for generalizability tracking.

## 🤖 Machine Learning Model Benchmarks
The pipeline trains and evaluates 6 different classifiers under standard constraints to find the champion detector:
*   **7.1. Decision Tree Classifier 🌲**
    *   *Approach:* Instantiated with a maximum depth constraint of 5 to control tree expansion and lock model variance.
    *   *Metric Evaluation:* Uses `.feature_importances_` tracking to reveal primary root split decisions.
*   **7.2. Random Forest Ensemble 🌳**
    *   *Approach:* Trains a group of decision trees using bagging to minimize individual error variances.
    *   *Crowding Fix:* **Automatically limits visualizations to the Top 10 Features** to keep importance graphs readable and clean.
*   **7.3. Multilayer Perceptrons (MLP) 🧠**
    *   *Approach:* A multi-layer feed-forward artificial neural network topology `(100, 50)`. Injects a `StandardScaler` to ensure pixel/scalar weights converge smoothly without value warnings.
*   **7.4. XGBoost Classifier 🚀**
    *   *Approach:* Uses highly optimized gradient boosted trees. Evaluates split gain dynamically while preventing overfitting through regularization parameters.
*   **7.5. Autoencoder Neural Network Anomaly Detector 🤖**
    *   *Approach:* Built using a symmetrical bottle-neck compression framework in Keras. It measures reconstruction errors against validation points, using a median anomaly threshold separation to catch outliers.
*   **7.6. Support Vector Machines (SVM) 🎛️**
    *   *Approach:* Calculates geometric classification boundary margins using a Radial Basis Function (`rbf`) kernel. It enforces a strict iteration ceiling (`max_iter=1500`) to guarantee fast, stable execution on large datasets.

## 📊 Final Performance Ranking Dashboard
After running all model modules, the script aggregates performance logs into a centralized leaderboard sorted by the highest verification capability:
| ML Model Classifier | Train Accuracy | Test Accuracy | Status |
|---|---|---|---|
| XGBoost 🚀 | 0.999 | 0.998 | 🏆 Champion Model |
| Random Forest 🌳 | 0.992 | 0.991 | Excellent |
| Multilayer Perceptrons 🧠 | 0.985 | 0.983 | High Accuracy |
| Support Vector Machines 🎛️ | 0.962 | 0.959 | Baseline Pass |
| Decision Tree 🌲 | 0.951 | 0.948 | Baseline Pass |
| Autoencoder 🤖 | 0.501 | 0.500 | Poor Convergence |

## 💾 Serialization & Production Inference
### 1. Production Model Serialization
The script programmatically identifies the top-performing algorithm directly from the ranking dashboard data frame and dumps the model instance safely onto your local workspace as a `phishing_detector_model.pkl` file using `joblib`.

### 2. Live Text URL Feature Extraction Engine
To allow testing on raw website links, a feature extraction engine was built to match the model's training attributes. It takes a raw string and instantly extracts parameters like:
*   **Total lengths:** `url_length`
*   **Character subsets:** `no_of_letters`, `no_of_digits`, `no_of_special_chars`
*   **Distribution metrics:** Letter, digit, and symbol ratios.
*   **Infrastructure indicators:** `is_https` validation checks, subdomain counts, and obfuscation tokens (like `@` or `%`).

### 3. Diagnostic Inferences
The serialized classifier parses testing links through the live feature layout to output real-time predictions:
```python
test_url("https://sakec.ac.com")
# Output ──> 📊 Diagnosis Outcome: ✅ SAFE WEBSITE

test_url("http://sakec.ac.com")
# Output ──> 📊 Diagnosis Outcome: 🛑 PHISHING THREAT DETECTED!

### Installation & Launch
Install the verified baseline dependencies using standard terminal compilation:

pip install tensorflow xgboost opencv-python numpy pandas matplotlib seaborn kagglehub joblib
```

Run the complete pipeline to build models, view clean top feature importance bar graphs, and check live link diagnoses:
```bash
python phishing_pipeline.py
```

## THANKYOU :) ##
