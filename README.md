# QR-code-generator

This project is a simple Python script that generates QR codes from user-provided data. QR codes (Quick Response codes) are a type of matrix barcode that can store various kinds of information such as URLs, contact information, and more. This project leverages the `qrcode` library in Python to create and save QR code images.

Features

- Generates QR codes from user input
- Saves QR codes as image files
- Customizable QR code version, error correction level, box size, and border size

Installation

To run this project, you need to have Python installed on your system along with the `qrcode` library. You can install the `qrcode` library using pip:

```sh
pip install qrcode[pil]
```

Usage

1. Clone the repository to your local machine.
2. Navigate to the project directory.
3. Run the script using Python.

```sh
python qr_code_generator.py
```

You will be prompted to enter the data you want to encode as a QR code and the filename for the QR code image.

Code Explanation

Importing Libraries

```python
import qrcode
```

The script starts by importing the `qrcode` library, which provides the functionality to generate QR codes.

Defining the QR Code Generator Function

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

- `generate_qr_code(data, filename)`: This function takes two arguments - the data to be encoded and the filename for the output image.
- `qrcode.QRCode`: Creates a QRCode object with specified parameters:
  - `version=1`: Controls the size of the QR code (1 is the smallest).
  - `error_correction=qrcode.constants.ERROR_CORRECT_L`: Sets the error correction level to Low.
  - `box_size=10`: Sets the number of pixels for each box in the QR code.
  - `border=4`: Sets the border size (minimum is 4).
- `qr.add_data(data)`: Adds the data to the QR code.
- `qr.make(fit=True)`: Generates the QR code.
- `qr.make_image(fill_color="black", back_color="white")`: Creates an image of the QR code with the specified fill and background colors.
- `img.save(filename)`: Saves the image to the specified filename.

Main Execution Block

```python
if __name__ == "__main__":
    data = input("Enter the data you want to encode as a QR code: ")
    filename = input("Enter the filename for the QR code image (e.g., output.png): ")

    generate_qr_code(data, filename)
    print(f"QR code saved as {filename}")
```

- `if __name__ == "__main__":`: Ensures that the script runs only when executed directly, not when imported as a module.
- `data = input("Enter the data you want to encode as a QR code: ")`: Prompts the user to enter the data to be encoded.
- `filename = input("Enter the filename for the QR code image (e.g., output.png): ")`: Prompts the user to enter the filename for the output image.
- `generate_qr_code(data, filename)`: Calls the function to generate and save the QR code.
- `print(f"QR code saved as {filename}")`: Confirms that the QR code has been saved.

Example

To generate a QR code for your LinkedIn profile, you can run the script and input your LinkedIn URL when prompted:

```sh
Enter the data you want to encode as a QR code: https://www.linkedin.com/in/your-profile
Enter the filename for the QR code image (e.g., output.png): linkedin_qr.png
QR code saved as linkedin_qr.png
```

This will create a QR code image named `linkedin_qr.png` that directs to your LinkedIn profile when scanned.
Contributing

If you would like to contribute to this project, please fork the repository and submit a pull request. For major changes, please open an issue first to discuss what you would like to change.
