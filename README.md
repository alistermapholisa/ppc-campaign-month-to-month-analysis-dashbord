# PPC Campaign Performance Dashboard

[![GitHub](https://img.shields.io/badge/GitHub-Repository-blue)](https://github.com/YOUR_USERNAME/ppc-dashboard)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0-orange)](CHANGELOG.md)

A dynamic, self-updating dashboard for tracking and analyzing month-to-month PPC (Pay-Per-Click) advertising campaign performance. This dashboard automatically fetches campaign data from a GitHub-hosted JSON file and displays real-time metrics, trends, and visualizations without requiring any backend infrastructure.

**Perfect for**: Digital marketing agencies, freelancers, and businesses tracking multi-platform advertising campaigns (Facebook, Google Ads, TikTok, LinkedIn, etc.).

---

## 📋 Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Installation](#installation)
- [Data Structure](#data-structure)
- [Configuration](#configuration)
- [Usage](#usage)
- [Elementor Integration](#elementor-integration)
- [Customization](#customization)
- [Troubleshooting](#troubleshooting)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features

- **📊 Real-Time Metrics**: Displays total leads, spend, followers, and cost-per-lead with automatic calculations
- **📈 Trend Analysis**: Month-to-month comparison showing percentage changes with directional indicators (↑↓)
- **📉 Interactive Charts**: Three customizable Chart.js visualizations:
  - Spend distribution by platform (doughnut chart)
  - Cost-per-click comparison (bar chart)
  - Click-through rate analysis (bar chart)
- **📱 Responsive Design**: Fully responsive layout optimized for desktop, tablet, and mobile devices
- **🎨 Scoped CSS**: All styles namespaced with `ppc-` prefix to prevent conflicts with Elementor and existing website code
- **🔄 Auto-Refresh**: Configurable automatic data refresh interval (default: 1 hour)
- **🚀 No Backend Required**: Pure HTML/JavaScript—deploy anywhere without server-side dependencies
- **🔗 GitHub Integration**: Data lives in version-controlled JSON file for easy collaboration and history tracking
- **⚡ Fast Loading**: Minimal dependencies (only Chart.js), loads in under 2 seconds
- **🔒 Secure**: Read-only dashboard, cannot modify your GitHub repository

---

## 🚀 Quick Start

Get your dashboard running in 10 minutes:

### 1. Create GitHub Repository

```bash
# Option 1: Using GitHub CLI
gh repo create ppc-dashboard --public --source=. --remote=origin --push

# Option 2: Create manually at https://github.com/new
# - Name: ppc-dashboard
# - Visibility: Public
# - Initialize with README
```

### 2. Upload Files

Upload these files to your repository:
- `data.json` - Campaign metrics
- `ppc-dashboard-snippet.html` - Dashboard code
- `README.md` - Documentation

### 3. Get Your Data URL

In GitHub, click on `data.json` → Click **Raw** → Copy the URL

Example: `https://raw.githubusercontent.com/YOUR_USERNAME/ppc-dashboard/main/data.json`

### 4. Configure Dashboard

Edit `ppc-dashboard-snippet.html` and update:

```javascript
const CONFIG = {
    dataUrl: 'https://raw.githubusercontent.com/YOUR_USERNAME/ppc-dashboard/main/data.json',
    refreshInterval: 3600000 // 1 hour in milliseconds
};
```

### 5. Embed in Elementor

```html
<!-- In Elementor HTML Widget, paste the entire content of ppc-dashboard-snippet.html -->
<!-- The dashboard will automatically load and display your campaign data -->
```

**Done!** Your dashboard is now live and will auto-update when you modify `data.json`.

---

## 📦 Installation

### Method 1: Direct Copy (Recommended for Elementor)

1. Copy the entire content of `ppc-dashboard-snippet.html`
2. In Elementor, add an **HTML** widget
3. Paste the code into the widget
4. Update the `dataUrl` configuration with your GitHub raw URL
5. Publish

### Method 2: iframe Embedding

If you want to isolate the dashboard completely:

```html
<iframe 
  src="https://raw.githubusercontent.com/YOUR_USERNAME/ppc-dashboard/main/ppc-dashboard-snippet.html" 
  style="width:100%; height:1200px; border:none; border-radius:8px;"
  title="PPC Campaign Dashboard">
</iframe>
```

**Note**: You must still configure the `dataUrl` in the HTML file before using this method.

### Method 3: Self-Hosted

1. Download `ppc-dashboard-snippet.html`
2. Host it on your own server or CDN
3. Update the `dataUrl` to point to your GitHub raw URL
4. Reference the hosted file in your website

---

## 📊 Data Structure

The dashboard expects a JSON file with the following structure:

### Complete Example

```json
{
  "campaigns": [
    {
      "month": "February 2026",
      "date": "2026-02-01",
      "platforms": [
        {
          "name": "Facebook Main Ad",
          "spend": 2500.00,
          "leads": 35,
          "followers": 0,
          "impressions": 55000,
          "clicks": 1800,
          "cpl": 71.43,
          "cpr": null,
          "cpc": 1.39,
          "ctr": 3.27,
          "notes": "Improved lead quality with higher-intent forms"
        },
        {
          "name": "Facebook Followers Ad",
          "spend": 750.00,
          "leads": 0,
          "followers": 380,
          "impressions": 6200,
          "clicks": 500,
          "cpl": null,
          "cpr": 1.97,
          "cpc": 1.50,
          "ctr": 8.06,
          "notes": "Strong brand engagement"
        },
        {
          "name": "Google Ads",
          "spend": 750.00,
          "leads": 8,
          "followers": 0,
          "impressions": 3500,
          "clicks": 120,
          "cpl": 93.75,
          "cpr": null,
          "cpc": 6.25,
          "ctr": 3.43,
          "notes": "Conversion tracking now active"
        }
      ],
      "totalSpend": 4000.00,
      "totalLeads": 43,
      "totalFollowers": 380,
      "challenges": [
        "Google Ads still ramping up",
        "Need to test new ad creatives"
      ],
      "recommendations": [
        "Scale successful Facebook campaigns",
        "Implement A/B testing on Google Ads",
        "Increase budget for top-performing platforms"
      ]
    },
    {
      "month": "January 2026",
      "date": "2026-01-03",
      "platforms": [
        {
          "name": "Facebook Main Ad",
          "spend": 2684.29,
          "leads": 32,
          "followers": 0,
          "impressions": 51723,
          "clicks": 1612,
          "cpl": 83.88,
          "cpr": null,
          "cpc": 1.66,
          "ctr": 3.12,
          "notes": "Initial lead generation campaign"
        }
      ],
      "totalSpend": 3701.28,
      "totalLeads": 32,
      "totalFollowers": 345,
      "challenges": [
        "Google Ads conversion tracking not functional",
        "Website stability issues"
      ],
      "recommendations": [
        "Implement Google Tag Manager",
        "Refine keyword strategy",
        "Implement higher-intent lead forms"
      ]
    }
  ]
}
```

### Field Descriptions

| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `month` | String | Yes | Campaign month (e.g., "February 2026") |
| `date` | String (YYYY-MM-DD) | Yes | Campaign start date for sorting |
| `platforms` | Array | Yes | Array of platform objects |
| `totalSpend` | Number | Yes | Sum of all platform spend |
| `totalLeads` | Number | Yes | Sum of all platform leads |
| `totalFollowers` | Number | Yes | Sum of all platform followers |
| `challenges` | Array | No | List of challenges encountered |
| `recommendations` | Array | No | List of recommendations for next month |

### Platform Object Fields

| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `name` | String | Yes | Platform name (e.g., "Facebook Main Ad") |
| `spend` | Number | Yes | Amount spent on this platform |
| `leads` | Number | Yes | Number of leads generated |
| `followers` | Number | Yes | Number of followers gained |
| `impressions` | Number | Yes | Total impressions |
| `clicks` | Number | Yes | Total clicks |
| `cpl` | Number | No | Cost per lead (calculated or provided) |
| `cpr` | Number | No | Cost per follower (calculated or provided) |
| `cpc` | Number | Yes | Cost per click |
| `ctr` | Number | Yes | Click-through rate (percentage) |
| `notes` | String | No | Additional notes about the campaign |

---

## ⚙️ Configuration

### Basic Configuration

Edit the `CONFIG` object in `ppc-dashboard-snippet.html`:

```javascript
const CONFIG = {
    // GitHub raw URL to your data.json file
    dataUrl: 'https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main/data.json',
    
    // Auto-refresh interval in milliseconds
    refreshInterval: 3600000 // 1 hour
};
```

### Refresh Interval Options

```javascript
// Update every 5 minutes
refreshInterval: 300000

// Update every 10 minutes
refreshInterval: 600000

// Update every 30 minutes
refreshInterval: 1800000

// Update every 1 hour (default)
refreshInterval: 3600000

// Update every 2 hours
refreshInterval: 7200000

// Disable auto-refresh (manual refresh only)
refreshInterval: null
```

### Color Customization

Edit the CSS color values in the `<style>` section:

```css
/* Primary colors */
#2563eb  /* Primary blue */
#1e40af  /* Dark blue */
#1e3a8a  /* Darker blue */

/* Status colors */
#10b981  /* Success green */
#f59e0b  /* Warning orange */
#ef4444  /* Error red */

/* Neutral colors */
#64748b  /* Gray text */
#1e293b  /* Dark text */
#f8fafc  /* Light background */
```

---

## 📈 Usage

### Monthly Update Workflow

1. **Collect Data**
   ```
   - Log into Facebook Ads Manager
   - Log into Google Ads
   - Gather metrics for the month
   ```

2. **Calculate Metrics**
   ```
   Cost Per Click (CPC) = Total Spend ÷ Total Clicks
   Click-Through Rate (CTR) = (Total Clicks ÷ Total Impressions) × 100
   Cost Per Lead (CPL) = Total Spend ÷ Total Leads
   ```

3. **Update data.json**
   - Go to your GitHub repository
   - Click on `data.json`
   - Click the **Edit** (pencil) icon
   - Add your new campaign data to the top of the `campaigns` array
   - Scroll down and click **Commit changes**

4. **Add Commit Message**
   ```
   Update campaign data for February 2026
   
   - Facebook Main Ad: 35 leads at R71.43 CPL
   - Facebook Followers: 380 new followers
   - Google Ads: 8 leads with conversion tracking active
   ```

### Example: Adding New Campaign Data

```json
{
  "month": "March 2026",
  "date": "2026-03-01",
  "platforms": [
    {
      "name": "Facebook Main Ad",
      "spend": 2800.00,
      "leads": 40,
      "followers": 0,
      "impressions": 60000,
      "clicks": 1950,
      "cpl": 70.00,
      "cpr": null,
      "cpc": 1.44,
      "ctr": 3.25,
      "notes": "Best performing month so far"
    },
    {
      "name": "Google Ads",
      "spend": 1200.00,
      "leads": 18,
      "followers": 0,
      "impressions": 5200,
      "clicks": 280,
      "cpl": 66.67,
      "cpr": null,
      "cpc": 4.29,
      "ctr": 5.38,
      "notes": "Significant improvement with refined keywords"
    }
  ],
  "totalSpend": 4000.00,
  "totalLeads": 58,
  "totalFollowers": 420,
  "challenges": [
    "Budget constraints limiting scale"
  ],
  "recommendations": [
    "Increase budget for Google Ads",
    "Test new Facebook audiences",
    "Implement retargeting campaigns"
  ]
}
```

---

## 🎨 Elementor Integration

### Step-by-Step Integration

1. **Open Elementor Editor**
   - Log into WordPress
   - Open the page where you want the dashboard
   - Click **Edit with Elementor**

2. **Add HTML Widget**
   - Search for "HTML" in the left panel
   - Drag the HTML widget to your desired location
   - Click **Edit** on the widget

3. **Paste Dashboard Code**
   ```html
   <!-- Paste the entire content of ppc-dashboard-snippet.html here -->
   <!-- Make sure to update the CONFIG.dataUrl first -->
   ```

4. **Configure Settings**
   - In the HTML widget, you can adjust:
     - Width: Full width or custom
     - Alignment: Left, center, or right
     - Custom CSS: Add additional styling if needed

5. **Publish**
   - Click **Update** to save the widget
   - Click **Publish** to make it live

### Advanced: Custom CSS for Elementor

If you need to adjust spacing or styling within Elementor:

```css
/* Increase top margin */
.ppc-dashboard-container {
    margin-top: 30px;
}

/* Adjust for specific Elementor columns */
.elementor-column .ppc-dashboard-container {
    padding: 20px;
}

/* Mobile adjustments */
@media (max-width: 768px) {
    .ppc-dashboard-container {
        padding: 12px;
    }
    
    .ppc-metrics-grid {
        grid-template-columns: 1fr;
    }
}
```

### Troubleshooting Elementor Integration

**Issue: Dashboard appears but styles look wrong**
- Solution: Hard refresh (Ctrl+Shift+R)
- Check browser console (F12) for CSS conflicts

**Issue: Dashboard doesn't load**
- Solution: Verify the `dataUrl` is correct
- Check that your GitHub repository is public
- Ensure JSON file has valid syntax

**Issue: Charts overlap with other elements**
- Solution: Increase the height of the HTML widget
- Adjust padding in the dashboard CSS

---

## 🎨 Customization

### Changing Chart Types

In the `renderCharts()` function, modify the `type` property:

```javascript
// Doughnut chart (default for spend)
type: 'doughnut'

// Bar chart (default for CPC and CTR)
type: 'bar'

// Line chart (good for trends)
type: 'line'

// Pie chart (alternative to doughnut)
type: 'pie'

// Radar chart (multi-dimensional comparison)
type: 'radar'
```

### Adding New Platforms

Simply add new platform objects to your `data.json`:

```json
{
  "name": "TikTok Ads",
  "spend": 500.00,
  "leads": 15,
  "followers": 250,
  "impressions": 45000,
  "clicks": 900,
  "cpl": 33.33,
  "cpr": 2.00,
  "cpc": 0.56,
  "ctr": 2.00,
  "notes": "Testing new platform"
}
```

### Customizing Colors

Edit the color values in the CSS:

```css
/* Change primary color from blue to green */
.ppc-metric-card {
    border-left: 4px solid #059669; /* Green instead of blue */
}

.ppc-header {
    border-bottom: 3px solid #059669;
}

.ppc-header h1 {
    color: #047857;
}
```

### Adding Custom Metrics

To add a new metric card, modify the metrics grid section:

```html
<div class="ppc-metric-card accent-purple">
    <div class="ppc-metric-label">ROI</div>
    <div class="ppc-metric-value">245%</div>
    <div class="ppc-metric-change positive">↑ 12% vs last month</div>
</div>
```

---

## 🔧 Troubleshooting

### Dashboard Shows "Error Loading Dashboard"

**Diagnosis:**
1. Open browser console (F12)
2. Look for specific error message
3. Check the following:

**Solutions:**

| Error | Cause | Solution |
| :--- | :--- | :--- |
| `404 Not Found` | Wrong data URL | Verify GitHub raw URL is correct |
| `CORS error` | Repository is private | Set repository to **Public** |
| `JSON parsing error` | Invalid JSON syntax | Validate at [JSONLint.com](https://www.jsonlint.com/) |
| `Network error` | No internet connection | Check your connection |

### Data Not Updating

**Checklist:**
- [ ] Has the refresh interval passed? (Default: 1 hour)
- [ ] Did you commit changes to GitHub?
- [ ] Is the JSON file valid?
- [ ] Is the repository still public?

**Solutions:**
1. Hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)
2. Clear browser cache
3. Wait for the next refresh cycle
4. Check GitHub for commit history

### Charts Not Displaying

**Diagnosis:**
1. Open browser console (F12)
2. Look for Chart.js errors
3. Check if Canvas element is supported

**Solutions:**
1. Verify Chart.js CDN is accessible: `https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js`
2. Try a different browser
3. Disable browser extensions that might block scripts
4. Check for JavaScript errors in console

### Elementor CSS Conflicts

**Symptoms:**
- Dashboard text is invisible
- Colors are wrong
- Layout is broken

**Solutions:**
1. The dashboard uses scoped CSS (all classes start with `ppc-`)
2. If conflicts persist, wrap in custom CSS:

```css
.ppc-dashboard-container * {
    all: revert; /* Reset to browser defaults */
}
```

---

## 📚 API Reference

### Configuration Object

```javascript
const CONFIG = {
    // Required: GitHub raw URL to data.json
    dataUrl: String,
    
    // Optional: Auto-refresh interval in milliseconds
    refreshInterval: Number | null
};
```

### Data Object Structure

```javascript
{
    campaigns: Array<Campaign>
}

Campaign {
    month: String,
    date: String (YYYY-MM-DD),
    platforms: Array<Platform>,
    totalSpend: Number,
    totalLeads: Number,
    totalFollowers: Number,
    challenges: Array<String>,
    recommendations: Array<String>
}

Platform {
    name: String,
    spend: Number,
    leads: Number,
    followers: Number,
    impressions: Number,
    clicks: Number,
    cpl: Number | null,
    cpr: Number | null,
    cpc: Number,
    ctr: Number,
    notes: String
}
```

### Utility Functions

```javascript
// Format currency (South African Rand)
formatCurrency(value: Number): String
// Example: formatCurrency(1234.56) → "R1,234.56"

// Format percentage
formatPercentage(value: Number): String
// Example: formatPercentage(3.12) → "3.12%"

// Calculate trend
calculateTrend(current: Number, previous: Number): Number | null
// Example: calculateTrend(100, 80) → 25 (25% increase)
```

---

## 🤝 Contributing

Contributions are welcome! Here's how to contribute:

1. **Fork the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/ppc-dashboard.git
   cd ppc-dashboard
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make your changes**
   - Update files as needed
   - Test thoroughly

4. **Commit and push**
   ```bash
   git add .
   git commit -m "Add: description of your changes"
   git push origin feature/your-feature-name
   ```

5. **Create a pull request**
   - Describe your changes
   - Link any related issues

### Contribution Ideas

- [ ] Add more chart types
- [ ] Implement budget forecasting
- [ ] Add year-over-year comparison
- [ ] Create export to PDF/CSV feature
- [ ] Add custom date range filtering
- [ ] Implement ROI calculations
- [ ] Add platform-specific recommendations engine

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 📞 Support

For help and support:

- **GitHub Issues**: [Create an issue](https://github.com/YOUR_USERNAME/ppc-dashboard/issues)
- **Documentation**: See [SETUP_INSTRUCTIONS.md](SETUP_INSTRUCTIONS.md) for detailed guides
- **Quick Start**: See [QUICK_START.md](QUICK_START.md) for rapid setup

### Frequently Asked Questions

**Q: Do I need to pay for anything?**
A: No! GitHub, Chart.js, and this dashboard are all free.

**Q: Can I use this for multiple clients?**
A: Yes! Create separate repositories for each client's data.

**Q: How often does the data update?**
A: By default, every 1 hour. You can configure this in the CONFIG object.

**Q: Can I modify the dashboard design?**
A: Yes! All CSS is customizable. See the Customization section.

**Q: What if I need help?**
A: Check the troubleshooting section or create a GitHub issue.

---

## 🎯 Roadmap

### Version 1.1 (Planned)
- [ ] Budget forecasting
- [ ] Year-over-year comparison
- [ ] Custom date range filtering

### Version 1.2 (Planned)
- [ ] Export to PDF/CSV
- [ ] ROI calculations
- [ ] Platform-specific recommendations

### Version 2.0 (Future)
- [ ] Backend integration for real-time data
- [ ] User authentication
- [ ] Multi-user collaboration

---

## 📊 Example Dashboard

Your dashboard will display:

```
┌─────────────────────────────────────────────────┐
│  PPC Campaign Performance Dashboard             │
│  Last Updated: February 28, 2026                │
├─────────────────────────────────────────────────┤
│                                                 │
│  Total Leads: 43 (↑ 34.4%)                      │
│  Total Spend: R4,000.00 (↑ 8.0%)                │
│  Followers: 380 (↑ 10.1%)                       │
│  Avg CPL: R93.02                                │
│                                                 │
├─────────────────────────────────────────────────┤
│  [Spend Distribution] [CPC Comparison] [CTR]    │
│  [Platform Performance Table]                   │
│  [Recommendations]                              │
└─────────────────────────────────────────────────┘
```

---

## 🙏 Acknowledgments

- Built with [Chart.js](https://www.chartjs.org/) for visualizations
- Hosted on [GitHub](https://github.com/) for data management
- Integrated with [Elementor](https://elementor.com/) for WordPress
- Inspired by modern data visualization practices

---

## 📝 Changelog

### Version 1.0 (February 28, 2026)
- Initial release
- Core dashboard features
- GitHub integration
- Elementor support
- Trend analysis
- Interactive charts

---

**Created for**: Digital Marketing Professionals  
**Purpose**: Track and optimize PPC advertising performance  
**License**: MIT  
**Repository**: [GitHub](https://github.com/YOUR_USERNAME/ppc-dashboard)

---

## 🚀 Get Started Now

1. Create a GitHub repository
2. Upload the three files
3. Update the configuration
4. Embed in Elementor
5. Start tracking your campaigns!

**Questions?** Check [SETUP_INSTRUCTIONS.md](SETUP_INSTRUCTIONS.md) or [QUICK_START.md](QUICK_START.md)

---

**Last Updated**: February 28, 2026  
**Maintained By**: Your Team  
**Version**: 1.0.0
