# Materia Status

Static site for status updates about the UCF instance of Materia.

## Overview

This is a single-page static status site that provides real-time information about the Materia application's operational status. The site is compatible with GitHub Pages and requires no backend infrastructure.

## Features

- 🟢 Real-time status indicator for overall system health
- 📝 Maintenance and outage updates section (displayed only when needed)
- ❓ Frequently Asked Questions (FAQ) section
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

### Method 1: Edit the External JSON File (Recommended)

The status page automatically loads data from `status.json`. To update the status:

1. Edit `status.json` with your current status information
2. Commit and push the changes to GitHub
3. The page will automatically load the new data (refreshes every 5 minutes, or on page reload)

Example `status.json`:
```json
{
  "overallStatus": "operational",
  "statusMessage": "All services are running normally.",
  "maintenanceUpdates": [],
  "faq": [
    {
      "question": "What is Materia?",
      "answer": "Materia is a learning tool creation platform used at UCF to create and deploy interactive learning widgets."
    }
  ]
}
```

### Method 2: Edit the HTML File Directly (Fallback)

If `status.json` is unavailable, the page uses default data embedded in `index.html`. You can modify the fallback `statusData` object in the `<script>` section:

```javascript
let statusData = {
    overallStatus: 'operational',
    statusMessage: 'All services are running normally.',
    maintenanceUpdates: [],
    faq: [...]
};
```

### JSON Structure

**Required Fields:**

- `overallStatus` (string): Current system status
  - `operational` - All systems running normally (green indicator)
  - `degraded` - Some services experiencing issues (amber indicator)
  - `outage` - Major service disruption (red indicator)
  - `maintenance` - Scheduled maintenance in progress (blue indicator)

- `statusMessage` (string): Brief description of the current status (displayed prominently below the status indicator)

- `maintenanceUpdates` (array): List of timestamped updates about maintenance or outages
  - Only displayed when the array is not empty
  - Each update has:
    - `date` (string): Timestamp (e.g., "2025-12-01 20:00 UTC")
    - `message` (string): Update message

- `faq` (array): Frequently asked questions
  - Each FAQ item has:
    - `question` (string): The question
    - `answer` (string): The answer

### Example: Maintenance Mode

```json
{
  "overallStatus": "maintenance",
  "statusMessage": "Scheduled maintenance is currently in progress.",
  "maintenanceUpdates": [
    {
      "date": "2025-12-01 20:30 UTC",
      "message": "Maintenance is proceeding as planned. Services remain available but may experience brief interruptions."
    },
    {
      "date": "2025-12-01 20:00 UTC",
      "message": "Scheduled maintenance window: 8:00 PM to 11:00 PM UTC."
    }
  ],
  "faq": [
    {
      "question": "When will maintenance be complete?",
      "answer": "Maintenance is expected to complete by 11:00 PM UTC."
    }
  ]
}
```

### Example: Outage

```json
{
  "overallStatus": "outage",
  "statusMessage": "Materia is currently unavailable. Our team is actively working to restore service.",
  "maintenanceUpdates": [
    {
      "date": "2025-12-01 15:30 UTC",
      "message": "Update: We have identified the cause and are implementing a fix. Service should be restored within the hour."
    },
    {
      "date": "2025-12-01 15:00 UTC",
      "message": "Initial report: The application is currently unavailable. Our team is investigating."
    }
  ],
  "faq": [
    {
      "question": "How can I stay updated?",
      "answer": "This page will be updated as we learn more. Please refresh periodically for the latest information."
    }
  ]
}
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
All CSS is in `styles.css` for easy customization. Modify colors, fonts, or layout as needed.

## Examples

See `status-examples.json` for complete examples of different status scenarios.

## License

This project is licensed under the GNU Affero General Public License v3.0. See the LICENSE file for details.

## Related Links

- [Materia on GitHub](https://github.com/ucfopen/Materia)
- [Materia Documentation](https://ucfopen.github.io/Materia-Docs/)
