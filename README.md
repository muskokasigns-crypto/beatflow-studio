# BeatFlow Studio

## AI-Powered Music Video Generator

BeatFlow Studio is an AI-driven platform that transforms music, lyrics, photos, and text prompts into engaging, beat-synced music videos. Similar to Freebeat.ai, it leverages advanced AI to automatically generate visuals synchronized with audio.

### Key Features

- **Automatic Beat Detection**: Analyzes audio to identify beats, tempo, and song structure
- **AI Video Generation**: Creates scene storyboards and generates visuals using AI models
- **Lyric Video Creation**: Automatically generates animated lyric videos
- **Music Analysis**: Extracts energy levels, BPM, key sections (intro, verse, chorus, outro)
- **Visual Customization**: AI-powered scene editing with style presets (cinematic, anime, neon, etc.)
- **Multi-Platform Export**: Supports various formats (16:9, 1:1, 9:16 for social media)
- **Batch Processing**: Generate multiple videos efficiently
- **REST API**: Full API for integration and automation

### Architecture

```
beathflow-studio/
├── backend/           # FastAPI server
├── frontend/          # React/TypeScript UI
├── ml-engine/         # ML models for beat detection & video generation
├── video-processor/   # Video encoding and effects
├── docs/              # Documentation
└── docker-compose.yml # Container orchestration
```

### Tech Stack

**Backend**:
- Python 3.11+
- FastAPI
- Librosa (audio analysis)
- OpenAI API (vision & text generation)
- SQLAlchemy (database)
- PostgreSQL

**Frontend**:
- React 18+
- TypeScript
- Tailwind CSS
- Redux for state management

**ML/Video**:
- PyTorch
- FFmpeg
- OpenCV
- Stable Diffusion / DALL-E (for visual generation)
- Librosa (audio processing)

### Getting Started

#### Prerequisites
- Docker & Docker Compose
- Python 3.11+
- Node.js 18+
- PostgreSQL
- API keys: OpenAI, etc.

#### Installation

```bash
# Clone repository
git clone https://github.com/muskokasigns-crypto/beatflow-studio.git
cd beatflow-studio

# Setup with Docker
docker-compose up -d

# Or manual setup
cd backend && pip install -r requirements.txt
cd ../frontend && npm install
```

#### Environment Setup

Create `.env` file:
```
DATABASE_URL=postgresql://user:password@localhost/beatflow
OPENAI_API_KEY=your_key_here
JWT_SECRET=your_secret_key
```

#### Running Locally

```bash
# Terminal 1: Backend
cd backend
python -m uvicorn main:app --reload

# Terminal 2: Frontend
cd frontend
npm start
```

Access at `http://localhost:3000`

### Project Structure

#### Backend (`/backend`)
- `main.py` - FastAPI app entry point
- `api/routes/` - API endpoints
- `services/` - Business logic
- `models/` - Database models
- `ml/` - ML models and audio processing

#### Frontend (`/frontend`)
- `src/components/` - React components
- `src/pages/` - Page components
- `src/services/` - API client services
- `src/store/` - Redux store

#### ML Engine (`/ml-engine`)
- `beat_detection/` - Audio analysis
- `video_generation/` - Scene generation
- `models/` - Pre-trained models

### API Endpoints

```
POST   /api/videos/create         - Create new video
GET    /api/videos/{id}           - Get video details
GET    /api/videos/list           - List user's videos
DELETE /api/videos/{id}           - Delete video
POST   /api/analyze/audio         - Analyze audio file
POST   /api/generate/storyboard   - Generate video storyboard
POST   /api/render/video          - Render final video
POST   /api/auth/login            - User login
POST   /api/auth/register         - User registration
```

### Workflow

1. **Upload**: User uploads audio file (MP3, WAV, or links from Spotify/YouTube)
2. **Analyze**: Backend analyzes audio for beats, tempo, structure
3. **Generate**: AI generates scene storyboard with descriptions
4. **Customize**: User reviews and customizes scenes via UI
5. **Render**: Video is rendered with effects and exported
6. **Download**: User downloads in preferred format

### Features in Development

- [ ] Real-time video preview
- [ ] Advanced scene editor
- [ ] AI choreography generation
- [ ] Lip-sync capabilities
- [ ] Multi-language support
- [ ] Collaboration features
- [ ] Video templates library
- [ ] Streaming platform integration

### Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

### License

MIT License - see LICENSE file

### Support

For issues and questions:
- GitHub Issues: [Report Bug](https://github.com/muskokasigns-crypto/beatflow-studio/issues)
- Email: support@beatflow.studio

### Roadmap

- Q1 2024: MVP launch with core features
- Q2 2024: Advanced customization tools
- Q3 2024: Mobile app
- Q4 2024: Enterprise features & API

---

**Made with ❤️ by the BeatFlow Team**
