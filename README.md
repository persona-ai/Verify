# Verify by Persona Developer API
Verify is a tool to automatically detect computer generated text. Verify is intended to be used for online platforms, educational institutions and induviduals building tools to mitigate against fake text.

### Geting Started
To get started with the Verify API, you first must upgrade your account to a pro acccount. This can be done by completing the following steps:

  1. Log into Verify at https://www.persona-ai.com/verify-login
  2. Once logged in, click the side menu in the top right
  3. Select "Upgrade Account"
  4. Follow the payment instructions. Once the payment has been completed, you will now have access to the developer API
  
Note during our research preview, the maximum requests we are serving in 10k a month. If your team needs more requests, please reach out.

### Python Quickstart
To use our API with Python, you can use the following code snippet:

```python
import requests

endpoint = "https://api.persona-ai.com/verify/detect"

params = {"text": "<my text>"}
auth = {"Authorization": "Bearer <key>"}

req = requests.post(endpoint, json=params, headers=auth)
print(req.json())
```

### cURL Quickstart
To use our API via the command line, you can use the following curl command:

```
curl -X POST -H "Authorization: Bearer <key>" -H "Content-Type: application/json" -d '{"text": "<my text>"}' https://api.persona-ai.com/verify/detect
```


### Nodejs Quickstart
To use our API with Nodejs, you can use the following code snippet:

```javascript
const request = require('request');

const endpoint = "https://api.persona-ai.com/verify/detect";
const params = {text: "<my text>"};
const auth = {Authorization: "Bearer <key>"};

request.post(
  {
    url: endpoint,
    json: params,
    headers: auth
  },
  function(error, response, body) {
    if (error) {
      console.error(error);
    } else {
      console.log(body);
    }
  }
);
```

### Parameter Details

The API has the following parameters:

| Parameter | Required | Default | Details |
| --- | --- | --- | --- |
| key | yes | none | The API key from your account. This must be passed as a header |
| text | yes | none | The text to be verified |

### Web Demo

A demo can be found at [https://www.persona-ai.com/verify](https://www.persona-ai.com/verify).

### Response

The API returns the following response:

| Parameter | Details |
| --- | --- |
| status | If a status code of 200 is returned, the request was successful. If a status code of 400 is returned, then the request failed. |
| detection | The labels that determine if the text is human or computer generated. |

An example of a response object would look something like this:

```JSON
{
  "status": "success",
  "detection": [
    {
      "label": "Human Written",
      "score": 0.99
    },
    {
      "label": "Computer Generated",
      "score": 0.01
    }
  ]
}
```

### Accuracy
Currently, we estimate Verify has a 93%-95% accuracy of flagging computer generated text. However, with how quickly the technology is changing, we recommend using the API as a tool, but not as a replacement for human review. There will be instances where Verify performs worse (such as mixed text, small amounts of computer generated text combined with human written text and very short texts).

### Rate Limits
Currently, we have a rate limit of 20 requests per minute in our research preview. If you need an increased rate limit, please contact us.
