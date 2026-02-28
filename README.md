PPC Campaign Performance Dashboard
A dynamic, self-updating dashboard for tracking and analyzing month-to-month PPC (Pay-Per-Click) advertising campaign performance. This dashboard pulls data from a GitHub-hosted JSON file and displays real-time metrics, trends, and comparative analysis across multiple advertising platforms.

Features
Real-Time Data Updates: Dashboard automatically fetches the latest campaign data from your GitHub repository
Multi-Platform Support: Track campaigns across Facebook, Google Ads, and other platforms simultaneously
Trend Analysis: Automatic month-to-month trend calculations showing performance improvements or declines
Interactive Charts: Visual representations of spend distribution, cost-per-click, and click-through rates
Responsive Design: Fully responsive layout that works on desktop, tablet, and mobile devices
Elementor Compatible: Easily embed the dashboard on your WordPress website using Elementor
No Backend Required: Completely static HTML/JavaScript—no server-side code needed
Scoped CSS: All styles are namespaced to prevent conflicts with existing website code
Auto-Refresh: Configurable auto-refresh interval to keep data current
Quick Start
1. Create a GitHub Repository
Create a new public repository on GitHub (or use an existing one) to host your campaign data.

2. Upload Files
Upload these three files to your repository:

data.json - Your campaign metrics
ppc-dashboard-snippet.html - The dashboard code
README.md - Documentation
3. Configure the Dashboard
Edit ppc-dashboard-snippet.html and update the data URL:

const CONFIG = {
    dataUrl: 'https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main/data.json',
    refreshInterval: 3600000 // 1 hour
};
4. Embed in Elementor
Open your WordPress page in Elementor
Add an HTML widget
Paste the contents of ppc-dashboard-snippet.html
Publish
Data Structure
The dashboard expects a JSON file with the following structure:

{
  "campaigns": [
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
          "notes": "Lead generation campaign"
        }
      ],
      "totalSpend": 3701.28,
      "totalLeads": 32,
      "totalFollowers": 345,
      "challenges": ["Challenge 1", "Challenge 2"],
      "recommendations": ["Recommendation 1", "Recommendation 2"]
    }
  ]
}
Dashboard Metrics
Metric	Description	Formula
Total Leads	Number of leads generated across all platforms	Sum of all platform leads
Total Spend	Total advertising budget spent	Sum of all platform spend
Followers Gained	Total new followers/subscribers acquired	Sum of all platform followers
Avg Cost Per Lead	Average cost to acquire one lead	Total Spend ÷ Total Leads
Cost Per Click (CPC)	Average cost per click	Platform Spend ÷ Platform Clicks
Click-Through Rate (CTR)	Percentage of impressions that resulted in clicks	(Platform Clicks ÷ Platform Impressions) × 100
Cost Per Follower (CPR)	Average cost to gain one follower	Platform Spend ÷ Platform Followers
Trend Analysis
The dashboard automatically calculates month-to-month trends for:

Total leads generated
Total advertising spend
Total followers gained
Trends are displayed as percentage changes with directional indicators (↑ for improvement, ↓ for decline).

Customization
Change Colors
Edit the CSS color values in the <style> section:

--primary-blue: #2563eb
--success-green: #10b981
--warning-orange: #f59e0b
--error-red: #ef4444
Adjust Refresh Interval
Modify the refreshInterval in milliseconds:

refreshInterval: 300000  // 5 minutes
refreshInterval: 600000  // 10 minutes
refreshInterval: 1800000 // 30 minutes
refreshInterval: 3600000 // 1 hour (default)
Change Chart Types
Modify the type property in the renderCharts() function:

type: 'doughnut'  // Circular chart
type: 'bar'       // Bar chart
type: 'line'      // Line chart
type: 'pie'       // Pie chart
Monthly Update Workflow
Collect campaign data from your advertising platforms (Facebook Ads Manager, Google Ads, etc.)
Calculate metrics using the formulas provided
Edit data.json in your GitHub repository
Add your new campaign data to the beginning of the campaigns array
Commit changes with a descriptive message
The dashboard will automatically refresh and display new data
Troubleshooting
Dashboard Shows Error
Check:

Is your GitHub repository set to Public?
Is the data URL correct in the configuration?
Does the data.json file have valid JSON syntax? (Test at JSONLint.com)
Solution:

Hard refresh your browser (Ctrl+Shift+R or Cmd+Shift+R)
Check the browser console (F12) for specific error messages
Data Not Updating
Check:

Has the refresh interval passed? (Default: 1 hour)
Is your browser caching old data?
Solution:

Hard refresh your browser
Clear browser cache
Wait for the next refresh cycle
Charts Not Displaying
Check:

Is Chart.js CDN accessible?
Are there JavaScript errors in the console?
Solution:

Open browser console (F12) and look for errors
Verify Chart.js CDN is reachable: https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js
Browser Compatibility
Chrome 90+
Firefox 88+
Safari 14+
Edge 90+
Technical Stack
Frontend: HTML5, CSS3, JavaScript (ES6+)
Data Source: JSON file hosted on GitHub
Charting: Chart.js 4.4.0
Hosting: GitHub (data) + Your website (dashboard)
Security
The dashboard is read-only; it cannot modify your GitHub repository
Keep your repository public for the dashboard to access data
Do not include sensitive information (API keys, passwords) in the JSON file
All data is fetched client-side; no server-side processing occurs
File Structure
your-repo/
├── data.json                      # Campaign metrics (updated monthly)
├── ppc-dashboard-snippet.html     # Dashboard code (embed in Elementor)
├── README.md                      # This file
└── SETUP_INSTRUCTIONS.md          # Detailed setup guide
Performance Considerations
Dashboard loads in under 2 seconds on typical connections
Auto-refresh is configurable to balance freshness with bandwidth usage
Charts are rendered client-side for instant interactivity
No external API calls except to GitHub for data
Future Enhancements
Potential features for future versions:

Year-over-year comparison
Budget forecasting
Platform-specific recommendations
Export to PDF/CSV
Custom date range filtering
ROI calculations
License
This project is provided as-is for personal and commercial use.

Support
For detailed setup instructions, troubleshooting, and advanced customization, refer to SETUP_INSTRUCTIONS.md.

For questions about:

GitHub: Visit GitHub Docs
Elementor: Visit Elementor Help
Chart.js: Visit Chart.js Docs
Version
Current Version: 1.0
Last Updated: February 28, 2026

Created for: BodyTwenty Studios Randridge
Purpose: Track and optimize PPC advertising campaign performance month-to-month
