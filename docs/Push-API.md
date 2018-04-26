# Push API

## Set up webhooks in your sipgate account

### Create a sipgate account

To begin developing applications using webhooks you first need to create a sigpgate account. There are different types of accounts: basic, simquadrat and team. All are slightly different but offer webhooks functionality. For the following examples we choose [sipgate basic](https://www.sipgatebasic.co.uk) because it's free (as in beer).

### Book sipgate.io

We will now show you how to book sipgate.io using the Feature Store.

![Book sipgate.io](./img/configure-sipgate-io-step1.png)

Log into your shiny, new sipgate account and go to the Feature Store. You can find a link in the navigation.

![Within the Feature Store click on the sipgate.io feature. It should look like this.](./img/configure-sipgate-io-step2.png)

Within the Feature Store click on the sipgate.io feature. It should look like this.

![Click on the orange button to book the free feature and follow the confirmation process.](./img/configure-sipgate-io-step3.png)

Click on the orange button to book the free feature and follow the confirmation process.

### Enable webhooks

We will now show you how to configure your URLs.

![Navigate to the sipgate.io category and click on "Incoming calls" or "Outgoing calls".](./img/configure-sipgate-io-step4.png)

Navigate to the sipgate.io category and click on "Incoming calls" or "Outgoing calls"

![Enter your URL and hit "Save".](./img/configure-sipgate-io-step5.png)

Enter your URL and hit "Save".


## API Reference & Examples

https://github.com/sipgate/sipgate.io

## Troubleshooting

---
title: "Troubleshooting"
excerpt: ""
---
Enable debug log
==============

You can enable logging for debugging purposes from your dashboard. You will find each request and the corresponding response in the logging table.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c46ea71-debug-sipgate-io-step1.png",
        "debug-sipgate-io-step1.png",
        1920,
        948,
        "#1c242c"
      ],
      "caption": "Click on \"Activate debug log\", read and confirm the security warning."
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/aee6e20-debug-sipgate-io-step3.png",
        "debug-sipgate-io-step3.png",
        1920,
        946,
        "#1c242c"
      ],
      "caption": "To view the logged requests, click on the icon within the \"Activate debug log\" row."
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/272c904-debug-sipgate-io-step3.png",
        "debug-sipgate-io-step3.png",
        1920,
        939,
        "#cccdce"
      ],
      "caption": "Your request should be logged and look like this."
    }
  ]
}
[/block]
Inspect incoming network traffic
========================

You can use `ngrep` to inspect incoming requests 
```shell
sudo ngrep -dany -Wbyline port 3000
```

The output should look like this
```
###
T 10.42.42.42:42528 -> 10.42.42.23:3000 [AP]
POST / HTTP/1.1.
Accept: application/xml, text/plain, text/html.
Accept-Charset: utf-8.
User-Agent: sipgate.io.
X-SIPGATE-JOBS: http://www.sipgate.de/jobs.
Content-Length: 84.
Content-Type: application/x-www-form-urlencoded; charset=UTF-8.
Accept-Encoding: gzip,deflate.
Host: gwen.fuglu.net:3000.
Via: 1.1 localhost (squid/3.1.20).
X-Forwarded-For: 217.10.77.113.
Cache-Control: max-age=259200.
Connection: keep-alive.
.

##
T 10.42.42.42:42528 -> 10.42.42.23:3000 [AP]
event=newCall&direction=in&from=anonymous&to=445603000514&callId=4932215337270853042
##
T 10.42.42.23:3000 -> 10.42.42.42:42528 [AP]
HTTP/1.1 200 OK.
X-Powered-By: Express.
Content-Type: application/xml; charset=utf-8.
Content-Length: 46.
Date: Tue, 23 May 2017 11:27:11 GMT.
Connection: keep-alive.
.
<Response><Dial><Voicemail/></Dial></Response>
#
``` 
