# Reproducing Expiring Refresh Token

This is a minimal example to reproduce the Twitter OAuth 2.0 issue reported [here](https://twittercommunity.com/t/refresh-token-expiring-with-offline-access-scope/168899) where the refresh_token expires in minutes or hours instead of 6 month.

This script will take a refresh_token and try to refresh it every n minutes. If the bug is valid this will start to return a 401 after a few minutes or sometimes after 12 hours.

# Usage

There's environment variables that have to be set. A valid start refresh token, you'd get one of these if you connect your Twitter account to your app through OAuth and even with the bug it will be valid for a couple of minutes. Grab that one and provide it to this script.

- TWITTER_REFRESH_TOKEN
- TWITTER_CLIENT_ID, TWITTER_CLIENT_SECRET: You can find these on https://developer.twitter.com in your app / environment
- TWITTER_REFRESH_INTERVAL_IN_MINUTES how much time are we waiting in-between refreshes


```
TWITTER_REFRESH_TOKEN=redacted \
TWITTER_CLIENT_ID=redacted \
TWITTER_CLIENT_SECRET=redacted \
TWITTER_REFRESH_INTERVAL_IN_MINUTES=60 \
go run main.go
```