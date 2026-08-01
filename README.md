# WearScanner 👕🔍

**A CNN-based fashion item classifier that pairs each prediction with automatic style feedback** ; vibe, recommended occasion, and accessory ideas. Trained on Fashion-MNIST, WearScanner predicts a clothing category from a 28×28 grayscale image and returns a short styling tip alongside the prediction.

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10%2B-orange?logo=tensorflow&logoColor=white)
[![PDF Report](https://img.shields.io/badge/Documentation-PDF_Report-red?style=flat-square&logo=adobeacrobatreader&logoColor=white)](./WearScanner%20Report.pdf)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/<your-username>/<your-repo>/blob/main/WearScanner-AISD.ipynb)
[![License: Academic](https://img.shields.io/badge/License-Academic_Use_Only-4B5563?style=flat-square&logo=academia)](https://opensource.org/licenses/MIT)

</div>

## Overview

WearScanner is a CNN trained on Fashion-MNIST that does two things at once:

1. **Classifies** an input clothing image into one of 10 categories.
1. **Recommends** a short style tip for that category (occasion, accessory ideas, matching colors).

Data loading, model, training, evaluation, and an interactive demo in a single notebook: `WearScanner.ipynb`.

## Model Architecture

`WearScanner_CNN` has 3 convolutional blocks followed by 2 fully-connected layers:

|Block       |Layers                                                                     |
|------------|---------------------------------------------------------------------------|
|Conv Block 1|Conv2D(32, 3×3) → BatchNorm → MaxPool(2×2) → Dropout(0.25)                 |
|Conv Block 2|Conv2D(64, 3×3) → BatchNorm → MaxPool(2×2) → Dropout(0.25)                 |
|Conv Block 3|Conv2D(128, 3×3) → BatchNorm → Dropout(0.4)                                |
|FC Block    |Flatten → Dense(256) → BatchNorm → Dropout(0.5) → Dense(128) → Dropout(0.5)|
|Output      |Dense(10, softmax)                                                         |

- **Optimizer:** Adam (lr = 0.001)
- **Loss:** Sparse categorical crossentropy
- **Batch size:** 128
- **Epochs:** 50
- **Data split:** Split 70/30 (random_state=42)

## Results

Trained for 50 epochs on Fashion-MNIST (70/30 → 49,000 train / 21,000 test samples). 

Metrics below are from TensorBoard logs and final test-set evaluation.

## Training vs. Testing Performance

| **Metric**    | **Training Set** | **Testing Set** |
|:--------------|-----------------:|----------------:|
| **Loss**      | 13%              | 22%             |
| **Accuracy**  | 96%              | 92%             |
| **Precision** | 96%              | 93%             |
| **Recall**    | 96%              | 92%             |


## Final Test Set Results

| **Evaluation Metric** | **Value** |
|:----------------------|----------:|
| **Accuracy**          | 92.92%    |
| **Precision**         | 93.13%    |
| **Recall**            | 92.92%    |
| **Training Samples**  | 49,000    |
| **Testing Samples**   | 21,000    |

### TensorBoard plots

![TensorBoard metrics](assets/TensorBoard%20Metrics.png)

*Loss, accuracy, precision, and recall curves across the 50 training epochs, for both train and test runs.*

### Interactive demo output

![Demo Output](assets/Demo%20Output.png)


*Example run: uploaded image alongside the 28×28 preprocessed grayscale transform, predicted class (**DRESS**, 91.59% confidence), and generated style tip.*

## Usage Guide

The complete step-by-step execution guide is documented directly inside the notebook:

[![Open In Colab](https://img.shields.io/badge/Google_Colab-Open_Notebook-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)](YOUR_COLAB_NOTEBOOK_LINK_HERE)

>  **Quick Note:** The interactive image-upload demo cell uses `google.colab.files.upload()`, which is designed for **Google Colab**. All model architecture, training, TensorBoard logging, and evaluation cells run seamlessly in any standard Jupyter environment.

## Dataset

[Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist); 70,000 grayscale 28×28 images across 10 clothing categories, loaded via `tensorflow.keras.datasets.fashion_mnist`. No manual download needed.

![Sample dataset grid](assets/Data%20Samples.png)

*Sample Fashion-MNIST images across all 10 target categories.*

| **Label** | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|:---------:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Class** | T-shirt/top | Trouser | Pullover | Dress | Coat | Sandal | Shirt | Sneaker | Bag | Ankle boot |


## Conclusion

WearScanner achieved strong performance on the Fashion-MNIST test set (92.92% accuracy, 93.13% precision, and 92.92% recall), demonstrating good generalization and reliability across clothing categories. As bonus work, the notebook also includes an interactive demo providing real-time style feedback.

### 📄 Academic Documentation

[![Read Report](https://img.shields.io/badge/Read_Full_Report-WearScanner_Report.pdf-E10600?style=for-the-badge&logo=adobeacrobatreader&logoColor=white)](./WearScanner%20Report.pdf)

> * **Model Architecture:** CNN design, layer configurations, and activation choices.
> * **Performance & Metrics:** Detailed justification for Accuracy, Precision, Recall, and Cross-Entropy Loss.
> * **Training Analysis:** TensorBoard visualization, epoch tracking, and regularization insights.
> * **References:** Academic citations and dataset benchmarks.

## Team

<div align="left">

[![Renad Alharthi](https://img.shields.io/badge/Renad_Alharthi-renadalh-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/renadalh)

[![Aliyah Alabdali](https://img.shields.io/badge/Aliyah_Alabdali-AliyahAlabdali-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/AliyahAlabdali)

[![Rahaf Almalki](https://img.shields.io/badge/Rahaf_Almalki-RahafAlmalki-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/RahafAlmalki)

</div>

---

<div align="center">

Made with ❤️ by the WearScanner team

</div>
