# 03 — Deep Learning

<div align="center">

[![Deep Learning](../assets/deep_learning_banner.png)](../README.md)

</div>

> My notes from the Deep Learning sessions of the Pupilica AI Bootcamp.

---

## What's in this folder

| File / Resource | Action / Type | Description |
|:---|:---|:---|
| `Deep_Learning_Practice.ipynb` | [![Practice Notebook](https://img.shields.io/badge/Jupyter-Practice-blue?logo=jupyter&style=flat-square)](./Deep_Learning_Practice.ipynb) | Exercises covering ANN digit classification (MNIST) and RNN sentiment analysis |
| `Deep_Learning_Training.ipynb` | [![Training Notebook](https://img.shields.io/badge/Jupyter-Training-orange?logo=jupyter&style=flat-square)](./Deep_Learning_Training.ipynb) | Comprehensive training notebook covering CNN image recognition (CIFAR-10) and RNN architectures |

---

## Topics Covered & Architectures

### 1. Artificial Neural Networks (ANN)
Fully connected networks modeled on biological neural connections. Core concepts include:
- **Forward Propagation**: Taking inputs $x$, computing the weighted sum at a neuron, adding a bias $b$, and passing through an activation function $\sigma$:
  $$z = w^T x + b$$
  $$a = \sigma(z)$$
- **Activation Functions**:
  - **ReLU (Rectified Linear Unit)**: Replaces negative values with zero, introducing sparsity and mitigating the vanishing gradient problem:
    $$\text{ReLU}(z) = \max(0, z)$$
  - **Sigmoid**: Compresses output to probability range $(0, 1)$ (ideal for binary classification):
    $$\sigma(z) = \frac{1}{1 + e^{-z}}$$
  - **Softmax**: Converts vector outputs into probability distributions that sum to 1 (essential for multi-class classification).
- **Backpropagation & Learning**: Calculates loss function gradients with respect to weights using the **Chain Rule**, adjusting weights backward through network layers using the **Adam** or **SGD** optimizer.

### 2. Convolutional Neural Networks (CNN)
Specially designed for grid-like topology inputs such as images, utilizing spatial correlation:
- **Convolution Operations**: Sliding kernel filters over the input image matrix to extract localized visual features (edges, textures, shapes), outputting **Feature Maps**.
- **Pooling (Max Pooling)**: Extracts the maximum value within a window (e.g. $2 \times 2$), reducing spatial dimensions (width, height) to lower computational overhead and introduce translation invariance.
- **Flattening**: Transforming 2D/3D feature maps into a 1D vector to feed into Dense fully-connected layers for final classification (e.g., CIFAR-10 image classes).

### 3. Recurrent Neural Networks (RNN)
Designed to handle sequential data (such as time series or natural language text) by maintaining an internal memory state:
- **Hidden State ($h_t$)**: The recurrent unit processes the input $x_t$ at step $t$ while referencing the prior step's hidden state $h_{t-1}$:
  $$h_t = \tanh(W_{hh} h_{t-1} + W_{xh} x_t + b_h)$$
- **Sequential Sentiment Classification**: Mapping tokenized reviews to indices, padding inputs to a fixed length (`pad_sequences`), embedding words in a dense space, and passing sequences through simple RNN cells to a final binary classification sigmoid unit.
- **Vanishing Gradient Problem**: Traditional RNNs suffer from vanishing gradients over long sequences because weights are multiplied repeatedly during backpropagation through time. This is solved by using gated architectures like **LSTMs** and **GRUs**.

---

## Key Things I Want to Remember
- Standard Dense layers ignore spatial structures in image inputs (flattening an image destroys pixel relationships). CNNs preserve spatial structure using local receptive fields.
- Neural networks are sensitive to input scale. Always normalize image pixel values from $[0, 255]$ to $[0, 1]$ before feeding them to ANN/CNN layers.
- Early Stopping callbacks monitor validation loss and halt training when validation performance plateaus, preventing overfitting.

---

[← Machine Learning](../02-Machine-Learning/) &nbsp;|&nbsp; [Next: NLP →](../04-NLP/)
