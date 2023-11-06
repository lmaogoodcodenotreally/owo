## Preview:
![image](https://github.com/lmaogoodcodenotreally/owo/assets/147619006/4ed67abc-c708-4a01-a0f1-cfe6c6538c49)

## Codeblock
```js
{
  api.id();                                                               // get cid & gid
  let channelId = cid;                                                    // cid defined by api
  await api.typing(channelId);                                            // initial type 
  let message = 'owo buy 100';                                            // msg
  var loop = true;                                                        // set loop
  let count = 0;                                                          // set count 
  while (loop) {
    await api.typing(channelId);                                          // type
    const sentMessage = await api.sendMessage(channelId, message);        // send message
    await api.deleteMessage(channelId, sentMessage.id);                   // delete message
    console.log(` [+]  Bought crate  (#${++count}) `);                    // log 
    await api.typing(channelId);                                          // type
    await api.delay(Math.floor(Math.random() * 500) + 4000);              // default timeout to bypass rate limit for "buy"
    await api.typing(channelId);                                          // type
    const messages = await api.getMessages(channelId);                    // get latest messages
    for (const msg of messages) {
      if (msg.content.includes("captcha")) {       
        console.log("Found 'captcha' message, stopping the loop.");       // bail on captcha + log
        loop = false;
        break;
      }
    }
  }
}
```
