# AI-Based Cloud Security Monitoring and Threat Detection System

## 🎯 Project Overview

This is a **professional, industry-ready** capstone project that implements an AI-powered cloud security monitoring system. The system monitors user activity, detects anomalies using machine learning, classifies attack types, and provides a comprehensive admin dashboard for security operations.

### Key Features

- ✅ **Cloud Activity Monitoring using Simulated Logs**
- ✅ **ML-Based Anomaly Detection** (Isolation Forest Algorithm)
- ✅ **Intelligent Attack Classification** (9 threat types)
- ✅ **Professional SOC-Style Dashboard**
- ✅ **Detailed User Activity Profiles**
- ✅ **Risk Level Assessment** (High/Medium/Low)
- ✅ **Dark-Themed Cybersecurity UI/UX**
- ✅ **Responsive Design**

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                   Cloud Activity Logs                    │
│              (Simulated User Behavior Data)              │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│            Machine Learning Pipeline                     │
│  ┌──────────────────────────────────────────────────┐  │
│  │    Isolation Forest (Unsupervised Learning)       │  │
│  │    - Anomaly Detection                            │  │
│  │    - Contamination Rate: 20%                      │  │
│  └──────────────────────────────────────────────────┘  │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│         Rule-Based Attack Classification Engine          │
│  - Data Breach        - DoS/DDoS                         │
│  - Account Hijacking  - Insider Threats                  │
│  - Malware Injection  - Shared Vulnerabilities          │
│  - Insecure APIs      - Cloud Misconfiguration          │
│  - Phishing Impact                                       │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│              Threat Detection Storage                    │
│           (detected_threats.csv)                         │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│          Flask Web Application + Dashboard               │
│  - Admin Dashboard (User Overview)                       │
│  - User Detail Pages (Threat Analysis)                   │
│  - REST API Endpoints                                    │
└─────────────────────────────────────────────────────────┘
```

---

## 📊 Detected Attack Types

The system can identify and classify the following cloud security threats:

| Attack Type | Description | Detection Criteria |
|------------|-------------|-------------------|
| **Data Breach** | Unauthorized data exfiltration | High network output + High CPU usage |
| **Account Hijacking** | Compromised user credentials | Excessive login attempts + High CPU |
| **Malware Injection** | Malicious code execution | Very high CPU + High network input |
| **Insecure APIs** | API vulnerability exploitation | High bidirectional network traffic |
| **Phishing Impact** | Successful phishing attacks | Abnormal login patterns |
| **DoS/DDoS** | Denial of Service attacks | Extreme network traffic |
| **Insider Threats** | Malicious internal activity | High CPU + Low login frequency |
| **Shared Vulnerabilities** | Multi-tenancy security issues | Multiple logins + High CPU |
| **Cloud Misconfiguration** | Security configuration errors | Low CPU + High network output |

---

## 🤖 Machine Learning Algorithm

### Isolation Forest (Unsupervised Anomaly Detection)

**Why Isolation Forest?**
- **Unsupervised Learning**: No labeled training data required
- **High Performance**: O(n log n) time complexity
- **Effective for Outliers**: Specifically designed for anomaly detection
- **Low False Positives**: Contamination parameter tuning

**How it Works:**
1. **Isolation**: Randomly selects features and split values
2. **Tree Construction**: Builds ensemble of isolation trees
3. **Path Length**: Anomalies have shorter average path lengths
4. **Scoring**: Assigns anomaly scores to each data point

**Implementation Details:**
```python
model = IsolationForest(
    contamination=0.20,      # Expect 20% anomalies
    n_estimators=100,        # 100 decision trees
    random_state=42          # Reproducibility
)
```

**Features Used:**
- `login_count`: Number of login attempts
- `cpu_usage`: CPU utilization percentage
- `network_in`: Incoming network traffic (MB)
- `network_out`: Outgoing network traffic (MB)

---

## 🗂️ Project Structure

```
cloud-security-system/
│
├── backend/
│   └── app.py                    # Flask web server & API
│
├── ml/
│   └── anomaly_detection.py      # ML model & data generation
│
├── frontend/
│   └── templates/
│       ├── admin_dashboard.html  # Main admin interface
│       └── user_detail.html      # Individual user analysis
│
├── static/
│   └── style.css                 # Professional dark theme CSS
│
├── dataset/
│   ├── cloud_logs.csv            # Simulated cloud activity data
│   └── detected_threats.csv      # Detected threats database
│
└── README.md                      # This file
```

---

## 📦 Technology Stack

### Backend
- **Python 3.x**
- **Flask**: Web framework
- **Pandas**: Data manipulation
- **Scikit-learn**: Machine learning
- **NumPy**: Numerical computing

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Professional dark theme
- **Vanilla JavaScript**: Interactive dashboard
- **No frameworks**: Pure, lightweight implementation

### Data Storage
- **CSV Files**: Lightweight, portable data storage

---

## 🚀 Installation & Setup

### Prerequisites
```bash
- Python 3.8 or higher
- pip (Python package manager)
```

### Step 1: Install Dependencies
```bash
pip install flask pandas scikit-learn numpy
```

### Step 2: Generate Sample Data
```bash
cd ml
python3 anomaly_detection.py
```

**Expected Output:**
```
============================================================
AI-Based Cloud Security Monitoring System
Anomaly Detection Engine
============================================================

📊 Generating simulated cloud activity data...
✓ Generated 200 cloud activity records

🤖 Training Isolation Forest model...
✓ Model trained on 200 records

🔍 Detecting anomalies...
✓ Detected 40 anomalies (20.0%)

🚨 Classifying attack types...
✓ Classified 40 threats
```

### Step 3: Run the Web Application
```bash
cd backend
python3 app.py
```

### Step 4: Access the Dashboard
Open your web browser and navigate to:
```
http://127.0.0.1:5000
```

---

## 💻 Usage Guide

### Admin Dashboard (`/admin`)

**Features:**
- View all monitored users
- See threat counts and risk levels
- Search/filter users
- Click on any user to view details

**Key Metrics:**
- Total Users Monitored
- Active Threats
- High Risk Users
- Detection Rate

### User Detail Page (`/user/<user_id>`)

**Information Displayed:**
- User activity statistics
- Detected security alerts
- Attack type classifications
- Risk level assessment
- Activity logs
- Security recommendations

**Available Actions:**
- Export user report
- Send security alert
- Return to admin dashboard

---

## 📡 API Endpoints

### Get All Users
```
GET /api/users
```
**Response:**
```json
{
  "success": true,
  "count": 200,
  "users": [...]
}
```

### Get User Details
```
GET /api/user/<user_id>
```
**Response:**
```json
{
  "success": true,
  "user": {
    "user_id": "USER_001",
    "total_logins": 15,
    "threat_count": 2,
    "threats": [...]
  }
}
```

### Get System Statistics
```
GET /api/statistics
```
**Response:**
```json
{
  "success": true,
  "total_users": 200,
  "total_threats": 40,
  "threat_distribution": {...},
  "risk_distribution": {...}
}
```

---

## 📈 Dataset Structure

### `cloud_logs.csv`
| Column | Type | Description |
|--------|------|-------------|
| `user_id` | String | Unique user identifier |
| `login_count` | Integer | Number of login attempts |
| `cpu_usage` | Float | CPU utilization (%) |
| `network_in` | Float | Incoming traffic (MB) |
| `network_out` | Float | Outgoing traffic (MB) |
| `login_status` | String | success/failed |

### `detected_threats.csv`
| Column | Type | Description |
|--------|------|-------------|
| `user_id` | String | Affected user |
| `attack_type` | String | Classified threat type |
| `risk_level` | String | High/Medium/Low |
| `cpu_usage` | Float | CPU at detection time |
| `network_out` | Float | Network output |
| `anomaly_score` | Float | ML confidence score |

---

## 🎨 UI/UX Design Principles

### Color Coding
- 🔴 **Red**: High risk threats
- 🟡 **Yellow**: Medium risk warnings
- 🔵 **Blue**: Low risk alerts
- 🟢 **Green**: Normal/safe status

### Design Philosophy
- **Dark Theme**: Reduces eye strain for SOC analysts
- **Card-Based Layout**: Clear information hierarchy
- **Hover Effects**: Interactive feedback
- **Responsive**: Works on all screen sizes
- **Professional**: Industry-standard aesthetics

---

## 🔮 Future Enhancements

### Phase 1 (Short-term)
- [ ] Real-time alert notifications (Email/SMS)
- [ ] Export reports to PDF
- [ ] User activity timeline visualization
- [ ] Custom rule creation interface

### Phase 2 (Medium-term)
- [ ] Integration with real cloud platforms (AWS, Azure, GCP)
- [ ] Deep learning models (LSTM for sequence analysis)
- [ ] Automated incident response
- [ ] Multi-factor authentication simulation

### Phase 3 (Long-term)
- [ ] Blockchain-based audit logging
- [ ] Federated learning for privacy
- [ ] Quantum-resistant encryption
- [ ] AI-powered threat hunting

---

## 🧪 Testing the System

### Test Scenarios

**1. Normal User Behavior**
- Low login count (1-7)
- Moderate CPU usage (20-65%)
- Normal network traffic (50-300 MB)

**2. Suspicious Activity**
- High login count (8-25)
- High CPU usage (70-99%)
- High network traffic (400-950 MB)

**3. Verify Detection**
- Check if suspicious users appear in threats
- Validate attack type classification
- Confirm risk level assignment

---

## 📚 Academic Context

### Project Category
**Final Year Capstone Project - Computer Science/Cybersecurity**

### Learning Outcomes
1. **Machine Learning**: Unsupervised anomaly detection
2. **Web Development**: Full-stack application design
3. **Cybersecurity**: Threat detection and classification
4. **Data Science**: Data analysis and visualization
5. **Software Engineering**: Professional code organization

### Suitable For
- B.Tech/B.E. Computer Science
- M.Tech Cybersecurity
- Information Security specializations
- Cloud Computing courses

---

## 🤝 Contributing

This is an academic project, but suggestions are welcome:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Submit a pull request

---

## 📄 License

This project is created for **educational purposes** as a final year capstone project.

---

## 👨‍💻 Author

**Final Year Capstone Project**  
AI-Based Cloud Security Monitoring and Threat Detection System  
2024

---

## 🙏 Acknowledgments

- **Scikit-learn**: For the Isolation Forest implementation
- **Flask**: For the lightweight web framework
- **Security Community**: For threat classification insights

---

## 📞 Support

For questions or issues:
1. Check the documentation above
2. Review the code comments
3. Examine the console logs
4. Test with sample data first

---

## ⚠️ Important Notes

1. **Simulated Data**: This system uses synthetic data for demonstration
2. **Educational Purpose**: Not for production security monitoring
3. **Expandable**: Architecture supports real data integration
4. **Well-Documented**: Code includes extensive comments

---

## 🎓 Presentation Tips

When presenting this project:

1. **Start with the Problem**: Cloud security threats are increasing
2. **Explain the Solution**: AI-powered detection and classification
3. **Demo the Dashboard**: Show live user interaction
4. **Discuss the Algorithm**: Explain Isolation Forest
5. **Show Results**: Demonstrate threat detection
6. **Future Work**: Discuss scalability and enhancements

---

## ✅ Project Checklist

- [x] Machine Learning implementation
- [x] Anomaly detection working
- [x] Attack classification logic
- [x] Flask backend API
- [x] Admin dashboard UI
- [x] User detail pages
- [x] Professional CSS styling
- [x] Sample dataset generation
- [x] Comprehensive documentation
- [x] Clean project structure

---

**Version**: 1.0.0  
**Last Updated**: 2024  
**Status**: ✅ Production Ready for Academic Submission
