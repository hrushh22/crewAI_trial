# CrewAI YouTube Content Creator

This project uses CrewAI to create AI-powered content from YouTube videos. It employs multiple AI agents working together to research, analyze, and create content based on YouTube video transcriptions.

## 🚀 Features

- YouTube video transcription extraction
- AI-powered content research
- Automated blog post generation
- Multi-agent collaboration using CrewAI
- Memory and caching capabilities for improved performance

## 📋 Prerequisites

- Python 3.8 or higher
- OpenAI API key
- Internet connection for YouTube access

## 🛠️ Installation

1. Clone the repository
```bash
git clone [your-repository-url]
cd [repository-name]
```

2. Create and activate a virtual environment
```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python -m venv venv
source venv/bin/activate
```

3. Install required packages
```bash
pip install -r requirements.txt
```

4. Set up environment variables
Create a `.env` file in the root directory with:
```
OPENAI_API_KEY=your-openai-api-key-here
```

## 📁 Project Structure

```
crewAi_trial/
├── .env                  # Environment variables (not in repo)
├── .gitignore           # Git ignore file
├── requirements.txt     # Project dependencies
├── agents.py           # AI agent definitions
├── crew.py            # Main CrewAI setup and execution
├── tasks.py           # Task definitions for agents
└── tools.py           # Custom tools for agents
```

## 🔧 Configuration

The project uses two main agents:
1. Blog Researcher: Analyzes YouTube video content
2. Blog Writer: Creates engaging content based on research

You can modify agent parameters in `agents.py`:
- Model selection
- Memory settings
- Verbosity levels
- Tool configurations

## 🚀 Usage

1. Make sure your virtual environment is activated
2. Run the main script:
```bash
python crew.py
```

3. The script will:
   - Research the specified topic
   - Extract relevant information
   - Generate content
   - Output the results

## 📝 Sample Input

You can modify the topic in `crew.py`:
```python
result = crew.kickoff(inputs={'topic': 'any topic of your choice'})
```

## 🔍 Code Examples

### Setting up an Agent
```python
blog_researcher = Agent(
    role='Blog Researcher from Youtube Videos',
    goal='get the relevant video transcription for the topic {topic}',
    verbose=True,
    memory=True,
    llm_model="gpt-4-turbo-preview",
    backstory="Expert in understanding videos in AI Data Science...",
    tools=[yt_tool],
    allow_delegation=True
)
```

### Creating a Crew
```python
crew = Crew(
    agents=[blog_researcher, blog_writer],
    tasks=[research_task, write_task],
    process=Process.sequential,
    memory=True,
    cache=True,
    max_rpm=100,
    share_crew=True
)
```

## ⚠️ Environment Variables

Required environment variables:
- `OPENAI_API_KEY`: Your OpenAI API key

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- CrewAI framework
- OpenAI API
- YouTube Data API

## 📫 Contact

[Your Name] - [your.email@example.com]
Project Link: [https://github.com/yourusername/yourrepositoryname]

## ❗ Common Issues and Solutions

1. API Rate Limits
   - Solution: Implement proper rate limiting in your requests
   - Check your OpenAI API quota

2. Memory Issues
   - Solution: Adjust batch sizes
   - Monitor memory usage

3. Model Access
   - Solution: Ensure you have access to the required OpenAI models
   - Check API key permissions

## 🔄 Updates

Keep your dependencies up to date:
```bash
pip install --upgrade -r requirements.txt
```
