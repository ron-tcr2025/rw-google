# RouteWISELY™ Google Maps Viewer

This is the primary HTML-based viewer for visualizing GeoJSON route data stored in Google Cloud Storage (GCS), built for RouteWISELY™. The project is designed for mobile drivers and supervisors who need real-time tracking, logging, and map rendering.

## ✅ Features

- Loads GeoJSON route files directly from GCS (`boone.geojson`)
- Displays route in **Google Maps** with red path
- Driver GPS tracking
- Live arrow-shaped marker with direction of travel
- Start / Pause / Stop buttons
- Logs each visited GPS coordinate with timestamp
- Responsive layout for mobile and web
- API key placeholder for manual insertion

## 🔐 Google Maps API Key

Update the line below in `googlemaps.html`:
```html
<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY_HERE"></script>
```

Replace `YOUR_GOOGLE_MAPS_API_KEY_HERE` with your valid key.

## 🌐 Hosted GeoJSON File

The app references:
```
https://storage.googleapis.com/rw-geojson-files/boone.geojson
```

Make sure:
- Your bucket has **Uniform Bucket-Level Access** enabled
- IAM role `Storage Object Viewer` is granted to `allUsers`
- File is publicly accessible

## 🧭 GPS Tracking Behavior

- **Start** begins live geolocation tracking using `navigator.geolocation.watchPosition`
- Adds a forward arrow marker at each update
- Coordinates and timestamps logged in-memory (console output)
- **Pause** stops updates without clearing the route
- **Stop** ends tracking session

## 📁 Files in This Repo

| File              | Description                                |
|-------------------|--------------------------------------------|
| `googlemaps.html` | Google Maps viewer for RouteWISELY         |
| `README.md`       | This documentation                         |

## 🧠 Autopilot Instructions for GitHub Copilot or ChatGPT

Future contributions must:
- Use `map.data.addGeoJson()` for any overlays
- Fetch all route files via HTTPS from GCS
- Use `watchPosition` for real-time logging
- Store logs locally for Phase 1 (server push in Phase 2)
- Maintain fallback option using Leaflet (`leaflet.html` not included here, but required in hosting)

## 🧱 Future Improvements

- GPX export of visited path
- Firebase push of session logs
- Supervisor dashboard viewer
- Project selection dropdown

---

© 2025 CloudRiver LLC. RouteWISELY™ is a trademark of CloudRiver. All rights reserved.
