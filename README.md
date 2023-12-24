# QR-Code-Image-Generator-from-a-Text-File
Read a text file and generate a QR code for each line.
import qrcode

def generate_qr_codes_from_file(file_path):
    with open(file_path, 'r') as file:
        lines = file.readlines()
        for idx, line in enumerate(lines):
            qr = qrcode.QRCode(
                version=1,
                error_correction=qrcode.constants.ERROR_CORRECT_L,
                box_size=10,
                border=4,
            )
            qr.add_data(line.strip())
            qr.make(fit=True)
            img = qr.make_image(fill_color="black", back_color="white")
            img.save(f"qrcode_{idx + 1}.png")

file_path = input("Enter the path of the text file: ")
generate_qr_codes_from_file(file_path)
