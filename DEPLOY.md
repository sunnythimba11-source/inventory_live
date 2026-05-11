# Zawadibora Farm Feeds Ltd - Live Inventory System

## How to Run Locally

1. Install Python 3 from: https://www.python.org/downloads/
2. Open PowerShell in this folder and run:
```
pip install -r requirements.txt
python app.py
```
3. Open browser to: http://localhost:5000

## Default Logins

| Username | Password | Role |
|----------|----------|------|
| admin | admin123 | Admin (can edit) |
| viewer | view123 | Viewer (read-only) |

## Deploy to PythonAnywhere (Free Hosting)

1. Create account at https://www.pythonanywhere.com
2. Go to Dashboard → Web → Add a new web app
3. Choose "Manual Configuration" → "Flask" → Python 3.10
4. Open "Files" tab and upload all files from this project
5. In the "Web" tab, set:
   - Source code: `/home/YOURUSERNAME/inventory_live`
   - Working directory: `/home/YOURUSERNAME/inventory_live`
   - WSGI configuration file: Click to edit, add:
```python
import sys
path = '/home/YOURUSERNAME/inventory_live'
if path not in sys.path: sys.path.append(path)
from app import app as application
```
6. Open a Bash console and run:
```
pip install --user flask flask-sqlalchemy flask-login werkzeug openpyxl
cd inventory_live
python -c "from app import app, db; app.app_context().push(); db.create_all()"
```
7. Go back to Web tab and click "Reload"
8. Your site is live at: https://YOURUSERNAME.pythonanywhere.com
