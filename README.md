# Smart-Contract-SlackBot
Slack ChatBot to post into the channel whenever anybody posts a fake ETH address.

!["Bot Demo"](https://s3-ap-southeast-2.amazonaws.com/media.canya.tech/SlackBotDemo.png "Bot Demo")

This is based on the excellent guide by Rigel Di Scala - https://chatbotslife.com/write-a-serverless-slack-chat-bot-using-aws-e2d2432c380e

For a really powerful alternative, check out https://github.com/PhABC/antiScamBot_slack

Note: Slack rate limits to 5000 events per hour, so if you have busy channels some might not get to the bot.


# Instructions

You have a choice: *Bot Events* (attach to specific channels), or *Workspace Events* (monitor all channels in your team).  Note: You can not monitor direct messages between users. But you can monitor public & private channels.

Follow the guide above. If you use Workspace Events, there is no need to set up a bot name.
Instead of IM messages in the guide, you want to register for *message.channels* and *message.groups* Events.

Post the python script into Lambda. It already has the authentication bit at the start.  

*Note:*  Slack requires that your endpoint return 200 OK within 3 seconds. We are posting an IM using the Slack postMessage API endpoint before returning 200. This works fine but any extra workload and we should really make this async.

