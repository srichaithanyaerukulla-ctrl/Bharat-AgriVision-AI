# Requirements Document
## Bharat-AgriVision-AI

---

## 1. Functional Requirements

### 1.1 Language Support
- **FR-1.1**: System shall support Hindi and English languages
- **FR-1.2**: User shall be able to switch between languages using radio buttons
- **FR-1.3**: All UI elements shall be displayed in the selected language
- **FR-1.4**: AI responses shall be generated in the selected language

### 1.2 User Input
- **FR-2.1**: System shall accept crop name as text input (max 100 characters)
- **FR-2.2**: System shall accept symptom description as text area (max 500 characters)
- **FR-2.3**: System shall validate that both fields are filled before processing
- **FR-2.4**: System shall provide placeholder examples in the selected language

### 1.3 AI Diagnosis
- **FR-3.1**: System shall use Groq API with LLaMA 3 model for AI processing
- **FR-3.2**: System shall generate structured diagnosis with three sections:
  - Disease/problem identification
  - Organic remedies (3-5 solutions)
  - Prevention tips
- **FR-3.3**: AI responses shall focus on organic and eco-friendly solutions
- **FR-3.4**: AI responses shall use simple, farmer-friendly language
- **FR-3.5**: System shall display loading indicator during AI processing

### 1.4 Output Display
- **FR-4.1**: System shall display diagnosis in a formatted, readable manner
- **FR-4.2**: System shall show success message when diagnosis is ready
- **FR-4.3**: System shall display error messages in the selected language
- **FR-4.4**: System shall handle API failures gracefully

### 1.5 User Interface
- **FR-5.1**: UI shall be responsive and mobile-friendly
- **FR-5.2**: UI shall have clean, professional styling
- **FR-5.3**: UI shall display application title and tagline
- **FR-5.4**: UI shall display footer with "Viksit Bharat 2047" branding
- **FR-5.5**: UI shall use green color scheme representing agriculture

---

## 2. Non-Functional Requirements

### 2.1 Security
- **NFR-1.1**: API keys shall be stored in environment variables only
- **NFR-1.2**: No credentials shall be hardcoded in source code
- **NFR-1.3**: System shall validate API key presence before operation
- **NFR-1.4**: Error messages shall not expose sensitive information
- **NFR-1.5**: Input fields shall have character limits to prevent abuse

### 2.2 Performance
- **NFR-2.1**: System shall respond to user input within 5 seconds (network dependent)
- **NFR-2.2**: UI shall load within 2 seconds on standard internet connection
- **NFR-2.3**: System shall handle concurrent users efficiently
- **NFR-2.4**: AI model shall use optimized parameters (temperature: 0.7, max_tokens: 1500)

### 2.3 Reliability
- **NFR-3.1**: System shall have 99% uptime when deployed
- **NFR-3.2**: System shall handle API failures without crashing
- **NFR-3.3**: System shall provide meaningful error messages
- **NFR-3.4**: System shall validate all user inputs

### 2.4 Maintainability
- **NFR-4.1**: Code shall follow modular architecture (MVC pattern)
- **NFR-4.2**: Code shall be well-commented and documented
- **NFR-4.3**: Code shall follow PEP 8 Python style guidelines
- **NFR-4.4**: Configuration shall be centralized in config.py
- **NFR-4.5**: System shall separate concerns (UI, AI, Config)

### 2.5 Scalability
- **NFR-5.1**: Architecture shall support easy addition of new languages
- **NFR-5.2**: System shall be cloud-ready for deployment
- **NFR-5.3**: System shall support horizontal scaling
- **NFR-5.4**: Database integration shall be possible without major refactoring

### 2.6 Usability
- **NFR-6.1**: UI shall be intuitive and require no training
- **NFR-6.2**: System shall work on mobile devices (responsive design)
- **NFR-6.3**: Text shall be readable on all screen sizes
- **NFR-6.4**: Buttons shall be easily clickable on touch devices
- **NFR-6.5**: Color contrast shall meet accessibility standards

### 2.7 Portability
- **NFR-7.1**: System shall run on Windows, macOS, and Linux
- **NFR-7.2**: System shall require only Python 3.10+ and pip
- **NFR-7.3**: System shall be deployable on Streamlit Cloud
- **NFR-7.4**: System shall be containerizable with Docker

### 2.8 Compatibility
- **NFR-8.1**: System shall work on modern web browsers (Chrome, Firefox, Safari, Edge)
- **NFR-8.2**: System shall support mobile browsers
- **NFR-8.3**: System shall not depend on AWS services
- **NFR-8.4**: System shall use widely available Python packages

---

## 3. Technical Requirements

### 3.1 Development Environment
- **TR-1.1**: Python version 3.10 or higher
- **TR-1.2**: Streamlit version 1.31.0
- **TR-1.3**: Groq API client version 0.4.2
- **TR-1.4**: python-dotenv for environment management

### 3.2 API Requirements
- **TR-2.1**: Valid Groq API key required
- **TR-2.2**: Internet connection required for AI inference
- **TR-2.3**: API rate limits shall be respected
- **TR-2.4**: Model: llama3-70b-8192

### 3.3 Deployment Requirements
- **TR-3.1**: Environment variables must be configured
- **TR-3.2**: All dependencies must be installed via requirements.txt
- **TR-3.3**: Application runs via: `streamlit run app.py`
- **TR-3.4**: Port 8501 should be available (default Streamlit port)

---

## 4. Constraints

### 4.1 Technical Constraints
- Must use Groq API (no AWS Bedrock)
- Must use Streamlit for frontend
- Must be Python-based
- Must not use databases (stateless application)

### 4.2 Business Constraints
- Must be free to use for farmers
- Must align with Viksit Bharat 2047 vision
- Must promote organic farming only
- Must be hackathon-ready

### 4.3 Time Constraints
- Must be production-ready
- Must be deployable immediately
- Must require minimal setup

---

## 5. Acceptance Criteria

### 5.1 Functionality
- ✅ User can select language
- ✅ User can input crop name and symptoms
- ✅ System generates AI diagnosis
- ✅ Diagnosis includes organic remedies
- ✅ Diagnosis includes prevention tips
- ✅ UI is responsive on mobile

### 5.2 Quality
- ✅ No hardcoded credentials
- ✅ Clean modular code
- ✅ Proper error handling
- ✅ Professional UI design
- ✅ Complete documentation

### 5.3 Deployment
- ✅ Runs with single command
- ✅ Works on multiple platforms
- ✅ Ready for cloud deployment
- ✅ No AWS dependency

---

## 6. Future Enhancements (Out of Scope)

- Voice input support
- Image-based disease detection
- Weather integration
- Market price information
- Community forum
- Offline mode
- SMS/WhatsApp integration
- Regional language support (Tamil, Telugu, etc.)
- Historical data tracking
- Expert consultation booking

---

**Document Version**: 1.0  
**Last Updated**: 2024  
**Status**: Approved
