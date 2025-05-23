# Y3S2-Assigment6

# GitHub Repo Fetcher Script

This guide walks you through creating a simple Bash script to fetch public repositories from a GitHub profile and save the raw JSON response to a file.

## Step 1: Open a Unix Terminal

Launch any Unix-based terminal (Linux, macOS, or WSL on Windows).

## Step 2: Create the Bash Script File

Run the following command to create and open a new script file using `nano`:

nano ~/getTxtGitRepo

## Step 3: Write the Script

Paste the following code into the nano editor:

#!/bin/bash

if [ -z "$1" ]; then
  echo "Usage: getTxtGitRepo [GitHub Profile URL]"
  exit 1
fi

url=$1
username=$(echo "$url" | sed -E 's|https?://github\\.com/([^/]+)/?.*|\\1|')

if [ -z "$username" ]; then
  echo "Invalid GitHub profile URL."
  exit 1
fi

curl -s -L \\
  -H "Accept: application/vnd.github+json" \\
  "https://api.github.com/users/$username/repos" > gitHubRepo.txt

echo "Raw JSON response saved to gitHubRepo.txt"

To save and exit:
- Press Ctrl + O to write the file.
- Press Enter to confirm.
- Press Ctrl + X to exit the editor.

## Step 4: Make the Script Executable

Run the following command to give the script execution permissions:

chmod +x ~/getTxtGitRepo

## Step 5: Run the Script

Use the script by passing a GitHub profile URL as an argument:

~/getTxtGitRepo https://github.com/MOEN-ERAK

This will save the list of public repositories in a file named `gitHubRepo.txt`.
