# Background Remover API

A **Django REST API** for removing image backgrounds using the `rembg` library.  
This project processes images **in-memory** and returns the result as a **transparent PNG**.  
It does **not store images on disk**, making it **fast and secure**.

---

## 🚀 Features
- Remove image background with **rembg**
- RESTful API with **Django REST Framework**
- **No file storage** – returns processed image directly
- Ready for **local development** and **integration** into other projects
- Supports **CORS for local testing**

---

## 📦 Requirements
- **Python 3.10+**
- Virtual environment (recommended)
- Dependencies listed in `requirements.txt`:
  ```txt
  Django==5.2.4
  djangorestframework==3.16.0
  django-cors-headers==4.7.0
  rembg==2.0.67
  onnxruntime==1.22.1
  pillow
  python-decouple==3.8
  ```

---

## ⚙️ Installation & Local Setup

1️⃣ **Clone the repository**
```bash
git clone https://github.com/<your-username>/remove-bg-image.git
cd remove-bg-image
```

2️⃣ **Create and activate a virtual environment**
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate
```

3️⃣ **Install dependencies**
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

4️⃣ **Run migrations**
```bash
python manage.py migrate
```

5️⃣ **Run the server**
```bash
python manage.py runserver
```

Your API will be available at:
```
http://127.0.0.1:8000/
```

---

## 🧪 How to Test the API

### 1. Postman (Manual Test)
- Method: **POST**
- URL:
  ```
  http://127.0.0.1:8000/remove-background/
  ```
- Body → **form-data** → Key: `image` (Type: File)

---

### 2. cURL (Terminal Test)

**Windows (PowerShell using `curl.exe`)**
```powershell
curl.exe -X POST http://127.0.0.1:8000/remove-background/ -F "image=@my_image.jpg" -o result.png
```

**Linux/Mac or Git Bash**
```bash
curl -X POST http://127.0.0.1:8000/remove-background/ -F "image=@my_image.jpg" --output result.png
```

- Sends the file and saves the processed PNG as `result.png`
- Open the file to verify the background removal

---

## 📂 Project Structure
```
remove-bg-image/
│
├─ config/              # Django project (settings, urls, wsgi)
├─ remover/             # Main app with views and API endpoints
├─ manage.py
├─ requirements.txt
├─ .gitignore
├─ LICENSE
└─ README.md
```

---

## ⚡ Notes
- This API is optimized for **local testing and learning**.
- For production deployment, you must configure:
  - `.env` for `SECRET_KEY` and `DEBUG`
  - Whitenoise or cloud storage for static files
  - Set proper `ALLOWED_HOSTS` for your domain or hosting provider
