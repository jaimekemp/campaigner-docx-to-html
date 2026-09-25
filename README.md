# 🟡 Campaigner HTML Converter

A lightweight, client-side web utility built for the Lifelong Learning team at Simon Fraser University. It converts Microsoft Word (`.docx`) email campaign drafts directly into sanitized, Campaigner-compliant HTML body containers (`<td>`), eliminating Word formatting cruft and automatically extracting campaign metadata.

---

## 🚀 How to Use

You do not need to install local packages or run command-line tools. You can use the converter directly in your browser:
1. Open the converter link in Google Chrome or any modern browser.
2. Drag and drop your campaign `.docx` draft into the upload zone (or click the zone to browse).
3. The converter parses the document locally in real-time:
   - **Subject Line & Preheader**: Extracted automatically from the draft's meta table and displayed in dedicated fields. Click the **Copy** buttons to copy them directly for Campaigner setup.
   - **HTML Output**: Sanitized code renders in the main output pane. Click **Copy HTML to Clipboard** and paste it directly into your email template's main body container (`<td id="emailBody">`).
4. Click **Reset All** to clear the output box, file buffer, and metadata fields for the next draft.

---

## 🛠️ Supported Styles & Formatting Rules

The converter applies targeted formatting rules based on the simplified Word template styles:

* **Meta Table (`meta table`):** Identifies the metadata table to extract the campaign **Subject Line** and **Preheader** into the top fields, automatically removing the table from the main body output.
* **Salutation:** Automatically initializes the email body with `<p>Hi [Contact.First Name],</p>`.
* **Headings (`heading 2`):** Word elements styled with `Heading 2` are converted into clean, unstyled `<h2>` section headers.
* **Subtitle (`subtitle`):** When text styled with `Subtitle` immediately precedes a content block, it merges with the following paragraph as:
  ```html
  <p>
    <strong>Subtitle:</strong><br />
    Paragraph body copy...
  </p>
