# Image Denoising Using Convolutional Autoencoders 

## Objective
To recover clean grayscale images from their noisy counterparts by training convolutional autoencoder models on paired noisy and clean images.

## Dataset Description
- Grayscale images of size **28 × 28**
- Pixel intensities scaled to the range **[0, 1]**
- Artificial noise added to generate corrupted images
- Training data consists of **(noisy image, ground-truth image)** pairs

## Model Architectures

### Model 1: Basic CNN Autoencoder (MSE-Based)
- Lightweight encoder–decoder convolutional network
- Encoder uses **Conv2D layers followed by MaxPooling**
- Decoder reconstructs images using **UpSampling and Conv2D**
- Optimization objective: **Mean Squared Error (MSE)**

**Results**
- PSNR: **20.63 dB**
- SSIM: **0.7554**

### Model 2: CNN Autoencoder with Hybrid Loss (MSE + SSIM)
- Autoencoder with an additional convolution layer in the latent space
- Loss function combines pixel-wise and structural similarity terms:

where **α = 0.8** and **β = 0.2**

- Training stabilized using **Early Stopping** and **ReduceLROnPlateau**

**Results**
- PSNR: **20.80 dB**
- SSIM: **0.7771**

### Model 3: Deep CNN Autoencoder with Combined Loss
- Deep encoder with multiple convolutional stages  
*(filter progression: 32 → 64 → 128)*
- Decoder mirrors the encoder structure using **UpSampling layers**
- Trained using the same **MSE + SSIM** combined loss

**Results**
- PSNR: **22.70 dB**
- SSIM: **0.8371**

## Performance Metrics
- **Peak Signal-to-Noise Ratio (PSNR)** for reconstruction fidelity
- **Structural Similarity Index Measure (SSIM)** for perceptual similarity

## Key Findings
- Incorporating **SSIM into the loss function** improves visual quality
- Increasing network depth enhances the model’s ability to learn spatial details
- The **deep convolutional autoencoder** delivers the strongest denoising results among all models

## Documentation
The accompanying report provides a comprehensive explanation of the model architectures, loss functions, experimental setup, and performance evaluation.
