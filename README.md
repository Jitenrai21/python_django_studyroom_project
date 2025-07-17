# 📚 StudyRoom Project

A simple Django-based web application for creating and managing study rooms, topics, and discussions — designed to help students connect, share knowledge, and collaborate.

---

## 📌 Features

- ✅ User authentication (register, login, logout)
- ✅ User profiles with editable information
- ✅ Create, update, and delete rooms
- ✅ Post messages and replies within rooms
- ✅ Browse recent activities and topics
- ✅ Responsive UI with reusable components

---

## 🗂️ Project Structure

```

StudyRoomProject/
├── base/                 # Main Django app
│   ├── templates/        # HTML templates
│   ├── admin.py
│   ├── models.py
│   ├── forms.py
│   ├── views.py
│   ├── urls.py
│   └── ...
│
├── static/               # Static files (CSS, JS, Images)
│   ├── styles/
│   ├── js/
│   └── images/
│
├── StudyRoom/            # Django project configuration
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── ...
│
├── Templates/            # Shared templates (base, navbar)
├── db.sqlite3            # SQLite database
├── manage.py             # Django CLI entry point
├── requirements.txt      # Python dependencies
└── Project_Structure     # project structure file

````

---

## 🚀 Getting Started

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/StudyRoomProject.git
cd StudyRoomProject
````

### 2️⃣ Create & activate a virtual environment

```bash
python -m venv env
# On Windows:
env\Scripts\activate
# On Mac/Linux:
source env/bin/activate
```

### 3️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Apply migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5️⃣ Run the development server

```bash
python manage.py runserver
```

Visit [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to use the app!

---

## ⚙️ Technologies Used

* **Python 3**
* **Django 5**
* **SQLite3** (default database)
* **HTML5**, **CSS3**, **JavaScript**

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

---

## 👤 Author

Jiten Rai (https://github.com/Jitenrai21)

```

