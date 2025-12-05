# Website Activation Manual

This manual guides you through the steps to replace placeholders and activate the full functionality of your "English with Ali" website.

## 1. Activate Contact Form (EmailJS)

To make the contact form actually send emails to you, we will use a service called **EmailJS**.

### Step A: Set up EmailJS Account
1.  Go to [https://www.emailjs.com/](https://www.emailjs.com/) and sign up for a free account.
2.  **Add a Service**:
    *   Click "Add New Service" on the dashboard.
    *   Select "Gmail" (or your preferred email provider).
    *   Click "Connect Account" and follow the prompts.
    *   Click "Create Service".
    *   **Copy the `Service ID`** (e.g., `service_xyz123`). Save this for later.
3.  **Create an Email Template**:
    *   Go to "Email Templates" on the left sidebar.
    *   Click "Create New Template".
    *   Design your email. You can use variables from your form like `{{name}}`, `{{email}}`, and `{{message}}`.
    *   Example Subject: `New Message from {{name}}`
    *   Example Content:
        ```text
        Name: {{name}}
        Email: {{email}}
        Message:
        {{message}}
        ```
    *   Click "Save".
    *   **Copy the `Template ID`** (e.g., `template_abc456`). Save this for later.
4.  **Get Your Public Key**:
    *   Go to "Account" (click your avatar in the top right).
    *   **Copy the `Public Key`** (e.g., `user_123456789`). Save this for later.

### Step B: Update the Code
1.  Open the file `index.html`.
2.  Find the `<head>` section (near the top).
3.  Add the EmailJS SDK script just before the closing `</head>` tag:
    ```html
    <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
    <script type="text/javascript">
       (function(){
          emailjs.init("YOUR_PUBLIC_KEY");
       })();
    </script>
    ```
    *Replace `"YOUR_PUBLIC_KEY"` with the key you copied in Step A.4.*

4.  Open the file `script.js`.
5.  Find the `Contact Form Handling` section (at the bottom).
6.  Replace the simulation code with the EmailJS sending code (see the updated `script.js` file I have prepared for you). You will need to insert your `Service ID` and `Template ID`.

---

## 2. Activate Calendly Booking

To allow students to actually book calls with you:

1.  Log in to your [Calendly](https://calendly.com/) account.
2.  Go to the event type you want to share (e.g., "Free Introductory Call").
3.  Click "Share".
4.  Click "Add to Website".
5.  Choose "Inline Embed".
6.  **Copy the URL** found inside the code snippet (it looks like `https://calendly.com/your-username/event-name`).
7.  Open `index.html`.
8.  Find the `Calendly Section` (search for `id="calendly"`).
9.  Locate this line:
    ```html
    <div class="calendly-inline-widget" data-url="https://calendly.com/" style="min-width:320px;height:630px;"></div>
    ```
10. Replace `https://calendly.com/` with your actual Calendly URL.

---

## 3. Replace Video & Images

### Video
1.  Record your "Hello" video.
2.  Name the video file `hello-video.mp4`.
3.  Take a screenshot or photo to use as the cover image and name it `video-poster.jpg`.
4.  Place both files in the `assets` folder of your project, replacing the placeholders.

### Images
*   If you want to add a real photo of yourself instead of the video or elsewhere, simply add the image file to the `assets` folder and update the `src` attribute in the `<img>` tag in `index.html`.

---

## 4. Update Privacy Policy

1.  Open `index.html`.
2.  Search for `id="privacy-modal"`.
3.  Read through the text inside `<div class="privacy-body">`.
4.  Replace the generic text and the placeholder `[User Note: ...]` with your actual legal details (address, specific data collection practices, etc.).

---

## 5. Deployment

Once you have made these changes:
1.  Upload your project files (`index.html`, `style.css`, `script.js`, `assets/`) to a hosting provider like **GitHub Pages** or **Netlify**.
2.  Your site will be live!
