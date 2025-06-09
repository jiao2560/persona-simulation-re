# Scalable Persona Simulation for Requirements Elicitation

**Supporting Instructor-Defined Scenarios via Multi-Agent LLM Frameworks**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![Development Status](https://img.shields.io/badge/status-in%20development-orange.svg)]()

## 🎯 Overview

Requirements elicitation is a critical skill in software engineering, yet students rarely experience authentic stakeholder interactions during their education. This system addresses the educational gap by enabling instructors to generate realistic stakeholder personas from user stories using LLM-powered multi-agent frameworks, allowing students to practice requirements elicitation through structured interviews.

### The Problem
- **70% of project failures** stem from poor requirements (CHAOS Report)
- Students miss nuances of real-world elicitation: ambiguity, conflict, stakeholder biases
- Existing tools require manual configuration and lack scalability
- No flexible platform for instructor-defined, domain-specific scenarios

### Our Solution
A scalable system where instructors upload user stories, and the system automatically generates diverse, domain-relevant personas with distinct goals and communication styles. Students then conduct structured interviews with these personas via an intuitive chat interface.

## ✨ Key Features

### 🔄 **User Story-Driven Persona Generation**
- Transform Agile user stories into detailed stakeholder personas
- Automatic extraction of role, goal, and motivation components
- Domain-specific knowledge and communication styles
- Context-aware persona profiles with realistic backstories

### 🤖 **Multi-Agent Orchestration**
- **LangGraph-based framework** for agent coordination
- Memory persistence across sessions
- Support for both one-on-one and roundtable interviews
- Inter-agent communication during group sessions

### 📚 **Educational Focus**
- Built specifically for software engineering education
- Instructor-friendly setup (< 15 minutes per scenario)
- Student performance tracking and analytics
- Assessment features with learning metrics

### 🎭 **Dual Interview Modes**
- **One-on-One**: Direct stakeholder interviews with memory retention
- **Roundtable**: Multi-persona sessions with dynamic interactions

## 🏗️ System Architecture

```
┌─────────────────────┐    ┌──────────────────────┐    ┌─────────────────────┐
│  Instructor         │    │   Persona            │    │  Multi-Agent        │
│  Interface          │───▶│   Generation         │───▶│  Orchestration      │
│                     │    │   Engine             │    │  Layer              │
└─────────────────────┘    └──────────────────────┘    └─────────────────────┘
                                                                     │
                                                                     ▼
                           ┌─────────────────────────────────────────────────┐
                           │            Student Interaction Frontend          │
                           │        (Streamlit-based Chat Interface)         │
                           └─────────────────────────────────────────────────┘
```

### Components
- **Instructor Interface**: Web-based dashboard for user story input and progress monitoring
- **Persona Generation Engine**: LLM-powered transformation with domain knowledge
- **Multi-Agent Orchestration**: LangGraph framework managing conversation state
- **Student Frontend**: Streamlit chat interface supporting multiple interview modes

## 🛠️ Technology Stack

- **🧠 AI Framework**: LangGraph (primary orchestration)
- **🤖 LLM**: OpenAI GPT-4
- **🖥️ Frontend**: Streamlit
- **🐍 Backend**: Python 3.11+
- **💾 Data**: PostgreSQL/LangSmith for logging
- **🔧 Development**: Git, pytest

## 🚀 Quick Start

### Prerequisites
- Python 3.11 or higher
- OpenAI API key
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/jiao2560/persona-simulation-re.git
   cd persona-simulation-re
   ```

2. **Set up virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment**
   ```bash
   cp .env.example .env
   # Edit .env and add your OpenAI API key:
   # OPENAI_API_KEY=your_api_key_here
   ```

5. **Verify installation**
   ```bash
   python test_setup.py
   ```

## 📖 Usage Examples

### Creating a User Story Scenario

```python
from src.persona_generation.story_parser import StoryParser

parser = StoryParser()

# Healthcare scenario example
user_story = """
As a hospital nurse, 
I want to update patient vitals quickly, 
So that medical staff have real-time data for treatment decisions.
"""

parsed_story = parser.parse_story(user_story)
print(f"Role: {parsed_story.role}")
print(f"Goal: {parsed_story.goal}")
print(f"Domain: {parsed_story.domain_context}")
```

### Sample Domain Scenarios

#### 🏥 Healthcare Management System
```
As a hospital nurse, I want to update patient vitals quickly, 
so that medical staff have real-time data.

As a doctor, I want to access patient history across departments, 
so that I can make informed diagnosis without delays.
```

#### 🛒 E-commerce Platform
```
As an online shopper, I want to save items to a wishlist, 
so that I can purchase them later.

As a store administrator, I want to track inventory in real-time, 
so that I can prevent stockouts.
```

#### 🎓 University Information System
```
As a student, I want to register for courses online, 
so that I can plan my academic schedule efficiently.

As an academic advisor, I want to view student transcripts, 
so that I can provide accurate guidance.
```

## 📊 Research Methodology

This system is part of a comprehensive research study employing:

- **Mixed Methods Design**: Sequential explanatory approach
- **Participants**: 80 students + 8 instructors across 2 universities
- **Evaluation Metrics**: 
  - Requirements Completeness Score (RCS)
  - Question Relevance Index (QRI)
  - Student confidence surveys
  - System usage analytics

### Key Research Questions
1. **RQ1**: How can we support instructors in generating realistic stakeholder personas from user stories?
2. **RQ2**: What orchestration frameworks best balance memory management, context sharing, extensibility, and educational usability?

## 🔬 Development Status

- ✅ **Repository Setup**: Basic structure and dependencies
- ✅ **Framework Selection**: LangGraph chosen based on systematic comparison
- ✅ **Architecture Design**: 4-tier system specification complete
- 🚧 **Implementation**: Currently developing persona generation pipeline
- ⏳ **Testing**: User study evaluation planned
- ⏳ **Deployment**: Educational pilot program preparation

## 📁 Project Structure

```
persona-simulation-re/
├── README.md                 # This file
├── requirements.txt          # Python dependencies
├── .env.example             # Environment variables template
├── src/                     # Source code
│   ├── persona_generation/  # User story parsing and persona creation
│   ├── orchestration/       # LangGraph multi-agent coordination
│   └── frontend/           # Streamlit user interface
├── data/                   # Datasets and scenarios
│   ├── scenarios/          # Domain-specific user story collections
│   └── templates/          # User story templates
├── docs/                   # Documentation
├── tests/                  # Unit and integration tests
└── config/                 # Configuration files
```

## 🎓 Research Context

This project is conducted as part of doctoral research at **Northeastern University, Vancouver** under the supervision of faculty in Software Engineering Education. The research aims to improve requirements elicitation training in computer science curricula through innovative AI-powered educational tools.

### Academic Contributions
- **Educational Technology**: Novel application of multi-agent systems in SE education
- **Requirements Engineering**: Scalable persona simulation methodology
- **Human-AI Interaction**: Educational usability in multi-agent LLM systems

## 🤝 Contributing

This is an active research project. Contributions, suggestions, and feedback are welcome:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Research Mentors**: Ildar Akhmetov and Mirjana Prpa for guidance and feedback
- **Technical Community**: LangGraph, AutoGen, and CrewAI open-source teams
- **Institution**: Northeastern University for research support
- **Conference**: Prepared for submission to SIGCSE '26

## 📞 Contact

**Wenbo (Leo) Jiao**  
📧 jiao.wenbo@northeastern.edu  
🏛️ Northeastern University, Vancouver, Canada  
🔗 [GitHub Repository](https://github.com/jiao2560/persona-simulation-re)

---

> *"Transforming software engineering education through realistic stakeholder simulation"*
