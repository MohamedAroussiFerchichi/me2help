# Me2Help AI — Mental Health Chat Assistant

A full-stack mental health support application with emotion detection, built with React, Node.js, and a Python ML service.

## Architecture

| Service | Technology | Default Port |
|---------|-----------|-------------|
| `me2helpClient` | React + Vite + TypeScript | 3000 |
| `me2helpServer` | Node.js + Express + MongoDB | 5000 |
| `me2helpAi` | Python + Flask + scikit-learn | 5001 |

---

## Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [Python](https://www.python.org/) 3.9+
- [MongoDB](https://www.mongodb.com/) (local or Atlas)
- [Git](https://git-scm.com/)

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

---

### 2. Python AI Service (`me2helpAi`)

```bash
cd me2helpAi

# Create and activate a virtual environment
python -m venv venv

# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

Create a `.env` file inside `me2helpAi/` (optional — defaults shown):

```env
PORT=5001
```

Start the service:

```bash
python app.py
```

> The Flask service will run at `http://localhost:5001`

---

### 3. Node.js Backend (`me2helpServer`)

```bash
cd me2helpServer
npm install
```

Create a `.env` file inside `me2helpServer/`:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/me2help
JWT_SECRET=your_super_secret_key_here
PYTHON_API=http://localhost:5001
```

Start the server:

```bash
node index.js
```

> The API server will run at `http://localhost:5000`

---

### 4. React Frontend (`me2helpClient`)

```bash
cd me2helpClient
npm install
```

Create a `.env` file inside `me2helpClient/`:

```env
back_end_API_URL=http://localhost:5000
GEMINI_API_KEY=your_gemini_api_key_here
```

Start the development server:

```bash
npm run dev
```

> The app will run at `http://localhost:3000`

---

## Running All Services

Open **three separate terminals** and run each service simultaneously:

```bash
# Terminal 1 — Python AI
cd me2helpAi && venv\Scripts\activate && python app.py

# Terminal 2 — Node.js Backend
cd me2helpServer && node index.js

# Terminal 3 — React Frontend
cd me2helpClient && npm run dev
```

---

## Environment Variables Summary

### `me2helpServer/.env`

| Variable | Required | Description |
|----------|----------|-------------|
| `MONGO_URI` | Yes | MongoDB connection string |
| `JWT_SECRET` | Yes | Secret key for signing JWT tokens |
| `PYTHON_API` | Yes | URL of the Python AI service |
| `PORT` | No | Server port (default: `5000`) |

### `me2helpClient/.env`

| Variable | Required | Description |
|----------|----------|-------------|
| `back_end_API_URL` | No | Backend URL (default: `http://localhost:5000`) |
| `GEMINI_API_KEY` | No | Google Gemini API key |

### `me2helpAi/.env`

| Variable | Required | Description |
|----------|----------|-------------|
| `PORT` | No | Flask service port (default: `5001`) |

---

## Build for Production

```bash
# Build the frontend
cd me2helpClient
npm run build
```

The static output will be in `me2helpClient/dist/`.
