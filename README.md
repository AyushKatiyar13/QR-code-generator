# QR Code Generator 📱

## Overview

This project provides a simple Python script to generate QR codes from user-provided data. QR codes (Quick Response codes) are matrix barcodes capable of storing various types of information, such as URLs, contact details, and more. The project uses the `qrcode` library to create and save QR code images.

## Features

- Generates QR codes from user input
- Saves QR codes as image files
- Customizable QR code version, error correction level, box size, and border size

## Installation

To run this project, ensure you have Python installed on your system and install the `qrcode` library using pip:

```sh
pip install qrcode[pil]
```

## Usage

1. **Clone the Repository**:
   ```sh
   git clone <repository-url>
   ```

2. **Navigate to the Project Directory**:
   ```sh
   cd qr-code-generator
   ```

3. **Run the Script**:
   ```sh
   python qr_code_generator.py
   ```

4. **Follow the Prompts**:
   - Enter the data you want to encode as a QR code.
   - Provide a filename for the QR code image.

## Code Explanation

### Importing Libraries

```python
import qrcode
```
- Imports the `qrcode` library to provide QR code generation functionality.

### Defining the QR Code Generator Function

```python
def generate_qr_code(data, filename):
    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    qr.add_data(data)
    qr.make(fit=True)

    img = qr.make_image(fill_color="black", back_color="white")
    img.save(filename)
```

- `generate_qr_code(data, filename)`: Function to generate and save a QR code.
  - **Parameters**:
    - `data`: The data to encode in the QR code.
    - `filename`: The filename for the QR code image file.
  - **QR Code Settings**:
    - `version=1`: Defines the size of the QR code.
    - `error_correction=qrcode.constants.ERROR_CORRECT_L`: Error correction level set to Low.
    - `box_size=10`: Size of each box in pixels.
    - `border=4`: Border size (minimum is 4).
  - **Image Generation**:
    - `fill_color="black"`: Color for the QR code.
    - `back_color="white"`: Background color.
  - **Saving**:
    - `img.save(filename)`: Saves the generated QR code image.

### Main Execution Block

```python
if __name__ == "__main__":
    data = input("Enter the data you want to encode as a QR code: ")
    filename = input("Enter the filename for the QR code image (e.g., output.png): ")

    generate_qr_code(data, filename)
    print(f"QR code saved as {filename}")
```

- Ensures the script runs directly and not when imported as a module.
- Prompts the user for data and filename.
- Calls `generate_qr_code(data, filename)` to create and save the QR code.
- Prints a confirmation message.

## Example

To generate a QR code for your LinkedIn profile, run the script and enter the following details:

```sh
Enter the data you want to encode as a QR code: https://www.linkedin.com/in/your-profile
Enter the filename for the QR code image (e.g., output.png): linkedin_qr.png
QR code saved as linkedin_qr.png
```

This will create a QR code image named `linkedin_qr.png` that directs to your LinkedIn profile when scanned.

## Contributing

If you wish to contribute to this project:
1. **Fork the Repository**.
2. **Submit a Pull Request** with your changes.
3. **Open an Issue** for major changes to discuss modifications.

I appreciate your interest in improving this project! 😊

## Thank you! ⭐😊
