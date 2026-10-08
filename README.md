# StyleGAN-Style CIFAR-10 Image Generator (TensorFlow)

This repository contains a **from-scratch implementation** of a compact, StyleGAN-inspired generative network trained on the color **CIFAR-10 dataset** using TensorFlow and Keras. This project explores advanced generative modeling architectures, mapping noise vectors to an intermediate style space to perform style mixing, attribute control, and smooth latent space interpolation.

---

## Core Theoretical Concepts

### 1. What is a GAN?
A **Generative Adversarial Network (GAN)** is a class of machine learning frameworks designed by Ian Goodfellow and his colleagues in 2014. It consists of two neural networks contesting with each other in a zero-sum game framework:

*   **The Generator ($G$):** Learns to generate plausible data. Its objective is to create fake images that are indistinguishable from the training dataset.
*   **The Discriminator ($D$):** Learns to distinguish between real data from the training set and fake data produced by the Generator.

### 2. Main Types of GANs
Since their inception, GAN architectures have evolved significantly to solve training instability, image resolution limits, and feature control issues:

*   **Vanilla GAN:** The original architecture using fully connected layers. It is highly prone to training instability and mode collapse.
*   **Deep Convolutional GAN (DCGAN):** Replaced fully connected layers with spatial convolutions and convolutional transpose layers.
*   **Conditional GAN (cGAN):** Directs the generation process by conditioning both the generator and discriminator on class labels.
*   **Wasserstein GAN (WGAN):** Implements the Wasserstein-1 distance to construct a smoother loss landscape.
*   **CycleGAN:** Utilizes a cycle-consistency loss term to perform unpaired image-to-image translation.
*   **StyleGAN:** Alters the generator architecture completely to treat the latent vector as an explicit "style" modifier at every resolution level.

### 3. What is StyleGAN?
Introduced by NVIDIA, **StyleGAN** radically changes how the generator architecture synthesizes images by processing the latent vector through a separate network called the **Mapping Network**.

#### Key Architectural Innovations:
1.  **Mapping Network ($f: z \to w$):** An 8-layer fully connected network transforms a traditional noise vector into an intermediate style space $w$. This disentangles the latent space.
2.  **Learned Constant Input:** The traditional input layer is discarded. The generator begins using a fixed, learned constant tensor block.
3.  **Adaptive Instance Normalization (AdaIN):** Modulates the spatial feature maps at every convolutional stage using the intermediate style vector $w$.
4.  **Stochastic Noise Injection:** Explicit Gaussian noise maps are added per-layer to add minor, non-semantic textures like fine details.

### 4. Uses & Applications of StyleGAN
*   **Synthetic Data Generation:** Creating high-fidelity, anonymized image profiles (e.g., medical imaging synthesis).
*   **Data Augmentation:** Expanding sparse datasets to balance rare classes or features.
*   **Creative Asset Generation:** Facilitating rapid concept prototyping for video-game environments, digital restorations, and artwork.
