# RouteWISELY™ – GitHub Copilot Development Notes

_Last updated: August 05, 2025_

This file is intended to guide GitHub Copilot, ChatGPT, or any other AI coding assistant to understand the structure, functionality, and roadmap of the RouteWISELY™ Google Maps viewer project.

---

## ✅ Features Already Implemented

1. **Google Maps Integration**
   - Uses Google Maps JavaScript API to render map.
   - Loads GeoJSON from a public GCS bucket.

2. **Dynamic GeoJSON Loading**
   - Fetches live file from: `https://storage.googleapis.com/rw-geojson-files/boone.geojson`
   - Zooms map to GeoJSON bounds.

3. **Direction of Travel**
   - Markers display full route (red).
   - Ready for directional bearing visuals (future enhancement).

4. **Driver Control Panel**
   - `Start`: Begins GPS-based logging.
   - `Pause`: Temporarily stops without clearing session.
   - `Stop`: Ends and finalizes the session.
   - Controls are visually accessible on mobile devices.

5. **Visited Marker Logging**
   - Logs driver location with timestamp on visit.
   - Visited markers turn green.
   - Logs to browser console (Firebase integration pending).

6. **Leaflet Fallback**
   - Alternate HTML viewer (`leaflet.html`) included in `/public`.
   - Manual fallback for offline or API failure scenarios.

7. **File Structure**
```
/public
├── googlemaps.html       # Primary production viewer
├── leaflet.html          # Backup viewer using Leaflet
├── index.html            # Optional splash page or redirect
├── route.geojson         # Local test file only
└── firebase.json         # Firebase hosting rules
```

---

## 🔐 API & Security Notes

- Maps API key must be placed manually into `googlemaps.html`.
- Recommend enabling restrictions:
  - HTTP referrer: `*.web.app`
  - Enabled APIs: Maps JavaScript API, Maps GeoLocation API (future), Places API (optional)

---

## 📌 Future Features for GitHub Copilot to Build

1. **Firebase Integration (Phase 2)**
   - Write visited marker logs to Firestore.
   - Include `timestamp`, `lat`, `lng`, `segment_id`, and `session_id`.

2. **Progress Tracking**
   - Add visual indicator (progress bar or percent completion).
   - Compare total markers vs. visited markers.

3. **Polyline Optimization**
   - Replace red dots with polylines using Google Directions API or Maps Snap-to-Road.

4. **Session Reporting**
   - Export logs to JSON or CSV.
   - Include metadata like session duration and driver ID.

5. **Supervisor Dashboard (Phase 3)**
   - Web app to monitor multiple driver sessions.
   - Load different `.geojson` files by selecting a project from dropdown.

6. **UI Improvements**
   - Add custom map themes (dark mode, branded overlays).
   - Better mobile responsiveness for in-vehicle use.

---

## 🧠 Design Principles

- Mobile-first UX for driver navigation
- Lightweight HTML/CSS/JS stack
- Cloud-hosted GeoJSON (no local embedding)
- Modular fallback system (Google Maps primary, Leaflet fallback)
- Logging-first architecture for route auditing

---

