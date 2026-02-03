# PRUDEV II MSME Support Portal

A comprehensive web application for managing Business Growth Experts (BGEs), MSMEs, and generating professional reports for the PRUDEV II (Private Sector Development Programme) in Uganda.

## Features

### 📝 Report Generation
- **Form-based Interface**: Easy-to-use form for documenting MSME visits
- **Auto-population**: BGE codes automatically filled when selecting BGE name
- **Comprehensive Fields**: Capture objectives, activities, SWOT analysis, leadership, gender considerations, waste management, climate adaptation, and BDS recommendations
- **Print-Optimized**: Professional PDF-ready report layouts with PRUDEV II branding
- **Auto-save**: Data persists in browser localStorage

### 🔐 Admin Panel
- **Secure Access**: Passcode-protected (default: `2026`)
- **BGE Management**: Add, view, and delete Business Growth Experts
- **MSME Management**: Add, view, and delete MSMEs
- **Assignment Tracking**: Link BGEs to specific MSMEs
- **Real-time Updates**: Changes reflect immediately across the application

### 💾 Data Management
- **LocalStorage**: All data persists in browser storage
- **Seed Data**: Pre-loaded with 10 BGEs and 16 MSMEs
- **No Backend Required**: Fully functional as a standalone HTML file
- **Export Ready**: Can be extended with Firebase for cloud sync

## Quick Start

### Option 1: Open Directly
1. Double-click `index.html` to open in your default browser
2. Start creating reports or access the admin panel

### Option 2: Local Server
```bash
# Navigate to the project directory
cd /Users/RICHOBUKU/.gemini/antigravity/scratch/prudev-msme-portal

# Start a simple HTTP server (Python 3)
python3 -m http.server 8000

# Open in browser
open http://localhost:8000
```

## Usage Guide

### Creating a Report
1. Click the **Report** tab in the navigation
2. Fill in the form fields:
   - Date and location
   - Select BGE name (code auto-fills)
   - Select MSME/business name
   - Complete all relevant sections
3. Click **Print Report** to generate a PDF-ready version

### Admin Panel Access
1. Click the **Admin** tab
2. Enter passcode: `2026`
3. Use the tabs to manage:
   - **BGEs**: Add/remove Business Growth Experts
   - **MSMEs**: Add/remove businesses
   - **Assignments**: Link BGEs to MSMEs

### URL Hash Navigation
You can pre-populate the BGE name by adding it to the URL:
```
index.html#Anena%20Sharon
```

## Pre-loaded Data

### Business Growth Experts (BGEs)
- **Gulu**: Anena Sharon, Bodo Deogratius, Obalim Stephen, Ojok Denis Giv
- **Lira**: Abeja Immaculate, AKELLO MIRRIAM, Ogwang Abel, ODONGO BONNY JAMES
- **Alebtong**: Ocen Joseph Steven
- **Lamwo**: Lanyero Docus

### MSMEs (Sample)
- A037 BIZ INVESTMENT LIMITED (Gulu)
- Acholi Shea Cooperative Ltd (Gulu)
- ABIMAC BUSINESS LINK (Lira)
- Gracefarm agribusiness company limited (Adjumani)
- And 12 more...

## Technical Stack

- **Frontend**: React 18 (CDN)
- **Styling**: Tailwind CSS
- **Storage**: Browser localStorage
- **Icons**: Custom SVG components
- **Fonts**: Inter (sans-serif), Playfair Display (serif)

## Browser Compatibility

Works in all modern browsers:
- ✅ Chrome/Edge (recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Opera

## Customization

### Change Admin Passcode
Edit line 65 in `index.html`:
```javascript
const ADMIN_PASSCODE = "2026"; // Change to your desired passcode
```

### Add More BGEs/MSMEs
Use the Admin Panel or edit the `SEED_BGES` and `SEED_MSMES` arrays in the code.

### Styling
The app uses Tailwind CSS. Modify the classes in the JSX to customize the appearance.

## Data Persistence

All data is stored in browser localStorage under these keys:
- `prudev_bges`: Business Growth Experts
- `prudev_msmes`: MSMEs
- `prudev_assignments`: BGE-MSME assignments

**Note**: Clearing browser data will reset the application to seed data.

## Future Enhancements

Potential features for future versions:
- Firebase integration for cloud sync
- Multi-user authentication
- Report history and archiving
- Export to PDF/Excel
- Mobile app version
- Dashboard analytics

## Support

For issues or questions, contact the PRUDEV II technical team.

## License

© 2026 PRUDEV II - Private Sector Development Programme

---

**Version**: 1.0.0  
**Last Updated**: February 2026
