# Google Sheets API Setup Guide

This guide will walk you through setting up Google Sheets API access for the PRUDEV II MSME Support Portal.

## Overview

Once configured, the portal will automatically fetch BGE and MSME data from your Google Sheets, eliminating the need for manual data entry.

---

## Step 1: Create a Google Cloud Project

1. **Go to Google Cloud Console**
   - Visit: https://console.cloud.google.com/
   - Sign in with your Google account

2. **Create a New Project**
   - Click the project dropdown at the top
   - Click "New Project"
   - Enter project name: `PRUDEV-MSME-Portal`
   - Click "Create"
   - Wait for the project to be created (takes a few seconds)

3. **Select Your Project**
   - Make sure your new project is selected in the dropdown

---

## Step 2: Enable Google Sheets API

1. **Navigate to APIs & Services**
   - In the left sidebar, click "APIs & Services" → "Library"
   - Or visit: https://console.cloud.google.com/apis/library

2. **Search for Google Sheets API**
   - In the search bar, type: `Google Sheets API`
   - Click on "Google Sheets API" from the results

3. **Enable the API**
   - Click the blue "Enable" button
   - Wait for it to be enabled

---

## Step 3: Create API Credentials

1. **Go to Credentials**
   - Click "APIs & Services" → "Credentials" in the left sidebar
   - Or visit: https://console.cloud.google.com/apis/credentials

2. **Create API Key**
   - Click "+ CREATE CREDENTIALS" at the top
   - Select "API key"
   - A popup will show your new API key
   - **IMPORTANT**: Copy this key immediately and save it somewhere safe

3. **Restrict the API Key (Recommended)**
   - Click "RESTRICT KEY" in the popup (or edit the key later)
   - Under "API restrictions":
     - Select "Restrict key"
     - Check only "Google Sheets API"
   - Under "Application restrictions" (optional but recommended):
     - Select "HTTP referrers (web sites)"
     - Add your domain (or use `*` for testing)
   - Click "Save"

---

## Step 4: Make Your Spreadsheets Publicly Readable

For each of your three spreadsheets, you need to make them accessible:

### MSME Cohort 1
1. Open: https://docs.google.com/spreadsheets/d/1SVO6vWr2Dn0CE02vxnlGO8daNiggCyI2/edit
2. Click "Share" button (top right)
3. Click "Change to anyone with the link"
4. Set permission to "Viewer"
5. Click "Done"

### MSME Cohort 2
1. Open: https://docs.google.com/spreadsheets/d/1glDn1U8fwo-UJCo5akk4gD1d25F45klg/edit
2. Click "Share" button (top right)
3. Click "Change to anyone with the link"
4. Set permission to "Viewer"
5. Click "Done"

### BGE Master List (SharePoint)
**Note**: The BGE list is on SharePoint, not Google Sheets. You have two options:
- **Option A**: Move the BGE list to Google Sheets (recommended for consistency)
- **Option B**: Keep it on SharePoint and manually update the portal's localStorage

---

## Step 5: Get Your Spreadsheet IDs

You already have these, but here's how to identify them:

### MSME Cohort 1
- URL: `https://docs.google.com/spreadsheets/d/1SVO6vWr2Dn0CE02vxnlGO8daNiggCyI2/edit?gid=374779689#gid=374779689`
- **Spreadsheet ID**: `1SVO6vWr2Dn0CE02vxnlGO8daNiggCyI2`
- **Sheet Name/GID**: `374779689` (we'll need to get the actual sheet name)

### MSME Cohort 2
- URL: `https://docs.google.com/spreadsheets/d/1glDn1U8fwo-UJCo5akk4gD1d25F45klg/edit?gid=1212040973#gid=1212040973`
- **Spreadsheet ID**: `1glDn1U8fwo-UJCo5akk4gD1d25F45klg`
- **Sheet Name/GID**: `1212040973`

---

## Step 6: Identify Sheet Names and Data Structure

For the API to work, I need to know:

1. **What is the name of each sheet tab?**
   - Open each spreadsheet
   - Look at the bottom tabs
   - Example: "Sheet1", "MSMEs", "Data", etc.

2. **What columns contain the data?**
   - For MSMEs, I need:
     - Business Name (which column? e.g., Column A)
     - Location (which column? e.g., Column B)
   - For BGEs, I need:
     - Name (which column?)
     - Location (which column?)
     - Code (which column?)

3. **What row does the data start?**
   - Row 1 (if no headers)
   - Row 2 (if row 1 has headers)

---

## Step 7: Provide Information to Me

Once you've completed the above steps, provide me with:

1. ✅ **Your API Key** (the one you created in Step 3)
2. ✅ **Sheet Names** for each spreadsheet (from Step 6)
3. ✅ **Data Structure** (which columns have which data)
4. ✅ **Starting Row** (where the actual data begins)

### Example Format:
```
API Key: AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

MSME Cohort 1:
- Spreadsheet ID: 1SVO6vWr2Dn0CE02vxnlGO8daNiggCyI2
- Sheet Name: "MSMEs"
- Column A: Business Name
- Column B: Location
- Data starts at: Row 2

MSME Cohort 2:
- Spreadsheet ID: 1glDn1U8fwo-UJCo5akk4gD1d25F45klg
- Sheet Name: "Cohort2"
- Column A: Business Name
- Column B: Location
- Data starts at: Row 2

BGE List:
- (If moved to Google Sheets)
- Spreadsheet ID: XXXXXX
- Sheet Name: "BGEs"
- Column A: Name
- Column B: Location
- Column C: Code
- Data starts at: Row 2
```

---

## What Happens Next?

Once you provide the information above, I will:

1. ✅ Update the portal to fetch data from Google Sheets
2. ✅ Add automatic data refresh functionality
3. ✅ Add a "Sync Now" button for manual updates
4. ✅ Show loading states while fetching data
5. ✅ Handle errors gracefully (if sheets are unavailable)
6. ✅ Keep localStorage as a fallback

---

## Security Notes

⚠️ **Important Security Considerations:**

1. **API Key Exposure**: The API key will be visible in the HTML file. This is acceptable for read-only access to public sheets.

2. **Restrict Your API Key**: Make sure to restrict it to only Google Sheets API and your domain.

3. **Don't Share Your API Key Publicly**: While it's in the code, don't post it on public forums or repositories.

4. **Monitor Usage**: Google Cloud Console lets you monitor API usage to detect any abuse.

---

## Troubleshooting

### "API key not valid" Error
- Make sure you enabled Google Sheets API
- Check that your API key is correctly copied
- Verify the key isn't restricted to a different domain

### "Permission denied" Error
- Ensure spreadsheets are set to "Anyone with the link can view"
- Check that you're using the correct spreadsheet IDs

### "Sheet not found" Error
- Verify the sheet name matches exactly (case-sensitive)
- Check that the sheet tab exists in the spreadsheet

---

## Ready to Proceed?

Once you have:
- ✅ Created a Google Cloud project
- ✅ Enabled Google Sheets API
- ✅ Created and copied your API key
- ✅ Made spreadsheets publicly readable
- ✅ Identified sheet names and data structure

**Provide me with the information from Step 7**, and I'll integrate it into your portal!

---

**Estimated Time**: 10-15 minutes
**Difficulty**: Beginner-friendly (just follow the steps)
**Cost**: Free (Google Sheets API has a generous free tier)
