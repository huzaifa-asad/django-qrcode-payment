# GS Petrol Pump QR App

A simple Django web app to generate and scan QR codes for payments. It includes a modern, responsive UI with theme modes (System/Light/Dark), QR generation with download/copy options, and QR scanning via image upload and drag-and-drop.

## Features

- Generate QR codes from text
- Download or open generated QR images, copy URL to clipboard
- Scan QR codes from uploaded images (PNG/JPG)
- Drag-and-drop upload with image preview
- Modern UI with theme modes (System/Light/Dark) and toasts

## Tech stack

- Python 3.12
- Django 5.2
- qrcode, Pillow for generating QR codes
- pyzbar + OpenCV for decoding QR codes

## Project structure

```python
djangoqr/
  manage.py
  requirements.txt
  core/                # Base pages, global styles
  scanner/             # Generate and Scan features
  djangoqr/            # Project settings and URLs
  media/               # Generated QR images (dev)
```

## Quick start

1. Clone and enter the project folder
2. Create a virtual environment and install dependencies
3. Run database migrations
4. Start the dev server

```bash
# 1) clone
git clone <your-repo-url>.git
cd djangoqr

# 2) venv + install
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 3) migrate
python manage.py migrate

# 4) run
python manage.py runserver
```

## Environment

- Development static files are served by Django with `DEBUG=True`.
- Generated QR images are written under `media/qr_codes/`. The `media/` folder is ignored in git.

## Settings notes

- STATIC_URL is configured as `/static/`.
- Templates use `{% load static %}` and `<link rel="stylesheet" href="{% static 'core/css/style.css' %}?v=2025-09-14">`.
- You can remove the `?v=...` query once you use hashed static files in production.

## Production tips

- Use `ManifestStaticFilesStorage` for cache-busted static assets.
- Serve static files via a web server or CDN (e.g., Nginx).
- Set `DEBUG=False` and configure `ALLOWED_HOSTS`.
- Configure a proper database (PostgreSQL, etc.).
- Store secrets via environment variables.

## Contributing

Please see [CONTRIBUTING.md](CONTRIBUTING.md) and our [Code of Conduct](CODE_OF_CONDUCT.md). Bug reports and feature requests are welcome—use the issue templates for a quick start.

## Security

If you find a security vulnerability, please review our [SECURITY.md](SECURITY.md) for responsible disclosure instructions.

## CI

This project includes a minimal GitHub Actions workflow (`.github/workflows/ci.yml`) that installs dependencies and runs `python manage.py check` on pushes and PRs.

## Lint/format (optional)

You can add Ruff/Black or flake8 if you want linting/formatting. Example commands:

```bash
pip install ruff black
ruff check .
black .
```

## License

MIT
