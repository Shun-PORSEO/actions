## LINE Notify Workflow

This repository includes a GitHub Actions workflow to send a notification to LINE via LINE Notify when manually triggered.

### Prerequisites

- Create a LINE Notify access token.
  - Go to `https://notify-bot.line.me/my/` and issue a token for the target chat.
  - Copy the token value.
- In your GitHub repository, add a Repository Secret named `LINE_NOTIFY_TOKEN` with the token value.

### Workflow

File: `.github/workflows/line-notify.yml`

Triggers: `workflow_dispatch` (manual trigger from GitHub UI)

Inputs:

- `message` (required): Text to send
- `sticker_package_id` (optional): Sticker package ID
- `sticker_id` (optional): Sticker ID

### How to Run

1. Open your repository on GitHub.
2. Go to the `Actions` tab.
3. Select "LINE Notify Manual Trigger".
4. Click `Run workflow`, fill `message` (and optional sticker fields), then run.

### Notes

- The workflow uses `curl` to call LINE Notify API `https://notify-api.line.me/api/notify` with the provided token.
- If `sticker_package_id` and `sticker_id` are both provided, a sticker will be included.
- The job fails fast if `LINE_NOTIFY_TOKEN` is not configured.
