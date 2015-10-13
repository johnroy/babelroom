# REST API #

The REST API is documented on http://docs.babelroom.apiary.io/
## [Click Here](http://docs.babelroom.apiary.io/) ##

This service allows an interactive exploration of the API along with auto-generation of client code in various languages, user comments and also the ability to execute live API calls to explore request / response details.

The examples in the API documentation refer to user 3 (apitest@example.com), their associated user data, account and conference. This data is populated by default on BabelRoom servers.

Some of the documentation is hand-written but much is automatically generated from the core IDL of data-structures.

We'll be expanding the API and it's documentation considerable over time as it's a core feature.

## Authentication ##
BabelRoom allows 2 methods to authenticate:
  1. A cookie based session id established via the _login_ API call **-AND-**
  1. A basic authentication scheme based off the API Key.
For security clients and servers should use SSL, or run on a VPN so the sessions and keys are not intercepted.

### Cookie Session ###
A browser temporary cookie is set after a successful call to the [login API](http://docs.babelroom.apiary.io/#post-%2Fapi%2Fv1%2Flogin). This cookie allows access as that logged-in user until the browser is closed.

### Basic Auth ###
An API access key can be generated here http://my.babelroom.com/home?nav=api. Adjust the URL accordingly for private servers.

To use the API key in http basic authentication, use the API key as username, there is no password (empty/blank). Refer to http://en.wikipedia.org/wiki/Basic_access_authentication#Client_side or google for other information sources. Where instructions require "`username:password`" you should use "`<your API Key>:`"