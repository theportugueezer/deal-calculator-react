# Deal Return Calculator - React Version 2.0

React application for generating accurate quotes and analysing deal profitability with multi currency support, PDF/CSV exports, and HubSpot integration (placeholder).

## 🚀 Features

- **Deal Management**: Comprehensive input forms for customer details, plan selection, and contract terms
- **Product Library**: 327+ transaction products with pricing across multiple currencies (AUD, USD, NZD, EUR, CAD)
- **Multi-Currency Support**: Real-time currency conversion with configurable exchange rates
- **Advanced Pricing**: 
  - Plan-based pricing (Basic, Professional, Enterprise)
  - Individual product discounts (absolute or percentage)
  - Custom cost price modeling for profitability scenarios
- **Financial Metrics**:
  - ARR, MRR, TCV calculations
  - Gross Profit & Margin analysis
  - LTV/CAC ratio with automatic assessment
  - Payback period calculations
- **Export Capabilities**:
  - PDF Quote generation
  - PDF Usage reports
  - CSV exports
- **HubSpot Integration**: Send quotes directly to HubSpot deals (placeholder implementation)

## 📁 Project Structure

```
deal-calculator-react/
├── public/
│   └── index.html
├── src/
│   ├── components/
│   │   ├── Header.jsx            # Currency selector & assessment badge
│   │   ├── DealInputs.jsx        # Customer & contract details form
│   │   ├── LicenseFees.jsx       # Portal seats, support, add-ons
│   │   ├── ProductManager.jsx    # Product search & selection
│   │   ├── ProductRow.jsx        # Individual product with volume & discounts
│   │   ├── KeyMetrics.jsx        # ARR, MRR, TCV display
│   │   ├── Profitability.jsx     # GP, LTV/CAC, Payback
│   │   ├── Actions.jsx           # Export & reset buttons
│   │   └── HubSpotModal.jsx      # Deal selection & quote sending
│   ├── data/
│   │   └── constants.js          # Products, pricing, exchange rates
│   ├── utils/
│   │   ├── calculations.js       # Metrics calculations & conversions
│   │   └── exports.js            # PDF & CSV generation
│   ├── styles/
│   │   └── HubSpotModal.css      # Modal-specific styles
│   ├── App.jsx                   # Main application component
│   ├── App.css                   # Global styles
│   ├── index.js                  # React entry point
│   └── index.css                 # Base styles
├── package.json                  # Dependencies & scripts
└── README.md                     # This file
```

## 🛠️ Setup Instructions

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. **Clone or download the project**

2. **Install dependencies**
   ```bash
   cd deal-calculator-react
   npm install
   ```

3. **Update Product Data** (Important!)
   
   The current `src/data/constants.js` contains only a sample of products - UPDATED

4. **Start the development server**
   ```bash
   npm start
   ```

   The app will open at `http://localhost:3000`

### Building for Production

```bash
npm run build
```

This creates an optimized production build in the `build/` folder.

## 🚢 Deployment

### Cloudflare Workers (Current Deployment)

Since your current deployment is on Cloudflare Workers at `https://deal-calculator.pmgoncalves0.workers.dev/`:

1. **Build the production version:**
   ```bash
   npm run build
   ```

2. **Deploy to Cloudflare:**
   - Upload the contents of the `build/` folder to your Cloudflare Workers site
   - Configure your Workers script to serve the static files
   - Ensure authentication middleware is properly configured

### Alternative Deployment Options

- **Vercel**: `vercel --prod`
- **Netlify**: Drag & drop the `build/` folder
- **AWS S3 + CloudFront**: Upload build folder to S3 bucket
- **GitHub Pages**: Configure in package.json and run `npm run deploy`

## 🔐 Authentication

The current deployment includes email-based authentication with session management. To add this to the React app:

1. Create a Cloudflare Worker or backend API endpoint
2. Implement the authentication flow (email code verification)
3. Add session storage (7-day validity)
4. Protect routes using authentication middleware

Example Worker structure:
```
/api/auth/send-code  → Send verification code
/api/auth/verify     → Verify code and create session
/api/calculator/*    → Protected calculator routes
```

## 📊 Using the Calculator

### Basic Workflow

1. **Select Currency**: Choose display currency in the header
2. **Enter Deal Details**: Customer name, plan, contract term, etc.
3. **Configure License Fees**: Portal seats, support level, add-ons
4. **Add Products**:
   - Search or browse the 327-product library
   - Add individual products or bulk-select all
   - Set volumes and apply discounts
   - Model custom cost prices for profitability analysis
5. **Review Metrics**: Check ARR, TCV, LTV/CAC ratio, and overall assessment
6. **Export**: Generate PDF quotes, usage reports, or CSV exports
7. **Send to HubSpot**: (Optional) Associate quote with a deal

### Key Calculations

- **ARR**: Annual Recurring Revenue from platform fees and licenses
- **TCV**: Total Contract Value over the contract term
- **LTV/CAC**: Lifetime Value to Customer Acquisition Cost ratio
  - ≥4.0 = Great (Hit the gong!)
  - ≥3.0 = Good
  - ≥2.0 = Average
  - <2.0 = Poor (Consult Finance Team)

## 🎨 Customization

### Adding More Products

Edit `src/data/constants.js`:

```javascript
export const PRODUCTS = [
  {
    id: 328,
    name: 'New Product Name',
    currency: 'USD',
    basePrice: 10.00,
    proPrice: 7.50,
    enterprisePrice: 5.00,
    costPrice: 2.00
  },
  // ... more products
];
```

### Modifying Exchange Rates

Update `EXCHANGE_RATES` in `src/data/constants.js`:

```javascript
export const EXCHANGE_RATES = {
  AUD: { AUD: 1, USD: 0.65, ... },
  // ... update rates
};
```

### Changing Plan Pricing

Modify `PLAN_PRICING` in `src/data/constants.js`:

```javascript
export const PLAN_PRICING = {
  'Basic': { platformFees: 3000, implementationFee: 2499 },
  // ... update plans
};
```

### Styling

- **Global styles**: Edit `src/App.css`
- **Component-specific**: Create new CSS files in `src/styles/`
- **Color scheme**: Update CSS variables or hex codes in App.css

## 🔌 HubSpot Integration

The current implementation includes a placeholder HubSpot integration. To connect to your actual HubSpot instance:

1. **Set up OAuth**:
   - Register your app in HubSpot
   - Get Client ID and Client Secret
   - Configure redirect URI

2. **Create Backend Endpoints**:
   ```
   POST /api/hubspot/auth     → OAuth authentication
   GET  /api/hubspot/deals    → Search deals
   POST /api/hubspot/quote    → Create quote on deal
   ```

3. **Update Frontend**:
   - Replace mock API calls in `src/components/HubSpotModal.jsx`
   - Add real OAuth flow
   - Handle token refresh

## 📝 Known Limitations & TODOs

- [ ] Complete HubSpot API integration (currently placeholder)
- [ ] Add logo image (convert to base64 and add to exports.js)
- [ ] Implement user authentication UI
- [ ] Add unit tests
- [ ] Add loading states and error boundaries
- [ ] Implement data persistence (localStorage or backend)
- [ ] Add product categories/tags for better organization
- [ ] Create admin panel for managing products and pricing

## 🐛 Troubleshooting

### PDF Generation Not Working

Ensure jsPDF is properly installed:
```bash
npm install jspdf jspdf-autotable
```

### Products Not Displaying

Check that all 327 products are properly added to `src/data/constants.js`

### Calculation Errors

Verify that:
- All numeric inputs have default values
- Currency conversion rates are up-to-date
- Product cost prices are defined

## 📚 Dependencies

- **react**: ^18.2.0 - UI library
- **react-dom**: ^18.2.0 - DOM rendering
- **jspdf**: ^2.5.1 - PDF generation
- **jspdf-autotable**: ^3.5.31 - PDF table formatting

## 🤝 Contributing

This is an internal tool. For feature requests or bug reports, contact the development team.

## 📄 License

Proprietary - Internal Use Only

## 📞 Support

For questions or issues:
- Technical: Contact development team
- Business Logic: Contact Finance Team (Jacqui)
- HubSpot Integration: Contact Sales Operations

---

**Version**: 2.0.0  
**Last Updated**: December 2024  
**Built with**: React 18, jsPDF
