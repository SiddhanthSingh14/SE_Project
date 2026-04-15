# Team members :-
1. Siddhanth Singh (24BCP266)
2. Dax Patel (24BCP269)

Problem statement - GearGuard: The Ultimate Maintenance Tracker

# GearGuard - Django + React Application

A maintenance tracker application built with Django backend and React frontend.

## 🚀 Quick Start

### Prerequisites
- Python 3.13+
- Node.js and npm
- Virtual environment

### Installation

1. **Install Python Dependencies**
   ```bash
   # Create and activate virtual environment
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   
   # Install Django and dependencies
   pip install -r requirements.txt
   ```

2. **Install Node Dependencies**
   ```bash
   npm install
   ```

3. **Run Database Migrations**
   ```bash
   python manage.py migrate
   ```

4. **Create a Superuser** (for Django admin access)
   ```bash
   python manage.py createsuperuser
   ```

5. **Build React Frontend**
   ```bash
   npm run build
   ```

### Running the Application

#### Development Mode

**Option 1: Django Server Only** (serves built React app)
```bash
source venv/bin/activate
python manage.py runserver
```
Then visit: http://127.0.0.1:8000/

**Option 2: Separate Frontend & Backend** (for React development)
```bash
# Terminal 1 - Django Backend
source venv/bin/activate
python manage.py runserver

# Terminal 2 - React Frontend
npm run dev
```
Then visit: http://localhost:5173/ (Vite dev server with HMR)

## 📁 Project Structure

```
Gardgear/
├── gardgear_backend/      # Django project settings
│   ├── settings.py        # Django configuration
│   └── urls.py            # URL routing
├── mainapp/               # Django app
│   ├── models.py          # Database models (Equipment, Maintenance, etc.)
│   ├── views.py           # API ViewSets
│   ├── serializers.py     # DRF serializers
│   ├── urls.py            # API routes
│   └── admin.py           # Django admin config
├── src/                   # React source files
│   ├── App.jsx            # Main React component
│   ├── main.jsx           # React entry point
│   └── assets/            # Static assets
├── dist/                  # React build output (served by Django)
├── manage.py              # Django management script
├── requirements.txt       # Python dependencies
└── package.json           # Node dependencies
```

## 🛠️ API Endpoints

All API endpoints are available at `/api/`:

- **Equipment**: `/api/equipment/`
  - List, create, view, update, delete equipment
  - Custom endpoint: `/api/equipment/{id}/maintenance_history/`
  
- **Maintenance Requests**: `/api/maintenance-requests/`
  - List, create, view, update, delete maintenance requests
  - Custom endpoint: `/api/maintenance-requests/by_status/`
  
- **Maintenance Logs**: `/api/maintenance-logs/`
  - List, create, view, update, delete logs

### API Features
- ✅ Filtering by status, category, priority
- ✅ Search functionality
- ✅ Ordering/sorting
- ✅ Pagination (10 items per page)
- ✅ CORS enabled for local development

## 🎨 Django Admin

Access the Django admin panel at: http://127.0.0.1:8000/admin/

Manage:
- Equipment inventory
- Maintenance requests
- Maintenance logs
- Users and permissions

## 🔧 Models

### Equipment
- Tracks equipment/gear with serial numbers
- Status: Operational, Under Maintenance, Retired
- Includes warranty and purchase information

### MaintenanceRequest
- Maintenance tasks and requests
- Priority levels: Low, Medium, High, Urgent
- Status tracking: Pending, In Progress, Completed, Cancelled
- Assignment to users and due dates

### MaintenanceLog
- Historical records of maintenance work
- Parts replaced and costs
- Linked to maintenance requests

## 🌐 React Frontend

The React app is built with:
- ⚡ Vite for fast development
- 🎯 Direct API integration with Django backend
- 📱 Responsive design
- 🔄 Live connection status indicator

## 📝 Development Tips

### Adding New Features

1. **Add a model**: Edit `mainapp/models.py`
2. **Create migrations**: `python manage.py makemigrations`
3. **Apply migrations**: `python manage.py migrate`
4. **Add serializer**: Edit `mainapp/serializers.py`
5. **Add ViewSet**: Edit `mainapp/views.py`
6. **Register routes**: Edit `mainapp/urls.py`

### React Development

- Edit React components in `src/`
- Run `npm run dev` for hot module replacement
- Build for production with `npm run build`
- Django will serve the built files automatically

## 🔒 Environment Variables

Create a `.env` file from `.env.example`:
```bash
cp .env.example .env
```

Then edit `.env` with your values.

## 📦 Production Deployment

1. Set `DEBUG=False` in Django settings
2. Configure `ALLOWED_HOSTS`
3. Run `python manage.py collectstatic`
4. Use a production WSGI server (gunicorn, uwsgi)
5. Serve static files with nginx or whitenoise

## 🤝 Contributing

Feel free to extend the models, add new features, or improve the React UI!

## 📄 License

This project is open source and available for modification.
