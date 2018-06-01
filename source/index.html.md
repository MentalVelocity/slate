---
title: LinkSense API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

includes:
  - errors

search: true
---
# Before You Start

Welcome to the LinkSense API! The LinkSense API is designed for developers, engineers, or anyone else who's comfortable creating custom-coded solutions or integrating with RESTful APIS.   

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

Need authentication information.

> To authorize, use this code:

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/example-endpoint')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
# With shell, you can just pass the correct email and api key with each request
curl -u emailaddress@mydomain.com:my_api_key https://app.linksense.io/api/v1/example-endpoint
```

```javascript
var request = new XMLHttpRequest();
request.open("POST", "https://app.linksense.io/api/v1/example-endpoint", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> Make sure to replace `my_api_key` with your API key, which can be obtained by logging into <a href="https://app.linksense.io/" target="_blank">https://app.linksense.io</a>.

LinkSense authenticates API requests by validating an API key that must be passed with each API call.  We use the built-in HTTP basic authentication scheme supported by most HTTP libraries.  Use your login email as the username and the API key as the password.



# Links

## Get Current Account

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/links')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl "https://app.linksense.io/api/v1/links" -X GET \
	-H "Accept: application/json" \
	-H "Content-Type: application/json" \
	-u emailaddress@mydomain.com:my_api_key \
	-H "Host: example.org" \
	-H "Cookie: "
```

```javascript
var request = new XMLHttpRequest();
request.open("GET", "https://app.linksense.io/api/v1/links", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json

```

This endpoint creates links.

### HTTP Request

`GET https://app.linksense.io/api/links`

