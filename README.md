# Automated Flood Mapping from Satellite Imagery

![Project Banner](/project.png))

---

## 🎯 Problem Statement

- Floods are among the most frequent and destructive natural disasters, with their intensity increasing due to climate change.
- Traditional optical satellites, which are like cameras in space, are often rendered useless by the heavy cloud cover that accompanies storms—precisely when flood data is most critical.
- There is a crucial need for a rapid, reliable, and automated system to map flood extents to aid in emergency response and damage assessment.

---

## 💡 Solution

To overcome the limitations of optical imagery, this project implements an end-to-end deep learning pipeline that uses **Synthetic Aperture Radar (SAR)** data from the **Sentinel-1 satellite**. SAR has the critical advantage of penetrating clouds, smoke, and darkness, enabling all-weather monitoring.

It involves:
1.  **Data Preparation:** Fetching and preprocessing SAR images (VV & VH polarizations) from a large-scale public dataset.
2.  **Deep Learning Model:** Utilizing a **U-Net architecture**, a powerful Convolutional Neural Network (CNN) specifically designed for precise image segmentation, to classify each pixel as either "Flood" or "No Flood".
3.  **Training & Output:** Training the model to generate accurate binary flood masks that can be used for visualization and analysis.


---

## 🗂️ Dataset

We use the **ETCI-2021 Flood Detection Dataset**, a comprehensive, large-scale dataset hosted on the Hugging Face Hub.

* **Source:** `blanchon/ETCI-2021-Flood-Detection` via Hugging Face Hub
* **Data Type:** Sentinel-1 SAR Images
* **Resolution:** 256x256 pixels per tile
* **Channels:** VV (Vertical Transmit, Vertical Receive) and VH (Vertical Transmit, Horizontal Receive) polarizations
* **Labels:** Pixel-perfect binary ground truth masks for flooded areas.

---

## 🧠 Model Architecture

The core of our project is the **U-Net model**, renowned for its effectiveness in biomedical and satellite image segmentation.

* **Encoder (Contracting Path):** Captures the context of the image (the "what") by downsampling through a series of convolutional and max-pooling layers.
* **Decoder (Expanding Path):** Rebuilds the image to its original resolution to pinpoint the exact location of features (the "where") using transposed convolutions.
* **Skip Connections:** The key innovation of U-Net. These connections pass fine-grained details from the encoder to the decoder, preventing data loss and resulting in highly precise segmentation boundaries.



---

## ⚙️ Setup and Installation

This project is designed to run in a Google Colab environment.

1.  **Clone the Repository (Optional):**
    ```bash
    git clone <your-repo-url>
    cd <your-repo-directory>
    ```
2.  **Install Dependencies:** The main training script ([`flood_mapping.ipynb`](flood_mapping.ipynb)) includes the necessary installation command at the top.
    ```python
    !pip install -q tensorflow huggingface_hub Pillow numpy scikit-learn matplotlib datasets
    ```
3.  **Hugging Face Authentication:** You will need a Hugging Face account and an Access Token with at least 'read' permissions to download the dataset.
    * Get your token from `Hugging Face Website -> Your Profile -> Settings -> Access Tokens`.

> The entire process, from data loading to training and visualization, is contained within the primary notebook/script.

---

## 📊 Sample Results

- ![1](/sample_results/1.png)
- ![2](/sample_results/2.png)
- ![3](/sample_results/3.png)