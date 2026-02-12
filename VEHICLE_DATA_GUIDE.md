# Vehicle Data Management Guide

This guide shows you how to manage vehicle pricing and model information using CSV files and a Python converter.

## 📁 File Structure

```
car-dealership-site/
├── data/
│   └── vehicles.json          # Auto-generated JSON (don't edit manually)
├── templates/
│   ├── Passenger Vehicles.csv
│   ├── Light Commercial.csv
│   ├── Medium Duty Trucks.csv
│   └── Heavy Duty GIGA.csv
├── excel_to_json.py           # Converter script
└── index.html                 # Website (loads data from JSON)
```

## 📊 How to Edit Vehicle Data

### Option 1: Edit CSV Files (Simplest)

1. **Open a CSV file in Excel:**
   - Open `templates/Passenger Vehicles.csv` (or any other category)
   - Double-click or use File → Open

2. **Edit the data:**
   - Model: Vehicle model name
   - Variant: Technical specs or sub-models
   - Price: Use format `₱XXX,XXX – ₱XXX,XXX` or `Price on Request`

3. **Save the file:**
   - File → Save (keep as CSV format)
   - Close Excel

4. **Generate JSON from CSV:**
   - Use the converter (see below)

### Option 2: Use Excel Workbook (Optional)

If you prefer a single Excel file:
1. Create `vehicles.xlsx` with sheets named:
   - "Passenger Vehicles"
   - "Light Commercial"
   - "Medium Duty Trucks"
   - "Heavy Duty GIGA"

2. Each sheet should have columns:
   - A: Model
   - B: Variant
   - C: 2026 Price Range (SRP)

3. Save and use the converter script

## 🔄 Converting CSV/Excel to JSON

### Prerequisites
Install Python (if not already installed):
- Windows: Download from [python.org](https://www.python.org/downloads/)
- Mac/Linux: `brew install python3`

Install required library:
```bash
pip install openpyxl
```

### Running the Converter

**For CSV Files:**
```bash
python excel_to_json.py
```
This will read all CSV files from `templates/` and generate `data/vehicles.json`

**For Excel File:**
```bash
python excel_to_json.py vehicles.xlsx
```

### Expected Output
```
✓ Successfully generated 'data/vehicles.json'
  Total categories: 4
  - Passenger Vehicles: 2 models
  - Light Commercial Vehicles: 1 model
  - Light to Medium Duty Trucks: 2 models
  - Heavy Duty & Special Purpose: 2 models
```

## 📱 Website Updates

Once you run the converter:
1. The new `data/vehicles.json` is generated
2. Refresh your website in the browser
3. Click each vehicle category to see the updated pricing tables

## ⚙️ JSON File Format (Reference)

The generated JSON structure:
```json
{
  "categories": [
    {
      "id": "passenger",
      "name": "Passenger Vehicles",
      "subtitle": "Personal & Family",
      "icon": "👨‍👩‍👧‍👦",
      "description": "Personal & Family vehicles...",
      "models": [
        {
          "model": "Isuzu D-MAX",
          "variant": "Pickup Truck...",
          "priceRange": "₱978,000 – ₱1,995,000"
        }
      ]
    }
  ]
}
```

## Troubleshooting

**"Python not found"**
- Install Python from [python.org](https://www.python.org)
- Add to PATH during installation

**"openpyxl not installed"**
- Run: `pip install openpyxl`

**CSV won't open in Excel**
- Use "File → Open" instead of double-clicking
- Select "All Files" as file type

**JSON not updating on website**
- Clear browser cache (Ctrl+Shift+Delete)
- Hard refresh (Ctrl+Shift+R)

## Quick Workflow

```
1. Edit CSV file in Excel
   ↓
2. Run: python excel_to_json.py
   ↓
3. Refresh website in browser
   ↓
4. Done! ✓
```

---

**Questions?** Contact your developer for setup assistance.
