# How to Install and Uninstall Microsoft Edge on Ubuntu

Microsoft Edge is a Chromium-based web browser developed by Microsoft, offering speed, security, and compatibility across platforms. This tutorial provides a step-by-step guide to install and uninstall Microsoft Edge on **Ubuntu 20.04, 22.04, or later**.

---

## Prerequisites

Ensure you have `sudo` privileges and an active internet connection.

---

## Step 1: Update Your System

```bash
sudo apt update && sudo apt upgrade -y
```

**Explanation:** Updates your system's package list and upgrades all existing packages.

---

## Step 2: Install Required Dependencies

```bash
sudo apt install software-properties-common apt-transport-https curl ca-certificates -y
```

**Explanation:** Installs tools required to manage repositories and download packages securely over HTTPS.

---

## Step 3: Add Microsoft’s GPG Key

```bash
curl -fSsL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor | sudo tee /usr/share/keyrings/microsoft-edge.gpg > /dev/null
```

**Explanation:** Downloads and saves Microsoft's official signing key to validate Edge packages.

---

## Step 4: Add the Microsoft Edge Repository

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft-edge.gpg] https://packages.microsoft.com/repos/edge stable main" | sudo tee /etc/apt/sources.list.d/microsoft-edge.list
```

**Explanation:** Adds Microsoft Edge's repository to your system's sources list.

---

## Step 5: Update the Package List

```bash
sudo apt update
```

**Explanation:** Refreshes the package index to include Microsoft Edge from the newly added repository.

---

## Step 6: Install Microsoft Edge (Stable Version)

```bash
sudo apt install microsoft-edge-stable -y
```

**Explanation:** Installs the stable version of Microsoft Edge browser.

---

### Optional: Install Edge Beta or Dev Versions

```bash
# Install Beta version
sudo apt install microsoft-edge-beta -y

# Install Dev version
sudo apt install microsoft-edge-dev -y
```

**Explanation:** Installs Microsoft Edge Beta or Dev versions, used for testing new features.

---

## Step 7: Launch Microsoft Edge

* From terminal:

  ```bash
  microsoft-edge
  ```
* Or from the applications menu: Search for "Microsoft Edge".

---

## Optional: Clean Up Old or Unused Packages

```bash
sudo apt autoremove -y
```

**Explanation:** Frees up disk space by removing packages that are no longer needed.

---

## Uninstalling Microsoft Edge

### Step 1: Remove the Edge Browser

```bash
sudo apt remove microsoft-edge-stable -y
```

**Explanation:** Uninstalls the stable version of Microsoft Edge.

> If you installed the Beta or Dev version, replace the package name accordingly:
>
> `microsoft-edge-beta` or `microsoft-edge-dev`

---

### Step 2: Remove the Repository and GPG Key

```bash
sudo rm /etc/apt/sources.list.d/microsoft-edge.list
sudo rm /usr/share/keyrings/microsoft-edge.gpg
```

**Explanation:** Deletes the Microsoft Edge repository and the key used for package verification.

---

### Step 3: Final Cleanup

```bash
sudo apt update && sudo apt autoremove -y
```

**Explanation:** Updates the package index and removes any remaining unused packages.

---

## Summary Table

| Action                    | Command                                                                                   | Result                                                 |                               |
| ------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------ | ----------------------------- |
| Update system             | `sudo apt update && sudo apt upgrade -y`                                                  | Keeps system up to date                                |                               |
| Install dependencies      | `sudo apt install software-properties-common apt-transport-https curl ca-certificates -y` | Installs necessary tools                               |                               |
| Add Microsoft GPG key     | \`curl ...                                                                                | sudo tee /usr/share/keyrings/microsoft-edge.gpg\`      | Adds package verification key |
| Add Edge repository       | \`echo "deb ..."                                                                          | sudo tee /etc/apt/sources.list.d/microsoft-edge.list\` | Adds Edge package source      |
| Refresh package list      | `sudo apt update`                                                                         | Recognizes new packages                                |                               |
| Install Edge              | `sudo apt install microsoft-edge-stable -y`                                               | Installs Microsoft Edge                                |                               |
| Uninstall Edge            | `sudo apt remove microsoft-edge-stable -y`                                                | Removes Edge browser                                   |                               |
| Remove repository and key | `sudo rm microsoft-edge.list && sudo rm microsoft-edge.gpg`                               | Deletes related files                                  |                               |
| Clean up                  | `sudo apt autoremove -y`                                                                  | Removes unused packages                                |                               |

---

## Troubleshooting

* **"Unable to locate package microsoft-edge-stable"**

  * Ensure you've added the repository and run `sudo apt update`.

* **"Permission denied"**

  * Use `sudo` to run commands that require elevated privileges.

* **Edge does not launch**

  * Run `microsoft-edge` in the terminal and check for error output.

---

## Conclusion

You have now learned how to properly install and uninstall Microsoft Edge on Ubuntu. This guide supports multiple versions (Stable, Beta, Dev), and ensures your system remains clean with optional cleanup steps.
