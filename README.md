# 🟡 Campaigner HTML Converter

A lightweight, client-side web utility built for the Lifelong Learning team at Simon Fraser University[cite: 2]. It converts Microsoft Word (`.docx`) email campaign drafts directly into sanitized, Campaigner-compliant HTML body containers (`<td>`), eliminating Word formatting cruft and automatically extracting campaign metadata[cite: 2].

---

## 🚀 How to Use

You do not need to install local packages or run command-line tools. You can use the converter directly in your browser:
1. Open the converter link in Google Chrome or any modern browser.
2. Drag and drop your campaign `.docx` draft into the upload zone (or click the zone to browse)[cite: 2].
3. The converter parses the document locally in real-time[cite: 2]:
   - **Subject Line & Preheader**: Extracted automatically from the draft's meta table and displayed in dedicated fields[cite: 2]. Click the **Copy** buttons to copy them directly for Campaigner setup[cite: 2].
   - **HTML Output**: Sanitized code renders in the main output pane[cite: 2]. Click **Copy HTML to Clipboard** and paste it directly into your email template's main body container (`<td id="emailBody">`)[cite: 2].
4. Click **Reset All** to clear the output box, file buffer, and metadata fields for the next draft[cite: 2].

---

## 🛠️ Supported Styles & Formatting Rules

The converter applies targeted formatting rules based on the simplified Word template styles:

- **Meta Table (`meta table`):** Identifies the metadata table to extract the campaign **Subject Line** and **Preheader** into the top fields, automatically removing the table from the main body output.
- **Salutation:** Automatically initializes the email body with `<p>Hi [Contact.First Name],</p>`.
- **Headings (`heading 2`):** Word elements styled with `Heading 2` are converted into clean, unstyled `<h2>` section headers.
- **Subtitle (`subtitle`):** When text styled with `Subtitle` immediately precedes a content block, it merges with the following paragraph into a single block with a bold label: `<p><strong>Subtitle:</strong><br />Paragraph body copy...</p>`.
- **Call-to-Action Buttons (`button`):** Elements styled as `Button` are converted into clean Campaigner button markup (`<p class="btn"><a href="...">Label</a></p>`). Embedded links inside the Word document are preserved directly without needing bracket notation.
- **Course & Event Cards (`event block`):** Preserves line breaks for date, time, and instructor listings. Only the first link or line (course/event title) is formatted with `<strong>` tags; subsequent links (such as instructor bios) remain unbolded.
- **Notes (`small note`):** Elements styled with `Small Note` output as `<p class="smallnote">...</p>`.
- **Lists (`list paragraph` / native bullets):** Consecutive list paragraphs or bullet items are properly collected and structured inside standard `<ul><li>...</li></ul>` containers.
- **Character Formatting (`emphasis`, `strong`):** Retains italic (`<em>`) and bold (`<strong>`) inline text styles while preserving native embedded hyperlinks.
- **Sign-offs & Signatures:** Retains custom sign-offs (e.g., *The Writer's Studio*) if present, or automatically defaults to standard SFU Continuing Studies footer contact information.
- **Cruft Stripping:** Cleans out Word-specific non-breaking spaces (`&nbsp;`, `\u00A0`), flattens leftover Word artifacts, and ensures uniform spacing for Campaigner delivery.
