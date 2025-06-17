# ServiceNowPDFExtraction
Extract PDFs from the ServiceNow, which can be used to extract any other documents too.

**Document Extractor**
This Python script is designed to efficiently download and organize "Viya 4" PDF documents directly from your ServiceNow instance. It's built for flexibility, allowing you to focus on a specific year's documents with ease.

**How it Works:**
**1) Year-Specific Focus:** At the very top of the script, you'll find a TARGET_YEAR variable. Simply change this to the year you want to process (e.g., "2024", "2025"), and the script will automatically adjust its search and saving behavior.
**2) ServiceNow Integration:** The script uses OAuth 2.0 for secure authentication with your ServiceNow instance. It then queries the ServiceNow API for "request items" (RITMs) belonging to a specific assignment group and, critically, filters these requests by the TARGET_YEAR right at the source. This means it only retrieves data for the year you're interested in, saving time and bandwidth.
**3) PDF Attachment Retrieval:** For each relevant request item, the script fetches its associated PDF attachments.
**4) Intelligent Document Filtering:** 

  Before saving, each PDF is carefully inspected:
  It checks if "Viya 4" is mentioned anywhere in the document.
  It skips documents related to "Viya 3" or "Viya 3.5."
  It attempts to find the RITM number within the document's content to ensure accurate naming.
  It dynamically identifies the year within the PDF's content or filename.
  Only PDFs confirmed to be "Viya 4" and matching the TARGET_YEAR are saved.
    
**Organized Saving: **Valid PDFs are saved into a dedicated folder structure, like Viya4_2025, ensuring your documents are neatly organized by year. It also prevents saving duplicate files.
**Comprehensive Summary:** After processing all relevant items, the script provides a detailed summary of how many "Viya 4" PDFs were saved for your chosen year, along with counts for various skipped categories.

**To Use This Script:**
**1) Set TARGET_YEAR:** Update the TARGET_YEAR variable to the desired year.
**2) Configure API Details:** Fill in your ServiceNow client_id, client_secret, token_url, instance URL, assignment_group_sys_id, and scope where indicated in the "USER CONFIGURATION" section.
**3) Verify Field Names:** Crucially, confirm that the opened_at field used in the query_params section is the correct ServiceNow backend name for the date field your custom API exposes for filtering. If you encounter errors, this is the first place to check (refer to ServiceNow's REST API Explorer or your instance's table definitions).
**4) Run the Script:** Execute the Python script, and it will begin fetching and saving your Viya 4 sizing documents.

This script streamlines the process of collecting critical "Viya 4" sizing information, keeping your document repository organized and up-to-date for your specified year.
