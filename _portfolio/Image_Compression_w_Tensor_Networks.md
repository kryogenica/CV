---
title: "Image Compression via Tensor Network"
excerpt: "Comprehensive guide to using Matrix Product States for efficient image compression, leveraging TensorFlow and the Fashion-MNIST dataset. <br/><img src='/images/tensor-network-compression.png' width='50%'>"
collection: portfolio
---

Google Colab notebook linked below is about using **Matrix Product States (MPS)** for lossy image compression, based on a paper titled "[Tensor Networks for Image Compression](https://diposit.ub.edu/dspace/bitstream/2445/96365/1/TFG_Fis_Trujillo_Boque_Alex.pdf)" by Alex Trujillo Boque.
Here's a brief summary of the key points:

- **TensorFlow and Libraries**: It imports TensorFlow, Keras, and other helper libraries for data manipulation and visualization.
- **Fashion-MNIST Dataset**: The notebook uses the Fashion-MNIST dataset, which contains images of clothing items. These images are preprocessed by scaling pixel values from 0 to 255 down to a range of 0 to 1.
- **Image Preprocessing**: A small patch of an image is extracted to create a square image, which is a requirement for the MPS algorithm.
- **Tensor Transformation**: The notebook demonstrates how to transform the image into a rank 4 tensor, which is necessary for using TensorFlow's `tf.extract_image_patches` function.
- **Density Matrix**: It shows how to create a density matrix from the image data, which is used in the MPS compression process.

The notebook includes code cells with detailed comments explaining each step of the process, from loading and preprocessing the data to applying the MPS algorithm for image compression.

[Repository](https://colab.research.google.com/github/kryogenica/Image-compression-using-Matrix-Product-States/blob/master/Image_compression.ipynb#scrollTo=7BGIZ7mpctpj).

python libarires: itertools, tensorflow, numpy, matplotlib, math.
