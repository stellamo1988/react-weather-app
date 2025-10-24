# Weather App 🌤️

A beautiful, responsive weather application built with HTML, CSS (Bootstrap), and JavaScript. Get real-time weather information for any city in the world.

![Weather App](https://img.shields.io/badge/version-1.0.0-blue.svg)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.0-purple.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

## 📋 Table of Contents

- [Features](#features)
- [Demo](#demo)
- [Installation](#installation)
- [Usage](#usage)
- [API](#api)
- [Technologies Used](#technologies-used)
- [File Structure](#file-structure)
- [How It Works](#how-it-works)
- [Customization](#customization)
- [Browser Support](#browser-support)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## ✨ Features

- 🔍 **Search by City** - Search for weather in any city worldwide
- 🌡️ **Real-time Data** - Get current temperature and conditions
- 📊 **Detailed Information** - View wind speed, humidity, visibility, pressure, UV index, and "feels like" temperature
- 🎨 **Beautiful UI** - Modern gradient design with glassmorphism effects
- 📱 **Fully Responsive** - Works seamlessly on desktop, tablet, and mobile devices
- ⚡ **Fast Loading** - Lightweight and optimized for performance
- 🌐 **No Installation Required** - Runs directly in the browser
- 🎯 **Auto-load** - Shows weather for Johannesburg on page load

## 🎥 Demo

Simply open the `weather-app.html` file in any modern web browser to see the app in action!

## 🚀 Installation

### Option 1: Download and Run (Easiest)

1. Download the `weather-app.html` file
2. Double-click the file to open it in your default web browser
3. That's it! No installation needed.

### Option 2: Clone Repository

```bash
# Clone this repository
git clone https://github.com/yourusername/weather-app.git

# Navigate to the project directory
cd weather-app

# Open the HTML file in your browser
open weather-app.html  # On macOS
start weather-app.html # On Windows
xdg-open weather-app.html # On Linux
```

### Option 3: Use with a Local Server

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (with http-server installed)
npx http-server

# Then open http://localhost:8000 in your browser
```

## 💡 Usage

### Basic Usage

1. **Open the App** - Open `weather-app.html` in your web browser
2. **Search for a City** - Type any city name in the search box
3. **View Weather** - Press Enter or click the "Search" button
4. **See Details** - View temperature, conditions, and detailed weather metrics

### Search Tips

- Enter city names in English (e.g., "London", "Tokyo", "New York")
- You can search by city name only or include country (e.g., "Paris, France")
- The app will automatically find the most relevant match

## 🔑 API

This app uses the [WeatherAPI](https://www.weatherapi.com/) service to fetch weather data.

### Current API Key

The app includes a free API key for demonstration purposes:
```javascript
const API_KEY = '7d77ecf93e1f4e1e8d9134829250110';
```

### Getting Your Own API Key

1. Visit [WeatherAPI.com](https://www.weatherapi.com/)
2. Sign up for a free account
3. Get your API key from the dashboard
4. Replace the API key in the code:

```javascript
// Find this line in the HTML file (around line 168)
const API_KEY = 'YOUR_NEW_API_KEY_HERE';
```

### API Features Used

- **Endpoint:** `https://api.weatherapi.com/v1/current.json`
- **Data Retrieved:**
  - Current temperature (Celsius)
  - Weather condition
  - Wind speed (km/h)
  - Humidity (%)
  - Visibility (km)
  - Pressure (mb)
  - "Feels like" temperature
  - UV index
  - Location name and country
  - Local time

## 🛠️ Technologies Used

- **HTML5** - Structure and content
- **CSS3** - Custom styling and animations
- **Bootstrap 5.3.0** - Responsive layout and components
- **JavaScript (ES6+)** - Application logic and API calls
- **WeatherAPI** - Weather data provider
- **SVG** - Vector icons for weather conditions

### Why These Technologies?

- **No Build Process** - Everything works without compilation
- **No Dependencies** - Single HTML file with CDN resources
- **Modern & Clean** - Uses latest web standards
- **Responsive** - Bootstrap ensures mobile-first design
- **Fast** - Minimal footprint and quick loading

## 📁 File Structure

```
weather-app/
│
├── weather-app.html          # Main application file (all-in-one)
└── README.md                 # This file
```

### Single File Architecture

The app uses a single HTML file containing:
- HTML structure (lines 1-145)
- CSS styles (lines 7-60)
- JavaScript logic (lines 147-260)

## ⚙️ How It Works

### Application Flow

1. **Page Load**
   - Bootstrap CSS is loaded from CDN
   - DOM elements are initialized
   - Default city (Johannesburg) weather is fetched automatically

2. **User Search**
   - User enters city name and clicks search or presses Enter
   - `handleSearch()` function is triggered
   - Input is validated (not empty)

3. **API Request**
   - `fetchWeather()` sends request to WeatherAPI
   - Loading state is shown on the button
   - Error handling catches invalid cities

4. **Display Results**
   - `displayWeather()` updates all weather information
   - Weather icon is selected based on conditions
   - Date is formatted for display
   - All metrics are updated with API data

5. **Error Handling**
   - Invalid cities show error message
   - Network errors are caught and displayed
   - Button is re-enabled after request completes

### Key Functions

```javascript
// Main Functions
fetchWeather(cityName)     // Fetches data from API
displayWeather(data)       // Updates UI with weather data
getWeatherIcon(condition)  // Returns appropriate weather icon

// Event Handlers
searchBtn.click            // Handles search button click
cityInput.keypress         // Handles Enter key in input
window.load                // Loads default city on startup
```

## 🎨 Customization

### Change Default City

```javascript
// Find this line (around line 257)
window.addEventListener('load', () => {
  fetchWeather('Johannesburg'); // Change to your city
});
```

### Modify Colors

```css
/* Find these in the <style> section */

/* Background gradient */
body {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  /* Change colors as desired */
}

/* Button color */
.search-btn {
  background: #667eea; /* Primary color */
}

/* Detail cards */
.weather-detail-card {
  background: #f0f4ff; /* Card background */
}
```

### Change Temperature Unit

To display Fahrenheit instead of Celsius:

```javascript
// In displayWeather() function, change:
document.getElementById('temperature').textContent = 
  `${Math.round(data.current.temp_f)}°F`; // Changed from temp_c to temp_f

document.getElementById('feelsLike').textContent = 
  `${Math.round(data.current.feelslike_f)}°F`; // Changed from feelslike_c
```

### Add More Weather Details

The API provides additional data you can display:
- `data.current.precip_mm` - Precipitation
- `data.current.cloud` - Cloud coverage
- `data.current.gust_kph` - Wind gust speed

## 🌐 Browser Support

| Browser | Supported Version |
|---------|------------------|
| Chrome  | Latest 2 versions |
| Firefox | Latest 2 versions |
| Safari  | Latest 2 versions |
| Edge    | Latest 2 versions |
| Opera   | Latest 2 versions |

### Required Features

- ES6+ JavaScript (async/await, fetch API)
- CSS3 (gradients, flexbox, grid)
- SVG support

## 🐛 Troubleshooting

### Common Issues

**Problem:** App doesn't load weather data

**Solutions:**
- Check your internet connection
- Verify the API key is valid
- Check browser console for error messages
- Try a different city name

---

**Problem:** "City not found" error

**Solutions:**
- Check spelling of city name
- Try including country name (e.g., "London, UK")
- Use English city names

---

**Problem:** Styling looks broken

**Solutions:**
- Ensure internet connection (Bootstrap loads from CDN)
- Clear browser cache
- Try a different browser
- Check if CDN is accessible

---

**Problem:** API key limit reached

**Solutions:**
- Get your own free API key from WeatherAPI.com
- Wait for the rate limit to reset
- Upgrade to a paid plan for higher limits

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/AmazingFeature`)
3. **Commit your changes** (`git commit -m 'Add some AmazingFeature'`)
4. **Push to the branch** (`git push origin feature/AmazingFeature`)
5. **Open a Pull Request**

### Ideas for Contributions

- Add 7-day forecast
- Add weather charts/graphs
- Implement geolocation for automatic city detection
- Add dark mode toggle
- Support multiple temperature units
- Add weather alerts
- Implement caching to reduce API calls
- Add more weather animations

## 📄 License

This project is licensed under the MIT License - see below for details:

```
MIT License

Copyright (c) 2025 Weather App

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 📞 Contact

-Project Maintainer:Stella Modise

- GitHub: @stellamo1988(https://github.com/stellamo188
- Email: modisesella38@gmail.com
  

## 🙏 Acknowledgments

- [WeatherAPI](https://www.weatherapi.com/) - For providing the weather data API
- [Bootstrap](https://getbootstrap.com/) - For the responsive CSS framework
- [Heroicons](https://heroicons.com/) - Inspiration for SVG icons
- All contributors who help improve this project

---

**Made with ❤️ and ☕**

If you found this project helpful, please consider giving it a ⭐ on GitHub!# react-weather-app
