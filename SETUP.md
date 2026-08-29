# BeatFlow Studio - Setup Guide

## Quick Start with Docker

### Prerequisites
- Docker & Docker Compose installed
- API keys (OpenAI)
- Git

### Steps

1. **Clone the repository**
```bash
git clone https://github.com/muskokasigns-crypto/beatflow-studio.git
cd beatflow-studio
```

2. **Create environment file**
```bash
cp .env.example .env
# Edit .env and add your API keys
```

3. **Start services**
```bash
docker-compose up -d
```

4. **Initialize database**
```bash
docker-compose exec backend alembic upgrade head
```

5. **Access the application**
- Frontend: http://localhost:3000
- Backend API: http://localhost:8000
- API Docs: http://localhost:8000/docs

---

## Manual Setup (Development)

### Backend Setup

1. **Install Python 3.11+**
```bash
python --version  # Should be 3.11 or higher
```

2. **Create virtual environment**
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Setup database**
```bash
# Create PostgreSQL database
creatdb beatflow_db

# Run migrations
alembic upgrade head
```

5. **Run backend**
```bash
uvicorn main:app --reload
```

### Frontend Setup

1. **Install Node.js 18+**
```bash
node --version  # Should be 18 or higher
```

2. **Install dependencies**
```bash
cd frontend
npm install
```

3. **Create .env file**
```bash
echo "REACT_APP_API_URL=http://localhost:8000/api" > .env
```

4. **Run frontend**
```bash
npm start
```

---

## Configuration

### Environment Variables

**Backend (.env)**
```
# Database
DATABASE_URL=postgresql://user:password@localhost/beatflow_db

# API Keys
OPENAI_API_KEY=sk-...
HUGGINGFACE_API_KEY=hf_...

# JWT
JWT_SECRET=your_secret_key_here
JWT_ALGORITHM=HS256

# Redis
REDIS_URL=redis://localhost:6379

# AWS (optional)
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=us-east-1
AWS_S3_BUCKET=beatflow-videos

# Email (optional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=
SMTP_PASSWORD=

# App Settings
APP_NAME=BeatFlow Studio
APP_VERSION=0.1.0
DEBUG=False
```

**Frontend (.env)**
```
REACT_APP_API_URL=http://localhost:8000/api
REACT_APP_ENV=development
REACT_APP_VERSION=$npm_package_version
```

---

## Testing

### Backend Tests
```bash
cd backend
pytest tests/ -v

# With coverage
pytest tests/ --cov=app
```

### Frontend Tests
```bash
cd frontend
npm test

# Coverage
npm test -- --coverage
```

---

## Development Workflow

### Creating a Feature

1. Create feature branch
```bash
git checkout -b feature/feature-name
```

2. Make changes and commit
```bash
git add .
git commit -m "feat: add new feature"
```

3. Push and create PR
```bash
git push origin feature/feature-name
```

### Code Style

**Python (Backend)**
- Use Black for formatting
- Use isort for imports
- Follow PEP 8

```bash
cd backend
black .
isort .
flake8 .
```

**JavaScript/TypeScript (Frontend)**
- Use ESLint
- Use Prettier
- Follow Airbnb style guide

```bash
cd frontend
npm run lint
npm run format
```

---

## Database Migrations

### Create Migration
```bash
cd backend
alembic revision --autogenerate -m "Add new table"
```

### Apply Migration
```bash
alembic upgrade head
```

### Rollback
```bash
alembic downgrade -1
```

---

## Troubleshooting

### Port Already in Use
```bash
# Find process using port 8000
lsof -i :8000
# Kill process
kill -9 <PID>
```

### Database Connection Issues
```bash
# Check PostgreSQL is running
pg_isready -h localhost

# Reset database
dropdb beatflow_db
createdb beatflow_db
alembic upgrade head
```

### Module Not Found Errors
```bash
# Ensure virtual environment is activated
source venv/bin/activate

# Reinstall dependencies
pip install -r requirements.txt
```

### CORS Issues
- Check CORS settings in backend (main.py)
- Verify frontend URL is in allowed origins

---

## Useful Commands

```bash
# View logs
docker-compose logs -f backend
docker-compose logs -f frontend

# Execute command in container
docker-compose exec backend python script.py

# Restart service
docker-compose restart backend

# Remove all containers and volumes
docker-compose down -v

# Rebuild images
docker-compose build --no-cache
```

---

## Performance Tuning

### Database
- Add indexes on frequently queried columns
- Use connection pooling
- Optimize queries with EXPLAIN ANALYZE

### Backend
- Enable caching with Redis
- Use background tasks (Celery)
- Optimize ML model loading
- Use async endpoints

### Frontend
- Enable code splitting
- Lazy load components
- Optimize images
- Enable gzip compression

---

For more help, see the main [README.md](README.md) or open an issue on GitHub.
