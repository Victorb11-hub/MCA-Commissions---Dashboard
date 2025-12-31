# MCA Commission Dashboard

A comprehensive, interactive dashboard for tracking Merchant Cash Advance (MCA) commissions, deals, and rep payouts.

![Dashboard Preview](https://img.shields.io/badge/Status-Production%20Ready-success)

## 🚀 Features

### Multi-Page Dashboard
- **Dashboard** - Overview with key metrics and recent deals
- **All Deals** - Complete searchable/filterable table of all deals
- **By Rep** - Individual rep performance and commission tracking

### Commission Tracking
- ✅ Track commissions for multiple reps with custom percentages
- ✅ Inline editing - click checkboxes to mark deals as paid
- ✅ Real-time calculation of outstanding balances
- ✅ PSF (Point Sale Fee) support
- ✅ Automatic 30-day clawback period calculation
- ✅ Clawback tracking for defaulted deals

### Deal Management
- ✅ Add new deals with custom commission splits
- ✅ Assign multiple reps per deal with individual percentages
- ✅ Track payment status, clawback period, and defaults
- ✅ Search and filter by client, lender, source, or status

### Rep Management
- ✅ Add new reps with custom commission percentages
- ✅ View detailed commission breakdown per rep
- ✅ See exactly what you owe each rep
- ✅ Track paid vs unpaid commissions

## 📊 Quick Start

### Option 1: Open Directly
1. Download `MCA_Dashboard_Final.html`
2. Open the file in any modern web browser (Chrome, Firefox, Safari, Edge)
3. Start tracking your commissions!

### Option 2: Host on GitHub Pages
1. Fork this repository
2. Go to Settings > Pages
3. Select "Deploy from a branch"
4. Choose `main` branch and `/` (root) folder
5. Your dashboard will be live at `https://[your-username].github.io/[repo-name]/MCA_Dashboard_Final.html`

## 💻 Usage

### Adding a New Deal
1. Click **"+ Add Deal"** button on Dashboard or All Deals page
2. Fill in deal details (Business name, date, lender, amount, etc.)
3. Enter commission percentage
4. Add PSF amount if applicable
5. Assign reps and their commission percentages
6. Click **"Add Deal"**

### Adding a New Rep
1. Go to the **"By Rep"** page
2. Click **"+ Add Rep"** button
3. Enter rep name and default commission percentage
4. Click **"Add Rep"**

### Marking Deals as Paid
- Simply **click the checkbox** next to "Paid?" in any table
- Changes sync across all pages automatically
- Rep's outstanding balance updates in real-time

### Handling Clawbacks (Defaults)
1. Find the deal in **All Deals** or rep modal
2. Click the **"Clawed Back?"** checkbox
3. Deal automatically marks as unpaid
4. Commission is reversed from rep's totals
5. Red warning badge appears

## 🎯 Understanding the Columns

### All Deals Page
- **Date** - When the deal was funded
- **Client** - Business name
- **Lender** - Funding company (CFG, Everest, etc.)
- **Amount** - Deal size
- **Commission** - Total commission earned (includes PSF)
- **Paid?** - Click to mark as paid/unpaid
- **Past Clawback Period?** - Auto-calculated (30 days from funded date)
- **Clawed Back?** - Mark if deal defaulted and commission was reversed

### Rep Modal
Shows the same info but filtered to that specific rep's deals, plus:
- **Their Commission** - The exact amount owed to that rep
- **Outstanding balance** - Total unpaid commissions

## 🔧 Technical Details

- **Built with**: Pure HTML/CSS/JavaScript - no dependencies!
- **Data Storage**: Browser memory (data resets on page refresh)
- **Browser Support**: Chrome, Firefox, Safari, Edge (latest versions)
- **File Size**: ~280 KB (all-in-one file)

## 📝 Data Structure

The dashboard uses two main data structures:

### Deal Object
```javascript
{
  id: 1,
  dealName: "ABC Company LLC",
  client: "John Smith",
  dateFunded: "2025-01-15",
  lender: "CFG",
  amount: 50000,
  rate: 1.42,
  totalCommission: 6500, // includes PSF
  psfAmount: 500,
  source: "JD Leads",
  paidOut: "YES", // or "NO"
  pastClawback: "YES", // auto-calculated
  clawedBack: "NO", // manually set
  rayCommission: 3250,
  shwekyCommission: 3250,
  riversCommission: 0
}
```

### Rep Object
```javascript
{
  totalOwed: 81651.20,
  totalPaid: 81651.20,
  outstanding: 0,
  numDeals: 31,
  percentage: 50,
  deals: [/* array of deals */]
}
```

## 🚨 Important Notes

### Data Persistence
- **Current version**: Data is stored in browser memory only
- Changes are **NOT saved** when you refresh the page
- For production use, consider implementing:
  - Backend API (Node.js, Python, etc.)
  - Database (PostgreSQL, MongoDB, etc.)
  - Google Sheets integration
  - LocalStorage (temporary solution)

### Calculations
- **Clawback Period**: Automatically calculated as 30 days from funded date
- **Commission**: Base commission + PSF amount
- **Rep Commission**: Total commission × Rep percentage
- **Outstanding**: Total Owed - Total Paid

## 🎨 Customization

### Change Theme Colors
Edit the CSS variables at the top of the HTML file:
```css
:root {
    --bg-dark: #0a0e1a;
    --accent-primary: #00ff88;
    --accent-warning: #ffaa00;
    --accent-danger: #ff3366;
    /* etc... */
}
```

### Add More Reps
Use the **"+ Add Rep"** button in the dashboard, or manually add to the `repData` object in the code.

### Modify Commission Structure
Edit the form fields in the "Add Deal" modal to match your business needs.

## 📈 Future Enhancements

Potential features to add:
- [ ] Backend database integration
- [ ] User authentication
- [ ] Export to Excel/CSV
- [ ] Email notifications for unpaid commissions
- [ ] Chart visualizations
- [ ] Mobile app version
- [ ] Multi-user support with permissions
- [ ] Automated commission calculations from lender contracts

## 🐛 Troubleshooting

**Q: My data disappeared after refreshing!**  
A: Data is stored in browser memory only. Implement backend storage for persistence.

**Q: Checkboxes aren't working**  
A: Make sure JavaScript is enabled in your browser.

**Q: Can I use this offline?**  
A: Yes! Download the HTML file and open it locally.

**Q: How do I backup my data?**  
A: Currently, you'd need to manually record deals. Future versions will include export functionality.

## 📄 License

MIT License - feel free to use and modify for your business needs.

## 🤝 Contributing

This is a single-file dashboard designed for simplicity. If you'd like to extend it:
1. Fork the repository
2. Make your changes
3. Submit a pull request

## 💬 Support

For issues or questions:
1. Check the code comments in the HTML file
2. Review this README
3. Open an issue in the GitHub repository

## 🎯 Best Practices

1. **Regularly backup your data** (until backend is implemented)
2. **Mark deals as paid immediately** to keep accurate records
3. **Use clawback feature** only when deals actually default
4. **Review outstanding balances** before paying reps
5. **Keep browser updated** for best performance

---

Built for MCA professionals who need a fast, reliable commission tracking system. 🚀
