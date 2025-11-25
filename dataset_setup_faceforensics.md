# FaceForensics++ Dataset Preparation Guide (300-Sample Version)

This guide documents how to download, organize, label, and prepare a reduced 300-video subset of the FaceForensics++ dataset for statistical analysis (PCA, LDA, Logistic Regression, QDA, KNN).  
No deep learning pipelines are used.

---

## 1. Project Goal

The purpose of this setup is to create a dataset with:

- A balanced binary target (real vs fake)
- Enough samples for:
  - PCA dimensionality analysis  
  - Parametric vs non-parametric classifier comparison  
  - Variance exploration across manipulation methods  

**Target Total: 300 videos**

### Dataset Distribution

| Class Type | Subcategory | Count |
|-----------|-------------|-------|
| Real | Original sequences | 100 |
| Fake | Deepfakes | 50 |
| Fake | Face2Face | 50 |
| Fake | FaceSwap | 50 |
| Fake | NeuralTextures | 50 |
| **Total** | | **300** |

This supports:

- Binary classification (real vs fake)
- Multiclass classification by manipulation type

---

## 2. Expected Folder Structure

After downloading, files should be arranged like this:

<img width="693" height="476" alt="image" src="https://github.com/user-attachments/assets/5763ae14-47c1-4dcb-9864-1313c387a666" />


---

## 3. Requirements

- Python 3.9+  
- The dataset download script (`faceforensics_download_v4.py`)  
- tqdm package  

Install tqdm if needed:

```bash 
pip install tqdm
mkdir -p ~/faceforensics_data

```
## 5. Download Commands (Compression = c23)
Run each command separately.

Download 100 original videos
```bash 
python faceforensics_download_v4.py \
    ~/faceforensics_data \
    -d original \
    -c c23 \
    -t videos \
    --num_videos 100 \
    --server EU2
```
Download manipulated videos
```bash 
python faceforensics_download_v4.py \
    ~/faceforensics_data \
    -d Deepfakes \
    -c c23 \
    -t videos \
    --num_videos 50 \
    --server EU2
```
```bash 
python faceforensics_download_v4.py \
    ~/faceforensics_data \
    -d Face2Face \
    -c c23 \
    -t videos \
    --num_videos 50 \
    --server EU2
```
```bash 
python faceforensics_download_v4.py \
    ~/faceforensics_data \
    -d FaceSwap \
    -c c23 \
    -t videos \
    --num_videos 50 \
    --server EU2
```
```bash 
python faceforensics_download_v4.py \
    ~/faceforensics_data \
    -d NeuralTextures \
    -c c23 \
    -t videos \
    --num_videos 50 \
    --server EU2
```
## 6. Verify Download Count
Expected: ~300 videos
```bash
find ~/faceforensics_data -name "*.mp4" | wc -l
```

