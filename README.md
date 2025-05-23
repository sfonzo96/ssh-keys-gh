# SSH Key Management Script

Available languages:

-   [English](README.md)
-   [Español](README.es.md)

This Bash script simplifies SSH key management for a user. It allows checking for existing SSH keys, displaying the
current public key, and generating a new ED25519 SSH key with a provided email.

> ⚠️ **Note**: This script is intended for **Linux** systems only. A Windows-compatible version (likely using
> PowerShell) is planned for a future update.

## Features

-   Check if an SSH key already exists (`id_ed25519.pub`)
-   Show the current SSH public key
-   Generate a new SSH key pair with a given email address
-   Optionally install `ssh-keygen` if it's not present
-   Automatically adds the key to `ssh-agent` if it's running

## Setup

Clone this repository to your local machine running the following commands:

```bash
git clone https://github.com/sfonzo96/ssh-keys-gh
cd ssh-keys-gh
```

## Usage

```bash
./set_ssh_key.sh [option] [email]
```

### Options

-   `-h`, `--help` Show usage information.

-   `-s`, `--show` Display the current SSH public key.

-   `-c`, `--check` Check if an SSH key already exists.

-   `-g`, `--generate <email>` Generate a new SSH key pair. Requires a valid email as an argument.

### Examples

Check if an SSH key exists:

```bash
./set_ssh_key.sh --check
```

Generate a new key with an email:

```bash
./set_ssh_key.sh --generate your_email@example.com
```

Show your current SSH public key:

```bash
./set_ssh_key.sh --show
```

## Add your SSH key to GitHub

-   After generating the SSH key, you need to add it to your GitHub account. Follow these steps:

    -   Copy the SSH key to your clipboard:
    -   Go to your GitHub account settings.
    -   Navigate to "SSH and GPG keys".
    -   Click on "New SSH key".
    -   Add a title for the key (e.g., "My Laptop SSH Key").
    -   Make sure the "Key type" field has the "Authentication Key" option selected.
    -   Paste the SSH key into the "Key" field.
    -   Click "Add SSH key".
    -   You may be prompted to enter your GitHub password to confirm the addition of the key.

-   Following those steps should allow you to _push_ and _pull_ from your GitHub repositories right away.

## Notes

-   If `ssh-keygen` is not installed, the script will prompt to install it using `apt-get`.
-   Keys are generated using the ED25519 algorithm and stored at `~/.ssh/id_ed25519`.

## Future Plans

-   Add support for Windows via PowerShell
-   Implement more advanced error handling

## References

-   [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
-   [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?tool=webui)
