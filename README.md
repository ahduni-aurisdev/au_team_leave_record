# AU Team Leave Record Widget

This is a custom Zoho People webtab designed for **Ahmedabad University** to manage team leave approvals in Zoho People. It provides a streamlined interface for managers to view, approve, and reject pending leave requests from their subordinates.

## Features

- **Pending Leave Dashboard**: Displays a list of pending leave requests for the logged-in user's subordinates.
- **Date Filtering**: Automatically fetches records from the last 30 days up to the next 60 days.
- **Detailed Information**: Shows employee name, leave type, application date, duration, and reason.
- **Action Buttons**: 
  - **Approve**: One-click approval for individual requests.
  - **Reject**: Rejection requires a mandatory reason input.
- **Bulk Actions**: Select multiple records to approve or reject them in batch.
- **Error Handling**: Robust handling of API responses and JSON parsing (including large integer support).

## Project Structure

```
c:\zoho\au_team_leave_record/
├── app/
│   ├── translations/   # Localization files
│   └── widget.html     # Main application file (UI & Logic)
├── server/
│   └── index.js        # Local development server
├── plugin-manifest.json # Widget configuration and permissions
└── package.json        # Project dependencies and scripts
```

## Technical Details

- **Frontend**: HTML, CSS, JavaScript (Vanilla).
- **External Libraries**: 
  - jQuery (for DOM manipulation)
  - Toastr (for notifications)
  - Zoho Widget SDK (`zpwidgetsdk.min.js`)
- **API Integration**: Uses `ZOHO.People.API.invokeUrl` to interact with Zoho People v3 APIs.
  - **Fetch**: GET `https://people.zoho.com/people/api/v3/leave-tracker/leaves`
  - **Approve**: PUT `https://people.zoho.com/people/api/v3/leave-tracker/leaves/{id}`
  - **Reject**: POST `https://people.zoho.com/people/api/v3/leave-tracker/leaves/{id}`

## Setup & Running

1. **Install Dependencies**:
   ```bash
   npm install
   ```

2. **Start Local Server**:
   ```bash
   npm start
   ```
   This runs `node server/index.js` to serve the widget locally for testing and development.

## Recent Updates

- **JSON Precision Fix**: Implemented a fix for large integer IDs losing precision during JSON parsing by treating them as strings.
- **API Method Update**: Changed rejection action from `PATCH` to `POST` to align with API requirements.
- **Dynamic User Context**: The widget now dynamically fetches the logged-in user's ID to retrieve relevant subordinate leaves.

## How to upload .zip as a WebTab in Zoho People
1. Run zet validate in command line terminal to validate the widget.
2. Run zet pack in command line terminal, this will create a .zip file in the dist/ folder.
3. Upload the .zip file in Zoho People WebTab to upload the widget.
