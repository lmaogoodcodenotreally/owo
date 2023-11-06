# Tired of manual buying?

## Preview:
in minutes
![image](https://github.com/lmaogoodcodenotreally/owo/assets/147619006/112ea33a-7f64-481d-b812-9184d28ca226)

![image](https://github.com/lmaogoodcodenotreally/owo/assets/147619006/4ed67abc-c708-4a01-a0f1-cfe6c6538c49)


## Bypassing

- Initial bot detection (captcha v1 for rate limitation / speed)
- Advanced captcha (advanced detection at "owobot.com/captcha")
- You can buy hundreds / thousand items without triggering detection or captcha thanks to the second bypass

## SOURCE 

```js
                                                                          //
{                                                                         //
  api.id();                                                               // initial api call for id (cid & gid)
  let channelId = cid;                                                    // cid from api.id()
  await api.typing(channelId);                                            // initial type
  let message = 'owo buy 100';                                            // def msg
  var loop = true;                                                        // def loop
  let count = 0;                                                          // def count
  let cycleCount = 0;                                                     // def cycle count
                                                                          //
  while (loop) {                                                          // loop
    await api.typing(channelId);                                          // type
    const sentMessage = await api.sendMessage(channelId, message);        // send msg
    await api.deleteMessage(channelId, sentMessage.id);                   // delete msg 
    console.log(` [+]  Bought crate  (#${++count}) `);                    // log
    await api.typing(channelId);                                          // type in cid
    await api.delay(Math.floor(Math.random() * 500) + 4000);              // initial rate limit bypass 1
    await api.typing(channelId);                                          // type in cid
    const messages = await api.getMessages(channelId);                    // define messages to getMessages (api)
                                                                          //
    for (const msg of messages) {                                         // search into messages
      if (msg.content.includes("captcha")) {                              // detect captcha
        console.log("Found 'captcha' message, stopping the loop.");       // log
        loop = false;                                                     // exit loop
        break;                                                            // bail
      }                                                                   //
    }                                                                     //
                                                                          //
    cycleCount++;                                                         //
    if (cycleCount % 10 === 0) {                                          // bot captch bypass 2 
      console.log("Waiting to attempt bypass bot detection...");          // log
      const waitTime = Math.floor(Math.random() * 5000) + 10000;          // def waitTime
      await api.delay(waitTime);                                          // wait for waitTime
    }                                                                     //
  }                                                                       //
}                                                                         //
                                                                          //
```
