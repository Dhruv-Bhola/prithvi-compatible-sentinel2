# 🌍 Prithvi EO 2.0 Sentinel-2 Time Series Generator

> Generate **Prithvi EO 2.0 compatible Sentinel-2 tensors** directly from the **Microsoft Planetary Computer**.

This repository provides an end-to-end pipeline for downloading, preprocessing, validating, and visualizing Sentinel-2 imagery to create inputs compatible with **IBM–NASA Prithvi EO 2.0** foundation models.

Instead of downloading large datasets manually, this notebook automatically retrieves Sentinel-2 imagery, selects the **6 spectral bands required by Prithvi EO 2.0**, constructs a **30-frame temporal sequence**, normalizes the data, and exports tensors ready for inference or fine-tuning.

---

# ✨ Features

- 🌍 Download Sentinel-2 Level-2A imagery
- 🛰️ Retrieve imagery directly from Microsoft Planetary Computer
- ☁️ Automatic cloud filtering
- 🌈 Uses only the **6 spectral bands required by Prithvi EO 2.0**
- 📅 Generate a fixed **30-frame temporal sequence**
- 📦 Export tensors in **(30, 6, 128, 128)** format
- 🔍 Automatic data validation
- 📈 RGB visualization of generated time series
- ⚡ Ready for inference and fine-tuning with Prithvi EO 2.0

---

# 📌 Output Format

The generated tensor has the following shape:

```text
(30, 6, 128, 128)
```

| Dimension | Description |
|------------|-------------|
| 30 | Temporal observations |
| 6 | Spectral bands required by Prithvi EO 2.0 |
| 128 × 128 | Spatial patch size |

---

# 🛰 Spectral Bands

This notebook downloads only the six Sentinel-2 bands required by **Prithvi EO 2.0**.

| Sentinel-2 Band | Description |
|-----------------|-------------|
| B02 | Blue |
| B03 | Green |
| B04 | Red |
| B08 | Near Infrared (NIR) |
| B11 | SWIR-1 |
| B12 | SWIR-2 |

No additional Sentinel-2 bands are processed.

---

# 📅 Temporal Processing

Prithvi EO 2.0 expects a fixed-length temporal sequence.

This pipeline automatically:

- Downloads Sentinel-2 observations
- Removes cloudy acquisitions
- Sorts imagery chronologically
- Generates exactly **30 temporal frames**
- Produces tensors with consistent dimensions

---

# 🗺 Data Source

Imagery is downloaded directly from

- Microsoft Planetary Computer
- Sentinel-2 Level-2A Collection

No local Sentinel-2 archive is required.

---

# 📦 Generated Dataset

Using this pipeline, I generated a public **Indian PASTIS Dataset** containing Prithvi EO 2.0 compatible Sentinel-2 tensors from multiple agricultural regions in India.

## 📥 Download Dataset

**Kaggle:**  
https://www.kaggle.com/datasets/dhruvbholaas/indian-pastis

### Included Locations

- Jind, Haryana
- Karnal, Haryana
- Nashik, Maharashtra
- Indore, Madhya Pradesh
- Additional agricultural locations across Madhya Pradesh

Every sample was generated using this notebook.

To generate data for a new location, simply modify:

```python
LATITUDE = ...
LONGITUDE = ...
START_DATE = "YYYY-MM-DD"
END_DATE = "YYYY-MM-DD"
```

The notebook automatically performs the remaining preprocessing steps and exports a Prithvi-compatible tensor.

---

# 🧠 Model Inference

The generated tensors were used for crop segmentation using fine-tuned **IBM–NASA Prithvi EO 2.0** models.

Available models include:

- ✅ Prithvi EO 2.0 + FCN
- ✅ Prithvi EO 2.0 + U-Net

Inference notebooks, trained weights, and additional projects are available on my Kaggle profile.

## 🔗 Kaggle Profile

https://www.kaggle.com/dhruvbholaas/

---

# 📁 Repository Structure

```text
.
├── Prithvi_TimeSeries_Generator.ipynb
└── README.md
```

---

# 🚀 Workflow

```text
AOI Selection
      │
      ▼
Search Sentinel-2 Images
      │
      ▼
Cloud Filtering
      │
      ▼
Download 6 Spectral Bands
      │
      ▼
Temporal Sorting
      │
      ▼
Generate 30 Time Frames
      │
      ▼
Normalization
      │
      ▼
Validation
      │
      ▼
Tensor Export
      │
      ▼
Visualization
```

---

# 📊 Visualization

The notebook generates RGB visualizations for every temporal observation to verify:

- Temporal consistency
- Cloud removal
- Spatial alignment
- Data quality

before exporting tensors for deep learning applications.

---

# 🎯 Applications

This pipeline can be used for:

- Crop Mapping
- Crop Classification
- Semantic Segmentation
- Land Cover Mapping
- Change Detection
- Earth Observation Research
- Foundation Model Fine-Tuning
- Prithvi EO 2.0 Inference
- Agricultural Monitoring
- Geospatial Deep Learning

---

# 🛠 Requirements

- Python 3.10+
- PyTorch
- NumPy
- Rasterio
- Planetary Computer SDK
- pystac-client
- stackstac
- matplotlib
- xarray

---

# ⭐ Why this Repository?

Most available Prithvi EO 2.0 tutorials assume that Sentinel-2 tensors are already prepared.

This repository focuses on the **data preparation stage**, providing a complete pipeline that converts raw Sentinel-2 imagery into **Prithvi EO 2.0 compatible tensors** with:

- 6 spectral bands
- 30 temporal observations
- Standardized tensor dimensions
- Automated preprocessing
- Cloud filtering
- Ready-to-use deep learning inputs

With only four parameters—

- Latitude
- Longitude
- Start Date
- End Date

—you can generate Prithvi EO 2.0 compatible Sentinel-2 tensors for **any location worldwide**.

---

# 🔖 Keywords

Prithvi EO 2.0 • IBM NASA • Sentinel-2 • Microsoft Planetary Computer • Remote Sensing • Foundation Model • Earth Observation • Time Series • Crop Mapping • Semantic Segmentation • GeoAI • Satellite Imagery • Deep Learning • PyTorch • Tensor Generation • Agricultural Monitoring

---

## ⭐ If you find this project useful, please consider giving it a star!

Contributions, suggestions, and improvements are always welcome.
