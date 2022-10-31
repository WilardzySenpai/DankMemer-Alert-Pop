# DankMemer-Alert-Pop
A re-creation of Dank Memer Alert Pop when they set a new news/alert on their. 

## What database I used?
- I used enmap to make this because enmap is way more easier to use and to understand (for me)

### Preview
![image](https://media.discordapp.net/attachments/1018692674963914783/1036624951509258250/ezgif-3-b87b9735c4.gif?width=480&height=350)

# Getting started
- NodeJS v18 above
- enmap, discord.js module - `npm install enmap discord.js`
- code editor
- JS knowledge
- DiscordJS knowledge

## Start
- First we need to login to our bot then after if you want you could set some new collections.
Now we need to set the database and location of it.

```js
// defining enmap
const Enmap = require('enmap');
```

```js
// Your client name then make a enmap data, the name of it, and the location
<Client>.dankMemer = new Enmap({ name: "alert", dataDir: "./databases/alert" });
```
Now lets returns the key's value, or the default given.
```js
// interaction/message event
client.usernews.ensure(interaction.guildId, {
  alert: [], // the name of the database, set it as string []
});
```
Now that we're done setting up and checking the data, we will now proceed to the commands and how the alert will activate.
We need here: 
- guildId, userId, the name of the database, .includes , .push & get .parameter.
```js
// /ping
// interaction parameter
const { guild } = interaction;
// now we will check if the user id was on the database if not give the alert message and run the command.
if (!client.dankMemer.get(guild.id, "alert").includes(interaction.user.id)) {
  return interaction.reply({ content: 'Hi' }).then(() => {
      interaction.followUp({ content: `<@${interaction.user.id}>`, embeds: [new EmbedBuilder().setColor(color).setTitle("You have an undread news!").setDescription("Use /news to read it!").setThumbnail("image")] })
  })
  // now we will check if the user id was on the database if yes return the command without alert message
} else if (client.dankMemer.get(guild.id, "alert").includes(interaction.user.id)) {
  return interaction.reply({ content: 'Hi' })
}
```
Now lets make a command that will set the user id in the database.
```js
// /alert
// this will add the user id and guil id of the user who use this command.
client.dankMemer.push('interaction.guild.id, interaction.user.id, "alert"');
interaction.reply({ content: "Hello" })
```
Lets delete the data of all the users in the database.
```js
// /set-news
client.dankMemer.clear()
interaction.reply({ content: "A new news has been set" })
```
## End
- And there ya go you have now created the dank memer alert pop up using enmap!

Invite my bot to see the re-creation of it.
Note that this feature will be out on the next update of my bot.
> [Click here.](https://discord.com/api/oauth2/authorize?client_id=1013477956905091144&permissions=2184563009&scope=applications.commands%20bot)
