# MNIST Handwritten Digit Generation using GAN

## 📌 Project Overview

This project implements a **Generative Adversarial Network (GAN)** using **TensorFlow and Keras** to generate handwritten digit images similar to the MNIST dataset.

The project was developed as part of my **academic assignment projects** while learning the fundamentals of **Deep Learning and Generative AI**.

The main objective was to understand how a GAN works by building and training both a **Generator** and a **Discriminator**, and observing how they learn through adversarial training.

---

## 🎯 Objectives

- Understand the fundamental architecture of a GAN.
- Preprocess and normalize the MNIST dataset.
- Build a Generator network to create synthetic handwritten digits.
- Build a Discriminator network to distinguish between real and generated images.
- Train the Generator and Discriminator using adversarial learning.
- Visualize generated images.
- Evaluate the Discriminator's ability to distinguish real images.
- Analyze the current limitations and identify areas for future improvement.

---

## 📊 Dataset

The project uses the **MNIST handwritten digit dataset**.

- Training images: 60,000
- Test images: 10,000
- Image size: 28 × 28 pixels
- Number of classes: 10 (digits 0–9)
- Image type: Grayscale

The pixel values were normalized from:

```text
0 – 255

to:

-1 - +1

This normalization is suitable for the Generator's tanh output activation.
```
---

## 🏗️ GAN Architecture

The GAN consists of two neural networks:

### Generator

The Generator takes a random noise vector of 100 dimensions and transforms it into a 784-dimensional representation of a 28 × 28 image.

```
Random Noise (100)
        ↓
Dense (256)
        ↓
LeakyReLU
        ↓
Dense (512)
        ↓
LeakyReLU
        ↓
Dense (1024)
        ↓
LeakyReLU
        ↓
Dense (784)
        ↓
tanh
        ↓
28 × 28 Image

```

### Discriminator

```
The Discriminator receives a flattened 784-dimensional image and predicts whether the image is real or generated.

Input Image (784)
        ↓
Dense (512)
        ↓
LeakyReLU
        ↓
Dense (256)
        ↓
LeakyReLU
        ↓
Dense (1)
        ↓
Sigmoid
        ↓
Real / Fake Prediction
```
---

## ⚙️ Training Configuration

| Parameter           |                Value |
| ------------------- | -------------------: |
| Dataset             |                MNIST |
| Noise Dimension     |                  100 |
| Batch Size          |                   64 |
| Training Iterations |               10,000 |
| Optimizer           |                 Adam |
| Learning Rate       |               0.0002 |
| Beta 1              |                  0.5 |
| Loss Function       | Binary Cross-Entropy |
| Generator Output    |                  784 |
| Image Size          |              28 × 28 |

---

## 🔄 Training Process

The GAN training process follows these steps:

Select a batch of real MNIST images.
Generate random noise vectors.
Use the Generator to create fake images.
Train the Discriminator using:
Real images → label 1
Fake images → label 0
Freeze the Discriminator during Generator training.
Train the Generator through the combined GAN.
Use misleading labels (1) so the Generator learns to produce images that can be classified as real.
Repeat the process for 10,000 iterations.

---

## 🖼️ Generated Images

The trained Generator was able to produce images with MNIST-like handwritten digit patterns.

The generated samples demonstrate that the Generator learned some characteristics of the training data, although the quality and consistency of the generated digits can still be improved.

---

## 📈 Model Evaluation

As part of the evaluation, the Discriminator was tested using the first 100 unseen images from the MNIST test dataset (X_test[:100]).

The current results were:
```
Real Image Accuracy: 52%
Average Real Image Score: 0.5274
```
The results indicate that the current Discriminator has difficulty clearly distinguishing between real and generated images and frequently produces predictions close to the decision boundary.

This is an important limitation of the current implementation and provides an opportunity for further experimentation and improvement.

---

## 🔍 Observations
The Generator successfully learned to produce MNIST-like patterns.
The generated images show characteristics of handwritten digits.
The Discriminator currently struggles to confidently distinguish real images from generated images.
The training loss fluctuates during adversarial training, which is common in GAN-based models.
The current results demonstrate the basic working principles of GANs while also highlighting the challenges involved in stabilizing GAN training.

---

## 🚀 Future Improvements

The current implementation is an academic learning project, and there is scope for further improvement.

Future work may include:

Increasing the number of training iterations.
Experimenting with different batch sizes.
Tuning the learning rate and optimizer parameters.
Improving the Generator architecture.
Improving the Discriminator architecture.
Adding Batch Normalization and Dropout where appropriate.
Experimenting with different GAN architectures.
Evaluating generated images using additional metrics.
Improving the quality and consistency of generated digits.
Investigating techniques for improving GAN training stability.

I intend to continue improving the model and addressing the current accuracy and image-quality concerns as part of my future learning and experimentation.
---
---

## 🛠️ Technologies Used
Python
TensorFlow
Keras
NumPy
Matplotlib
Jupyter Notebook

---

## 📚 Learning Outcomes

Through this project, I gained practical understanding of:

Generative Adversarial Networks
Generator and Discriminator architectures
Random noise generation
Image normalization
Dense neural networks
LeakyReLU activation
Sigmoid and Tanh activations
Binary Cross-Entropy
Adam optimization
Adversarial training
Model evaluation
GAN training challenges

---

## 🎓 Academic Context

This project was developed as part of my academic assignment projects to gain hands-on experience with Deep Learning and Generative AI concepts.

The project focuses not only on achieving model performance, but also on understanding the underlying architecture, training process, evaluation, and limitations of GANs.

The current results represent the state of the model during this academic implementation. Further experimentation and optimization are planned to address the identified performance concerns.

---

## 👩‍💻 Author

Apeetha Srinivasan

Aspiring Data Scientist | Machine Learning & Deep Learning Enthusiast

---

## ⭐ Future Direction

This project is part of my ongoing learning journey in Data Science, Machine Learning, Deep Learning, and Generative AI.

I plan to revisit this implementation and experiment with architectural and training improvements to achieve better image quality and more reliable real/fake classification.
