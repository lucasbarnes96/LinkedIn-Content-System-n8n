# LinkedIn Content System (n8n)

This n8n workflow automates the process of extracting insights from YouTube transcripts, generating LinkedIn posts with AI, and creating matching watercolor editorial illustrations.

## Features

- **Transcript Mining**: Uses Gemini to extract raw facts, logical pivots, and concrete data from YouTube transcripts.
- **Narrative Architecture**: Orchestrates a single narrative thread to ensure the post is cohesive and punchy.
- **AI Image Generation**: Generates high-quality watercolor-style infographics (9:16) that match the post's metaphors.
- **Google Sheets Integration**: Tracks content status (Pending -> Review -> Ready -> Complete).
- **LinkedIn Publishing**: Automatically uploads the final image and post text to LinkedIn.

## Prerequisites

To use this workflow, you will need:
- An [n8n](https://n8n.io/) instance.
- A **Google Cloud Console** project with:
    - Google Sheets API enabled.
    - Google Drive API enabled.
    - Vertex AI / Gemini API enabled.
- A **LinkedIn** Developer account for post publishing.

## Setup Instructions

1.  **Import the Workflow**: Import the `workflow.json` file into your n8n instance.
2.  **Configure Google Sheet**:
    - Create a Google Sheet with a sheet named `Main`.
    - Add the following columns: `YouTube Transcript`, `Content Status`, `Created At`, `LinkedIn Text Post`, `Image Link`, `Post Status`, `row_number`.
    - Place your transcript in the `YouTube Transcript` column and set `Content Status` to `Pending`.
3.  **Configure Credentials**:
    - Set up your Google Sheets, Google Drive, Google Gemini, and LinkedIn credentials in n8n.
4.  **Update Node Parameters**:
    - In the **Get Transcript** node, replace `YOUR_GOOGLE_SHEET_ID` with your sheet's ID.
    - In the **Save Image** node, replace `YOUR_GOOGLE_DRIVE_FOLDER_ID` with the ID of the folder where you want to store generated images.
    - In the **Create a post** node, update the LinkedIn `Person` ID with your own.

## Workflow Logic

- **Schedule Trigger**: Runs daily at 8 AM.
- **Manual Trigger**: For immediate testing.
- **Transcript Miner -> Content Engine**: Pure AI-driven content generation pipeline using Gemini.
- **Merge & Image Gen**: Combines post data with the image prompt to create the visual asset.
- **Update/Post**: Syncs everything back to the Google Sheet and publishes to LinkedIn.
