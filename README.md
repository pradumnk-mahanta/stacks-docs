<p align="center">
  <img src="assets/playstore-listing/logo.png" alt="Stacks logo" width="128" height="128" />
</p>

<h1 align="center">Stacks</h1>

<p align="center">Manage your Docker stacks from an Android phone.</p>

<p align="center">
  <a href="#supported-services">Supported services</a> ·
  <a href="#service-setup-guides">Setup</a> ·
  <a href="#troubleshooting--raising-issues">Troubleshooting</a> ·
  <a href="#privacy--terms">Privacy &amp; Terms</a>
</p>

## Overview

Open Stacks to see which services are online, check why a container stopped, or pull up a shell. You can keep your Komodo, Portainer, Docker API, and SSH connections on one dashboard.

You’ll need **Android 12 or later**. Your phone connects straight to the addresses you enter, over your local network, a VPN, or a reverse proxy. There’s no Stacks account to set up.

## Supported Services

| Service | What you can connect |
| --- | --- |
| **Komodo** | One connection covers the servers managed by that Komodo instance. |
| **Portainer** | One connection covers the environments managed by that Portainer instance. |
| **Docker API** | Add each Docker engine separately. You can pair each engine with one SSH connection for host files and a host shell. |
| **SSH Connection** | Add each host separately to use its shell and manage Docker and Compose. |

What you can do on a particular server depends on your account permissions and the files it can access.

## Features by Service

### Komodo

Pick a server to see its CPU, memory, storage, tags, and stacks. You can create a stack from a template, write Compose in the app, use a Git repository, or point to files already on the host.

- Open a stack’s **Compose** or **Environment** tab to edit it. Compose has Table and Raw modes and a YAML formatter. Environment values are hidden by default.
- For a Git-backed stack, tap refresh in **Compose** to compare the upstream files with the last deployed copies. You can check for changes while the stack keeps running.
- Start, restart, or stop a stack, check for image updates, or deploy it. Choose **Destroy** to take a stack down and keep its Komodo record, or **Delete Stack** to remove the record.
- Start, stop, or restart a container, read its logs, or open `sh`, `bash`, or an attach session.
- Review operation history, run configured procedures and actions, manage Git provider and registry accounts, and browse or prune host images.

### Portainer

Pick an environment to see its stacks and available CPU, memory, and container information. Create a stack from Compose you write in the app or from a Git repository.

- Use **Details**, **Compose**, and **Environment** to inspect a stack and edit the fields Portainer supports.
- On a Git-backed stack, tap refresh in **Compose** to compare the main file with the deployed copy. The read-only preview lets you see what’s upstream without redeploying. Older private repositories may ask for Git credentials for that check.
- Use **Pull Image & Redeploy** to pull images and recreate services, or **Delete Stack** to remove a stack.
- Start, stop, or restart containers, open their logs or terminals, view Docker events, manage registries and Git credentials, and browse or prune images.

### Docker API

Open an engine to see its capacity, recent events, Compose projects, standalone containers, and images. You can start, stop, and restart containers, read their logs, open `sh` or `bash` in running containers, and prune unused images after confirming.

If you want to edit a project’s Compose or environment files, use **Add Host Access** to connect over SSH. Once it’s set up, open the project’s **Compose** or **Environment** tab to edit existing files. Save your changes, then use **Redeploy** or **Pull Image & Redeploy** when you’re ready. The terminal icon in the Docker service’s title bar opens a shell on the host.

**Pull Images & Restart** downloads images and restarts the running containers with their existing configuration and images. Use a Compose redeploy to apply a new image or a saved Compose change.

### SSH Connection

Use your SSH account to manage Docker on a host. You can see recent events and images, and start, stop, restart, or read logs for containers. The terminal icon in the service’s title bar opens a host shell. A container’s terminal icon opens a shell inside that container.

Use **Add Stack** to deploy an existing Compose file. To change a stack, open its **Compose** or **Environment** tab, edit the files, and redeploy when ready. Stacks looks for projects under the **Root Directory**, which defaults to `/srv/stacks`. You can change it in the service’s three-dot menu or under **Stack Details**.

Your SSH account needs permission to run Docker and Docker Compose v2. File editing also needs SFTP access and permission to read and write the project files.

For both Docker API and SSH, **Delete Stack** removes the project’s containers and networks, even if its Compose file is missing. Stacks keeps volumes and images. If the files are accessible over SSH, you can also choose to delete the Compose and environment files listed in the confirmation. The files are kept by default.

### Across the App

- Hold and drag a service card to move it. Stacks remembers the order and keeps your place in service lists as you browse.
- Tap or swipe between service tabs. Pull down to refresh while the last known status stays visible. If Stacks is still waiting for the first status result, the card shows **Checking**.
- Container logs refresh every five seconds. You can also refresh them yourself and choose to see the last 100, 500, or 1,000 lines.
- To change your terminal shortcuts, open **Settings > Quick Commands** or scroll to the end of the terminal shortcuts and tap the pencil. Put one command on each line and tap **Save**. Tap a shortcut in the terminal to run it.
- In **Settings**, pick Light or Dark mode or export and import a JSON settings backup. Check **About** for your app version, **Credits** for project links, and **Feedback & Support** to report a problem or suggest a feature.

### Premium Access

Open **Settings > Premium Access > Get Premium Access** to see purchase options on Google Play. If you’ve already purchased, use **Restore purchases** with the Google Play account you used to buy it.

Premium unlocks custom terminal shortcuts, Compose and environment editing in Table mode, YAML formatting in Raw mode, adding registries and Git providers in Komodo and Portainer, and SSH host access for Docker API connections. You can still edit Compose and environment files in Raw mode wherever your connection supports it. Built-in terminal shortcuts and standalone SSH connections are available without Premium.

With Premium, use **Settings > Show Service Logos** to display provider logos. Free accounts use generic service icons.

In the Compose table, tap the pencil beside a key to rename it. For service, network, and named volume names, Stacks previews the references it can update in the current file before you apply the change.

## Service Setup Guides

### Connecting Komodo

1. Tap **+** on the dashboard and choose **Komodo**.
2. Give the connection a **Server Alias** and enter the **Komodo Endpoint**, for example `http://192.168.1.100:9120` or `https://komodo.example.com`.
3. Choose how to sign in.
   - **Username & Password** uses your Komodo account. Enter the six-digit code if two-factor authentication is enabled. After you sign in, Stacks tries to create a dedicated key for future connections.
   - **API Key & Secret** uses credentials you create in your Komodo profile’s API key settings. Paste both into Stacks.
4. Tap **Connect**. If Android asks for local network access, allow it so Stacks can reach a server on your LAN.

### Connecting Portainer

1. In Portainer, go to **My account > Access tokens**. Create a token for Stacks and copy it when it’s shown.
2. In Stacks, tap **+** and choose **Portainer**.
3. Enter a **Server Alias**, the **Portainer Endpoint** (for example, `https://192.168.1.100:9443`), and your **Access token**.
4. If your HTTPS endpoint uses a self-signed or private-CA certificate, enter its verified **Certificate SHA-256 fingerprint** if Android doesn’t already trust it.
5. Tap **Connect** and allow local network access if prompted.

### Connecting Docker API

1. Make sure your phone can reach the Docker API over a trusted network, VPN, or secured reverse proxy. Use TLS and authentication over untrusted networks.
2. In Stacks, tap **+** and choose **Docker API**.
3. Enter a **Server Alias** and a **Docker Endpoint**, for example `https://docker.example.com:2376`.
4. Choose the authentication your endpoint expects.
   - **Client certificate** uses a certificate and private key installed in Android’s credential settings. Tap **Choose certificate** to select it.
   - **Proxy bearer token** uses the token required by your HTTPS reverse proxy.
   - **None** is for endpoints already protected by a trusted private network or another access control.
5. If needed, enter the verified **Certificate SHA-256 fingerprint** for the HTTPS endpoint.
6. Tap **Connect**. Repeat for each engine you want to add.

#### Adding SSH Host Access to a Docker Engine

1. Open the Docker service’s three-dot menu and choose **Add Host Access**. You can also reach it from **Compose** or **Environment**.
2. Enter the **SSH Endpoint**, **Username**, and **Root Directory**. Leave `/srv/stacks` as the root if that’s where you keep your projects.
3. Choose **Password**, **Private key**, or **No authentication**. Paste a private key or pick a key file, and enter its passphrase if it has one. **No authentication** requires a server that accepts an unauthenticated session or an empty password.
4. Enter the verified **Host key SHA-256 fingerprint** or compare the fingerprint shown on first connection with your server’s known host key before trusting it.
5. Tap **Save Host Access**. The SSH account needs to reach the same Docker engine as your API connection and have access to the project files.

Host access is part of that Docker service on the dashboard. Choose **Edit Host Access** in the three-dot menu to change it. If you change the Docker API endpoint, set up host access again for the new engine.

### Connecting SSH

1. Tap **+** and choose **SSH Connection**.
2. Enter a **Server Alias**, **SSH Endpoint** (for example, `ssh://192.168.1.100:22`), **Username**, and **Root Directory**.
3. Choose **Password**, **Private key**, or **No authentication**. Use **No authentication** only with a server that accepts an unauthenticated session or an empty password.
4. Enter a verified **Host key SHA-256 fingerprint**, or verify the fingerprint shown on first connection against your server’s known host key.
5. Tap **Connect**. Open the service to manage its stacks and containers, or tap the terminal icon for a host shell.

## Troubleshooting & Raising Issues

- **Stacks can’t reach the server.** Check your Wi-Fi or VPN, the endpoint address and port, and the server firewall. If you previously denied local network access, you can enable it in Android’s app settings.
- **Sign-in failed.** Tap the pencil on the service card to check the connection details. Make sure your token is still valid or your SSH username, key, or password is correct. For Docker host access, use **Edit Host Access** instead.
- **The certificate or SSH host key changed.** Verify the new fingerprint against your server before updating the connection.
- **The Compose or Environment tab asks for host access.** Open the Docker service menu and tap **Add Host Access** to give Stacks an SSH connection for the project files.
- **A Compose or environment file is missing.** Check the **Root Directory**, file location, and SSH permissions. If Komodo or Portainer keeps the file in its own data volume, use that service’s editor or make the file accessible to the SSH account, then tap **Reload**.
- **Host access points to a different engine.** Check which Docker engine the SSH account is using. It must be the one you added through the Docker API.
- **The host terminal button is unavailable.** Finish setting up SSH authentication and verify the host key.
- **A Docker container terminal fails through a reverse proxy.** Check that the proxy forwards the connection upgrade.
- **The Compose editor flags a YAML error.** Switch to **Raw** and tap **Format** to use two-space indentation while keeping your blank lines. If it points to a line and column, fix the syntax there and try again. Tap **Save** when you’re done.
- **The file changed while you were editing.** Reload it and review your edits against the latest copy before saving again.
- **You pulled an image but the container is still on the old version.** Redeploy to recreate the container with the new image. Use **Pull Image & Redeploy** with SSH host access, or redeploy through Komodo or Portainer.

### Reporting an Issue

Found a bug or missing a feature? Open an issue and include your Android version and device model, which service you’re using and its version, and whether you connect over local Wi-Fi, a VPN, or a reverse proxy. For bugs, tell us what you expected, what happened, and how to reproduce it. An on-screen error or screenshot can help once you’ve removed passwords, tokens, keys, and other private details. [GitHub issue tracker](https://github.com/pradumnk-mahanta/stacks-docs/issues)

## Privacy & Terms

Stacks has no ads or analytics. Settings, credentials, and cached service information stay on your device. Android Keystore protects your saved credentials, and Stacks sends authentication details only when needed to connect to the services you configure. Connections go directly to your servers. Google Play handles Premium purchases and reports purchase status to the app.

Settings backups leave out credentials, private keys, saved certificate and SSH host trust, and terminal quick commands. On a new device, sign in again and verify your certificates or host keys. [Privacy Policy](PRIVACY_POLICY.md)

Use Stacks with infrastructure you’re authorized to access. You’re responsible for securing your endpoints, keeping backups, and reviewing actions like redeploying stacks, deleting resources, and pruning images. Stacks is provided as is, without warranties. [Terms and Conditions](TERMS_AND_CONDITION.md)
