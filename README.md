# AbdoCode add-ons

First-party optional instruction skills and a read-only Gmail MCP connector. This repository contains no AbdoCode application source, user projects, profiles or credentials.

## Install

In AbdoCode, open **Settings > Extensions > Download from GitHub**, choose a release or paste its pinned raw package URL and SHA-256. Review the captured package, install, then enable it. Skills are inserted with **Use in next message**. MCP servers connect only after pressing **Connect**.

For private repositories, sign in through GitHub CLI (`gh auth login`) and select **Use my GitHub CLI sign-in** in the download dialog. AbdoCode reuses the local authenticated GitHub transport without reading its token into the interface. An authorized user can also import a downloaded package folder through **Import folder**. Installing never runs scripts. Updates are explicit: review a new version, remove the old package, then install and enable the new copy.

## Gmail

The connector requires Node.js 18 or newer. Enable the Gmail API in your Google Cloud project and obtain a user-authorized OAuth access token with the `gmail.readonly` scope. Enter it in the package **Credentials** form, which stores it in the native vault. Do not put it in chat, the manifest or this repository. Press **Connect** and test the `profile` tool. An expired token must be renewed in Credentials. OAuth login and automatic refresh are not included in this version.

The connector exposes profile, labels, message search and message reading. It cannot send, delete or modify email. Accounts are not connected merely by installing the package.

Official API references: [message search](https://developers.google.com/workspace/gmail/api/reference/rest/v1/users.messages/list), [message reading](https://developers.google.com/workspace/gmail/api/reference/rest/v1/users.messages/get).

## Release format

`release/*.json` captures text files into a versioned document. `SHA256SUMS` records exact download hashes. Published application catalog entries use a full Git commit ID. The native downloader accepts only this format from raw.githubusercontent.com, limits size, verifies SHA-256, and applies the existing local installer validation. A hash proves which bytes were downloaded, not that third-party code is trustworthy.
