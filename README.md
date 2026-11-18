# Gujarati OCR and Translation

Optical Character Recognition (OCR) and translation pipeline for printed and handwritten Gujarati text using Google Cloud Vision and Translation APIs. Supports both Python and Node.js.

---

## Data Flow

```
+------------------------------------------+
| Input Image (Local File / GCS URI)       |
+------------------------------------------+
                    |
                    v
+------------------------------------------+
| Vision Client (Authentication & Payload) |
+------------------------------------------+
                    |
                    v
+------------------------------------------+
| Google Cloud Vision API                  |
| (DOCUMENT_TEXT_DETECTION, hint: 'gu')    |
+------------------------------------------+
                    |
                    v
+------------------------------------------+
| Extracted Gujarati Text                  |
+------------------------------------------+
          |                        |
          v                        v
+---------------------+  +---------------------+
| synchronous.txt     |  | Google Translate    |
| (Raw Text Output)   |  | (Detect & Translate)|
+---------------------+  +---------------------+
                                   |
                                   v
                         +---------------------+
                         | English Translation |
                         +---------------------+
```

---

## Project Structure

```text
OCR_gujrati/
├── samples/
│   ├── handwritten_gujarati.jpeg
│   ├── guj.png
│   └── test.png
├── ocr_guj.py
├── requirements.txt
├── config.py.example
├── index.js
├── package.json
├── config.js.example
├── synchronous.txt
├── ocr_result_detailed.txt
├── .gitignore
└── README.md
```

---

## Setup and Installation

### Python

1. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   # Windows PowerShell:
   .\venv\Scripts\Activate.ps1
   # Linux/macOS:
   source venv/bin/activate
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Configure Google Cloud credentials:
   - Place your service account JSON file as `credentials.json` and set:
     ```powershell
     $env:GOOGLE_APPLICATION_CREDENTIALS = "$PWD\credentials.json"
     ```
   - Or copy `config.py.example` to `config.py` and enter your credentials.

4. Run:
   ```bash
   # Default sample
   python ocr_guj.py

   # Specific local image
   python ocr_guj.py -i samples/guj.png

   # Google Cloud Storage URI
   python ocr_guj.py -g gs://bucket-name/image.png
   ```

### Node.js

1. Install dependencies:
   ```bash
   npm install
   ```

2. Configure credentials:
   - Set `GOOGLE_APPLICATION_CREDENTIALS`, or copy `config.js.example` to `config.js`.

3. Run:
   ```bash
   node index.js
   node index.js samples/guj.png
   ```

---

## Output

Recognized text is saved to `synchronous.txt`.

Example output for `samples/handwritten_gujarati.jpeg`:
```text
⌽ - ૨ ગુણી સીમેન્ટ
★ - ૧૪ જગદંબા
O - ૧૦ કચ્છી
△ - ૭ રેતી
```
