#  VibeCheck: AI-Powered Semantic Movie Search 🎬🤖
**VibeCheck** is a full-stack "Semantic Search" engine that understands the vibe of a movie rather than just matching keywords. Instead of searching for "Batman," you can search for "*A dark, rainy night in a corrupt city with a masked hero*," and the AI will mathematically find the best matches.

## 🚀 Live Demo
- **Web Interface**: https://vibecheck-aimoviesearch.netlify.app/

- **API Documentation**: https://kavy1445-semantic-movie-search.hf.space/docs

## 🧠 How it Works
Traditional search looks for exact words. **VibeCheck** uses **Vector Embeddings**:

2. **Transform**: I used the ```all-mpnet-base-v2``` Transformer model to turn 5,000+ movie plots into 768-dimensional vectors.

4. **Store**: These vectors are stored in a **FAISS** (Facebook AI Similarity Search) index for lightning-fast mathematical comparisons.

6. **Search**: When you enter a prompt, the system converts your "vibe" into a vector and finds the "Nearest Neighbors" in the vector space using **Cosine Similarity**.

## 🛠️ Tech Stack
- **Machine Learning**: Python, Sentence-Transformers (Hugging Face), FAISS, NumPy.

- **Backend**: FastAPI (Asynchronous Python), Uvicorn.

- **Deployment**: Docker, Hugging Face Spaces (Backend), Netlify (Frontend).

- **Frontend**: Tailwind CSS, JavaScript (Vanilla ES6+), FontAwesome.

- **Data Source**: TMDB (The Movie Database) API.

## 🏗️ System Architecture & Engineering Challenges
This project wasn't just about ML; it was about solving real-world deployment hurdles:

- **The "Pickle" Problem**: Solved environment-specific crashes by migrating from Python Pickles to universal CSV metadata storage.

- **Memory Optimization**: Optimized the ```Dockerfile``` to use ```cpu-only``` PyTorch builds to fit within free-tier cloud RAM limits.

- **The ISP/CORS Bypass**: Because regional ISPs often block TMDB, I architected a **Backend Proxy Gateway**. My FastAPI server acts as a bridge, fetching posters and descriptions from the US-based server to ensure 100% uptime for users in restricted regions.
## 📂 Project Structure
```bash
├── main.py              # FastAPI Backend & TMDB Proxy Logic
├── build_vector_db.py   # Script to generate FAISS index & Embeddings
├── movie_metadata.csv   # Processed movie data
├── movie_vibes.index    # Pre-computed FAISS Vector Index
├── Dockerfile           # Deployment configuration
├── requirements.txt     # Python dependencies
└── frontend/
    └── index.html       # Glassmorphism UI & JS Search Logic
```
## 🛠️ Local Setup
######  Clone the repo:
```bash
git clone https://github.com/your-username/vibecheck.git
```
###### Install Dependencies:
```bash
pip install -r requirements.txt
```
###### Run the API:
```bash
uvicorn main:app --reload
```
Open the UI: Simply open ```index.html``` in your browser.

## 🌟 Future - Roadmap
- [ ] Add "Genre" and "Year" filters to the semantic search.

- [ ] Implement a "Surprise Me" button based on random vector sampling.

- [ ] Support for multi-language prompts (Hindi, Spanish, etc.).

------------


> **Developed with ❤️ by Kavy Bhalani**
