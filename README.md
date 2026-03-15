<div align="center">

# 🧙 sys-wiz

**Interactive System Architecture Visualizer & Simulator**

Design, simulate, and stress-test distributed system architectures — all from your browser.

[![TypeScript](https://img.shields.io/badge/TypeScript-95.5%25-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-16-000?logo=next.js)](https://nextjs.org/)
[![Socket.IO](https://img.shields.io/badge/Socket.IO-4-010101?logo=socket.io)](https://socket.io/)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-000?logo=vercel)](https://vercel.com/)

</div>

---

## ✨ Features

### 🏗️ Architecture Designer
Drag-and-drop canvas powered by **React Flow** to visually design system architectures. Add nodes for services, databases, load balancers, caches, and more — then connect them with edges to define data flows.

### ⚡ Real-Time Simulation
Run live simulations of your architectures via a dedicated **simulation server**. Watch requests flow through your system in real-time over **WebSocket** connections, observing how components behave under load.

### 📊 Metrics Dashboard
Visualize performance metrics with interactive **D3.js** charts. Track throughput, latency, error rates, and resource utilization across your architecture's components.

### 🤖 AI Architecture Advisor
Get intelligent architecture recommendations powered by **Google Gemini AI**. Ask questions about your design, receive optimization suggestions, and explore trade-offs — all within the app.

### 🔥 Load Testing with Locust
Stress-test your simulated architectures using **Locust**, a Python-based load testing framework. Generate realistic traffic patterns, simulate spike loads, and watch bottlenecks emerge in real-time on the canvas.

### 🌗 Dark / Light Theme
Fully themed UI with dark and light mode toggle.

---

## 🏛️ Architecture

This is a **TypeScript monorepo** managed with [npm workspaces](https://docs.npmjs.com/cli/using-npm/workspaces):

```
sys-wiz/
├── apps/
│   ├── web/                    # Next.js 16 frontend
│   │   └── src/
│   │       ├── app/
│   │       │   ├── architect/  # Canvas-based architecture designer
│   │       │   ├── simulate/   # Live simulation view
│   │       │   ├── metrics/    # Performance metrics dashboard
│   │       │   ├── ai/         # AI architecture advisor
│   │       │   └── api/ai/     # AI API route handler
│   │       └── components/
│   │           ├── canvas/     # React Flow canvas components
│   │           ├── nodes/      # Architecture node types
│   │           ├── panels/     # Side panels & config
│   │           ├── simulation/ # Simulation controls & visuals
│   │           ├── metrics/    # D3 chart components
│   │           ├── ai/         # AI chat interface
│   │           ├── layout/     # App shell & navigation
│   │           └── ui/         # Shared UI primitives (shadcn)
│   │
│   └── simulation-server/      # Express + Socket.IO backend
│       └── src/
│           ├── engine/         # Simulation engine core
│           ├── handlers/       # WebSocket & REST handlers
│           │   ├── simulation-handler   # Simulation lifecycle
│           │   ├── flow-handler         # Data flow management
│           │   └── traffic-injection-handler  # Locust REST API
│           └── index.ts        # Server entry point
│
├── packages/
│   └── shared/                 # Shared types & utilities
│
├── locust-loadtest.py          # Locust load test definitions
├── LOCUST_GUIDE.md             # Load testing documentation
└── vercel.json                 # Vercel deployment config
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Next.js 16, React 19, TypeScript |
| **Canvas** | React Flow (`@xyflow/react`) |
| **Charts** | D3.js |
| **State** | Zustand |
| **UI Components** | shadcn/ui, Lucide Icons, Tailwind CSS 4 |
| **Real-time** | Socket.IO (client + server) |
| **Backend** | Express, Node.js, tsx |
| **AI** | Google Generative AI (Gemini) |
| **Load Testing** | Locust (Python) |
| **Deployment** | Vercel |
| **Monorepo** | npm workspaces |

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** ≥ 18
- **npm** ≥ 9
- **Python** 3.8+ *(optional, for Locust load testing)*

### Installation

```bash
# Clone the repository
git clone https://github.com/Harsh-Goel-1/sys-wiz.git
cd sys-wiz

# Install dependencies (all workspaces)
npm install

# Set up environment variables
cp .env.example .env
```

### Configure Environment

Edit `.env` with your values:

```env
# Gemini API Key (for AI Architecture Advisor)
GEMINI_API_KEY=your_gemini_api_key_here

# Simulation Server
SIMULATION_SERVER_PORT=3001

# Next.js
NEXT_PUBLIC_SIMULATION_SERVER_URL=http://localhost:3001
```

> **Note:** Get a Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey) to enable the AI advisor feature.

### Run Development Servers

```bash
# Start both the web frontend and simulation server concurrently
npm run dev
```

This will start:
- 🌐 **Web app** at `http://localhost:3000`
- ⚙️ **Simulation server** at `http://localhost:3001`

You can also start them individually:

```bash
npm run dev:web    # Next.js frontend only
npm run dev:sim    # Simulation server only
```

---

## 🔥 Load Testing

sys-wiz includes built-in support for **Locust** load testing. See the full [Locust Guide](./LOCUST_GUIDE.md) for detailed instructions.

### Quick Start

```bash
# Install Locust
pip install -r requirements.txt

# Start your simulation in the web UI first, then run:
locust -f locust-loadtest.py --host=http://localhost:3001
```

Open `http://localhost:8089` to configure and launch load tests. Watch the results appear in real-time on your architecture canvas!

---

## 📦 Build

```bash
# Build all packages and apps for production
npm run build
```

---

## 🌐 Deployment

The project is configured for deployment on **Vercel**. The `vercel.json` handles the build pipeline:

1. Builds the shared package first
2. Builds the Next.js web app
3. Serves from `apps/web/.next`

---

## 📄 License

This project is open source. See the repository for license details.
