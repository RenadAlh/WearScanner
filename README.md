# WearScanner 👕🔍

**A CNN-based fashion item classifier that pairs each prediction with automatic style feedback** ; vibe, recommended occasion, and accessory ideas. Trained on Fashion-MNIST, WearScanner predicts a clothing category from a 28×28 grayscale image and returns a short styling tip alongside the prediction.

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10%2B-orange?logo=tensorflow&logoColor=white)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/<your-username>/<your-repo>/blob/main/WearScanner-AISD.ipynb)

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

## Usage

Open `WearScanner.ipynb` in Jupyter, JupyterLab, or Google Colab and run all cells top to bottom. The notebook:

1. Loads Fashion-MNIST and explores/visualizes sample images
1. Preprocesses and re-splits the data 70/30
1. Builds and trains the CNN
1. Logs metrics to TensorBoard
1. Evaluates on the test set (loss, accuracy, precision, recall)
1. Runs an interactive demo — upload a clothing image and get a prediction + style tip

> The image-upload demo cell uses `google.colab.files.upload()`, so that specific cell only works in Colab. Everything else runs in any standard Jupyter environment.

## Dataset

[Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist); 70,000 grayscale 28×28 images across 10 clothing categories, loaded via `tensorflow.keras.datasets.fashion_mnist`. No manual download needed.

![Sample dataset grid](assets/Data%20Samples.png)

*Sample Fashion-MNIST images across all 10 target categories.*

| **Label** | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|:---------:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Class** | T-shirt/top | Trouser | Pullover | Dress | Coat | Sandal | Shirt | Sneaker | Bag | Ankle boot |


## Conclusion

WearScanner achieved strong performance on the Fashion-MNIST test set (92.92% accuracy, 93.13% precision, and 92.92% recall), demonstrating good generalization and reliability across clothing categories. As bonus work, the notebook also includes an interactive demo providing real-time style feedback.

## References

1. Han Xiao, Kashif Rasul, and Roland Vollgraf. *Fashion-MNIST: A Novel Image Dataset for Benchmarking Machine Learning Algorithms.* arXiv, 2017.
1. TensorFlow Team. *TensorBoard.* https://www.tensorflow.org/tensorboard, 2025.
1. StackExchange Community. *Overfitting in Neural Network.* https://stats.stackexchange.com/questions/292700/overfitting-in-neural-network. Accessed 2025-11-21.
1. Pushparaja Murugan. *Implementation of Deep Convolutional Neural Network in Multi-Class Categorical Image Classification.* arXiv, 2018.
1. Olivia Nocentini, Jaeseok Kim, Muhammad Zain Bashir, and Filippo Cavallo. *Image Classification Using Multiple Convolutional Neural Networks on the Fashion-MNIST Dataset.* Sensors (Basel, Switzerland), 22, 2022.

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
