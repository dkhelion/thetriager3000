# Privacy Policy

_Last updated: 2025-06-29_

This privacy policy explains how your data is handled by the Triager Chrome Extension (“the Extension”).

## 1. Overview

The Extension is designed to assist technicians in streamlining ticket creation within the AutoTask platform. It does so by interacting with the AutoTask web interface, extracting visible text elements (such as contact info), populating ticket fields, and performing limited UI automation.

## 2. Information Collection

**The Extension does not collect or transmit any personally identifiable information (PII) or private user data to external servers.** However, it **does read data** visible in the current browser tab (e.g., contact name, phone number, department) **strictly for the purpose of automating form completion**.

Specifically:

- No background tracking, analytics, or telemetry is used.
- No browsing history is accessed.
- No cookies, credentials, or external website data is read or stored.

### 🔍 What the Extension Reads:
- Contact name, phone, department, location (from the current AutoTask page)
- Page text (for field population purposes)
- Keyboard events (for detecting custom hotkey activation)

This data is processed **in memory** and is never sent off-device unless an error occurs (see section 5).

## 3. Storage

The Extension uses `chrome.storage.sync` to store user-defined settings like:

- Custom hotkeys
- Queue names
- Resource names
- A boolean to enable/disable "Thanks Dan" popup

All data is scoped to the Chrome user profile and synced securely by Chrome itself.

## 4. Permissions

The Extension requests the following Chrome permissions:

- `storage`: to save user preferences
- `scripting` or host access to `autotask.net`: to inject scripts into the AutoTask interface

These permissions are strictly required for the Extension to function and are never used for unauthorized access.

## 5. Error Reporting

If an exception occurs, the Extension **captures the error context and sends it to a private Discord webhook** you control. This includes:

- Error message, line number, stack trace
- The current ticket title (if available)
- Page URL and user agent string
- The user’s selected “primary resource” name, if stored

**This mechanism is only triggered on runtime exceptions or unhandled promise rejections**, and is used solely for debugging and support.

If you wish to disable this reporting, you can either:
- Modify the source code to remove the webhook,
- Or comment out the `sendToWebhook` logic in the error handlers.

## 6. “Thanks Dan” Popup

If enabled in settings, a small on-screen "thanks dan!" popup is displayed after successful script runs. It does not track or log anything.

## 7. Third-Party Access

The Extension does **not** include:
- Third-party analytics
- Ad tracking
- Cross-site data scraping

No data is shared with or accessed by third parties.

## 8. Updates

This policy may be updated as the Extension evolves. The latest version will always be included in the GitHub repository or Chrome Web Store listing.

## 9. Contact

If you have any concerns or questions about this policy or the Extension’s behavior, please open an issue on the GitHub repository or contact the developer directly via the Chrome Web Store listing.

---

**Summary**: This Extension automates the AutoTask UI locally, respects user privacy, and only stores minimal preferences. It does not collect or share personal data unless an error occurs, in which case only technical metadata is sent to a private webhook.
