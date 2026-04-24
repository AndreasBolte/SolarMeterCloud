# Google Sheets Setup (SolarMeterCloud)

## 1. Requirements
- A standard Google account (no Workspace required)
- Web browser
- Internet connection

---

## 2. Create a new Google Sheet
1. Open Google Drive  
2. Click **New → Google Sheets**  
3. Name the document, e.g. **SolarMeterCloud – Live Data**  
4. Create the required tabs (worksheets), for example:
   - `raw_data`
   - `daily`
   - `monthly`
   - `charts`

---

## 2.5 Prepare the sheet for external updates (Update Cells)

External tools such as Node‑RED or Apps Script can only update the sheet if it is prepared correctly.

### Define a fixed structure
- **Row 1:** Headers (e.g. `Timestamp`, `Power`, `Energy`, `Voltage`)  
- **Rows 2+:** Data rows to be filled automatically  
- Use a dedicated tab for incoming data, e.g. `raw_data`

---

## 2.6 Grant access to the service account (required for updating cells)

Node‑RED or Apps Script can only write to the sheet if the service account has **Editor** permissions.

1. Open the Google Sheet  
2. Click **Share**  
3. Add the service account email:
4. Set permission to **Editor**  
5. Confirm

Only after this step can external systems update cells reliably.

---

## 2.7 Important: The sheet/tab name must match exactly

Node‑RED requires the **exact** tab name to locate the correct worksheet.

If the name differs even slightly, updates will fail with errors like:

- “Sheet not found”
- “Unable to locate range”
- “Invalid sheet ID”

### Example

If your tab is named:
raw_data

Then Node‑RED must also use:
raw_data

Not:

- `Raw_Data`  
- `raw-data`  
- `Sheet1`  
- `data`  

Google Sheets identifies each tab strictly by name.  
If the name does not match, the update will fail.

---

## 2.8 Test the update path

Before continuing with publishing or embedding:

1. Write a test value into a known cell (e.g. `raw_data!B2`) using Node‑RED or Apps Script  
2. Reload the sheet in the browser  
3. Confirm that the value appears  
4. If not, check:
   - Service account permissions  
   - Tab name  
   - Cell range  
   - Node‑RED configuration

This ensures the update mechanism works before moving on.

## 2.9 Create a chart in Google Sheets

Before you can publish an interactive chart, you must first create it inside Google Sheets.

### Steps to create the chart

1. Select the data range you want to visualize  
   - Example: cell `F6` or a range like `F6:G20`
2. Go to **Insert → Chart**  
3. The **Chart editor** will open on the right side

### Chart type and data range

In the Chart editor:

- **Chart type:** select a suitable overview chart (e.g. line chart, area chart, or column chart)  
- **Data range:** make sure it points to your desired range, e.g.  
  - `F6`  
  - or `F6:G20`  
  depending on your data layout

### Custom formatting

Under the **Customize** tab in the Chart editor:

- Apply your own formatting:
  - Colors
  - Line thickness
  - Axis labels
  - Legend
- Use **custom formatting** so the chart matches your SolarMeterCloud style.

This ensures the chart is readable, consistent, and visually aligned with your project.

---
### Number formatting: Prefix for units

In the **Chart editor → Customize → Series → Key value**, you can define a **prefix** for the displayed values.  
Enter the unit **with a leading space**, for example:

- ` kWh`
- ` W`
- ` V`

This ensures that the unit is shown directly in the chart labels without modifying the underlying data.

## 2.10 Publish to the web (Interactive embed link)

To embed charts or live data from Google Sheets into SolarMeterCloud, you must publish the sheet or chart using the **interactive embed link**.

### Steps

1. Open your Google Sheet  
2. Click on the chart you created  
3. Go to **File → Publish to the web**  
4. Select **Embed**  
5. Choose **Interactive**  
6. Click **Publish**  
7. Copy the generated embed link and **save it** — this link is required for embedding.

### Important

- This is **not** the normal Google Sheets URL.  
- Only the **interactive embed link** works inside an iframe.  
- Without this link, charts will not load or update correctly.

### Example (interactive chart embed)

```html
<iframe 
  width="227" 
  height="50" 
  seamless 
  frameborder="0" 
  scrolling="no" 
  src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRfUsWwHuXq7c6nPdIOcbMGO6H4wfInrEk2udqtVtTVkVuvqEJSua-_I36V6sDZ48Vk7TDtaFmJpitE/pubchart?oid=734868573&format=interactive">
</iframe>






