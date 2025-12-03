# 🚀 Quick Start Guide - Deal Return Calculator React

## Get Up and Running in 5 Minutes

### Step 1: Install Node.js (if you haven't already)
Download from: https://nodejs.org/ (Choose LTS version)

### Step 2: Extract the Project
Extract the `deal-calculator-react` folder to your desired location

### Step 3: Open Terminal/Command Prompt
- **Windows**: Open folder, type `cmd` in address bar, press Enter
- **Mac**: Right-click folder, select "New Terminal at Folder"
- **Linux**: Right-click folder, select "Open in Terminal"

### Step 4: Install Dependencies
```bash
npm install
```
(Wait 1-2 minutes for installation to complete)

### Step 5: Start the Application
```bash
npm start
```

The app will automatically open in your browser at `http://localhost:3000`

## 🔥 Important: Add Complete Product Data

The current version includes only 30 sample products. You need to:

1. Open `src/data/constants.js`
2. Replace the PRODUCTS array with all 327 products from your original HTML
3. Copy the entire PRODUCTS array from your HTML file's `<script>` section
4. Save the file

## 📦 Building for Production

When ready to deploy:

```bash
npm run build
```

This creates a `build/` folder with optimized files ready for deployment.

## ✅ What Works Out of the Box

- ✅ Deal input forms
- ✅ Product management (search, add, remove)
- ✅ Multi-currency calculations
- ✅ Discount management
- ✅ Metrics calculations
- ✅ PDF Quote export
- ✅ PDF Usage export
- ✅ CSV export
- ✅ Assessment badges

## 🔧 What Needs Configuration

- ⚠️ Complete product data (add remaining 297 products)
- ⚠️ HubSpot API integration (currently placeholder)
- ⚠️ Authentication setup (for production deployment)
- ⚠️ Logo image (add base64 encoded logo to exports.js)

## 🆘 Troubleshooting

### "npm: command not found"
➡️ Install Node.js from https://nodejs.org/

### "Port 3000 is already in use"
➡️ Stop the other process or change port:
```bash
PORT=3001 npm start
```

### Calculator looks broken
➡️ Clear browser cache (Ctrl+Shift+R on Windows/Linux, Cmd+Shift+R on Mac)

### PDF export not working
➡️ Ensure jsPDF installed:
```bash
npm install jspdf jspdf-autotable
```

## 📊 Using the Calculator

1. **Select Currency** (top right)
2. **Fill in deal details** (left column)
3. **Add products** (middle column)
   - Search or browse
   - Set volumes
   - Apply discounts
4. **Review metrics** (right column)
5. **Export** (bottom right)

## 🎯 Next Steps

1. ✅ Add all 327 products to `src/data/constants.js`
2. Test all functionality thoroughly
3. Customize colors/branding if needed
4. Set up production deployment
5. Configure authentication
6. Integrate with real HubSpot API

## 📞 Need Help?

Check the full README.md for detailed documentation.

---

Happy Calculating! 🧮
