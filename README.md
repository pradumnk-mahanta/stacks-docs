<p align="center">
  <img src="assets/playstore-listing/logo.png" alt="Stacks Logo" width="128" height="128" />
</p>

<h1 align="center">Stacks</h1>

<p align="center">
  <strong>Native Android management for self-hosted container infrastructure.</strong><br>
  Monitor, manage, and orchestrate Komodo, Portainer, and Docker engines directly from your phone.
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#supported-services">Supported Services</a> •
  <a href="#features-by-service">Features</a> •
  <a href="#service-setup-guides">Setup Guides</a> •
  <a href="#troubleshooting--raising-issues">Troubleshooting & Issues</a> •
  <a href="#privacy--terms">Privacy & Terms</a>
</p>

---

## Overview

**Stacks** lets you manage Komodo, Portainer, Docker engines, and SSH hosts from your Android phone. Browse servers and stacks, manage containers, read logs, open terminals, and edit supported Compose and environment files.

Stacks requires **Android 12 or later**. Your phone connects directly to the endpoints you configure, using your local network, VPN, or reverse proxy. There is no Stacks cloud account or relay.

### Key Highlights

* **Multiple services:** Keep Komodo, Portainer, Docker API, and SSH connections together on one dashboard. Add multiple Docker engines, each with its own optional SSH host access.
* **Background refresh:** Keep the last known Online or Offline status visible while a connection refreshes. A connection without a previous result shows Checking during its first check.
* **Container tools:** Start, stop, restart, read logs, and open terminals where supported.
* **Stack workspaces:** Switch between Details, Compose, and Environment to inspect and manage your stacks.
* **Private settings:** Credentials are encrypted on your device. Stacks does not collect analytics or telemetry.
* **Appearance:** Choose Light or Dark mode in Settings and toggle service logos.

---

## Supported Services

| Service | Connection Scope | Available Tools |
| :--- | :--- | :--- |
| **Komodo** | Multiple servers per connection | Server monitoring, tags, stack deployment and editing, container tools, operation history, procedures, actions, Git provider accounts, registries, and images. |
| **Portainer** | Multiple environments per connection | Environment overview, stack deployment and editing, container tools, recent events, registries, Git credentials, and images. |
| **Docker API** | Multiple saved connections, one engine per connection | Engine overview, Compose project grouping, container tools, recent events, and images. Add one SSH host-access connection per engine for host terminals and Compose/environment file editing. |
| **SSH Connection** | One host per connection | Docker overview, container tools, recent events, images, a host terminal, and deployment and editing of existing Compose files. |

Available operations depend on your account permissions, server configuration, and access to the relevant files.

---

## Features by Service

### Komodo

* Monitor server CPU, memory, storage, and tags. Select a server to filter its stacks.
* Browse stacks, edit tags, and use Start, Restart, and Stop controls.
* Create stacks using templates, UI-defined Compose, Git repositories, or host files.
* Open a stack's **Details**, **Compose**, and **Environment** tabs. Edit Compose in Table or Raw mode, format YAML, and edit environment variables with values hidden by default.
* Check for stack updates and run supported update or deployment actions.
* Start, stop, and restart containers. Open container logs or choose a `sh`, `bash`, or attach terminal session.
* Review operation history and detailed execution output.
* Run configured procedures and actions, manage Git provider and registry accounts, and browse or prune host images.

### Portainer

* Browse environments and their available CPU, memory, and container information. Select an environment to filter stacks.
* Create stacks from UI-defined Compose or a Git repository, including repository authentication when needed.
* Use the **Details**, **Compose**, and **Environment** stack workspace to inspect and edit supported stacks.
* Use **Pull Image & Redeploy** to pull images and recreate services.
* Start, stop, and restart containers; read logs; and open container terminals.
* Review recent Docker events, manage registries and Git credentials, and browse or prune environment images.

### Docker API

* Add multiple engines as separate services, each with its own alias, endpoint, credentials, and optional SSH host access.
* View engine capacity, recent events, Compose projects, and standalone containers.
* Start, stop, and restart containers, read logs, and open `sh` or `bash` terminals in running containers.
* Browse engine images and prune unused images after confirmation.
* Open **Details**, **Compose**, and **Environment** for a Compose project. The Docker API alone cannot directly edit Compose or environment files; use **Add Host Access** to enable file access over SSH.
* With host access, fetch and edit existing host files, save changes, and use **Redeploy** or **Pull Image & Redeploy** to apply them.
* Tap the terminal icon in the service title bar to open the associated host's SSH shell.

**Pull Images & Restart** downloads images and restarts running containers with their existing configuration and creation-time images. To apply updated images or saved Compose changes, use a Compose redeployment.

### SSH Connection

* Manage Docker and Compose on a host using your SSH account.
* Tap the terminal icon in the service title bar to open a shell on the host. Container terminal buttons open shells inside running containers.
* Use **Add Stack** to deploy an existing Compose file on the host.
* Edit existing Compose and environment files in the stack workspace, then redeploy to apply changes.
* Set a **Root Directory** for Compose projects; the default is `/srv/stacks`. Change it through **Root Directory** in the service's three-dot menu or from Stack Details.
* Start, stop, and restart containers, read logs, browse images, and review recent events.

The SSH account needs permission to run Docker and Docker Compose v2. Editing files also requires SFTP access and permission to read and write those files.

### Across the App

* Long-press and drag dashboard service cards to change their order. Release to save the order for future app launches.
* Pull down to refresh service information. Existing status and content stay visible during background refreshes.
* Container logs refresh automatically every five seconds, with manual refresh and 100, 500, or 1,000-line views.
* Add/Edit Service forms keep the Connect or Save button below the scrollable fields and above the keyboard. A centered spinner appears while the request is in progress.
* Open **Settings > Feedback & Support** for documentation, bug reports, and feature requests. **About** shows your installed app version, and **Credits** links to the Docker, Komodo, and Portainer projects.
* Export service settings and preferences to a JSON backup and import them from Settings. Backups exclude credentials, private keys, and saved host/certificate trust. On a new device, reconnect services and verify their hosts or certificates again.

---

## Service Setup Guides

### Connecting Komodo

1. Tap **+** on the dashboard, then choose **Komodo**.
2. Enter a **Server Alias** and **Komodo Endpoint**, such as `http://192.168.1.100:9120` or `https://komodo.example.com`.
3. Choose an authentication method:
   * **Username & Password:** Enter your Komodo account details. If two-factor authentication is enabled, enter the six-digit code when prompted. Stacks creates a dedicated connection key after sign-in so it does not need to store your account password.
   * **API Key & Secret:** Create a dedicated key in your Komodo profile's API key settings, then enter its key and secret.
4. Tap **Connect** and allow local network access if Android prompts you.

### Connecting Portainer

1. In Portainer, open **My account**, find **Access tokens**, and create a token for Stacks. Copy the token when it is shown.
2. In Stacks, tap **+** and choose **Portainer**.
3. Enter a **Server Alias**, **Portainer Endpoint** (for example, `https://192.168.1.100:9443`), and the **Access token**.
4. For a self-signed or private-CA HTTPS endpoint, enter the verified server certificate fingerprint in **Certificate SHA-256 fingerprint** if needed.
5. Tap **Connect** and allow local network access if prompted.

### Connecting Docker API

1. Make your Docker API reachable from your phone through a trusted network, VPN, or secured reverse proxy. Use TLS and authentication for access over untrusted networks.
2. In Stacks, tap **+** and choose **Docker API**.
3. Enter a **Server Alias** and **Docker Endpoint**, such as `https://docker.example.com:2376`.
4. Choose an authentication method:
   * **Client certificate:** Install your client certificate and private key in Android's credential settings, then tap **Choose certificate** in Stacks.
   * **Proxy bearer token:** Enter the token required by your HTTPS reverse proxy.
   * **None:** Use only when your endpoint is protected by a trusted private network or another appropriate access control.
5. If needed, enter the verified HTTPS server certificate fingerprint in **Certificate SHA-256 fingerprint**.
6. Tap **Connect**. Repeat these steps to add another engine.

#### Adding SSH Host Access to a Docker Engine

Host access belongs to the selected Docker engine and does not create a separate dashboard service.

1. Open the Docker service and choose **Add Host Access** from its three-dot menu. You can also use the button in its Compose or Environment tab.
2. Enter the **SSH Endpoint**, **Username**, and **Root Directory**. For projects under `/srv/stacks`, leave the default root or enter your host's actual directory.
3. Choose **Password**, **Private key**, or **No authentication**. For a private key, paste it or choose a key file and enter its passphrase if required. No authentication only works when the SSH server accepts an unauthenticated session or an empty password.
4. Enter a verified **Host key SHA-256 fingerprint**, or compare the fingerprint presented on first connection with your server's known host key before trusting it.
5. Tap **Save Host Access**. The SSH account must target the same Docker engine as this API connection and have access to the project files.
6. Open a stack's **Compose** or **Environment** tab to load its files. Save edits, then redeploy when you want to apply them.
7. Tap the terminal icon in the service title bar to open a host shell. Use **Edit Host Access** in the three-dot menu to change the connection later.

Each Docker service has one associated SSH connection. Changing its Docker API endpoint clears the previous host-access association; configure host access for the new endpoint again.

### Connecting SSH

1. Tap **+** on the dashboard and choose **SSH Connection**.
2. Enter a **Server Alias**, **SSH Endpoint** (such as `ssh://192.168.1.100:22`), **Username**, and **Root Directory**.
3. Choose **Password**, **Private key**, or **No authentication**, and supply the required credentials. No authentication requires a server that accepts an unauthenticated session or an empty password.
4. Enter a verified **Host key SHA-256 fingerprint**, or compare and trust the presented fingerprint on first connection.
5. Tap **Connect**. The account must be able to run Docker on that host.
6. Open the service to manage containers and stacks, or tap its title-bar terminal icon to open a host shell.

---

## Troubleshooting & Raising Issues

### Common Solutions

* **Connection timed out or endpoint unreachable:** Check your phone's network or VPN connection, the endpoint address and port, and the host firewall. Allow local network access if Android prompts you; if previously denied, enable it in Android app settings.
* **Authentication failed:** Use the instance card's pencil button to check connection details. Confirm that API tokens are still valid and that your SSH account and key or password are correct. For Docker host access, use **Edit Host Access** in the service menu.
* **Certificate or SSH host key changed:** Verify the new fingerprint against the server before updating saved connection details.
* **Compose or Environment says host connectivity is required:** Open the Docker service's three-dot menu and choose **Add Host Access**. Docker API access alone does not provide access to host project files.
* **Compose or Environment file not found:** Check Root Directory, the actual file locations, and the SSH account's file permissions. Files managed by Portainer or Komodo may be stored in that service's data volume rather than at a directly accessible host path. Use the managing service's editor or make the project files accessible on the SSH host, then choose **Reload**.
* **Host access targets a different engine:** Check that the SSH account's Docker connection targets the same engine as the selected Docker API service.
* **Host terminal button is unavailable:** Complete SSH authentication and host-key verification for the service or its associated host access.
* **Docker container terminal will not connect through a reverse proxy:** Ensure the proxy forwards the Docker terminal connection upgrade.
* **A file changed before saving:** Reload it and review your changes against the latest host copy before saving again.
* **Images were pulled but containers still use the old version:** Restarting does not recreate containers. Use **Pull Image & Redeploy** through SSH host access, or redeploy through Komodo or Portainer.

### How to Raise an Issue

Report bugs or request features through the **[GitHub issue tracker](https://github.com/pradumnk-mahanta/stacks-docs/issues)**.

Include:

1. Your Android version and device model.
2. The service name and version.
3. Whether you connect over local Wi-Fi, a VPN, or a reverse proxy.
4. What you expected, what happened, and the steps to reproduce it.
5. The on-screen error message, with private details removed.

Never include passwords, API keys, tokens, private keys, or other secrets in issue reports or screenshots.

---

## Privacy & Terms

### Privacy Summary

* Stacks does not collect analytics or telemetry and has no advertising.
* Settings, credentials, and cached service information are stored on your Android device. Credentials are encrypted using Android Keystore protection.
* Connections go to the server endpoints you choose. Authentication details are sent only as required to connect to those services; Stacks does not operate a cloud relay.
* Portable backups exclude credentials, private keys, and saved host/certificate trust.

Read the full **[Privacy Policy](PRIVACY_POLICY.md)**.

### Terms Summary

* Stacks is a client for infrastructure you provide and authorize it to access.
* You are responsible for securing endpoints, maintaining backups, and reviewing server actions such as redeployment, removal, and image pruning.
* Stacks is provided as is, without warranties.

Read the full **[Terms and Conditions](TERMS_AND_CONDITION.md)**.
