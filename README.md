# DSA-Visualizer
Interactive MERN-based DSA visualizer for exploring sorting, searching, and graph algorithms with real-time animations, operation counters, and execution metrics. Completed runs are stored in MongoDB through an Express REST API, demonstrating a complete React–Node–MongoDB workflow.

dsa.sim — DSA Algorithm Simulator

An interactive full-stack DSA visualizer built with the MERN stack. Explore sorting, searching, and graph algorithms through step-by-step animations while tracking comparisons, swaps, execution time, and complete run history stored in MongoDB.

Features

Sorting Algorithms

Bubble Sort

Selection Sort

Insertion Sort

Merge Sort

Quick Sort

Animated bar-chart visualization

Live comparison and swap counters

Searching Algorithms

Linear Search

Binary Search

Generated sorted arrays

Highlighted active search range

Live search progress

Graph Algorithms

Breadth-First Search (BFS)

Depth-First Search (DFS)

Dijkstra's Algorithm

SVG-based node and edge visualization

Live distance labels

Run History

Every completed algorithm run is sent to the backend and stored in MongoDB.

The History section supports:

Viewing previous runs

Filtering runs by category

Tracking algorithm, input size, comparisons, and execution time

Deleting individual runs

Clearing complete history

Viewing aggregated statistics

This demonstrates a complete MERN data flow:

React → Express → MongoDB → React

Tech Stack

Frontend

React

Vite

JavaScript

CSS

SVG / Canvas-based visualization

Backend

Node.js

Express.js

MongoDB

Mongoose

Development

REST API

Nodemon

npm

Project Structure

dsa-visualizer/
│
├── backend/
│   ├── config/
│   │   └── db.js
│   ├── models/
│   │   └── Run.js
│   ├── routes/
│   │   └── runs.js
│   ├── server.js
│   ├── .env.example
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── algorithms/
    │   │   ├── sorting.js
    │   │   ├── searching.js
    │   │   └── graph.js
    │   ├── components/
    │   │   ├── Sidebar
    │   │   ├── SortingVisualizer
    │   │   ├── SearchingVisualizer
    │   │   ├── GraphVisualizer
    │   │   └── HistoryPanel
    │   ├── App.jsx
    │   ├── api.js
    │   └── index.css
    ├── index.html
    ├── package.json
    └── vite.config.js

Getting Started

Prerequisites

Make sure you have installed:

Node.js

npm

MongoDB locally, or a MongoDB Atlas connection

1. Clone the Repository

git clone <your-repository-url>
cd dsa-visualizer

2. Setup the Backend

cd backend
npm install
cp .env.example .env

Update .env with your MongoDB connection string and port if required.

Start the backend:

npm run dev

Or:

npm start

The backend runs on:

http://localhost:5000

Check the API health:

curl http://localhost:5000/api/health

3. Setup the Frontend

Open a second terminal:

cd frontend
npm install
npm run dev

The frontend runs on:

http://localhost:5173

If the backend uses a different URL, create frontend/.env:

VITE_API_URL=http://localhost:5000/api

API Endpoints

Method

Endpoint

Description

GET

/api/runs

Get recent algorithm runs

GET

/api/runs/stats

Get average time and comparisons per algorithm

POST

/api/runs

Save a completed run

DELETE

/api/runs/:id

Delete a specific run

DELETE

/api/runs

Clear all run history

The /api/runs endpoint can optionally filter results by category:

/api/runs?category=sorting
/api/runs?category=searching
/api/runs?category=graph

How It Works

Select an algorithm from the sidebar.

Configure the available parameters such as input size, speed, or target.

Start the visualization.

Watch each algorithm step animate in real time.

Track comparisons, swaps, distances, and execution time.

After completion, the run is sent to the Express backend.

The backend stores the run in MongoDB.

The History section retrieves and displays the stored data.

Algorithm Implementation

The algorithms are implemented as step generators. Each generated step contains the information required by the visualizer to update the UI.

For sorting algorithms, steps include:

{
  array,
  compare,
  swap,
  sorted
}

This makes it possible to add new algorithms without changing the core visualization and history logic.

Extending the Project

Add a New Sorting Algorithm

Add a step-generator function inside:

frontend/src/algorithms/sorting.js

Generate snapshots containing the required state.

Register the algorithm in the SORTERS map.

The existing visualizer and history system can then use it.

Improve Graph Visualization

The current graph uses a fixed layout and adjacency structure, making BFS, DFS, and Dijkstra easy to compare. A future improvement could be a random graph generator for more varied inputs.

Add Statistics Charts

The backend already provides aggregated statistics through:

GET /api/runs/stats

This can be used to build charts comparing average execution time and comparisons across algorithms.

Learning Goals

This project combines DSA concepts with full-stack development by connecting:

Algorithm design

Time and operation tracking

Interactive visualization

React component architecture

REST API development

MongoDB data persistence

CRUD operations

Frontend-backend communication

Future Improvements

Add more sorting and graph algorithms

Add randomized graph generation

Add algorithm complexity information

Add performance comparison charts

Add customizable graph nodes and edges

Add more detailed execution statistics

Improve mobile responsiveness

License

This project is available for educational and personal use.
