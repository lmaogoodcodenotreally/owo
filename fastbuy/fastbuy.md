![image](https://github.com/lmaogoodcodenotreally/owo/assets/147619006/4ed67abc-c708-4a01-a0f1-cfe6c6538c49)

## Codeblock
```js
{
  api.id();
  let channelId = cid;
  await api.typing(channelId);
  let message = 'owo buy 100';
  var loop = true;
  let count = 0;
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
  }
}
```
