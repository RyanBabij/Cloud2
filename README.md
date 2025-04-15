# CloudFit

**CloudFit** is a geolocation-powered fitness web application designed to gamify outdoor activity. Using Google Maps, Firebase Firestore, and browser geolocation, CloudFit tracks user movement, sets dynamic fitness goals via location markers, and rewards users for reaching nearby points.

## Overview

CloudFit aims to:
- Encourage physical activity through real-world movement tracking.
- Offer a gamified experience with score tracking and progress feedback.
- Allow users to see and interact with map-based fitness markers.

## Features

- **Live Geolocation Tracking**  
  Detects and displays user position on an interactive Google Map.

- **Fitness Marker System**  
  Dynamically generated map markers serve as exercise goals. Users are rewarded with points for approaching them within a defined radius.

- **Firebase Integration**  
  Stores user marker data and positions using Firestore, scoped to individual users.

- **Custom Distance Calculations**  
  Uses Haversine formula for calculating distance between points to track marker proximity.

- **Cookie-Based Sessions**  
  Lightweight session management with browser cookies for identifying users.

- **User Feedback System**  
  Displays live data such as:
  - Current score
  - Closest marker distance
  - User coordinates and elevation
  - Local temperature (planned via OpenWeatherMap API)

## 🛠Technologies Used

| Area         | Tech Stack                     |
|--------------|--------------------------------|
| Frontend     | HTML5, CSS3, JavaScript (ES5)  |
| Mapping API  | Google Maps JavaScript API     |
| Realtime DB  | Firebase Firestore             |
| Hosting      | Compatible with Apache/PHP     |
| Utility APIs | OpenWeatherMap (planned)       |

## Installation

1. **Clone the Repo**
   ```bash
   git clone https://github.com/RyanBabij/Cloud2.git
   cd Cloud2
   ```

2. **Set Up Local Server**
   - Place the project inside your server's root directory (`htdocs` if using XAMPP).
   - Start Apache and navigate to `http://localhost/Cloud2`.

3. **Configure Firebase**
   - Use your own Firebase project credentials.
   - Replace the `firebaseConfig` object in your JavaScript with your project details from the Firebase console.

4. **Enable Google Maps API**
   - Enable the Maps JavaScript API in your [Google Cloud Console](https://console.cloud.google.com/).
   - Replace the API key in the script URL:
     ```html
     <script async defer
       src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap">
     </script>
     ```

5. *(Optional)*: Set up OpenWeatherMap if you plan to show live weather data.

## Application Logic

- **Map Initialization**
  - Loads Google Map centered on Melbourne, AU (can be changed).
  - Starts real-time position tracking via `navigator.geolocation`.

- **Marker Generation**
  - Retrieves existing user markers from Firestore.
  - Users can earn points by walking within `CREDIT_DISTANCE` (~55m) of a marker.

- **Scoring System**
  - Points are tracked via a local counter (`totalPoints`).
  - Marker proximity updates every 5 seconds.

- **User Identity**
  - Cookies track `userid` and `username`.
  - All marker data in Firestore is scoped per user ID.

## Future Improvements

- Elevation display using Google Elevation API
- Real weather info via OpenWeatherMap
- Marker difficulty levels or variety
- Responsive UI / Progressive Web App support
- Daily streak system or badges
