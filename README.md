# AI Career Guidance System 🎯

An AI-powered career guidance web application that evaluates a user's interests, skills, aptitude, personality, and work preferences to recommend a suitable career path.

The system combines a **Django web application** with a **Machine Learning Decision Tree classifier** to generate career recommendations based on user responses.

## Features

* **User Registration & Login** — Secure user authentication using Django's built-in authentication system.
* **Career Assessment** — Users complete an assessment covering interests, skills, aptitude, personality, and work preferences.
* **AI Career Recommendation** — A trained Decision Tree model predicts a suitable career based on assessment scores.
* **Personal Dashboard** — Provides authenticated users with access to the career assessment and profile features.
* **Career Results** — Displays the recommended career after completing the assessment.
* **Career History** — Users can view their previous career recommendations.
* **Profile Management** — Users can update their personal information.
* **Password Management** — Users can change their account password.
* **Result Management** — Users can delete previous career assessment results.
* **Offline ML Model** — The trained model is stored locally and loaded using Joblib.
* **SQLite Database** — Stores user accounts and career assessment results.

## How It Works

The system evaluates five major areas:

1. **Interest**
2. **Skills**
3. **Aptitude**
4. **Personality**
5. **Work Preference**

Each section contains multiple questions. The user's responses are converted into scores, which are then passed to the trained Machine Learning model.

```text
User
 │
 ▼
Registration / Login
 │
 ▼
Career Assessment
 │
 ▼
Calculate Section Scores
 │
 ├── Interest
 ├── Skills
 ├── Aptitude
 ├── Personality
 └── Work Preference
 │
 ▼
Decision Tree Model
 │
 ▼
Career Prediction
 │
 ▼
Save Result
 │
 ▼
Display Recommended Career
```

## Machine Learning

The project uses a **Decision Tree Classifier** from Scikit-learn.

### Input Features

The model uses five features:

```text
interest
skills
aptitude
personality
work
```

### Output

The model predicts a career category based on these five assessment scores.

The trained model is stored at:

```text
guidance/ml/career_model.pkl
```

The training dataset is located at:

```text
guidance/ml/career_data.csv
```

### Training the Model

The model can be retrained using:

```bash
python guidance/ml/train_model.py
```

This reads `career_data.csv`, trains the Decision Tree classifier, and saves the resulting model as `career_model.pkl`.

## Tech Stack

| Technology    | Purpose                              |
| ------------- | ------------------------------------ |
| Python        | Application and ML development       |
| Django        | Web application framework            |
| HTML          | Frontend structure                   |
| CSS           | User interface styling               |
| SQLite        | Database                             |
| Pandas        | Dataset processing                   |
| Scikit-learn  | Machine Learning                     |
| Decision Tree | Career prediction algorithm          |
| Joblib        | Saving and loading the trained model |

## Project Structure

```text
AI-Career-Guidance-System/
│
├── career_guidance/
│   ├── career_guidance/
│   │   ├── __init__.py
│   │   ├── settings.py
│   │   ├── urls.py
│   │   └── wsgi.py
│   │
│   ├── guidance/
│   │   ├── migrations/
│   │   ├── ml/
│   │   │   ├── career_data.csv
│   │   │   ├── career_model.pkl
│   │   │   └── train_model.py
│   │   │
│   │   ├── templates/
│   │   │   ├── accounts/
│   │   │   └── guidance/
│   │   │
│   │   ├── models.py
│   │   └── views.py
│   │
│   └── manage.py
│
├── .gitignore
├── dependencies.txt
└── README.md
```

## Installation

### Prerequisites

* Python 3.11 or compatible Python version
* pip
* Git

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/AI-Career-Guidance-System.git
cd AI-Career-Guidance-System
```

### 2. Create a Virtual Environment

Windows:

```bash
python -m venv env
```

Activate it:

```bash
env\Scripts\activate
```

Linux/macOS:

```bash
python3 -m venv env
source env/bin/activate
```

### 3. Install Dependencies

```bash
pip install django pandas scikit-learn joblib
```

### 4. Navigate to the Django Project

```bash
cd career_guidance
```

### 5. Apply Database Migrations

```bash
python manage.py migrate
```

### 6. Start the Development Server

```bash
python manage.py runserver
```

Open the local development server in your browser:

```text
http://127.0.0.1:8000/
```

## Database

The application uses **SQLite** with Django's ORM.

The `CareerResult` model stores:

* User
* Recommended career
* Assessment scores
* Result creation timestamp

User authentication is handled using Django's built-in authentication system.

## Model Training

The training script uses the dataset:

```text
guidance/ml/career_data.csv
```

The following features are used:

```python
[
    "interest",
    "skills",
    "aptitude",
    "personality",
    "work"
]
```

The target variable is:

```text
career
```

The trained Decision Tree model is serialized using Joblib.

## Security Notes

For development, Django's configuration currently uses a local secret key and `DEBUG = True`.

Before deploying this application publicly:

* Move the Django `SECRET_KEY` to an environment variable.
* Set `DEBUG = False`.
* Configure `ALLOWED_HOSTS`.
* Use a production database if required.
* Configure HTTPS and appropriate security settings.
* Do not commit passwords, API keys, or other secrets.

## Future Improvements

* Improve the Machine Learning model with additional algorithms.
* Compare multiple ML models and evaluate their accuracy.
* Add model performance metrics.
* Provide confidence scores for career recommendations.
* Add more career categories and training data.
* Add personalized career explanations.
* Add skill-development recommendations.
* Add course and certification recommendations.
* Add a responsive/mobile-friendly interface.
* Deploy the application to a cloud platform.
* Add automated model retraining.

## Purpose

This project was developed as an educational project demonstrating the integration of:

**Django + Machine Learning + SQLite + User Authentication**

It demonstrates how a trained Machine Learning model can be integrated into a web application to provide personalized predictions based on user-provided data.

## License

This project is intended for educational and portfolio purposes.
