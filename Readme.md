## Description

This project, implemented in a Jupyter notebook (`SE6003A1.ipynb`), demonstrates a complete cryptographic workflow on a plaintext file, including:

1. **Hashing**: Compute and save the SHA-512 digest of the input file as digest_file.hex
2. **Asymmetric Cryptography (RSA-4096)**:
   - Generate an RSA-4096 key pair.
   - Sign the plaintext file with the private key(RSA_public_key.pem).
   - Verify the signature using the public key(RSA_private_key.pem).
   - output the signed_file
3. **Symmetric Cryptography (AES-256 in ECB mode)**:
   - Generate an AES-256 key and save it in binary format(AES_key.txt).
   - Encrypt the plaintext file using the RSA public key and output as encrypted_AES_key.txt.
   - Decrypt the ciphertext back to plaintext using RSA private key.
   - Verify the decrypted output matches the original.
4. **Integrity Verification**:
   - Compute the SHA-512 digest of the decrypted file.
   - Compare digests of original and decrypted files to confirm integrity.

## Prerequisites

- Python 3.6 or higher
- `cryptography` library
- `hashlib`, `os` modules (standard library)

## Installation

1. Clone or download this repository.

2. (Optional) Create and activate a virtual environment:

   ```
   python -m venv venv
   source venv/bin/activate    # Linux/Mac
   venv\Scripts\activate     # Windows
   ```

3. Install dependencies:

   ```
   pip install cryptography
   ```

## Usage

1. Place your plaintext file in the project root and update the file path in the notebook if necessary.
2. Open `SE6003A1.ipynb` in Jupyter Notebook or JupyterLab.
3. Run the cells sequentially:
   - Cells 1–2: Compute SHA-512 digest.
   - Cells 3–4: Generate RSA key pair and sign/verify.
   - Cells 5–7: Generate AES key, encrypt and decrypt the file.
   - Cells 8–11: Verify decrypted data and compare hash digests.
4. Inspect the generated files:
   - `digest_file.hex`, `digest_decrypted_file.hex` (SHA-512 digests)
   - `RSA_private_key.pem`, `RSA_public_key.pem` (RSA keys)
   - `signed_file` (RSA signature)
   - `AES_key.txt`, `decrypted_AES_key.txt` (AES keys)
   - `ciphertext_file`, `decrypted_file` (AES encrypted/decrypted data)

## Project Structure

```
├── SE6003A1.ipynb
├── plaintext_file.txt         # Input file to be processed
├── digest_file.hex            # SHA-512 of original file
├── RSA_private_key.pem        # Generated RSA private key
├── RSA_public_key.pem         # Generated RSA public key
├── signed_file                # RSA signature
├── AES_key.txt                # AES-256 key in binary
├── decrypted_AES_key.txt      # AES key after decryption (should match)
├── ciphertext_file            # Encrypted data
├── decrypted_file             # Decrypted plaintext
└── digest_decrypted_file.hex  # SHA-512 of decrypted file
```

