
# Bluebot

A bot for posting RSS feed updates to Bluesky using Node.js and Docker.

## Features
- Fetches RSS feeds and posts new updates to a Bluesky account.
- Avoids duplicate posts by tracking links locally.
- Fetches metadata (title, description, thumbnail) for embedded links.
- Adheres to Bluesky's API rate limits.

## Requirements
- [Node.js](https://nodejs.org/) version 16 or higher.
- A Bluesky account.

## Getting Started

Follow these steps to set up and run the bot:

### 1. Clone the repository
```bash
git clone https://github.com/cgillinger/bluebot.git
cd bluebot
```

### 2. Install dependencies
Run the following command to install all required dependencies:
```bash
npm install
```

### 3. Configure the `.env` file
- A `.env` file is included in the repository with placeholder values. Open it and replace placeholders with your actual Bluesky credentials:
```env
BLUESKY_USERNAME=your_username@provider.com
BLUESKY_PASSWORD=your_secure_password
```
- **Important**: The `.env` file must remain in the project directory for the bot to work.

### 4. Update RSS Feeds
- Open the `bot.mjs` file in a text editor.
- Locate the `RSS_FEEDS` array:
```javascript
const RSS_FEEDS = [
  { url: 'https://example.com/rss-feed-1.xml', title: 'Example Feed 1' },
  { url: 'https://example.com/rss-feed-2.xml', title: 'Example Feed 2' },
];
```
- Replace the placeholder URLs with the RSS feed URLs you want the bot to monitor. Optionally, add a `title` for each feed.

### 5. Start the bot
Run the bot using:
```bash
npm start
```

The bot will:
- Fetch new entries from the configured RSS feeds.
- Post them to your Bluesky account if they haven't been posted already.
- Repeat every 5 minutes.

## Common Issues and Troubleshooting

### Invalid Bluesky Credentials
If you see an error like `Invalid identifier or password`, ensure that:
1. Your `.env` file is correctly configured with valid Bluesky credentials.
2. Your Bluesky account is active and accessible.

### Rate Limit Errors
If the bot encounters rate limits (status code `429`), it will automatically pause and retry after the required wait time.

### Missing Dependencies
If the bot fails to start due to missing modules, run:
```bash
npm install
```

### Remote Repository Issues
If pushing to GitHub gives an error like `remote: Repository not found`:
1. Check that the correct remote URL is set:
   ```bash
   git remote -v
   ```
2. Update it if necessary:
   ```bash
   git remote set-url origin https://github.com/cgillinger/bluebot.git
   ```

## Additional Notes
- The bot uses placeholders for RSS feeds and requires manual updates in `bot.mjs` to set the actual feeds.
- `.env` is intentionally included in the repository because it contains only placeholder data.

## License
This project is licensed under the ISC License.

## Contributing
Contributions are welcome! Open an issue or submit a pull request if you'd like to help improve the project.