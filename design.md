# System Design Document
## Bharat-AgriVision-AI

---

## 1. System Overview

Bharat-AgriVision-AI is a bilingual AI-powered web application designed to assist Indian farmers with crop health diagnostics. The system uses LLaMA 3 (70B) via Groq API to provide intelligent, organic farming solutions in Hindi and English.

### 1.1 Vision
Align with Viksit Bharat 2047 by empowering farmers with accessible AI technology for sustainable agriculture.

### 1.2 Key Objectives
- Provide instant crop health diagnostics
- Promote organic farming practices
- Break language barriers
- Enable mobile accessibility
- Ensure data security

---

## 2. Architecture

### 2.1 High-Level Architecture

```
┌─────────────────────────────────────────────────┐
│              User Interface Layer               │
│         (Streamlit Frontend - ui.py)            │
└─────────────────┬───────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────┐
│           Application Layer (app.py)            │
│  - Request Routing                              │
│  - Session Management                           │
│  - Error Handling                               │
└─────────────────┬───────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────┐
│         Business Logic Layer                    │
│         (ai_engine.py)                          │
│  - Prompt Engineering                           │
│  - AI Model Integration                         │
│  - Response Processing                          │
└─────────────────┬───────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────┐
│         Configuration Layer                     │
│         (config.py)                             │
│  - Environment Variables                        │
│  - Application Settings                         │
└─────────────────┬───────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────┐
│         External Services                       │
│         (Groq API - LLaMA 3)                    │
└─────────────────────────────────────────────────┘
```

### 2.2 Design Pattern
**Model-View-Controller (MVC)**
- **Model**: ai_engine.py (AI logic)
- **View**: ui.py (UI components)
- **Controller**: app.py (orchestration)

---

## 3. Component Design

### 3.1 Configuration Module (config.py)

**Purpose**: Centralized configuration management

**Responsibilities**:
- Load environment variables
- Store application constants
- Validate configuration
- Provide language settings

**Key Classes**:
```python
class Config:
    - GROQ_API_KEY
    - GROQ_MODEL
    - APP_TITLE
    - SUPPORTED_LANGUAGES
    - validate()
```


### 3.2 AI Engine Module (ai_engine.py)

**Purpose**: Handle AI inference and prompt engineering

**Responsibilities**:
- Initialize Groq client
- Create structured prompts
- Call AI model
- Process responses
- Handle errors

**Key Classes**:
```python
class AIEngine:
    - __init__()
    - create_prompt(crop_name, symptoms, language)
    - get_diagnosis(crop_name, symptoms, language)
```

**Prompt Structure**:
1. System context (agricultural expert)
2. Input data (crop, symptoms)
3. Language specification
4. Output format (diagnosis, remedies, prevention)

### 3.3 UI Module (ui.py)

**Purpose**: Manage all user interface components

**Responsibilities**:
- Apply custom CSS
- Render UI components
- Handle user interactions
- Display results
- Show error messages

**Key Methods**:
```python
class UI:
    - apply_custom_css()
    - render_header(language)
    - render_language_selector()
    - render_input_form(language)
    - render_submit_button(language)
    - render_diagnosis(diagnosis)
    - render_error(error_message)
    - render_warning(language)
    - render_footer()
```

### 3.4 Main Application (app.py)

**Purpose**: Application orchestration and flow control

**Responsibilities**:
- Initialize application
- Validate configuration
- Coordinate UI and AI modules
- Handle user workflow
- Manage state

**Flow**:
1. Initialize app configuration
2. Validate API key
3. Render language selector
4. Display input form
5. Process user submission
6. Call AI engine
7. Display results

---

## 4. Data Flow

### 4.1 Request Flow

```
User Input → Language Selection → Form Submission
     ↓
Validation → AI Engine → Prompt Creation
     ↓
Groq API Call → LLaMA 3 Processing
     ↓
Response → Formatting → Display to User
```

### 4.2 Detailed Sequence

1. **User Action**: Selects language, enters crop and symptoms
2. **Validation**: Check if fields are filled
3. **Prompt Creation**: Format input into structured prompt
4. **API Call**: Send to Groq with LLaMA 3 model
5. **Processing**: AI generates diagnosis
6. **Response**: Return structured output
7. **Display**: Show formatted result to user

---

## 5. Security Design

### 5.1 API Key Management
- Stored in environment variables only
- Never committed to version control
- Validated at startup
- Not exposed in logs or errors

### 5.2 Input Validation
- Character limits on inputs
- Sanitization of user data
- Prevention of injection attacks

### 5.3 Error Handling
- Generic error messages to users
- Detailed logs for debugging
- No sensitive data exposure

---

## 6. UI/UX Design

### 6.1 Design Principles
- **Simplicity**: Minimal, intuitive interface
- **Accessibility**: Large buttons, clear text
- **Responsiveness**: Mobile-first design
- **Cultural**: Bilingual support

### 6.2 Color Scheme
- Primary: Green (#4CAF50) - Agriculture
- Secondary: Light green (#E8F5E9)
- Accent: Orange (#FF9800) - Warnings
- Text: Dark gray (#262730)

### 6.3 Layout
- Centered single-column layout
- Clear visual hierarchy
- Adequate spacing
- Touch-friendly buttons

---

## 7. Performance Considerations

### 7.1 Response Time
- Groq API: ~2-4 seconds
- UI rendering: <1 second
- Total user wait: ~3-5 seconds

### 7.2 Optimization
- Caching Groq client
- Minimal dependencies
- Efficient prompt design
- Streamlit session state

---

## 8. Scalability

### 8.1 Horizontal Scaling
- Stateless application design
- No database dependency
- Cloud-ready architecture

### 8.2 Future Enhancements
- Add caching layer (Redis)
- Implement rate limiting
- Add database for history
- Support more languages

---

## 9. Deployment Architecture

### 9.1 Local Development
```
Developer Machine
    ↓
Python 3.10+ Environment
    ↓
Streamlit Server (Port 8501)
    ↓
Groq API (Internet)
```

### 9.2 Production Deployment
```
Streamlit Cloud / AWS / Azure
    ↓
Load Balancer
    ↓
Application Instances
    ↓
Groq API
```

---

## 10. Technology Justification

### 10.1 Why Streamlit?
- Rapid development
- Built-in responsive design
- Easy deployment
- Python-native

### 10.2 Why Groq API?
- Fast inference (LPU technology)
- Cost-effective
- No AWS dependency
- Easy integration

### 10.3 Why LLaMA 3?
- State-of-the-art performance
- Multilingual support
- Open-source model
- Large context window

---

## 11. Error Handling Strategy

### 11.1 Error Types
1. **Configuration Errors**: Missing API key
2. **Validation Errors**: Empty fields
3. **API Errors**: Network, rate limits
4. **Runtime Errors**: Unexpected exceptions

### 11.2 Handling Approach
- Graceful degradation
- User-friendly messages
- Logging for debugging
- Retry mechanisms

---

## 12. Testing Strategy

### 12.1 Unit Testing
- Test AI prompt generation
- Test input validation
- Test configuration loading

### 12.2 Integration Testing
- Test API integration
- Test end-to-end flow
- Test error scenarios

### 12.3 User Testing
- Test on mobile devices
- Test in Hindi and English
- Test with real farmers

---

## 13. Monitoring & Logging

### 13.1 Metrics to Track
- API response times
- Error rates
- User language preferences
- Common crop queries

### 13.2 Logging Strategy
- Application logs
- Error logs
- API call logs
- User interaction logs

---

## 14. Future Roadmap

### Phase 1 (Current)
- ✅ Bilingual support
- ✅ AI diagnosis
- ✅ Organic solutions

### Phase 2 (Next)
- Image-based disease detection
- Voice input support
- SMS integration

### Phase 3 (Future)
- Regional languages
- Community forum
- Expert consultation
- Market price integration

---

**Document Version**: 1.0  
**Last Updated**: 2024  
**Status**: Production Ready
