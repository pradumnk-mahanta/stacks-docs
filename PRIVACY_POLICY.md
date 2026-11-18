# Privacy Policy for Stacks

**Effective Date:** November 14, 2026  
**Last Updated:** November 14, 2026  

Stacks ("we," "our," or "us"), developed by **Pradumn Mahanta** (Application ID: `win.itryto.stacks`), is committed to protecting your privacy. This Privacy Policy describes how Stacks handles user information when you use our Android application.

---

### 1. Overview & Core Philosophy

Stacks is a native Android management utility for self-hosted container infrastructure (including Komodo, Portainer, Docker API, and SSH connections). Our core privacy philosophy is simple: **we do not collect, harvest, store, transmit, or sell your personal information or telemetry.** Your data, endpoints, server configurations, and credentials remain entirely on your device and your private infrastructure.

---

### 2. Information We Do NOT Collect

* **No Personal Identification Information (PII):** We do not require you to create an account, register, or provide personal details such as your name, email address, physical address, or phone number.
* **No Server-Side Tracking or Analytics:** Stacks does not transmit telemetry, usage analytics, crash metrics, host addresses, or container names to any developer-operated servers or third-party analytics platforms.
* **No Advertising Identifiers or Trackers:** The application contains zero advertising SDKs, ad brokers, or third-party behavioral trackers.

---

### 3. Data Handled Locally on Your Device

All configurations and settings are stored strictly **locally on your device** in app-private storage:

* **Configured Service Endpoints:** Server URLs and aliases you configure are stored locally to allow connecting to your instances.
* **Authentication Credentials:** Usernames, session tokens, API credentials, and SSH passwords, private keys, and passphrases are stored in encrypted app-private files using AES-GCM encryption backed by the hardware-isolated Android Keystore. Passwords are never saved in plaintext.
* **Cached Inventory:** Basic server and stack structures are cached locally on-device to enable fast startup and background refreshing without blank states.
* **User Preferences:** Appearance preferences (Light or Dark mode), service logo display toggles, and layout settings are stored locally.

You may completely erase all locally stored data at any time by clearing the app data in Android **Settings > Apps > Stacks > Clear data**, or by uninstalling the application.

---

### 4. Direct Network Connections

* **Direct Infrastructure Connections:** When you connect to an instance, your device establishes a direct network connection (HTTP, HTTPS, or SSH) to the host endpoint specified by you (e.g. via local Wi-Fi, WireGuard, Tailscale, or reverse proxy). Stacks acts purely as a direct client; no requests are proxied, inspected, or routed through any intermediary servers.
* **Self-Hosted Security:** You are responsible for ensuring that your server endpoints use appropriate transport security and strong access credentials.

---

### 5. Android Permissions Used

Stacks requests only the minimal permissions necessary for core container management:

* `INTERNET`: Required to connect directly to user-configured server endpoints and WebSocket terminal sessions.
* `ACCESS_NETWORK_STATE`: Required to detect network availability and provide connection status indicators.

---

### 6. Portable Backup & Exports

Stacks provides an explicit settings export/import feature:
* Settings exports are executed via Android's secure Storage Access Framework document picker.
* Exported JSON files deliberately exclude all private keys, API secrets, passwords, and JWT session tokens.

---

### 7. Children's Privacy

Stacks does not target or knowingly collect information from children under the age of 13. The application is a specialized technical utility with zero data collection.

---

### 8. Changes to This Privacy Policy

If we update this Privacy Policy, the revised policy will be published in the public documentation repository:  
https://github.com/pradumnk-mahanta/stacks-docs

Continued use of the application signifies acceptance of any updates.

---

### 9. Contact & Inquiries

For questions or concerns regarding this Privacy Policy, you can open an issue at:  
https://github.com/pradumnk-mahanta/stacks-docs/issues
