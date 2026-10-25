# Google Drive setup

Sharp Axe can save your data to one file in your Google Drive: `Sharp Axe/sharp-axe-data.json`. Then you can open your to-dos on another device.

The app can see only the files that it made (scope `drive.file`). It cannot see anything else in your Drive.

You make a free Google "Client ID" one time. This takes about 10 minutes.

## Step 1. Put the app online

1. In the GitHub repository, go to **Settings → Pages**.
2. Under **Source**, select **GitHub Actions**.
3. Merge to `main`. The app is published at `https://jakeseegers.github.io/SharpAxeMethod/`.

Google sign-in does not work when you open `index.html` as a file. Use the web address.

## Step 2. Make a Google Cloud project

1. Go to <https://console.cloud.google.com/>.
2. Make a new project, for example "Sharp Axe".
3. Go to **APIs & Services → Library**. Find **Google Drive API** and select **Enable**.

## Step 3. Set up the consent screen

1. Go to **APIs & Services → OAuth consent screen**.
2. Select **External**. Type an app name and your email.
3. Add the scope `https://www.googleapis.com/auth/drive.file`.
4. Under **Test users**, add your Google account.

## Step 4. Make the Client ID

1. Go to **APIs & Services → Credentials → Create credentials → OAuth client ID**.
2. For **Application type**, select **Web application**.
3. Under **Authorized JavaScript origins**, add `https://jakeseegers.github.io`.
4. Select **Create**. Copy the Client ID. It ends with `.apps.googleusercontent.com`.

## Step 5. Connect

1. Open the app. Open the **⋯** menu and select **Google Drive**.
2. Paste the Client ID when the app asks. Then allow access.

You can also put the Client ID in `index.html`, in `const GOOGLE_CLIENT_ID = ""`. Then the app does not ask. The Client ID is not a secret.

## How it works

- When Google Drive is on, the app saves your data to Drive a few seconds after each change.
- When you connect, if Drive has a newer copy (from another device), the app asks if you want to load it.
- Google keeps you signed in for 1 hour. After that, open the menu and select **Google Drive** to sign in again. Your data stays on the device until then.
- To stop, select **Disconnect Google Drive** in the menu. Your Drive file stays.
