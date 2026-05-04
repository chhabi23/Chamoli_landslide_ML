# Chamoli Landslide Susceptibility Mapping

## Overview

This project performs landslide susceptibility mapping for the Chamoli district (Uttarakhand, India) using machine learning models.
The workflow integrates geospatial raster data and landslide inventory points to generate a high-resolution susceptibility map.

The pipeline includes:

* Feature extraction from raster datasets
* Spatial cross-validation
* Model training (Random Forest & XGBoost)
* Evaluation using AUROC and F1-score
* Pixel-wise prediction to generate a susceptibility GeoTIFF

---

## 🚀 Run Instantly (Google Colab)

Click below to run the notebook without any setup:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1p2S8NDlOSD6uG5las51AsvlT2cLCTOOD)


---

## 📂 Dataset Requirements

Before running the notebook, upload the following files into the Colab environment:

### 1. Raster Layers (`.tif`)

* slope
* aspect
* TWI
* NDVI
* InSAR velocity (optional)
* InSAR coherence (optional)

### 2. Landslide Inventory (`.shp`)

Shapefile containing:

* latitude
* longitude
* landslide label (1 = presence, 0 = absence)

> Ensure all raster layers are aligned (same CRS, resolution, and extent).

---

## ⚙️ Methodology

### Models Used

* Random Forest
* XGBoost

### Validation Strategy

* Spatial GroupKFold (5 folds)

### Feature Sets

* **Run 1:** Slope, Aspect, TWI, NDVI
* **Run 2:** + InSAR (velocity, coherence)

---

## 📊 Results Summary

| Model            | AUROC    | F1 Score |
| ---------------- | -------- | -------- |
| RF — No InSAR    | 0.73     | 0.56     |
| RF — With InSAR  | 0.51     | 0.12     |
| XGB — No InSAR   | 0.70     | 0.59     |
| XGB — With InSAR | **0.77** | **0.63** |

**Best Model:** XGBoost with InSAR features

---

## 🗺️ Outputs

Generated files:

* `susceptibility_map_30m.tif` → Final landslide susceptibility map
* `feature_importance.png` → Feature importance visualization
* `comparison_chart.png` → Model comparison
* `susceptibility_maps.png` → Visual output maps

---

## ▶️ How to Run

1. Open the notebook in Google Colab
2. Upload required raster and shapefile data
3. Run all cells sequentially

---

## 📦 Installation (Local - Optional)

```bash
pip install -r requirements.txt
```

> Note: Local execution may require proper setup of GDAL/PROJ dependencies.

---

## ⚠️ Notes

* Google Colab is recommended due to geospatial dependency compatibility
* Raster alignment is required for accurate predictions
* InSAR data coverage may reduce dataset size

---

## 📈 Key Insights

* InSAR features significantly improved XGBoost performance
* Random Forest struggled with reduced data after InSAR filtering
* NDVI and TWI were strong predictors in the absence of InSAR

---

## 📌 Project Structure

```
├── chamoli_landslide_susceptibility.ipynb
├── requirements.txt
```

---

## 📄 License

This project is for academic and research purposes.

---

## 👤 Author

Chhabi Tiwari
