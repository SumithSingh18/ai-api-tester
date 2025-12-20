# Google AI Studio API Tester

A Flask web application for testing Google Gemini API keys and models. Built with Docker support for easy deployment.

## Features

- Test Google Gemini API keys
- Support for multiple Gemini models (1.5 Flash, 1.5 Pro, 2.0 Flash Experimental)
- Clean terminal-style UI
- Docker containerization
- Error handling for rate limits and API issues

## Project Structure

```
google-ai-tester/
├── app/
│   └── app.py              # Main Flask application
├── templates/
│   └── index.html          # Web interface
├── Docker/
│   ├── Dockerfile          # Docker build configuration
│   └── .dockerignore       # Docker ignore rules
├── requirements.txt        # Python dependencies
├── .gitignore             # Git ignore rules
└── README.md              # This file
```

## Local Development

### Prerequisites

- Python 3.13+
- Virtual environment (venv)

### Setup

1. Clone the repository
2. Create and activate virtual environment:
   ```bash
   python -m venv venv
   venv\Scripts\activate  # Windows
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the application:
   ```bash
   python app/app.py
   ```
5. Open http://localhost:5000 in your browser

## Docker Deployment

### Build and Run Locally

```bash
# Build the image
docker build -f Docker/Dockerfile -t aichatbot-api-tester .

# Run the container
docker run -p 5000:5000 aichatbot-api-tester
```

### Using Docker Hub Image

```bash
# Pull and run from Docker Hub
docker run -p 5000:5000 sumithsingh001/aichatbot-api-tester:latest
```

## Usage

1. Get your API key from [Google AI Studio](https://aistudio.google.com/)
2. Open the web interface at http://localhost:5000
3. Enter your API key
4. Select a Gemini model
5. Enter your prompt
6. Click "SEND PROMPT"

## Supported Models

- `gemini-2.0-flash-exp` - Gemini 2.0 Flash (Experimental)
- `gemini-1.5-flash` - Gemini 1.5 Flash (Recommended)
- `gemini-1.5-pro` - Gemini 1.5 Pro

## Rate Limits

Google AI Studio free tier has the following limits:

- 15 requests per minute
- 1500 requests per day

If you encounter rate limit errors, wait before making additional requests.

## Common Issues

### Rate Limit Exceeded (429)

- Wait for rate limits to reset
- Try using `gemini-1.5-flash` model (higher limits)
- Check usage in Google AI Studio dashboard

### Model Not Found (404)

- Verify model name is correct
- Use `gemini-1.5-flash` for most reliable results

### Invalid API Key (403)

- Generate new API key from Google AI Studio
- Ensure API key has proper permissions

## Development Notes

- Flask app runs on `0.0.0.0:5000` for Docker compatibility
- Templates are located in `../templates/` relative to app.py
- Error handling includes specific messages for common API issues

## Repository

- GitHub: https://github.com/SumithSingh18/ai-api-tester
- Docker Hub: sumithsingh001/aichatbot-api-tester:latest

## License

This project is for educational and testing purposes.
