
## SOURCE
```js
{
  api.id();
  let channelId = cid;
  await api.typing(channelId);
  let message = 'owo crate';
  var loop = true;
  let count = 0;
  let cycleCount = 0;
  
  while (loop) {
    await api.typing(channelId);
    const sentMessage = await api.sendMessage(channelId, message);
    await api.deleteMessage(channelId, sentMessage.id);
    console.log(` [+]  Bought crate  (#${++count}) `);
    await api.typing(channelId);
    await api.delay(Math.floor(Math.random() * 500) + 4000);
    await api.typing(channelId);
    const messages = await api.getMessages(channelId);

    for (const msg of messages) {
      if (msg.content.includes("captcha")) {
        console.log("Found 'captcha' message, stopping the loop.");
        loop = false;
        break;
      }
    }

    cycleCount++;
    if (cycleCount % 10 === 0) {
      console.log("Waiting to attempt bypass bot detection...");
      const waitTime = Math.floor(Math.random() * 5000) + 10000;
      await api.delay(waitTime);
    }
  }
}

```
