# 🟡 Campaigner HTML Converter

A lightweight, client-side web utility built for the Lifelong Learning team at Simon Fraser University. It converts Microsoft Word (`.docx`) email campaign drafts directly into sanitized, Campaigner-compliant HTML body containers (`<td>`), eliminating Word formatting cruft and automatically extracting campaign metadata.

---

## 🚀 How to Use

You do not need to install local packages or run command-line tools. You can use the converter directly in your browser:

1. Open the hosted converter link in Google Chrome.
2. Drag and drop your campaign `.docx` draft into the upload zone (or click the zone to browse).
3. The converter parses the document locally in real-time:
   * **Subject Line & Preheader:** Extracted automatically and displayed in dedicated fields above the editor. Click the individual **Copy** buttons to paste them directly into Campaigner setup.
   * **Target `<td>` HTML Output:** Sanitized code renders in the main output pane. Click **Copy HTML to Clipboard** and paste it directly into your email template's main body container (`<td id="emailBody">`).
4. Click **Reset All** to clear the output box, file buffer, and metadata fields for the next draft.

---

## 🛠️ Parsing & Formatting Rules Applied

* **Salutation:** Automatically initializes the body with `<p>Hi [Contact.First Name],</p>`.
* **Headings (`<h2>`):** Converts Word heading tags and brand red text runs (`#CC0633`, `#C00000`) into clean, unstyled `<h2>` section headers.
* **Call-to-Action Buttons:** Detects `[button]` labels and converts anchor links into Campaigner CTA button markup (`<p class="btn"><a class="btn" href="...">Label</a></p>`).
* **Course & Event Cards:** Formats event dates, times, and instructor listings with standardized bold titles and line breaks.
* **Sign-offs & Signatures:** Retains unit-specific sign-offs (e.g., The Writer's Studio) or defaults to standardized Continuing Studies footer contact info.
* **Footnotes & References:** Extracts citations to the footer, strips internal Word bookmark anchors (`_Int_`), and auto-links plain-text URLs.
* **Cruft Stripping:** Removes non-breaking spaces (`&nbsp;`), flattens nested `<ul>`/`<li>` structures into clean paragraphs, and ignores internal campaign metadata tags.
