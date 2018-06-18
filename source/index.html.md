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

LinkSense authenticates API requests by validating an API key that must be passed with each API call.  We use the built-in HTTP basic authentication scheme supported by most HTTP libraries.  Use your login email as the username and the API key as the password.

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



# Domains

## List Domains

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request GET \
  --url "https://app.linksense.io/api/v1/links"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("GET", "https://app.linksense.io/api/v1/links", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain_url": "my.domain",
    "fallback_url": "http://plyfe.com",
    "invalid_link_url": "http://plyfe.com"
  },
  {
    "domain_url": "testdomain.io",
    "fallback_url": "http://google.com/fallback",
    "invalid_link_url": "http://google.com/invalid_link"
  }
]
```

This endpoint returns a list of domains.

### HTTP Request

`GET https://app.linksense.io/api/links`

## Add a Domain

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Post.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
request.body({"fallback_url":"http://apple.com/fallback2","invalid_link_url": "http://google.com/invalid_link"})
response = http.request(request)
```

```shell
curl --request POST \
  --url https://app.linksense.io/api/v1/domains/testdomain.io \
  --header 'Authorization: emailaddress@mydomain.com:my_api_key' \
  --header 'Content-Type: application/json' \
  --data '{
    "fallback_url": "http://apple.com/fallback2",
    "invalid_link_url": "http://google.com/invalid_link"
}
```

```javascript
var request = new XMLHttpRequest();
request.open("POST", "https://app.linksense.io/api/v1/domains", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
var data = JSON.stringify({"fallback_url":"http://apple.com/fallback2","invalid_link_url": "http://google.com/invalid_link"});
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain_url": "my.domain",
    "fallback_url": "http://plyfe.com",
    "invalid_link_url": "http://plyfe.com"
  },
  {
    "domain_url": "testdomain.io",
    "fallback_url": "http://google.com/fallback",
    "invalid_link_url": "http://google.com/invalid_link"
  }
]
```

This endpoint adds a domain.

### HTTP Request

`POST https://app.linksense.io/api/v1/domains/testdomain.io`

## Update a Domain

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Patch.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
request.body({"fallback_url":"http://apple.com/fallback2","invalid_link_url": "http://google.com/invalid_link"})
response = http.request(request)
```

```shell
curl --request PATCH \
  --url https://app.linksense.io/api/v1/domains/testdomain.io \
  --header 'Authorization: emailaddress@mydomain.com:my_api_key' \
  --header 'Content-Type: application/json' \
  --data '{
    "fallback_url": "http://apple.com/fallback2",
    "invalid_link_url": "http://google.com/invalid_link"
}
```

```javascript
var request = new XMLHttpRequest();
request.open("PATCH", "https://app.linksense.io/api/v1/domains", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
var data = JSON.stringify({"fallback_url":"http://apple.com/fallback2","invalid_link_url": "http://google.com/invalid_link"});
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain_url": "my.domain",
    "fallback_url": "http://plyfe.com",
    "invalid_link_url": "http://plyfe.com"
  },
  {
    "domain_url": "testdomain.io",
    "fallback_url": "http://google.com/fallback",
    "invalid_link_url": "http://google.com/invalid_link"
  }
]
```

This endpoint updates a domain.

### HTTP Request

`PATCH https://app.linksense.io/api/v1/domains/testdomain.io`

## Get a Domain

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains/testdomain.io')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request GET \
  --url https://app.linksense.io/api/v1/domains/testdomain.io \
  --header 'Authorization: emailaddress@mydomain.com:my_api_key' \
  --header 'Content-Type: application/json' \
```

```javascript
var request = new XMLHttpRequest();
request.open("POST", "https://app.linksense.io/api/v1/domains/testdomain.io", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
{
  "domain_url": "testdomain.io",
  "fallback_url": "http://apple.com/fallback2",
  "invalid_link_url": "http://google.com/invalid_link"
}
```

This endpoint gets a domain.

### HTTP Request

`GET https://app.linksense.io/api/v1/domains/testdomain.io`

## Delete a Domain

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains/testdomain.io')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Delete.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request DELETE \
  --url https://app.linksense.io/api/v1/domains/testdomain.io \
  --header 'Authorization: emailaddress@mydomain.com:my_api_key' \
  --header 'Content-Type: application/json' \
```

```javascript
var request = new XMLHttpRequest();
request.open("DELETE", "https://app.linksense.io/api/v1/domains/testdomain.io", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns the following json response:

```json
DELETED
```

This endpoint deletes a domain.

### HTTP Request

`DELETE https://app.linksense.io/api/v1/domains/testdomain.io`

# Links

## Get all links for a domain

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains/my.domain/links')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request GET \
  --url "https://app.linksense.io/api/v1/domains/my.domain/links"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("GET", "https://app.linksense.io/api/v1/domains/my.domain/links", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain_name": "my.domain",
    "slug": "3smrpq",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:20251?&body=STATEHOOD",
    "webhook_url": null,
    "clicks_all_time": 12,
    "tags": [
      "882405"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "zkcxsf",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:77088?&body=JOIN",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "881806"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "fr3n2y",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=Hey%20Bestie!%20Happy%20National%20Best%20Friends%20Day.%20%0D%0AEnjoy%20a%20complimentary%20Infrared%20Wellness%20Pod%20session%20at%20Seattle%20Sun%20because%20you%20deserve%20it.%20Join%20the%20text%20club%20and%20get%20your%20FREE%20session.%20It's%20easy,%20just%20click%20here%20to%20join:%20my.domain/rcjo3u%0D%0A%0D%0AJoin%20today%20and%20you'll%20have%20until%206/30%20to%20redeem%20your%20session.%0D%0A%0D%0ASeattlesuntan.com/locations",
    "webhook_url": null,
    "clicks_all_time": 2089,
    "tags": [
      "875421"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "9iucbj",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=I%20thought%20you%20might%20enjoy%20a%20little%20Rest%20and%20Relaxation%20on%20National%20Best%20Friends%20Day.%20%0D%0AEnjoy%20a%20complimentary%20Infrared%20Body%20Treatment%20at%20Desert%20Sun%20by%20joining%20the%20text%20club.%20Just%20click%20here%20to%20join%20and%20get%20your%20free%20session:%20my.domain/6i8s88%0D%0AJoin%20the%20club%20today%20and%20you'll%20have%20until%206/30%20to%20redeem%20your%20treatment.%0D%0A%0D%0ADesertsuntanning.com/locations%0D%0A%0D%0A",
    "webhook_url": null,
    "clicks_all_time": 2393,
    "tags": [
      "878748"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "rfwld1",
    "type": "simple",
    "type_name": "Simple Link",
    "name": "Test Link",
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": "http://www.google.com/webhook",
    "clicks_all_time": 0,
    "tags": [
      "myawesometag"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "bjfibq",
    "type": "simple",
    "type_name": "Simple Link",
    "name": "Test Link",
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": "http://www.google.com/webhook",
    "clicks_all_time": 0,
    "tags": [
      "myawesometag"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "foobar12",
    "type": "simple",
    "type_name": "Simple Link",
    "name": "Test Link",
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": "http://www.google.com/webhook",
    "clicks_all_time": 0,
    "tags": [
      "myawesometag"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "va40cx",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=It's%20National%20Best%20Friends%20Day,%20let's%20celebrate%20and%20%22SPA%22%20together.%20%0D%0A%0D%0AI%20joined%20the%20Seattle%20Sun%20Light%20Spa%20Text%20Club%20and%20got%20a%20free%20session%20in%20the%20relaxing%20Infrared%20Wellness%20Pod.%20Join%20the%20Text%20Club%20and%20you%20can%20get%20a%20free%20session%20too.%20Just%20click%20here%20to%20join:%20my.domain/azjkvl%0D%0A%0D%0ALet%20me%20know%20when%20you%20get%20ur%20free%20session%20so%20we%20can%20schedule%20our%20spa%20service%20together.%0D%0A",
    "webhook_url": null,
    "clicks_all_time": 19,
    "tags": [
      "875421"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "azjkvl",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:20800?&body=BFDay2Join",
    "webhook_url": null,
    "clicks_all_time": 218,
    "tags": [
      "875421"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "6cbtd7",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=I%20just%20entered%20to%20win%20$500!%20You%20should%20enter%20too!%0D%0A%0D%0AClick%20here%20to%20enter:%20my.domain/ijvcjb",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "881816"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "ijvcjb",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": "Test",
    "fallback_url": "sms:47400?&body=Money",
    "webhook_url": null,
    "clicks_all_time": 1,
    "tags": [
      "881816"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "unrj7c",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=It's%20National%20Best%20Friends%20Day.%20Time%20to%20celebrate!%0D%0AI%20just%20joined%20the%20Desert%20Sun%20Text%20Club%20and%20got%20a%20free%20Infrared%20Body%20Treatment.%20Join%20the%20text%20club%20and%20you%20can%20get%20your%20free%20session%20too.%20Just%20click%20here:%0D%0Amy.domain/6i8s88%0D%0A%0D%0ALet%20me%20know%20when%20you%20get%20your%20free%20session%20so%20we%20can%20schedule%20our%20spa%20service%20together.",
    "webhook_url": null,
    "clicks_all_time": 49,
    "tags": [
      "878748"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "6i8s88",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:77155?&body=BFF2JOIN",
    "webhook_url": null,
    "clicks_all_time": 444,
    "tags": [
      "878748"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "ydtxtf",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=It's%20National%20Best%20Friends%20Day,%20let's%20celebrate%20and%20%22SPA%22%20together.%20%0D%0A%0D%0AI%20joined%20the%20Seattle%20Sun%20Tan%20Text%20Club%20and%20got%20a%20free%20session%20in%20the%20relaxing%20Infrared%20Wellness%20Pod.%20Join%20the%20Text%20Club%20and%20you%20can%20get%20a%20free%20session%20too.%20Just%20click%20here%20to%20join.%20my.domain/rcjo3u%0D%0A%0D%0ALet%20me%20know%20when%20you%20get%20ur%20free%20session%20so%20we%20can%20schedule%20our%20spa%20service%20together.%0D%0A",
    "webhook_url": null,
    "clicks_all_time": 23,
    "tags": [
      "875421"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "v8u0jl",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=It's%20National%20Best%20Friends%20Day,%20let's%20SPA%20together.%20I%20just%20joined%20the%20Seattle%20Sun%20Tan%20Text%20Club%20and%20received%20a%20free%20session%20in%20their%20relaxing%20Infrared%20Wellness%20Pod.%20You%20can%20get%20your%20free%20session%20too%20by%20clicking%20here.%0D%0A%0D%0ALet%20me%20know%20when%20you%20get%20your%20free%20session%20so%20we%20can%20schedule%20our%20spa%20sessions%20together.%0D%0A%0D%0A",
    "webhook_url": null,
    "clicks_all_time": 4,
    "tags": [
      "875421"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "rcjo3u",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:99999?&body=Friends2Join",
    "webhook_url": null,
    "clicks_all_time": 155,
    "tags": [
      "875421"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "zobwvy",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.amazon.com/tc",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "881806",
      "4-test"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "olfttc",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.mycompany.com/login",
    "webhook_url": "http://127.0.0.1:3008/update_link_click",
    "clicks_all_time": 0,
    "tags": [
      "1",
      "17-tatango_2"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "y0aqp4",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.gap.com/browse/category.do?cid=8792&departmentRedirect=true&sop=true&mlink=5058,15109466,HP_Promo_W&clink=15109466#department=136",
    "webhook_url": null,
    "clicks_all_time": 1,
    "tags": [
      "880101",
      "1-fallsale2017"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "iw2ynd",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "1",
      "15-test_clicked"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "1rvveh",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "1",
      "7-fall_sale"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "efvwgf",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "1",
      "15-test_clicked"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "6xoa8g",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "1",
      "7-fall_sale"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "gebhim",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "1",
      "5-link_to_test"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "flh2uk",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "1",
      "7-fall_sale"
    ],
    "rules": []
  }
]
```

This endpoint returns a list of links for a domain.

### HTTP Request

`GET https://app.linksense.io/api/v1/domains/my.domain/links`

## Get a single link

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request GET \
  --url "https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("GET", "https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
{
  "domain_name": "my.domain",
  "slug": "ijvcjb",
  "type": "simple",
  "type_name": "Simple Link",
  "name": null,
  "description": "Test",
  "fallback_url": "sms:47400?&body=Money",
  "webhook_url": null,
  "clicks_all_time": 1,
  "tags": [
    "881816"
  ],
  "rules": []
}
```

This endpoint returns a single link.

### HTTP Request

`GET https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb`

## Update a link

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Put.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
request.body({"domain_name": "my.domain","slug": "ijvcjb","description": "Test","fallback_url": "sms:47400?&body=Money","clicks_all_time": 1,"tags": ["881816"],"rules": []});
response = http.request(request)
```

```shell
curl --request PUT \
  --url "https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
	--data '{
      "domain_name": "my.domain",
      "slug": "ijvcjb",
      "description": "Test",
      "fallback_url": "sms:47400?&body=Money",
      "clicks_all_time": 1,
      "tags": [
          "881816"
      ],
      "rules": []
  }'
```

```javascript
var request = new XMLHttpRequest();
request.open("PUT", "https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
var data = JSON.stringify({"domain_name": "my.domain","slug": "ijvcjb","description": "Test","fallback_url": "sms:47400?&body=Money","clicks_all_time": 1,"tags": ["881816"],"rules": []});
request.send(null);
```

> The above command returns JSON structured like this:

```json
{
  "domain_name": "my.domain",
  "slug": "ijvcjb",
  "type": "simple",
  "type_name": "Simple Link",
  "name": null,
  "description": "Test",
  "fallback_url": "sms:47400?&body=Money",
  "webhook_url": null,
  "clicks_all_time": 1,
  "tags": [
    "881816"
  ],
  "rules": []
}
```

This endpoint updates a link.

### HTTP Request

`PUT https://app.linksense.io/api/v1/domains/my.domain/links/ijvcjb`

## Fetch Link Status

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/stats')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::POST.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
request.body({"links": ["my.domain/va40cx"]});
response = http.request(request)
```

```shell
curl --request POST \
  --url "https://app.linksense.io/api/v1/stats"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
	--data '{
  	"links": [
  		"my.domain/va40cx"
  	]
  }'
```

```javascript
var request = new XMLHttpRequest();
request.open("POST", "https://app.linksense.io/api/v1/stats", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
var data = JSON.stringify({"links": ["my.domain/va40cx"]});
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain": "my.domain",
    "slug": "va40cx",
    "clicks_all_time": 19,
    "clicks_today": 0,
    "clicks_last_7_days": 19,
    "last_30_by_day": {
      "2018-05-11": 0,
      "2018-05-12": 0,
      "2018-05-13": 0,
      "2018-05-14": 0,
      "2018-05-15": 0,
      "2018-05-16": 0,
      "2018-05-17": 0,
      "2018-05-18": 0,
      "2018-05-19": 0,
      "2018-05-20": 0,
      "2018-05-21": 0,
      "2018-05-22": 0,
      "2018-05-23": 0,
      "2018-05-24": 0,
      "2018-05-25": 0,
      "2018-05-26": 0,
      "2018-05-27": 0,
      "2018-05-28": 0,
      "2018-05-29": 0,
      "2018-05-30": 0,
      "2018-05-31": 0,
      "2018-06-01": 0,
      "2018-06-02": 0,
      "2018-06-03": 0,
      "2018-06-04": 0,
      "2018-06-05": 0,
      "2018-06-06": 0,
      "2018-06-07": 1,
      "2018-06-08": 17,
      "2018-06-09": 0,
      "2018-06-10": 1,
      "2018-06-11": 0
    }
  }
]
```

This endpoint fetches a link status.

### HTTP Request

`PUT https://app.linksense.io/api/v1/stats`

## Create a Single Link

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/links')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::POST.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
request.body({"domain_name": "my.domain","slug": "foobar12","description": null,"name": "Test Link","fallback_url": "http://www.google.com","webhook_url": "http://www.google.com/webhook","tags": "myawesometag","rules": []});
response = http.request(request)
```

```shell
curl --request POST \
  --url "https://app.linksense.io/api/v1/links"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
	--data '{
      "domain_name": "my.domain",
      "slug": "foobar12",
      "description": null,
      "name": "Test Link",
      "fallback_url": "http://www.google.com",
      "webhook_url": "http://www.google.com/webhook",
      "tags": "myawesometag",
      "rules": []
  }'
```

```javascript
var request = new XMLHttpRequest();
request.open("POST", "https://app.linksense.io/api/v1/links", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
var data = JSON.stringify({"domain_name": "my.domain","slug": "foobar12","description": null,"name": "Test Link","fallback_url": "http://www.google.com","webhook_url": "http://www.google.com/webhook","tags": "myawesometag","rules": []});
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain_name": "my.domain",
    "slug": "foobar13",
    "type": "simple",
    "type_name": "Simple Link",
    "name": "Test Link",
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": "http://www.google.com/webhook",
    "clicks_all_time": 0,
    "tags": [
      "myawesometag"
    ],
    "rules": []
  }
]
```

This endpoint creates a link.

### HTTP Request

`PUT https://app.linksense.io/api/v1/links`

## Create Multiple Links

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/links/multi')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::POST.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
request.body({"domain_name": "my.domain","count": 2,"description": null,"name": "Test Link","fallback_url": "http://www.google.com","webhook_url": "http://www.google.com/webhook","tags": "myawesometag","rules": []});
response = http.request(request)
```

```shell
curl --request POST \
  --url "https://app.linksense.io/api/v1/links/multi"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
	--data '{
    "domain_name": "my.domain",
    "count": 2,
      "description": null,
      "name": "Test Link",
      "fallback_url": "http://www.google.com",
      "webhook_url": "http://www.google.com/webhook",
      "tags": "myawesometag",
      "rules": []
  }'
```

```javascript
var request = new XMLHttpRequest();
request.open("POST", "https://app.linksense.io/api/v1/links/multi", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
var data = JSON.stringify({"domain_name": "my.domain","count": 2,"description": null,"name": "Test Link","fallback_url": "http://www.google.com","webhook_url": "http://www.google.com/webhook","tags": "myawesometag","rules": []});
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain_name": "my.domain",
    "slug": "qddpyk",
    "type": "simple",
    "type_name": "Simple Link",
    "name": "Test Link",
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": "http://www.google.com/webhook",
    "clicks_all_time": 0,
    "tags": [
      "myawesometag"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "ctz3sy",
    "type": "simple",
    "type_name": "Simple Link",
    "name": "Test Link",
    "description": null,
    "fallback_url": "http://www.google.com",
    "webhook_url": "http://www.google.com/webhook",
    "clicks_all_time": 0,
    "tags": [
      "myawesometag"
    ],
    "rules": []
  }
]
```

This endpoint creates multiple links.

### HTTP Request

`PUT https://app.linksense.io/api/v1/links/multi`

## Delete a Link

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/domains/my.domain/links/foobar13')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::DELETE.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request DELETE \
  --url "https://app.linksense.io/api/v1/domains/my.domain/links/foobar13"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("DELETE", "https://app.linksense.io/api/v1/domains/my.domain/links/foobar13", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
DELETED
```

This endpoint deletes a link.

### HTTP Request

`PUT https://app.linksense.io/api/v1/domains/my.domain/links/foobar13`

# Tags

## List all Tags

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/tags')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request GET \
  --url "https://app.linksense.io/api/v1/tags"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("GET", "https://app.linksense.io/api/v1/tags", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
{
  "clicks_all_time": 0,
  "clicks_today": 0,
  "clicks_last_7_days": 0,
  "last_30_by_day": {
    "2018-05-11": 0,
    "2018-05-12": 0,
    "2018-05-13": 0,
    "2018-05-14": 0,
    "2018-05-15": 0,
    "2018-05-16": 0,
    "2018-05-17": 0,
    "2018-05-18": 0,
    "2018-05-19": 0,
    "2018-05-20": 0,
    "2018-05-21": 0,
    "2018-05-22": 0,
    "2018-05-23": 0,
    "2018-05-24": 0,
    "2018-05-25": 0,
    "2018-05-26": 0,
    "2018-05-27": 0,
    "2018-05-28": 0,
    "2018-05-29": 0,
    "2018-05-30": 0,
    "2018-05-31": 0,
    "2018-06-01": 0,
    "2018-06-02": 0,
    "2018-06-03": 0,
    "2018-06-04": 0,
    "2018-06-05": 0,
    "2018-06-06": 0,
    "2018-06-07": 0,
    "2018-06-08": 0,
    "2018-06-09": 0,
    "2018-06-10": 0,
    "2018-06-11": 0
  },
  "links_count": 0,
  "clicked_links_count": 0
}
```

This endpoint returns a list of all tags.

### HTTP Request

`GET https://app.linksense.io/api/v1/tags`

## Tag Details

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/tags/foo')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request GET \
  --url "https://app.linksense.io/api/v1/tags/foo"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("GET", "https://app.linksense.io/api/v1/tags/foo", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
{
  "clicks_all_time": 0,
  "clicks_today": 0,
  "clicks_last_7_days": 0,
  "last_30_by_day": {
    "2018-05-11": 0,
    "2018-05-12": 0,
    "2018-05-13": 0,
    "2018-05-14": 0,
    "2018-05-15": 0,
    "2018-05-16": 0,
    "2018-05-17": 0,
    "2018-05-18": 0,
    "2018-05-19": 0,
    "2018-05-20": 0,
    "2018-05-21": 0,
    "2018-05-22": 0,
    "2018-05-23": 0,
    "2018-05-24": 0,
    "2018-05-25": 0,
    "2018-05-26": 0,
    "2018-05-27": 0,
    "2018-05-28": 0,
    "2018-05-29": 0,
    "2018-05-30": 0,
    "2018-05-31": 0,
    "2018-06-01": 0,
    "2018-06-02": 0,
    "2018-06-03": 0,
    "2018-06-04": 0,
    "2018-06-05": 0,
    "2018-06-06": 0,
    "2018-06-07": 0,
    "2018-06-08": 0,
    "2018-06-09": 0,
    "2018-06-10": 0,
    "2018-06-11": 0
  },
  "links_count": 0,
  "clicked_links_count": 0
}
```

This endpoint returns the details of a tag.

### HTTP Request

`GET https://app.linksense.io/api/v1/tags/foo`

## List Links for a Tag

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/tags/881816/links')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Get.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request GET \
  --url "https://app.linksense.io/api/v1/tags/881816/links"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("GET", "https://app.linksense.io/api/v1/tags/881816/links", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns JSON structured like this:

```json
[
  {
    "domain_name": "my.domain",
    "slug": "ijvcjb",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": "Test",
    "fallback_url": "sms:47400?&body=Money",
    "webhook_url": null,
    "clicks_all_time": 1,
    "tags": [
      "881816"
    ],
    "rules": []
  },
  {
    "domain_name": "my.domain",
    "slug": "6cbtd7",
    "type": "simple",
    "type_name": "Simple Link",
    "name": null,
    "description": null,
    "fallback_url": "sms:?&body=I%20just%20entered%20to%20win%20$500!%20You%20should%20enter%20too!%0D%0A%0D%0AClick%20here%20to%20enter:%20my.domain/ijvcjb",
    "webhook_url": null,
    "clicks_all_time": 0,
    "tags": [
      "881816"
    ],
    "rules": []
  }
]
```

This endpoint returns the links of a tag.

### HTTP Request

`GET https://app.linksense.io/api/v1/tags/881816/links`

## Delete all Links for a Tag

```ruby
require 'net/http'
require 'uri'

uri = URI.parse('https://app.linksense.io/api/v1/tags/foo/destroy_links')
http = Net::HTTP.new(uri.host, uri.port)
request = Net:HTTP::Delete.new(uri.request_url)
request.basic_auth("emailaddress@mydomain.com", "my_api_key")
response = http.request(request)
```

```shell
curl --request DELETE \
  --url "https://app.linksense.io/api/v1/tags/foo/destroy_links"
	--header "Accept: application/json" \
	--header "Content-Type: application/json" \
	--header 'Authorization: emailaddress@mydomain.com:my_api_key'
```

```javascript
var request = new XMLHttpRequest();
request.open("DELETE", "https://app.linksense.io/api/v1/tags/foo/destroy_links", false);
request.setRequestHeader("Authorization", "Basic " + btoa("emailaddress@mydomain.com:my_api_key"));
request.send(null);
```

> The above command returns a 200 OK response:

This endpoint deletes all links for a tag.

### HTTP Request

`GET https://app.linksense.io/api/v1/tags/foo/destroy_links`
