# Twilio.AspNet

[![Build status](https://ci.appveyor.com/api/projects/status/813hnjynh8ncamwj?svg=true)](https://ci.appveyor.com/project/TwilioAPI/twilio-aspnet)

Twilio tools for ASP.NET MVC 3-5 for use with v5.x of the Twilio helper library.

The plan is to support ASP.NET Core soon.

## Twilio.AspNet.Mvc

### Requirements

Requires .NET 4.5.1 or later with ASP.NET MVC 3-5.

### Installation

```
Install-Package Twilio.AspNet.Mvc
```

### Incoming SMS

```c#
using Twilio.AspNet.Common;
using Twilio.AspNet.Mvc;
using Twilio.TwiML;

namespace WebApplication23.Controllers
{
    public class SmsController : TwilioController
    {
        // GET: Sms
        public TwiMLResult Index(SmsRequest request)
        {
            var response = new MessagingResponse();
            response.Message(
                $"Hey there {request.From}! " +
                "How 'bout those Seahawks?"
            );
            return TwiML(response);
        }
    }
}
```

### Incoming Voice Call

```c#
using Twilio.AspNet.Common;
using Twilio.AspNet.Mvc;
using Twilio.TwiML;

namespace WebApplication23.Controllers
{
    public class VoiceController : TwilioController
    {
        // GET: Voice
        public TwiMLResult Index(VoiceRequest request)
        {
            var response = new VoiceResponse();
            response.Say($"Welcome. Are you from {request.FromCity}?");
            return TwiML(response);
        }
    }
}
```
