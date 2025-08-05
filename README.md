# ArcGIS Online Feature Layer Overwrite from Google Sheets

A Jupyter Notebook that:

- Authenticates to a **private** Google Sheet via Service Account  
- Reads the sheet into pandas, converts to a SpatialDataFrame (if `Lat`/`Long` present)  
- Deletes and re–adds all records in an existing ArcGIS Online feature layer  
- Can be scheduled to run daily from ArcGIS Online

## Prerequisites

- ArcGIS Online account with overwrite permissions  
- ArcGIS API for Python available in your notebook  
- Google Cloud project with Sheets API and Drive API enabled  
- Service Account JSON key downloaded  
- Google Sheet shared with the Service Account’s email  
- Target Feature Layer Item ID  

## Setup

1. **Enable APIs**  
   - In Google Cloud Console, enable **Google Sheets API** and **Drive API**.  
2. **Create Service Account**  
   - In IAM & Admin → Service Accounts, create an account, grant “Sheets Viewer” and “Drive Viewer”, then generate a JSON key.  
3. **Share Sheet**  
   - In Google Sheets, share with the Service Account’s `client_email`.  
4. **Upload JSON**  
   - In the notebook’s Files pane, upload the JSON into `/home`.  
5. **Configure Variables**  
   ```python
   SERVICE_ACCOUNT_FILE = "your-key.json"
   SHEET_ID            = "yourSheetId"
   LAYER_ITEM_ID       = "yourLayerItemId"
   AGO_ORG_URL         = "https://www.arcgis.com"

## Running
- Open the notebook and run all cells in order.
- Verify console output for row and feature counts.

## Scheduling
- Publish the notebook in ArcGIS Online, open its item page, select Schedule, choose a frequency and time, and save.
