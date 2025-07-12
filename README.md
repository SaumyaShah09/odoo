# StackIt - Q&A Platform MVP

A minimal Q&A forum platform built with Django, similar to Stack Overflow. This project is designed for a 4-member development team working collaboratively.

## 🚀 Features

- **User Authentication**: Registration, login, logout with optional GitHub OAuth
- **Question Management**: Ask, edit, delete questions with rich text editor
- **Answer System**: Answer questions, accept/unaccept answers
- **Voting System**: Upvote/downvote questions and answers
- **Tagging**: Multi-select tags for questions
- **Notifications**: Real-time notifications for answers, mentions, votes
- **Reputation System**: Earn reputation through community engagement
- **Search**: Search questions by title, content, or tags
- **Admin Dashboard**: Moderation tools for admins
- **Responsive Design**: Bootstrap-based responsive UI

## 🛠 Tech Stack

- **Backend**: Django 4.2+, Django REST Framework
- **Database**: SQLite (development), PostgreSQL (production ready)
- **Frontend**: Bootstrap 5, jQuery
- **Rich Text**: CKEditor
- **Authentication**: django-allauth with GitHub integration
- **Other**: django-taggit, crispy-forms

## 📋 Prerequisites

- Python 3.10+
- pip
- virtualenv (recommended)
- Git

## 🔧 Installation & Setup

### 1. Clone the Repository

\`\`\`bash
git clone <repository-url>
cd stackit-mvp
\`\`\`

### 2. Create Virtual Environment

\`\`\`bash
python -m venv venv

# On Windows
venv\\Scripts\\activate

# On macOS/Linux
source venv/bin/activate
\`\`\`

### 3. Install Dependencies

\`\`\`bash
pip install -r requirements.txt
\`\`\`

### 4. Environment Configuration

\`\`\`bash
cp .env.example .env
\`\`\`

Edit `.env` file with your configuration:
- Generate a new SECRET_KEY
- Configure database settings (if using PostgreSQL)
- Set up email settings (for production)
- Add GitHub OAuth credentials (optional)

### 5. Database Setup

\`\`\`bash
python manage.py makemigrations
python manage.py migrate
\`\`\`

### 6. Create Superuser

\`\`\`bash
python manage.py createsuperuser
\`\`\`

### 7. Collect Static Files

\`\`\`bash
python manage.py collectstatic
\`\`\`

### 8. Run Development Server

\`\`\`bash
python manage.py runserver
\`\`\`

Visit `http://127.0.0.1:8000` to see the application.

## 👥 Team Structure & Development Workflow

### Team Member Responsibilities

**👤 Dev 1 - Authentication & Users**
- \`apps/users/\` - User models, profiles, authentication
- User registration, login, logout functionality
- Profile management and user settings
- Admin tools for user moderation

**👤 Dev 2 - Questions Management**
- \`apps/questions/\` - Question CRUD operations
- Rich text editor integration (CKEditor)
- Tagging system implementation
- Question search and filtering

**👤 Dev 3 - Answers & Voting**
- \`apps/answers/\` - Answer CRUD operations
- \`apps/votes/\` - Voting system for questions/answers
- Accept/unaccept answer functionality
- Reputation calculation logic

**👤 Dev 4 - Notifications & Frontend**
- \`apps/notifications/\` - Notification system
- Django signals for notification triggers
- Frontend templates and Bootstrap integration
- Navbar and overall layout

### Git Workflow

1. **Branch Naming Convention**:
   - \`feature/auth-system\` (Dev 1)
   - \`feature/questions-crud\` (Dev 2)
   - \`feature/voting-system\` (Dev 3)
   - \`feature/notifications\` (Dev 4)

2. **Commit Message Guidelines**:
   \`\`\`
   type(scope): description
   
   Examples:
   feat(auth): add user registration form
   fix(questions): resolve tag filtering issue
   docs(readme): update installation instructions
   style(templates): improve responsive design
   \`\`\`

3. **Development Process**:
   - Create feature branch from \`main\`
   - Develop and test locally
   - Create pull request for code review
   - Merge after approval

## 🧪 Testing

Run tests for all apps:

\`\`\`bash
python manage.py test
\`\`\`

Run tests for specific app:

\`\`\`bash
python manage.py test apps.users
python manage.py test apps.questions
python manage.py test apps.answers
python manage.py test apps.votes
python manage.py test apps.notifications
\`\`\`

Run with coverage:

\`\`\`bash
coverage run --source='.' manage.py test
coverage report
coverage html
\`\`\`

## 🔍 Code Quality

### Pre-commit Hooks Setup

\`\`\`bash
pre-commit install
\`\`\`

### Manual Code Formatting

\`\`\`bash
# Format code with black
black .

# Sort imports with isort
isort .

# Check code style with flake8
flake8 .
\`\`\`

## 📁 Project Structure

\`\`\`
stackit/
├── apps/
│   ├── core/           # Base models, views, utilities
│   ├── users/          # User management (Dev 1)
│   ├── questions/      # Question CRUD (Dev 2)
│   ├── answers/        # Answer system (Dev 3)
│   ├── votes/          # Voting system (Dev 3)
│   └── notifications/  # Notification system (Dev 4)
├── templates/          # HTML templates
├── static/            # CSS, JS, images
├── media/             # User uploads
├── stackit/           # Django project settings
├── requirements.txt   # Python dependencies
├── .env.example      # Environment variables template
└── README.md         # This file
\`\`\`

## 🔌 API Endpoints

The project includes REST API endpoints:

- \`/api/v1/users/\` - User management
- \`/api/v1/questions/\` - Questions CRUD
- \`/api/v1/answers/\` - Answers CRUD
- \`/api/v1/votes/\` - Voting operations
- \`/api/v1/notifications/\` - Notifications

API documentation available at \`/api/v1/\` when running the server.

## 🚀 Deployment

### Production Settings

1. Set \`DEBUG=False\` in production
2. Configure PostgreSQL database
3. Set up email backend (SMTP)
4. Configure static files serving (WhiteNoise or CDN)
5. Set proper \`ALLOWED_HOSTS\`

### Docker Deployment (Optional)

\`\`\`dockerfile
# Dockerfile example
FROM python:3.10-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
RUN python manage.py collectstatic --noinput

EXPOSE 8000
CMD ["gunicorn", "stackit.wsgi:application", "--bind", "0.0.0.0:8000"]
\`\`\`

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (\`git checkout -b feature/amazing-feature\`)
3. Commit your changes (\`git commit -m 'Add amazing feature'\`)
4. Push to the branch (\`git push origin feature/amazing-feature\`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

If you encounter any issues:

1. Check the GitHub Issues page
2. Review the documentation
3. Contact the development team

## 🎯 Roadmap

### Phase 1 (MVP) ✅
- Basic Q&A functionality
- User authentication
- Voting system
- Notifications

### Phase 2 (Future)
- Comment system
- Advanced search with Elasticsearch
- Real-time notifications with WebSockets
- Mobile app API
- Advanced moderation tools
- Gamification features

---

**Happy Coding! 🚀**
\`\`\`
\`\`\`

```python file=".pre-commit-config.yaml" type="code"
repos:
  - repo: https://github.com/psf/black
    rev: 23.11.0
    hooks:
      - id: black
        language_version: python3.10

  - repo: https://github.com/pycqa/isort
    rev: 5.12.0
    hooks:
      - id: isort
        args: ["--profile", "black"]

  - repo: https://github.com/pycqa/flake8
    rev: 6.1.0
    hooks:
      - id: flake8
        args: [--max-line-length=88, --extend-ignore=E203]

  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-added-large-files
