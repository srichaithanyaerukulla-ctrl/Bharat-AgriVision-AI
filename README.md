# 🌾 Bharat-AgriVision-AI

**Viksit Bharat 2047 - Empowering Farmers with AI**

A bilingual (Hindi & English) AI-powered crop health assistant designed for Indian farmers, leveraging cutting-edge AI technology to provide organic farming solutions.

---

## 📋 Problem Statement

Indian farmers face significant challenges in:
- Early detection of crop diseases
- Access to expert agricultural advice
- Language barriers (most resources in English only)
- Expensive chemical treatments
- Lack of organic farming knowledge

**Bharat-AgriVision-AI** addresses these challenges by providing instant, AI-powered crop health diagnostics in both Hindi and English, focusing on organic and eco-friendly solutions.

---

## 💡 Solution

An intelligent web application that:
- Accepts crop name and symptom descriptions from farmers
- Uses advanced AI (LLaMA 3 via Groq API) to diagnose crop health issues
- Provides organic remedies using locally available materials
- Offers prevention tips to avoid future problems
- Delivers all information in simple, farmer-friendly language
- Works seamlessly on mobile devices

---

## 🛠️ Technology Stack

| Component | Technology |
|-----------|-----------|
| **Frontend** | Streamlit |
| **Backend** | Python 3.10+ |
| **AI Model** | LLaMA 3 (70B) via Groq API |
| **Configuration** | Environment Variables |
| **Architecture** | Modular MVC Pattern |

---

## 📁 Project Structure

```
Bharat-AgriVision-AI/
│
├── app.py                 # Main application entry point
├── requirements.txt       # Python dependencies
├── README.md             # Project documentation
├── requirements.md       # Detailed requirements
├── design.md             # System architecture
├── .env.example          # Environment variables template
├── .gitignore           # Git ignore rules
│
└── src/
    ├── __init__.py      # Package initializer
    ├── config.py        # Configuration management
    ├── ai_engine.py     # AI/ML logic
    └── ui.py            # UI components
```

---

## 🚀 Setup Instructions

### Prerequisites

- Python 3.10 or higher
- Groq API key ([Get it here](https://console.groq.com))
- pip package manager

### Installation Steps

1. **Clone the repository**
```bash
git clone <repository-url>
cd Bharat-AgriVision-AI
```

2. **Create virtual environment**
```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Set up environment variables**

Create a `.env` file in the root directory:
```bash
GROQ_API_KEY=your_groq_api_key_here
```

Or set it directly:
```bash
# Windows
set GROQ_API_KEY=your_groq_api_key_here

# macOS/Linux
export GROQ_API_KEY=your_groq_api_key_here
```

5. **Run the application**
```bash
streamlit run app.py
```

6. **Access the application**

Open your browser and navigate to: `http://localhost:8501`

---

## 📱 Usage

1. **Select Language**: Choose between Hindi (हिंदी) or English
2. **Enter Crop Name**: Type the name of your crop (e.g., Wheat, Rice, Tomato)
3. **Describe Symptoms**: Provide details about the problem (e.g., yellow spots, wilting)
4. **Get Diagnosis**: Click the button to receive AI-powered analysis
5. **Review Results**: Read the diagnosis, organic remedies, and prevention tips

---

## ✨ Features

- ✅ Bilingual support (Hindi & English)
- ✅ AI-powered crop health diagnosis
- ✅ Organic farming solutions
- ✅ Prevention tips and best practices
- ✅ Mobile-responsive design
- ✅ Secure API key handling
- ✅ Clean, modular architecture
- ✅ Error handling and validation
- ✅ Fast response times (Groq API)
- ✅ No AWS dependency

---

## 🔒 Security

- API keys stored in environment variables
- No hardcoded credentials
- Input validation and sanitization
- Error messages don't expose sensitive information

---

## 🌐 Deployment

### Streamlit Cloud

1. Push code to GitHub
2. Connect to [Streamlit Cloud](https://streamlit.io/cloud)
3. Add `GROQ_API_KEY` in Secrets management
4. Deploy!

### Docker (Optional)

```dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["streamlit", "run", "app.py"]
```

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

---

## 📄 License

This project is open-source and available under the MIT License.

---

## 👥 Authors

Built for **Viksit Bharat 2047** initiative to empower Indian farmers with AI technology.

---

## 🙏 Acknowledgments

- Groq for providing fast AI inference
- Streamlit for the amazing web framework
- Indian farming community for inspiration

---

## 📞 Support

For issues or questions:
- Open an issue on GitHub
- Contact: [your-email@example.com]

---

**🇮🇳 Jai Jawan, Jai Kisan, Jai Vigyan!**
