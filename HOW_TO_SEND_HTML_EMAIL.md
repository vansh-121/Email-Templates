# How to Send HTML Email Templates in Outlook

## ⚠️ Important: DO NOT Copy-Paste HTML Directly

When you copy HTML code and paste it into Outlook, it strips out the styling and structure, making it look broken.

## ✅ Recommended Methods to Send HTML Emails:

### **Method 1: Using Outlook with HTML File (Best for Testing)**

1. Save your HTML file (e.g., `north-star-event-outlook-compatible.html`)
2. Open the HTML file in your **web browser** (Chrome, Edge, Firefox)
3. Press `Ctrl + A` to select all the rendered content
4. Press `Ctrl + C` to copy
5. Open Outlook and create a new email
6. Press `Ctrl + V` to paste
7. The email should maintain its formatting

### **Method 2: Insert as HTML in Outlook (Windows)**

1. Create a new email in Outlook
2. Go to the **Insert** tab
3. Click **Attach File** → **Browse This PC**
4. Select your HTML file
5. Click the dropdown arrow next to **Insert**
6. Choose **Insert as Text**
7. The HTML will be inserted with proper formatting

### **Method 3: Using PowerShell Script (Most Reliable)**

Create a `.ps1` file with this script:

```powershell
$outlook = New-Object -ComObject Outlook.Application
$mail = $outlook.CreateItem(0)
$mail.Subject = "Meet Valura.ai at North Star 2025"
$mail.HTMLBody = Get-Content "E:\2centscapital\Email Templates\north-star-event-outlook-compatible.html" -Raw
$mail.Display()
```

Save it as `send-email.ps1` and run it from PowerShell.

### **Method 4: Using Email Marketing Services (Best for Production)**

For sending to multiple recipients, use:
- **Mailchimp** - Import HTML template
- **SendGrid** - Upload HTML
- **Amazon SES** - Send HTML emails via API
- **Brevo (Sendinblue)** - HTML template import

### **Method 5: Using Gmail (Alternative)**

1. Open Gmail
2. Compose new email
3. Press `Ctrl + Shift + C` (or click the three dots → "Default styling")
4. Copy the HTML code
5. Use a browser extension like "Insert HTML" to paste the HTML
6. Or paste into Gmail's HTML editor

---

## 🚫 Why Copy-Paste Doesn't Work

Outlook's editor is based on Microsoft Word's rendering engine, which:
- Strips out `<style>` tags
- Removes CSS classes
- Ignores external stylesheets
- Converts tables and layouts to simplified versions
- Removes media queries and responsive code

## ✅ Best Practice

**Always test HTML emails by:**
1. Opening the HTML file in a browser first
2. Copying from the **rendered version** (not the code)
3. Or using proper email sending tools/services

---

## 📧 For Bulk Sending

If you need to send this to multiple people:
- Use an email marketing platform (Mailchimp, SendGrid, etc.)
- They handle HTML rendering properly
- Provide analytics and tracking
- Ensure better deliverability
