# Lorenz Attractor Based RGB Image Encryption and Decryption in Python

## Project Overview

This project implements RGB image encryption and decryption using the **Lorenz chaotic attractor** in Python. The Python implementation is used as a reference for the corresponding SystemVerilog implementation.

The Lorenz system generates three chaotic variables, **X, Y, and Z**, which are used as encryption keys for the three RGB channels.

The implementation demonstrates Lorenz-based XOR encryption and decryption for:

1. Lorenz attractor generation
2. X, Y, and Z chaotic sequence generation
3. 16-bit Q8.8 fixed-point conversion
4. 8-bit RGB key generation
5. RGB image encryption
6. RGB image decryption
7. Pixel-by-pixel and SHA-256 verification

The same Lorenz-generated keys are used for both encryption and decryption.

## Repository Structure

```text
Lorenz-RGB-Image-Encryption/
│
├── README.md
├── Lorenz_RGB_Encryption.ipynb
│
├── input/
│   └── test_image.png
│
└── output/
    ├── encrypted_image.png
    ├── decrypted_image.png
    ├── lorenz_attractor.png
    └── test_vectors.csv
```

## How to Run

### Google Colab

Open Lorenz_RGB_Encryption.ipynb.
Open the notebook in Google Colab.
Run the code from the beginning.
When prompted, upload an RGB test image.
The image is converted to an RGB NumPy array.
The Lorenz attractor generates the X, Y, and Z chaotic sequences.
The Lorenz values are converted into 16-bit Q8.8 fixed-point values.
The upper 8 bits are XORed with the lower 8 bits to generate 8-bit keys.
X is used as the Red-channel key.
Y is used as the Green-channel key.
Z is used as the Blue-channel key.
The RGB image is encrypted using XOR.
The encrypted image is decrypted using the same keys.
Verification results are displayed.
The generated images and test-vector file are saved in the output directory.

## Lorenz System
The Lorenz chaotic system is defined as:

dx/dt = σ(y - x)


dy/dt = x(ρ - z) - y


dz/dt = xy - βz

The parameters used are:

σ  = 10
ρ  = 28
β  = 8/3

Initial conditions:

X0 = 1
Y0 = 1
Z0 = 1

Time step:

dt = 0.01

## Key Generation

The Lorenz floating-point values are converted into 16-bit Q8.8 fixed-point values.

16-bit value = round(Lorenz value × 256)

The 16-bit value is divided into upper and lower 8-bit values:

Upper 8 bits
Lower 8 bits

The final 8-bit key is generated using:

Key = Upper 8 bits XOR Lower 8 bits

The RGB key mapping is:

Lorenz Variable	RGB Channel
X	Red
Y	Green
Z	Blue

## Output Files

The output/ directory contains:

encrypted_image.png
decrypted_image.png
lorenz_attractor.png
test_vectors.csv

### Test Vectors

A CSV file containing the encryption test vectors is generated.

Each row contains information related to:

Pixel index
Lorenz X value
Lorenz Y value
Lorenz Z value
16-bit X value
16-bit Y value
16-bit Z value
8-bit Red key
8-bit Green key
8-bit Blue key
Original RGB values
Encrypted RGB values
Decrypted RGB values
Results
 
## Results

Test	Result
Lorenz attractor generation	PASS
X, Y, Z sequence generation	PASS
RGB key generation	PASS
RGB image encryption	PASS
RGB image decryption	PASS

Image verification:

Verification	Result
Different pixels	0
Maximum difference	0
Ciphertext generation	PASS
Decryption check	PASS
SHA-256 check	PASS

