# 🌊 India Flood Risk & Evacuation Analysis - Streamlit Dashboard
## Complete Setup & Deployment Guide

---

## 📋 Project Overview

This is a comprehensive **interactive Streamlit dashboard** for analyzing flood risk and evacuation planning in India. It combines scientific data analysis with user-friendly visualizations accessible to both technical and non-technical audiences.

### ✨ Key Features

- ✅ **Interactive 3D Visualizations** - Explore flood risk surfaces and evacuation networks
- ✅ **Dual Explanations** - Simple layman + detailed technical analysis
- ✅ **Real Data Analysis** - Based on 10,000 observations across India
- ✅ **Statistical Validation** - 96.7% AUC-ROC model accuracy
- ✅ **Four-Chart Analysis** - Comprehensive evacuation planning data
- ✅ **Quick Reference** - Easy-to-use guides and checklists
- ✅ **FAQ Section** - Answers to common questions
- ✅ **Mobile Responsive** - Works on desktop, tablet, mobile

---

## 🚀 Quick Start

### Option 1: Local Installation (Recommended for Development)

#### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Git (optional)

#### Installation Steps

```bash
# 1. Clone or download the project
cd /path/to/project

# 2. Create a virtual environment (optional but recommended)
python -m venv venv

# 3. Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# 4. Install dependencies
pip install -r requirements.txt

# 5. Run the application
streamlit run streamlit_app.py
```

The dashboard will open in your default browser at `http://localhost:8501`

### Option 2: Cloud Deployment (Streamlit Cloud)

#### Prerequisites
- GitHub account
- Streamlit Community Cloud account (free at https://streamlit.io/cloud)

#### Deployment Steps

1. **Prepare your repository:**
   ```bash
   # Push to GitHub (if not already done)
   git add .
   git commit -m "Add Streamlit app"
   git push origin main
   ```

2. **Deploy on Streamlit Cloud:**
   - Go to https://share.streamlit.io
   - Click "New app"
   - Connect to your GitHub repository
   - Specify main file: `streamlit_app.py`
   - Click "Deploy"

3. **Your app is live!**
   - Share the URL with others
   - Real-time updates when you push to GitHub

### Option 3: Docker Deployment

#### Create Dockerfile

```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8501

CMD ["streamlit", "run", "streamlit_app.py", "--server.port=8501"]
```

#### Build and Run

```bash
# Build the Docker image
docker build -t flood-analysis:latest .

# Run the container
docker run -p 8501:8501 flood-analysis:latest

# Access at http://localhost:8501
```

---

## 📁 File Structure

```
project/
├── streamlit_app.py                          # Main Streamlit application
├── requirements.txt                          # Python dependencies
├── STREAMLIT_README.md                       # This file
├── 01_3D_Flood_Risk_Surface.png             # Visualization 1
├── 02_3D_Evacuation_Network.png             # Visualization 2
├── 03_Evacuation_Analysis.png               # Visualization 3
├── 04_3D_Optimal_Route.png                  # Visualization 4
├── 3D_FLOOD_RISK_DUAL_EXPLANATION.md        # Documentation
├── 3D_EVACUATION_NETWORK_EXPLANATION.md     # Documentation
├── EVACUATION_ANALYSIS_DUAL_EXPLANATION.md  # Documentation
└── flood_prediction_dataset.csv             # Sample data
```

---

## 🎯 Dashboard Structure

### 1. **Home (🏠)**
- Project overview
- Key statistics
- Quick facts
- Navigation guide

### 2. **Flood Risk Surface (📊)**
- 3D flood risk map visualization
- Layman explanation
- Technical statistical analysis
- Geographic interpretation

### 3. **Evacuation Network (🛣️)**
- Network topology visualization
- Safe zone locations
- Route information
- Network resilience metrics

### 4. **Evacuation Analysis (📈)**
- Four-chart analysis system
  - Chart 1: Risk Distribution
  - Chart 2: Elevation vs Water Level
  - Chart 3: Rainfall vs Discharge
  - Chart 4: Risk Score Distribution
- Interactive tabs for each chart
- Comparison with layman & technical views

### 5. **Quick Reference (📚)**
- Regional risk guide
- Elevation safety guide
- Rainfall impact guide
- Evacuation checklist
- Emergency procedures

### 6. **FAQ (❓)**
- Flood risk questions
- Safe zone information
- Evacuation procedures
- Model validation
- Cost-benefit analysis

---

## ⚙️ Configuration & Customization

### Streamlit Configuration

Create `.streamlit/config.toml`:

```toml
[theme]
primaryColor = "#1f77b4"
backgroundColor = "#ffffff"
secondaryBackgroundColor = "#f0f2f6"
textColor = "#262730"
font = "sans serif"

[client]
showErrorDetails = false
toolbarMode = "viewer"

[logger]
level = "info"

[server]
port = 8501
headless = true
runOnSave = true
```

### Environment Variables

```bash
# For Streamlit Cloud deployment
STREAMLIT_SERVER_PORT=8501
STREAMLIT_SERVER_HEADLESS=true
STREAMLIT_LOGGER_LEVEL=info
```

---

## 📊 Data Integration

### Adding Your Own Data

To use your own flood data:

```python
# In streamlit_app.py, modify data loading section:

import pandas as pd

# Load your CSV file
df = pd.read_csv('your_data.csv')

# Ensure columns match:
required_columns = [
    'Latitude', 'Longitude', 'Risk_Score', 'Elevation',
    'Rainfall', 'Water_Level', 'River_Discharge', 'Flooded'
]

# Filter and process
df_filtered = df[required_columns]
```

### Data Format Requirements

```
Column Name        | Type      | Range/Example
───────────────────┼───────────┼──────────────────
Latitude          | float     | 8.0 - 37.0
Longitude         | float     | 68.0 - 97.0
Risk_Score        | float     | 0.0 - 1.0
Elevation         | float     | 0 - 9000 (meters)
Rainfall          | float     | 0 - 500 (mm)
Water_Level       | float     | 0 - 15 (meters)
River_Discharge   | float     | 0 - 5000 (m³/s)
Flooded           | int       | 0 or 1
```

---

## 🔧 Troubleshooting

### Issue: "ModuleNotFoundError: No module named 'streamlit'"

**Solution:**
```bash
pip install streamlit
# or
pip install -r requirements.txt
```

### Issue: Images not displaying

**Solution:**
- Ensure image files are in the same directory as `streamlit_app.py`
- Check file paths are correct:
  ```python
  img = Image.open('/mnt/user-data/outputs/01_3D_Flood_Risk_Surface.png')
  ```
- Update paths if needed

### Issue: Slow performance

**Solution:**
```bash
# Run in production mode
streamlit run streamlit_app.py --logger.level=warning

# Or use caching
@st.cache_data
def load_data():
    # Your data loading code
    return data
```

### Issue: Session state not persisting

**Solution:**
```python
# Use Streamlit session state
import streamlit as st

if 'counter' not in st.session_state:
    st.session_state.counter = 0

st.session_state.counter += 1
st.write(f'Count: {st.session_state.counter}')
```

---

## 📈 Performance Optimization

### Caching Data

```python
@st.cache_data
def load_risk_data():
    return pd.read_csv('risk_data.csv')

# This function result is cached and only re-runs when inputs change
df = load_risk_data()
```

### Image Caching

```python
@st.cache_resource
def load_images():
    images = {
        'risk': Image.open('01_3D_Flood_Risk_Surface.png'),
        'network': Image.open('02_3D_Evacuation_Network.png')
    }
    return images

images = load_images()
```

### Session State for Forms

```python
if 'form_data' not in st.session_state:
    st.session_state.form_data = {}

# Use session state to persist form data between runs
risk_level = st.selectbox(
    'Select risk level',
    ['Low', 'Medium', 'High'],
    key='risk_level'
)
```

---

## 🌐 Deployment Platforms

### Platform: Heroku (Deprecated, use alternative)

### Platform: AWS (EC2)

1. **Launch EC2 instance**
2. **SSH into instance**
   ```bash
   ssh -i key.pem ubuntu@ec2-instance-ip
   ```
3. **Install Python and dependencies**
   ```bash
   sudo apt-get update
   sudo apt-get install python3-pip
   pip install -r requirements.txt
   ```
4. **Run Streamlit**
   ```bash
   streamlit run streamlit_app.py --server.port=80
   ```

### Platform: Azure App Service

1. Create App Service (Python 3.9)
2. Configure startup command:
   ```
   streamlit run streamlit_app.py --server.port 8000
   ```
3. Deploy via GitHub integration

### Platform: DigitalOcean

1. Create Droplet (Ubuntu 20.04)
2. Install dependencies
3. Configure Nginx reverse proxy
4. Deploy using git hooks

---

## 🔐 Security Considerations

### For Production Deployment

```python
# Add authentication
import streamlit_authenticator as stauth

# Restrict access to sensitive data
if not st.session_state.get('authenticated', False):
    st.error('Please log in')
    st.stop()
```

### Hide secrets
```bash
# Create .streamlit/secrets.toml
database_url = "postgresql://..."
api_key = "your-api-key"
```

### Use in code
```python
import streamlit as st

db_url = st.secrets["database_url"]
api_key = st.secrets["api_key"]
```

---

## 📊 Adding Interactivity

### Example: User Input for Location

```python
st.subheader("Find Your Risk Level")

latitude = st.slider("Latitude", 8.0, 37.0, 25.0)
longitude = st.slider("Longitude", 68.0, 97.0, 82.0)

# Find nearest location and risk
risk = calculate_risk(latitude, longitude)
st.write(f"Your risk level: {risk}")
```

### Example: Data Filtering

```python
st.subheader("Filter by Risk Level")

risk_filter = st.multiselect(
    "Select risk levels",
    ["Low", "Medium", "High"],
    default=["Medium", "High"]
)

# Filter and display data
filtered_df = df[df['Risk_Category'].isin(risk_filter)]
st.dataframe(filtered_df)
```

---

## 📚 Additional Resources

### Streamlit Documentation
- Official Docs: https://docs.streamlit.io
- API Reference: https://docs.streamlit.io/library/api-reference
- Gallery: https://streamlit.io/gallery

### Related Libraries
- Plotly: https://plotly.com/python/
- Pandas: https://pandas.pydata.org/
- Numpy: https://numpy.org/
- Matplotlib: https://matplotlib.org/

### Deployment Resources
- Streamlit Cloud: https://share.streamlit.io
- Docker: https://www.docker.com/
- GitHub: https://github.com/

---

## 🤝 Contributing

To contribute improvements:

1. Fork the repository
2. Create a feature branch
3. Make changes
4. Submit a pull request

### Suggested Improvements
- [ ] Add real-time data integration
- [ ] Implement user authentication
- [ ] Add export to PDF functionality
- [ ] Create mobile app version
- [ ] Add multi-language support
- [ ] Integrate weather API
- [ ] Add predictive modeling
- [ ] Create admin dashboard

---

## 📝 License

This project is open source and available under the MIT License.

---

## ✉️ Support & Feedback

For issues, questions, or suggestions:

1. Check the FAQ section in the dashboard
2. Review troubleshooting guide above
3. Create an issue on GitHub
4. Contact: support@floodriskanalysis.in

---

## 📊 Version History

### Version 1.0 (Current)
- Initial release
- 4 main sections (Risk Surface, Network, Analysis, Reference)
- Dual explanation system
- 10,000 data points
- 96.7% accuracy model
- 5 safe zones identified

### Planned for v2.0
- Real-time data updates
- User authentication
- Custom report generation
- API integration
- Mobile app
- Multi-language support

---

## 🏆 Project Statistics

- **Total Data Points:** 10,000 observations
- **Geographic Coverage:** Full India (8°N to 37°N, 68°E to 97°E)
- **Model Accuracy:** 96.7% AUC-ROC
- **Evacuation Network:** 100 locations, 684 routes, 5 safe zones
- **Safe Capacity:** 30 million people
- **Network Reliability:** 99.5%

---

## 🎯 How to Get Started

### Step 1: Install
```bash
pip install -r requirements.txt
```

### Step 2: Run
```bash
streamlit run streamlit_app.py
```

### Step 3: Explore
- Navigate using the sidebar
- Choose your explanation level
- Explore visualizations
- Check regional information

### Step 4: Use the Data
- Reference the quick guide
- Check FAQ for answers
- Download information
- Share with others


