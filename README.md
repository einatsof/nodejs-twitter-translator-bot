# Twitter Translation Bot

A Twitter bot that automatically quote retweets new tweets from specific users, translating them if they are written in a specific language. The bot uses the [`Twitter API v2`](https://github.com/plhery/node-twitter-api-v2) to interact with Twitter, [`languagedetect`](https://github.com/FGRibreau/node-language-detect) for language detection, and [`google-translate-api-x`](https://github.com/AidanWelch/google-translate-api) for translation.

## Features

- Monitors specific users' tweets in real-time.
- Detects the language of the tweets.
- Translates tweets from a specified language to another.
- Quote retweets the translated tweet.

## Important Notice

### Twitter API Changes

**Please note:** The Twitter API has undergone significant changes, and some features that were previously free may now require a paid plan. This includes access to certain endpoints and higher rate limits. Before using this bot, ensure that your Twitter Developer account is set up with the necessary access levels to avoid any interruptions.

For more details, please refer to the [Twitter API Documentation](https://developer.twitter.com/en/docs/twitter-api) and [pricing information](https://developer.twitter.com/en/docs/twitter-api/getting-started/about-twitter-api).

## Prerequisites

Before running this bot, ensure you have the following:

- Node.js installed on your system.
- A Twitter Developer account with API keys and tokens.
    - You can generate these through the [Twitter Developer Portal](https://developer.twitter.com/en/portal/dashboard).
    - A tool to get the bot token - https://github.com/smaeda-ks/tw-oob-oauth-cli

## Installation

1. Clone this repository to your local machine:
```bash
git clone https://github.com/your-username/twitter-translation-bot.git
cd twitter-translation-bot
```

2. Install the necessary dependencies:
```bash
npm install
```

3. Create a .env file in the root directory and add your Twitter API keys and tokens:
```dosini
APP_KEY=your-app-key
APP_SECRET=your-app-secret
ACCESS_TOKEN=your-access-token
ACCESS_SECRET=your-access-secret
```

## Usage

1. Configure the bot:
    - In the main script, you can specify the users to monitor and the language settings:
    ```js
    const interval = 60 * 60 * 1000; // 1 hour polling interval

    const users = {
      '12': 'jack' // 'twitter id': 'name'
    };

    const FROM_LANGUAGE = 'dutch';  // The language you want to translate from
    const FROM_LANGUAGE_ISO = 'nl'; // ISO code of the language
    const TO_LANGUAGE_ISO = 'en';   // ISO code of the target language
    ```
    - Adjust the polling interval by changing the interval variable in the script.
    - Replace '12': 'jack' with the Twitter IDs and names of the users you want to monitor.
    - Replace the values of `FROM_LANGUAGE`, `FROM_LANGUAGE_ISO` & `TO_LANGUAGE_ISO` to the desired langugages (You should first check the supported languages by `languagedetect` and `google-translate-api-x`).

2. Run the bot:
Start the bot with the following command:
```bash
node index.js
```
The bot will poll Twitter every hour to check for new tweets from the specified users. If a tweet is in the specified language, it will be translated and quote retweeted with the translation.
 