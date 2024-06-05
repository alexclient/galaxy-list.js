# Galaxy List NPM Package

The offical Node SDK to interact with [Galaxy List](http://galaxylist.srvmc.net:25566/)'s API.

```
npm i galaxy-list.js
```

# Getting Started

To post your bot's stats to Galaxy List, you will need a Discord client and the `galaxy-list.js` package defined.

```js
const { Client, Events, GatewayIntentBits } = require("discord.js");
const galaxyList = require("galaxy-list.js");

const client = new Client({ intents: [GatewayIntentBits.Guilds] });
```

## POSTing bot's stats

First, define your Discord client, and then provide your Universe List API Key found in your bot's edit page.

```js
const Discord = require("discord.js");
const client = new Discord.Client();
const API_KEY = "YOUR_API_KEY";

// Login to your bot
client.login("BOT_TOKEN");

// Post stats
client.on("ready", () => {
  setInterval(async () => {
    try {
      await postStats(client, API_KEY);
    } catch (error) {
      console.error(`Failed to post stats: ${error}`);
    }
  }, 5 * 60 * 1000); // Posts every 5 minutes
});
```

#### Debug Mode

If you want to log the response message to the console, add `true` as parameter. <br>
_await postStats(client, API_KEY, true);_

## GETing bot's info

Provide a Discord bot ID of a bot that is on [Galaxy List](http://galaxylist.srvmc.net:25566/).

```js
const botId = "123456789"; // Replace this with the ID of the bot.

galaxyList
  .fetchBot(botId)
  .then((botData) => {
    console.log(botData);
  })
  .catch((err) => {
    console.error(err);
  });
```

## GETing server's info

Provide a Discord server ID of a server that is on [Galaxy List](http://galaxylist.srvmc.net:25566/servers).

```js
const serverId = "123456789"; // Replace this with the ID of the server.

galaxyList
  .fetchServer(serverId)
  .then((serverData) => {
    console.log(serverData);
  })
  .catch((err) => {
    console.error(err);
  });
```

## GETing bots's votes

Provide a Discord bot ID of a bot that is on [Galaxy List](http://galaxylist.srvmc.net:25566/bots).

```js
const botId = "123456789"; // Replace this with the ID of the bot.

galaxyList
  .fetchVotes(botId)
  .then((votes) => {
    console.log(votes);
  })
  .catch((err) => {
    console.error(err);
  });
```

## Check Vote from user

Provide a Discord bot ID of a bot that is on [Galaxy List](http://galaxylist.srvmc.net:25566/) and a Discord user ID.

```js
const botId = "123456789"; // Replace this with the ID of the bot.
const userId = "987654321"; // Replace this with the ID of the user.

galaxyList
  .checkVote(botId, userId)
  .then((voteData) => {
    console.log(voteData);
  })
  .catch((err) => {
    console.error(err);
  });
```

# Credits

This API was originally created by [AlexClient](https://portafolio.supramc.xyz) and was later modified by [Jose](https://github.com/jair507).
