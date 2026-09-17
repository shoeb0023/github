# Managing Multiple GitHub Accounts in VS Code

This guide outlines how to seamlessly manage and switch between a primary (default) GitHub account and a secondary/temporary GitHub account on the same machine using local Git repository configurations.

## The Problem

When working with multiple GitHub accounts, Git and the Windows Credential Manager often cache credentials for your primary account (`shoeb310`), causing permission errors (`403 Forbidden` or `Repository not found`) when trying to push code to a secondary account (`shoeb0023`).

## The Solution: Local Repository Configuration

Instead of changing your global Git settings or messing with Windows Credentials every time, you can override the configuration locally for each specific project folder.

## Step-by-Step Implementation

### 1. Clone the Repository (with Username Prefix)

When cloning your secondary account's repository, include your secondary username in the remote URL to guide Git on which identity to associate with the connection:

```bash
git clone https://shoeb0023@github.com/shoeb0023/your-repo-name.git
cd your-repo-name

2. Configure Local User Credentials
Set the Git username and email locally inside this project folder so they override your global account settings:

git config --local user.name "shoeb0023"
git config --local user.email "shoeb0023@gmail.com"

3. Force Remote URL Authentication
Ensure your remote origin explicitly points to the correct account:

git remote set-url origin https://shoeb0023@github.com/shoeb0023/your-repo-name.git

4. Commit and Push
Make your changes, stage them, commit, and push normally:

git add .
git commit -m "feat: initial commit for secondary project"
git push origin main

Note: Authenticate using your secondary account credentials or Personal Access Token when prompted.

Verification Commands
Check Current Active User for This Repo
git config user.name
git config user.email

Check Current Remote Repository URL
git remote -v

Verify Last Commit Author Details
git log -1




