# n8n with PostgreSQL and Worker

Starts n8n with PostgreSQL as database, and the Worker as a separate container.

## Start

To start n8n simply start docker-compose by executing the following
command in the current folder.

**IMPORTANT:** But before you do that change the default users and passwords in the [`.env`](.env) file!

```
docker-compose up -d
```

To stop it execute:

```
docker-compose stop
```

## Configuration

The default name of the database, user and password for PostgreSQL can be changed in the [`.env`](.env) file in the current directory.


### Switching to a Webhook node instead of the Telegram trigger, I’m still facing the same problem as it suddenly started to error.

Register Your Webhook:

**POST Method**
```
https://api.telegram.org/bot[YOURBOTTOKEN]/setWebhook?url=[YOURWEBHOOK]
```

Delete Your Webhook (Set empty string on url webhook):

**POST Method**
```
https://api.telegram.org/bot[YOURBOTTOKEN]/setWebhook?url=
```

After doing that, I accidentally discovered that posting ‘test’ to the group would not trigger anything, but posting ‘/test’ (or anything that starts with ‘/’) would trigger n8n. So I did the next two items.

**Privacy Mode:**

1. Disable privacy mode:
   - Open a chat with BotFather.
   - Send the command /mybots to see a list of your bots.
   - Select your bot and use the command Edit Bot Privacy to turn off privacy mode.

**Group Admin:**

1. Ensure that your bot is an admin in the group chat. For the bot to receive all messages in a group, it typically needs to have admin permissions.