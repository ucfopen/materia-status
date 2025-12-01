# Materia Status

Static site for status updates about the UCF instance of Materia.

## Overview

This is a single-page static status site that provides real-time information about the Materia application's operational status. The site is compatible with GitHub Pages and requires no backend infrastructure.

## Features

- 🟢 Real-time status indicator for overall system health
- 📊 Individual service status monitoring
- 📝 Incident history and updates
- 📱 Responsive design for mobile and desktop
- ⚡ Fast, lightweight, and self-contained
- 🎨 Clean, professional interface

## GitHub Pages Setup

This site is ready to be deployed to GitHub Pages:

1. Go to your repository Settings
2. Navigate to "Pages" in the left sidebar
3. Under "Source", select the branch you want to deploy (e.g., `main`)
4. Select "/ (root)" as the folder
5. Click "Save"

Your status page will be available at: `https://ucfopen.github.io/materia-status/`

## Updating Status

### Method 1: Edit the HTML File Directly

Open `index.html` and modify the `statusData` object in the `<script>` section:

```javascript
const statusData = {
    overallStatus: 'operational', // operational, degraded, outage, maintenance
    services: [
        { name: 'Web Application', status: 'operational' },
        // ... add or modify services
    ],
    incidents: [
        // Add incidents here
    ]
};
```

### Method 2: Use the External JSON File (Future Enhancement)

The `status.json` file can be used to manage status data separately. To enable this:

1. Modify `index.html` to fetch data from `status.json`
2. Update `status.json` with current status information
3. Commit and push changes

### Status Values

**Overall Status:**
- `operational` - All systems running normally
- `degraded` - Some services experiencing issues
- `outage` - Major service disruption
- `maintenance` - Scheduled maintenance in progress

**Service Status:**
- `operational` - Service is running normally
- `degraded` - Service is experiencing issues
- `outage` - Service is unavailable

**Incident Status:**
- `resolved` - Incident has been resolved
- `investigating` - Team is investigating
- `monitoring` - Issue is being monitored
- `critical` - Critical incident in progress

## Example: Adding an Incident

```javascript
incidents: [
    {
        title: 'Database Performance Issues',
        status: 'resolved',
        date: '2025-12-01 14:30 UTC',
        description: 'We experienced temporary database performance degradation. The issue has been resolved and all services are operating normally.'
    }
]
```

## Local Development

To test the site locally:

1. Open `index.html` in a web browser
2. Or use a simple HTTP server:
   ```bash
   python3 -m http.server 8000
   ```
3. Navigate to `http://localhost:8000`

## Customization

### Colors
The status page uses color coding:
- 🟢 Green (#10b981) - Operational
- 🟡 Amber (#f59e0b) - Degraded/Warning
- 🔴 Red (#ef4444) - Outage/Critical
- 🔵 Blue (#3b82f6) - Maintenance/Info

### Styling
All CSS is embedded in `index.html` for easy customization. Look for the `<style>` section to modify colors, fonts, or layout.

## License

This project is licensed under the GNU Affero General Public License v3.0. See the LICENSE file for details.

## Related Links

- [Materia on GitHub](https://github.com/ucfopen/Materia)
- [Materia Documentation](https://ucfopen.github.io/Materia-Docs/)
