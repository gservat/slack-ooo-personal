# Personal Out of Office Bot for Slack
This bot acts as you and will respond to DMs and Channel mentions with a message while you are away.

## Features
- Start time: Set a start and the bot will wait until set time before listening and responding
- End time: Set an end time and the bot will shut off on a set time
- Respond to IM/Multi-Person IM when someone directly messages you
- Respond to a channel where you are directly mentioned (@username)
- Reminder buffer: Bot will not respond to user/channel until a give time has elapsed (to prevent spamming)
- Auto Mark: Bot can mark all your messages as read

## Personal Slack Token
You can generate your personal Slack Token here: [https://api.slack.com/web](https://api.slack.com/web)

## Install
1. Clone this [repository](https://github.com/shaunburdick/slack-ooo-personal.git)
2. `npm install`
3. Copy `./config.default.js` to `./config.js` and fill it out
4. `npm start`

## Test
1. `npm install` (make sure your NODE_ENV != `production`)
2. `npm test`

## Docker
Build an image using `docker build -t your_image:tag`

Official Image [shaunburdick/slack-ooo-personal](https://registry.hub.docker.com/u/shaunburdick/slack-ooo-personal/)

### Configuration Environment Variables
You can set the configuration of the bot by using environment variables. ENVIRONMENT_VARIABLE=Default Value
- APP_MESSAGE='', Your OoO Message
- APP_REMINDER=28800000, Time to wait before responding to person/channel again (in milleseconds)
- APP_RESPOND_DM=true, If true, will respond to Direct messages
- APP_RESPOND_CHANNEL=false, If true, will respond on Channel mentions
- APP_TIMEBOX_START=0, Time to start responding (Timestamp in milliseconds, or [parsable](http://dygraphs.com/date-formats.html) date)
- APP_TIMEBOX_END=0, Time to stop responding (Timestamp in milliseconds, or [parsable](http://dygraphs.com/date-formats.html) date)
- SLACK_TOKEN=xoxb-foo, Your Slack Token
- SLACK_AUTO_RECONNECT=true, Reconnect on disconnect
- SLACK_AUTO_MARK=false, Mark messages as read

Set them using the `-e` flag while running docker:

```
docker run -it \
-e SLACK_TOKEN=xobp-blarty-blar-blar \
-e APP_MESSAGE='I am out of the office' \
-e APP_TIMEBOX_START='2015-12-24 17:00:00' \
-e APP_TIMEBOX_END='2015-12-26 08:00:00' \
shaunburdick/slack-ooo-personal:latest
```
