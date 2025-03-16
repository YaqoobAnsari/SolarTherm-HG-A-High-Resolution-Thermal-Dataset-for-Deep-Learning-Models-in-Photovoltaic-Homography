# SolarTherm-HG-A-High-Resolution-Thermal-Dataset-for-Deep-Learning-Models-in-Photovoltaic-Homography

### **Overview**
SolarTherm-HG is a **large-scale, high-resolution thermal imaging dataset** designed to support deep learning models in **thermal homography** for **photovoltaic (PV) systems**. It contains **12,460 raw thermal images (640×512 resolution)**, systematically captured under diverse conditions. The dataset is expanded to **49,840 images (320×256 resolution)** through patching and preprocessing, with homography pairs generated for deep learning applications.

SolarTherm-HG is designed to aid researchers in **thermal image processing, homography estimation, and PV system fault detection**. The dataset captures various environmental conditions, including different cleanliness levels, time-of-day variations, and image perspectives.

📂 **Dataset DOI**: [10.7910/DVN/E4OXHQ](https://doi.org/10.7910/DVN/E4OXHQ](https://doi.org/10.7910/DVN/IPU9RS)  
🛠 **GitHub Repository**: [SolarTherm-HG Repository](https://github.com/SolarTherm-HG/Dataset)  

---

## **Key Features**
✅ **Large-Scale Dataset**: 12,460 raw thermal images, expanded to 49,840 images for deep learning applications.  
✅ **High-Resolution Thermal Imaging**: Captured at **640×512 pixels**, downsampled to **320×256** for deep learning compatibility.  
✅ **Diverse Capture Conditions**:
- 4 **different times of the day** (8 AM, 10 AM, 12 PM, 2 PM) to account for natural temperature variations.
- 4 **different heights** (10 cm, 20 cm, 30 cm, 40 cm) for varying perspectives.
- 2 **inclination angles** (30° and 60°) to introduce geometrical diversity.
- 5 **cleanliness levels** (clean, soiled for 1-4 days).  
✅ **Homography Dataset Generator**: Generates synthetic **homography pairs** with controlled perturbations, distortions, and ground-truth homography matrices.  
✅ **Preprocessing Pipeline**: **Glare suppression, noise reduction, feature enhancement, and image normalization** to optimize images for deep learning.  
✅ **Deep Learning Compatibility**: Benchmarked using **HomographyNet**, **ORB**, and **SIFT**.  

---

## **Dataset Structure**
The dataset is structured into four main folders:

📂 **Raw Data**  
Contains the original high-resolution **640×512** images in **.tiff format**, categorized by cleanliness, capture time, and camera angle.  
- `Clean PV/` – Clean panels  
- `Soiled_1/` – Soiled for 1 day  
- `Soiled_2/` – Soiled for 2 days  
- `Soiled_3/` – Soiled for 3 days  
- `Soiled_4/` – Soiled for 4 days  
Each cleanliness folder contains **subfolders** organized by **time-of-day, camera inclination, and height**.  

📂 **Preprocessed Data**  
Processed images **(320×256 resolution)** with noise reduction, glare suppression, and contrast enhancement.  

📂 **Homography Pairs**  
Contains image pairs for homography estimation:
- `original_patch/` – Reference patch  
- `warped_patch/` – Distorted patch  
- `homography_matrix.npy` – Ground-truth homography transformation  
- `metadata.txt` – Image metadata  

📂 **Code**  
Contains scripts for **preprocessing, dataset generation, and homography estimation**:  
- `preprocess.py` – Applies preprocessing pipeline (denoising, glare removal, feature enhancement).  
- `datagen.py` – Generates homography pairs with controlled perturbations.  
- `data_split.py` – Splits dataset into training, validation, and test sets (50-25-25 split).  

---

## **Installation & Usage**
### **1️⃣ Clone the Repository**
```bash
git clone https://github.com/SolarTherm-HG/Dataset.git
cd Dataset
```

### **2️⃣ Install Dependencies**
Ensure you have Python **3.8+** and install required packages:
```bash
pip install -r requirements.txt
```

### **3️⃣ Preprocess Raw Images**
To apply the preprocessing pipeline (denoising, glare suppression, feature enhancement):
```bash
python preprocess.py --input_folder RawData --output_folder PreprocessedData
```

### **4️⃣ Generate Homography Pairs**
To create synthetic homography pairs:
```bash
python datagen.py --input_folder PreprocessedData --output_folder HomographyPairs
```

### **5️⃣ Split Dataset**
To prepare the dataset for deep learning:
```bash
python data_split.py --input_folder HomographyPairs --output_folder DatasetSplits
```

---

## **Benchmarking & Validation**
### **Feature-Based Homography Estimation**
We tested SolarTherm-HG with **ORB and SIFT** feature detectors. The dataset showed **high inlier ratios**, confirming its suitability for feature-based homography estimation.  
📈 **Results:** ORB consistently achieved **inlier ratios between 0.92 and 0.98**, while SIFT ranged between **0.55 and 0.83**.

### **Deep Learning Performance**
HomographyNet was trained on SolarTherm-HG, achieving a **Mean Average Corner Error (MACE) reduction from 16.65 px to 9.6 px over five days**, confirming its value for deep learning applications.

---

## **Use Cases**
🔹 **Deep Learning for Homography Estimation** – Training neural networks for **thermal image alignment and transformation**.  
🔹 **PV System Fault Detection** – Identifying **thermal anomalies and inefficiencies** in solar panels.  
🔹 **Feature Matching & Spatial Calibration** – Benchmarking **ORB, SIFT, and deep learning-based approaches**.  
🔹 **Thermal Image Preprocessing Research** – Evaluating **glare suppression, noise reduction, and feature enhancement techniques**.  

---

## **Contributing**
We welcome contributions to improve the dataset and codebase!  
To contribute:
1. Fork the repository.
2. Create a new branch (`feature-xyz`).
3. Commit changes (`git commit -m "Added new feature"`).
4. Push to your fork (`git push origin feature-xyz`).
5. Open a pull request.

For issues or suggestions, open a **GitHub Issue**.

---

## **Citation**
If you use SolarTherm-HG in your research, please cite:
```bibtex
@article{yaqoob2025solartherm,
  title={SolarTherm-HG: A High-Resolution Thermal Dataset for Advancing Deep Learning Models in Photovoltaic Homography},
  author={Yaqoob, Mohammed and Ansari, Mohammed Yusuf and Pillai, Dhanup Somasekharan and Flushing, Eduardo Feo},
  journal={Scientific Data},
  year={2025},
  doi={10.7910/DVN/E4OXHQ}
}
```

---

## **Acknowledgments**
This dataset was developed at **Carnegie Mellon University-Qatar** and **Qatar Environment and Energy Research Institute (QEERI)**, supported by the **AICC grant AICC04-0715-210006** from the **Qatar National Research Fund**.

For questions, contact: **[yansari@andrew.cmu.edu](mailto:yansari@andrew.cmu.edu)**  
 
