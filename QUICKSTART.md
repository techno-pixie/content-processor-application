### Prerequisites (Non-Kafka Version)
- Python 3.9+
- Node 16+
- npm

### Quick Start (2 steps)


**Step 1: Start Backend API**
```bash
cd content-processor-application/backend
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

**Step 2: Start Frontend (new terminal)**
```bash
cd content-processor-application/frontend
npm install
npm run dev
```

### Prerequisites (Kafka Version)
-
- Python 3.9+
- Node 16+
- npm

### Quick Start (3 steps)
**Step 1: Start Kafka**
```bash
docker-compose up -d

# Wait for Kafka to start (~15 seconds)
docker-compose logs kafka | grep "started"
```

**Step 2: Start Backend API**
```bash
cd content-processor-application/backend
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
USE_KAFKA=true uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

**Step 2: Start Frontend (new terminal)**
```bash
cd content-processor-application/frontend
npm install
npm run dev
```

### Additional (Python unit test)
```bash
cd content-processor-application
python3 -m venv .venv
source .venv/bin/activate
pytest tests/ -v
pytest --cov=backend/processor_app --cov-report=term --cov-report=html backend/tests/ #for coverage report
```