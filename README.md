# GHA Dashboard

A lightweight, single-file GitHub Actions dashboard that runs entirely in the browser — no server, no build step, no dependencies.

## Features

- Displays the latest workflow runs per repository, filtered by your GitHub username
- Status badges with live color coding (success, failure, running, queued, cancelled, skipped)
- Auto-refreshes on a configurable interval with a live countdown
- Manual refresh button
- Skeleton loading state on first load

## Setup

### 1. Clone the repo

```bash
git clone <repo-url>
cd gha-dashboard
```

### 2. Create your config file

Copy the example config and fill in your values:

```bash
cp config.js.example config.js
```

Edit `config.js`:

```js
window.GHA_CONFIG = {
  token: 'ghp_YOUR_TOKEN_HERE',       // GitHub Personal Access Token
  username: 'your-github-username',   // Your GitHub username
  refreshInterval: 30,                // Seconds between auto-refreshes
  repos: [
    'owner/repo1',
    'owner/repo2'
  ]
};
```

### 3. Generate a GitHub Personal Access Token

1. Go to [GitHub Settings → Developer settings → Personal access tokens](https://github.com/settings/tokens)
2. Generate a new token (classic or fine-grained)
3. Required scopes:
   - **Public repos only:** no scopes required (token still helps avoid rate limits)
   - **Private repos:** `repo` + `workflow`

### 4. Open in browser

Just open `index.html` directly in your browser:

```bash
open index.html
```

No web server needed.

## Configuration Reference

| Field             | Type     | Description                                      |
|-------------------|----------|--------------------------------------------------|
| `token`           | string   | GitHub Personal Access Token                     |
| `username`        | string   | GitHub username to filter runs by                |
| `refreshInterval` | number   | Seconds between auto-refreshes (default: `30`)   |
| `repos`           | string[] | List of repos in `owner/repo` format             |

## Security Note

`config.js` is listed in `.gitignore` to prevent accidentally committing your token. Never commit your token to version control.
