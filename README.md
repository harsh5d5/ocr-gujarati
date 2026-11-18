# Gujarati OCR & Translation (ગુજરાતી OCR)

A clean pipeline for Optical Character Recognition (OCR) and translation of printed and handwritten Gujarati text using Google Cloud Vision and Translation APIs, supporting both **Python** and **Node.js (JavaScript)**.

---

## 📁 Project Structure

```text
OCR_gujrati/
├── samples/
│   ├── handwritten_gujarati.jpeg # Handwritten Gujarati note
│   ├── guj.png                 # Printed Gujarati news snippet
│   └── test.png                # Gujarati text test sample
├── ocr_guj.py                  # Python OCR & Translation script (CLI enabled)
├── requirements.txt            # Python dependencies
├── config.py.example           # Python credentials template
├── index.js                    # Node.js OCR & Translation script
├── package.json                # Node.js package definition
├── config.js.example           # Node.js credentials template
├── synchronous.txt             # Clean OCR output file
├── ocr_result_detailed.txt     # Line-by-line translation and breakdown
├── .gitignore                  # Git ignore rules for keys and dependencies
└── README.md                   # Project documentation
```

---

## ⚙️ Prerequisites

- **Python**: 3.8+ (for Python pipeline)
- **Node.js**: 16+ (for JavaScript pipeline)
- **Google Cloud Platform (GCP)** Account with:
  - Cloud Vision API enabled
  - Cloud Translation API enabled
  - Service Account credentials

---

## 🐍 Python Setup & Usage

### 1. Setup Virtual Environment & Install Dependencies
```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

### 2. Configure Credentials
Either:
- Set environment variable pointing to your service account key:
  ```powershell
  $env:GOOGLE_APPLICATION_CREDENTIALS = "$PWD\credentials.json"
  ```
- Or copy `config.py.example` to `config.py` and enter your details.

### 3. Run Python OCR
```powershell
# Default handwritten sample:
python ocr_guj.py

# Specific image:
python ocr_guj.py -i samples/guj.png

# Remote Google Cloud Storage (GCS) URI:
python ocr_guj.py -g gs://your-bucket-name/image.png
```

---

## 🟨 Node.js (JavaScript) Setup & Usage

### 1. Install Dependencies
```powershell
npm install
```

### 2. Configure Credentials
Either:
- Use `credentials.json` with `GOOGLE_APPLICATION_CREDENTIALS`
- Or copy `config.js.example` to `config.js` and enter your details.

### 3. Run Node.js OCR
```powershell
# Default handwritten sample:
node index.js

# Specific image:
node index.js samples/guj.png
```

---

## 📝 Sample Handwritten Output ([synchronous.txt](synchronous.txt))

```text
⌽ - ૨ ગુણી સીમેન્ટ
★ - ૧૪ જગદંબા
O - ૧૦ કચ્છી
△ - ૭ રેતી
```

### Breakdown:
- **⌽ - ૨ ગુણી સીમેન્ટ**: 2 bags / sacks of cement
- **★ - ૧૪ જગદંબા**: 14 Jagadamba (cement supplier/brand)
- **O - ૧૦ કચ્છી**: 10 Kutchi (cement/tiles/blocks)
- **△ - ૭ રેતી**: 7 measures of sand
