# physics-rss-aggregator

A production-ready RSS/Atom aggregator for physics research topics (ion traps, quantum networks, cavity QED). Combines arXiv search with journal feeds.

## 🚀 Live Demo

Once deployed, your application will be accessible at your Render URL (e.g., `https://your-app-name.onrender.com`).

## Features

- **FastAPI Backend**: High-performance async web framework
- **arXiv Integration**: Search and aggregate physics research papers
- **RSS/Atom Feeds**: Aggregate content from multiple journal feeds
- **Caching**: TTL-based caching for improved performance
- **Responsive UI**: Clean web interface for browsing aggregated content
- **Automatic Deployment**: CI/CD pipeline with GitHub Actions

## 🌐 Deployment Setup

### Prerequisites

- GitHub account
- Render account (free tier available at https://render.com)

### Step 1: Fork the Repository

This repository is already forked and ready for deployment!

### Step 2: Set Up Render Web Service

1. **Create a Render Account**:
   - Go to https://render.com and sign up
   - Connect your GitHub account

2. **Create a New Web Service**:
   - Click "New +" → "Web Service"
   - Connect this GitHub repository
   - Configure the service:
     - **Name**: `physics-rss-aggregator` (or your preferred name)
     - **Environment**: `Python 3`
     - **Build Command**: `pip install -r requirements.txt`
     - **Start Command**: `uvicorn app:app --host 0.0.0.0 --port $PORT`
     - **Instance Type**: Free (or choose based on your needs)

3. **Deploy**:
   - Click "Create Web Service"
   - Render will automatically deploy your application
   - Note your app URL (e.g., `https://physics-rss-aggregator.onrender.com`)

### Step 3: Enable Automatic Deployment with GitHub Actions (Optional)

For automatic deployment on every push to main:

1. **Get Your Render Deploy Hook**:
   - In Render dashboard, go to your web service
   - Navigate to "Settings" → "Deploy Hook"
   - Copy the deploy hook URL

2. **Add Deploy Hook to GitHub Secrets**:
   - Go to your GitHub repository
   - Navigate to "Settings" → "Secrets and variables" → "Actions"
   - Click "New repository secret"
   - Name: `RENDER_DEPLOY_HOOK`
   - Value: Paste your Render deploy hook URL
   - Click "Add secret"

3. **Verify Workflow**:
   - The GitHub Actions workflow (`.github/workflows/deploy.yml`) is already configured
   - Push any changes to the `main` branch to trigger automatic deployment
   - Check the "Actions" tab in GitHub to monitor deployment status

### Alternative: Deploy with render.yaml

This repository includes a `render.yaml` file for infrastructure-as-code deployment:

1. Go to your Render dashboard
2. Click "New +" → "Blueprint"
3. Connect this repository
4. Render will automatically detect the `render.yaml` and deploy accordingly

## 🛠️ Local Development

### Prerequisites

- Python 3.11 or higher
- pip

### Installation

```bash
# Clone the repository
git clone https://github.com/qiskit-advocate/physics-rss-aggregator.git
cd physics-rss-aggregator

# Install dependencies
pip install -r requirements.txt

# Run the application
uvicorn app:app --reload
```

The application will be available at http://localhost:8000

### Configuration

Edit `feeds.yaml` to customize RSS feeds and arXiv search parameters:

```yaml
normal_feeds:
  - https://example.com/feed.xml
  - https://another-feed.com/rss

arxiv:
  max_results: 75
  sort_by: submittedDate
  sort_order: descending
```

## 📚 API Documentation

Once deployed, visit:
- Interactive API docs: `https://your-app-url/docs`
- Alternative API docs: `https://your-app-url/redoc`

### Endpoints

- `GET /` - Web interface
- `GET /api/search?topic=quantum+computing` - Search and aggregate feeds

## 🔄 CI/CD Pipeline

This repository includes a GitHub Actions workflow that:

1. ✅ Checks out code on every push to main
2. ✅ Sets up Python 3.11 environment
3. ✅ Installs dependencies
4. ✅ Runs basic import tests
5. ✅ Triggers Render deployment (if deploy hook is configured)

## 📝 Project Structure

```
physics-rss-aggregator/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions workflow
├── templates/
│   └── index.html              # Web UI template
├── app.py                      # FastAPI application
├── feeds.yaml                  # RSS feed configuration
├── feeds.example.yaml          # Example configuration
├── requirements.txt            # Python dependencies
├── render.yaml                 # Render deployment config
├── Dockerfile                  # Docker configuration
└── README.md                   # This file
```

## 🔧 Technologies Used

- **FastAPI**: Modern Python web framework
- **uvicorn**: ASGI server
- **aiohttp**: Async HTTP client
- **feedparser**: RSS/Atom feed parser
- **Jinja2**: Template engine
- **PyYAML**: YAML configuration parser

## 📦 Dependencies

All dependencies are listed in `requirements.txt` and automatically installed during deployment.

## 🌟 Features to Add

Potential enhancements:
- User authentication
- Saved searches and preferences
- Email notifications for new papers
- Advanced filtering options
- Export to BibTeX/RIS formats

## 🤝 Contributing

Feel free to fork this repository and submit pull requests with improvements!

## 📄 License

This project is open source and available for educational and research purposes.

## 🆘 Troubleshooting

### Deployment Issues

- **Build fails**: Check Python version compatibility (requires 3.11+)
- **App doesn't start**: Verify all dependencies in `requirements.txt`
- **Timeout errors**: Consider upgrading to a paid Render plan for better performance

### GitHub Actions Issues

- **Workflow doesn't trigger**: Ensure the workflow file is in `.github/workflows/`
- **Deploy hook fails**: Verify the `RENDER_DEPLOY_HOOK` secret is correctly set

## 📧 Support

For issues or questions, please open an issue on GitHub.

---

**Note**: This application is configured for automatic deployment on Render. The free tier may have cold start delays (up to 30 seconds) after periods of inactivity.
