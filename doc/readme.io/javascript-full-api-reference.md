---
category: 5ae0c2c9fa0ec6000345c0ac
title: JavaScript Full API Reference
---


# mixpanel


<hr>
## mixpanel.init
This function initializes a new instance of the Mixpanel tracking object. 
All new instances are added to the main mixpanel object as sub properties (such as 
mixpanel.library_name) and also returned by this function. To define a 
second instance on the page, you would call:

```javascript
mixpanel.init('new token', { your: 'config' }, 'library_name');

```
and use it like so:

```javascript
mixpanel.library_name.track(...);
```



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **token** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | Your Mixpanel API token |
| **config** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | A dictionary of config options to override. <a href="https://github.com/mixpanel/mixpanel-js/blob/8b2e1f7b/src/mixpanel-core.js#L87-L110">See a list of default config options</a>. |
| **name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-optional">optional</span> | The name for the new mixpanel instance that you want created |


<hr>
## mixpanel.push
push() keeps the standard async-array-push 
behavior around after the lib is loaded. 
This is only useful for external integrations that 
do not wish to rely on our convenience methods 
(created in the snippet).

### Usage:

```javascript
mixpanel.push(['register', { a: 'b' }]);
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **item** | <span class="mp-arg-type">Array</span></br></span><span class="mp-arg-required">required</span> | A [function_name, args...] array to be executed |


<hr>
## mixpanel.disable
Disable events on the Mixpanel object. If passed no arguments, 
this function disables tracking of any event. If passed an 
array of event names, those events will be disabled, but other 
events will continue to be tracked.
Note: this function does not stop other mixpanel functions from 
firing, such as register() or people.set().



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **events** | <span class="mp-arg-type">Array</span></br></span><span class="mp-arg-optional">optional</span> | An array of event names to disable |


<hr>
## mixpanel.track
Track an event. This is the most important and 
frequently used Mixpanel function.

### Usage:

```javascript
// track an event named 'Registered'
mixpanel.track('Registered', {'Gender': 'Male', 'Age': 21});

```
To track link clicks or form submissions, see track_links() or track_forms().


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **event_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | The name of the event. This can be anything the user does - 'Button Click', 'Sign Up', 'Item Purchased', etc. |
| **properties** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | A set of properties to include with the event you're sending. These describe the user who did the event or details about the event itself. |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback function will be called after tracking the event. |


<hr>
## mixpanel.set_group
Register the current user into one/many groups.

### Usage:

```javascript
 mixpanel.set_group('company', ['mixpanel', 'google']) // an array of IDs
 mixpanel.set_group('company', 'mixpanel')
 mixpanel.set_group('company', 128746312)
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **group_key** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | Group key |
| **group_ids** | <span class="mp-arg-type">Array or String or Number</span></br></span><span class="mp-arg-required">required</span> | An array of group IDs, or a singular group ID |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.add_group
Add a new group for this user.

### Usage:

```javascript
 mixpanel.add_group('company', 'mixpanel')
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **group_key** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | Group key |
| **group_id** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-required">required</span> | A valid Mixpanel property type |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.remove_group
Remove a group from this user.

### Usage:

```javascript
 mixpanel.remove_group('company', 'mixpanel')
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **group_key** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | Group key |
| **group_id** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-required">required</span> | A valid Mixpanel property type |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.track_with_groups
Track an event with specific groups.

### Usage:

```javascript
 mixpanel.track_with_groups('purchase', {'product': 'iphone'}, {'University': ['UCB', 'UCLA']})
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **query** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> |  |
| **event_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> |  |
| **properties** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-required">required</span> |  |
| **groups** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-required">required</span> |  |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.get_group
Look up reference to a Mixpanel group

### Usage:

```javascript
  mixpanel.get_group(group_key, group_id)
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **group_key** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | Group key |
| **group_id** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-required">required</span> | A valid Mixpanel property type |


<hr>
## mixpanel.track_links
Track clicks on a set of document elements. Selector must be a 
valid query. Elements must exist on the page at the time track_links is called.

### Usage:

```javascript
// track click for link id #nav
mixpanel.track_links('#nav', 'Clicked Nav Link');

```

### Notes:
This function will wait up to 300 ms for the Mixpanel 
servers to respond. If they have not responded by that time 
it will head to the link without ensuring that your event 
has been tracked.  To configure this timeout please see the 
set_config() documentation below.
If you pass a function in as the properties argument, the 
function will receive the DOMElement that triggered the 
event as an argument.  You are expected to return an object 
from the function; any properties defined on this object 
will be sent to mixpanel as event properties.

| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **query** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | A valid DOM query, element or jQuery-esque list |
| **event_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | The name of the event to track |
| **properties** | <span class="mp-arg-type">Object or Function</span></br></span><span class="mp-arg-optional">optional</span> | A properties object or function that returns a dictionary of properties when passed a DOMElement |


<hr>
## mixpanel.track_forms
Track form submissions. Selector must be a valid query.

### Usage:

```javascript
// track submission for form id 'register'
mixpanel.track_forms('#register', 'Created Account');

```

### Notes:
This function will wait up to 300 ms for the mixpanel 
servers to respond, if they have not responded by that time 
it will head to the link without ensuring that your event 
has been tracked.  To configure this timeout please see the 
set_config() documentation below.
If you pass a function in as the properties argument, the 
function will receive the DOMElement that triggered the 
event as an argument.  You are expected to return an object 
from the function; any properties defined on this object 
will be sent to mixpanel as event properties.

| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **query** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | A valid DOM query, element or jQuery-esque list |
| **event_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | The name of the event to track |
| **properties** | <span class="mp-arg-type">Object or Function</span></br></span><span class="mp-arg-optional">optional</span> | This can be a set of properties, or a function that returns a set of properties after being passed a DOMElement |


<hr>
## mixpanel.time_event
Time an event by including the time between this call and a 
later 'track' call for the same event in the properties sent 
with the event.

### Usage:

```javascript
// time an event named 'Registered'
mixpanel.time_event('Registered');
mixpanel.track('Registered', {'Gender': 'Male', 'Age': 21});

```
When called for a particular event name, the next track call for that event 
name will include the elapsed time between the 'time_event' and 'track' 
calls. This value is stored as seconds in the '$duration' property.


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **event_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | The name of the event. |


<hr>
## mixpanel.register
Register a set of super properties, which are included with all 
events. This will overwrite previous super property values.

### Usage:

```javascript
// register 'Gender' as a super property
mixpanel.register({'Gender': 'Female'});

// register several super properties when a user signs up
mixpanel.register({
    'Email': 'jdoe@example.com',
    'Account Type': 'Free'
});
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **properties** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-required">required</span> | An associative array of properties to store about the user |
| **days** | <span class="mp-arg-type">Number</span></br></span><span class="mp-arg-optional">optional</span> | How many days since the user's last visit to store the super properties |


<hr>
## mixpanel.register_once
Register a set of super properties only once. This will not 
overwrite previous super property values, unlike register().

### Usage:

```javascript
// register a super property for the first time only
mixpanel.register_once({
    'First Login Date': new Date().toISOString()
});

```

### Notes:
If default_value is specified, current super properties 
with that value will be overwritten.

| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **properties** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-required">required</span> | An associative array of properties to store about the user |
| **default_value** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | Value to override if already set in super properties (ex: 'False') Default: 'None' |
| **days** | <span class="mp-arg-type">Number</span></br></span><span class="mp-arg-optional">optional</span> | How many days since the users last visit to store the super properties |


<hr>
## mixpanel.unregister
Delete a super property stored with the current user.



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **property** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | The name of the super property to remove |


<hr>
## mixpanel.identify
Identify a user with a unique ID instead of a Mixpanel 
randomly generated distinct_id. If the method is never called, 
then unique visitors will be identified by a UUID generated 
the first time they visit the site.


### Notes:
You can call this function to overwrite a previously set 
unique ID for the current user. Mixpanel cannot translate 
between IDs at this time, so when you change a user's ID 
they will appear to be a new user.
When used alone, mixpanel.identify will change the user's 
distinct_id to the unique ID provided. When used in tandem 
with mixpanel.alias, it will allow you to identify based on 
unique ID and map that back to the original, anonymous 
distinct_id given to the user upon her first arrival to your 
site (thus connecting anonymous pre-signup activity to 
post-signup activity). Though the two work together, do not 
call identify() at the same time as alias(). Calling the two 
at the same time can cause a race condition, so it is best 
practice to call identify on the original, anonymous ID 
right after you've aliased it. 
<a href="https://mixpanel.com/help/questions/articles/how-should-i-handle-my-user-identity-with-the-mixpanel-javascript-library">Learn more about how mixpanel.identify and mixpanel.alias can be used</a>.

| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **unique_id** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-optional">optional</span> | A string that uniquely identifies a user. If not provided, the distinct_id currently in the persistent store (cookie or localStorage) will be used. |


<hr>
## mixpanel.reset
Clears super properties and generates a new random distinct_id for this instance. 
Useful for clearing data when a user logs out.




<hr>
## mixpanel.get_distinct_id
Returns the current distinct id of the user. This is either the id automatically 
generated by the library or the id that has been passed by a call to identify().


### Notes:
get_distinct_id() can only be called after the Mixpanel library has finished loading. 
init() has a loaded function available to handle this automatically. For example:

```javascript
// set distinct_id after the mixpanel library has loaded
mixpanel.init('YOUR PROJECT TOKEN', {
    loaded: function(mixpanel) {
        distinct_id = mixpanel.get_distinct_id();
    }
});
```


<hr>
## mixpanel.alias
Create an alias, which Mixpanel will use to link two distinct_ids going forward (not retroactively). 
Multiple aliases can map to the same original ID, but not vice-versa. Aliases can also be chained - the 
following is a valid scenario:

```javascript
mixpanel.alias('new_id', 'existing_id');
...
mixpanel.alias('newer_id', 'new_id');

```
If the original ID is not passed in, we will use the current distinct_id - probably the auto-generated GUID.


### Notes:
The best practice is to call alias() when a unique ID is first created for a user 
(e.g., when a user first registers for an account and provides an email address). 
alias() should never be called more than once for a given user, except to 
chain a newer ID to a previously new ID, as described above.

| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **alias** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | A unique identifier that you want to use for this user in the future. |
| **original** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-optional">optional</span> | The current identifier being used for this user. |


<hr>
## mixpanel.set_config
Update the configuration of a mixpanel library instance.
The default config is:

```javascript
{
  // super properties cookie expiration (in days)
  cookie_expiration: 365

  // super properties span subdomains
  cross_subdomain_cookie: true

  // debug mode
  debug: false

  // if this is true, the mixpanel cookie or localStorage entry
  // will be deleted, and no user persistence will take place
  disable_persistence: false

  // if this is true, Mixpanel will automatically determine
  // City, Region and Country data using the IP address of
  //the client
  ip: true

  // opt users out of tracking by this Mixpanel instance by default
  opt_out_tracking_by_default: false

  // opt users out of browser data storage by this Mixpanel instance by default
  opt_out_persistence_by_default: false

  // persistence mechanism used by opt-in/opt-out methods - cookie
  // or localStorage - falls back to cookie if localStorage is unavailable
  opt_out_tracking_persistence_type: 'localStorage'

  // customize the name of cookie/localStorage set by opt-in/opt-out methods
  opt_out_tracking_cookie_prefix: null

  // type of persistent store for super properties (cookie/
  // localStorage) if set to 'localStorage', any existing
  // mixpanel cookie value with the same persistence_name
  // will be transferred to localStorage and deleted
  persistence: 'cookie'

  // name for super properties persistent store
  persistence_name: ''

  // names of properties/superproperties which should never
  // be sent with track() calls
  property_blacklist: []

  // if this is true, mixpanel cookies will be marked as
  // secure, meaning they will only be transmitted over https
  secure_cookie: false

  // the amount of time track_links will
  // wait for Mixpanel's servers to respond
  track_links_timeout: 300

  // should we track a page view on page load
  track_pageview: true

  // if you set upgrade to be true, the library will check for
  // a cookie from our old js library and import super
  // properties from it, then the old cookie is deleted
  // The upgrade config option only works in the initialization,
  // so make sure you set it when you create the library.
  upgrade: false

  // extra HTTP request headers to set for each API request, in
  // the format {'Header-Name': value}
  xhr_headers: {}

  // protocol for fetching in-app message resources, e.g.
  // 'https://' or 'http://'; defaults to '//' (which defers to the
  // current page's protocol)
  inapp_protocol: '//'

  // whether to open in-app message link in new tab/window
  inapp_link_new_window: false
}
```



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **config** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-required">required</span> | A dictionary of new configuration values to update |


<hr>
## mixpanel.get_config
returns the current config object for the library.




<hr>
## mixpanel.get_property
Returns the value of the super property named property_name. If no such 
property is set, get_property() will return the undefined value.


### Notes:
get_property() can only be called after the Mixpanel library has finished loading. 
init() has a loaded function available to handle this automatically. For example:

```javascript
// grab value for 'user_id' after the mixpanel library has loaded
mixpanel.init('YOUR PROJECT TOKEN', {
    loaded: function(mixpanel) {
        user_id = mixpanel.get_property('user_id');
    }
});
```

| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **property_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | The name of the super property you want to retrieve |


<hr>
## mixpanel.opt_in_tracking
Opt the user in to data tracking and cookies/localstorage for this Mixpanel instance



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **options** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | A dictionary of config options to override |
| **options.track** | <span class="mp-arg-type">function</span></br></span><span class="mp-arg-optional">optional</span> | Function used for tracking a Mixpanel event to record the opt-in action (default is this Mixpanel instance's track method) |
| **options.track_event_name=$opt_in** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Event name to be used for tracking the opt-in action |
| **options.track_properties** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | Set of properties to be tracked along with the opt-in action |
| **options.enable_persistence=true** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | If true, will re-enable sdk persistence |
| **options.persistence_type=localStorage** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Persistence mechanism used - cookie or localStorage - falls back to cookie if localStorage is unavailable |
| **options.cookie_prefix=__mp_opt_in_out** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Custom prefix to be used in the cookie/localstorage name |
| **options.cookie_expiration** | <span class="mp-arg-type">Number</span></br></span><span class="mp-arg-optional">optional</span> | Number of days until the opt-in cookie expires (overrides value specified in this Mixpanel instance's config) |
| **options.cross_subdomain_cookie** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | Whether the opt-in cookie is set as cross-subdomain or not (overrides value specified in this Mixpanel instance's config) |
| **options.secure_cookie** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | Whether the opt-in cookie is set as secure or not (overrides value specified in this Mixpanel instance's config) |


<hr>
## mixpanel.opt_out_tracking
Opt the user out of data tracking and cookies/localstorage for this Mixpanel instance



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **options** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | A dictionary of config options to override |
| **options.delete_user=true** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | If true, will delete the currently identified user's profile and clear all charges after opting the user out |
| **options.clear_persistence=true** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | If true, will delete all data stored by the sdk in persistence |
| **options.persistence_type=localStorage** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Persistence mechanism used - cookie or localStorage - falls back to cookie if localStorage is unavailable |
| **options.cookie_prefix=__mp_opt_in_out** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Custom prefix to be used in the cookie/localstorage name |
| **options.cookie_expiration** | <span class="mp-arg-type">Number</span></br></span><span class="mp-arg-optional">optional</span> | Number of days until the opt-in cookie expires (overrides value specified in this Mixpanel instance's config) |
| **options.cross_subdomain_cookie** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | Whether the opt-in cookie is set as cross-subdomain or not (overrides value specified in this Mixpanel instance's config) |
| **options.secure_cookie** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | Whether the opt-in cookie is set as secure or not (overrides value specified in this Mixpanel instance's config) |


<hr>
## mixpanel.has_opted_in_tracking
Check whether the user has opted in to data tracking and cookies/localstorage for this Mixpanel instance



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **options** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | A dictionary of config options to override |
| **options.persistence_type=localStorage** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Persistence mechanism used - cookie or localStorage - falls back to cookie if localStorage is unavailable |
| **options.cookie_prefix=__mp_opt_in_out** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Custom prefix to be used in the cookie/localstorage name |


<hr>
## mixpanel.has_opted_out_tracking
Check whether the user has opted out of data tracking and cookies/localstorage for this Mixpanel instance



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **options** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | A dictionary of config options to override |
| **options.persistence_type=localStorage** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Persistence mechanism used - cookie or localStorage - falls back to cookie if localStorage is unavailable |
| **options.cookie_prefix=__mp_opt_in_out** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Custom prefix to be used in the cookie/localstorage name |


<hr>
## mixpanel.clear_opt_in_out_tracking
Clear the user's opt in/out status of data tracking and cookies/localstorage for this Mixpanel instance



| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **options** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | A dictionary of config options to override |
| **options.enable_persistence=true** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | If true, will re-enable sdk persistence |
| **options.persistence_type=localStorage** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Persistence mechanism used - cookie or localStorage - falls back to cookie if localStorage is unavailable |
| **options.cookie_prefix=__mp_opt_in_out** | <span class="mp-arg-type">string</span></br></span><span class="mp-arg-optional">optional</span> | Custom prefix to be used in the cookie/localstorage name |
| **options.cookie_expiration** | <span class="mp-arg-type">Number</span></br></span><span class="mp-arg-optional">optional</span> | Number of days until the opt-in cookie expires (overrides value specified in this Mixpanel instance's config) |
| **options.cross_subdomain_cookie** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | Whether the opt-in cookie is set as cross-subdomain or not (overrides value specified in this Mixpanel instance's config) |
| **options.secure_cookie** | <span class="mp-arg-type">boolean</span></br></span><span class="mp-arg-optional">optional</span> | Whether the opt-in cookie is set as secure or not (overrides value specified in this Mixpanel instance's config) |



# mixpanel.people


<hr>
## mixpanel.people.set
Set properties on a user record.

### Usage:

```javascript
mixpanel.people.set('gender', 'm');

// or set multiple properties at once
mixpanel.people.set({
    'Company': 'Acme',
    'Plan': 'Premium',
    'Upgrade date': new Date()
});
// properties can be strings, integers, dates, or lists
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **prop** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and values. |
| **to** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | A value to set on the given property name |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.set_once
Set properties on a user record, only if they do not yet exist. 
This will not overwrite previous people property values, unlike 
people.set().

### Usage:

```javascript
mixpanel.people.set_once('First Login Date', new Date());

// or set multiple properties at once
mixpanel.people.set_once({
    'First Login Date': new Date(),
    'Starting Plan': 'Premium'
});

// properties can be strings, integers or dates
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **prop** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and values. |
| **to** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | A value to set on the given property name |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.unset
Unset properties on a user record (permanently removes the properties and their values from a profile).

### Usage:

```javascript
mixpanel.people.unset('gender');

// or unset multiple properties at once
mixpanel.people.unset(['gender', 'Company']);
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **prop** | <span class="mp-arg-type">Array or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an array, this is a list of property names. |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.increment
Increment/decrement numeric people analytics properties.

### Usage:

```javascript
mixpanel.people.increment('page_views', 1);

// or, for convenience, if you're just incrementing a counter by
// 1, you can simply do
mixpanel.people.increment('page_views');

// to decrement a counter, pass a negative number
mixpanel.people.increment('credits_left', -1);

// like mixpanel.people.set(), you can increment multiple
// properties at once:
mixpanel.people.increment({
    counter1: 1,
    counter2: 6
});
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **prop** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and numeric values. |
| **by** | <span class="mp-arg-type">Number</span></br></span><span class="mp-arg-optional">optional</span> | An amount to increment the given property |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.append
Append a value to a list-valued people analytics property.

### Usage:

```javascript
// append a value to a list, creating it if needed
mixpanel.people.append('pages_visited', 'homepage');

// like mixpanel.people.set(), you can append multiple
// properties at once:
mixpanel.people.append({
    list1: 'bob',
    list2: 123
});
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **list_name** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and values. |
| **value** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | value An item to append to the list |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.remove
Remove a value from a list-valued people analytics property.

### Usage:

```javascript
mixpanel.people.remove('School', 'UCB');
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **list_name** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and values. |
| **value** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | value Item to remove from the list |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.union
Merge a given list with a list-valued people analytics property, 
excluding duplicate values.

### Usage:

```javascript
// merge a value to a list, creating it if needed
mixpanel.people.union('pages_visited', 'homepage');

// like mixpanel.people.set(), you can append multiple
// properties at once:
mixpanel.people.union({
    list1: 'bob',
    list2: 123
});

// like mixpanel.people.append(), you can append multiple
// values to the same list:
mixpanel.people.union({
    list1: ['bob', 'billy']
});
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **list_name** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and values. |
| **value** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | Value / values to merge with the given property |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.track_charge
Record that you have charged the current user a certain amount 
of money. Charges recorded with track_charge() will appear in the 
Mixpanel revenue report.

### Usage:

```javascript
// charge a user $50
mixpanel.people.track_charge(50);

// charge a user $30.50 on the 2nd of january
mixpanel.people.track_charge(30.50, {
    '$time': new Date('jan 1 2012')
});
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **amount** | <span class="mp-arg-type">Number</span></br></span><span class="mp-arg-required">required</span> | The amount of money charged to the current user |
| **properties** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-optional">optional</span> | An associative array of properties associated with the charge |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called when the server responds |


<hr>
## mixpanel.people.clear_charges
Permanently clear all revenue report transactions from the 
current user's people analytics profile.

### Usage:

```javascript
mixpanel.people.clear_charges();
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.people.delete_user
Permanently deletes the current people analytics profile from 
Mixpanel (using the current distinct_id).

### Usage:

```javascript
// remove the all data you have stored about the current user
mixpanel.people.delete_user();
```




# mixpanel.group


<hr>
## mixpanel.group.set
Set properties on a group.

### Usage:

```javascript
mixpanel.get_group('company', 'mixpanel').set('Location', '405 Howard');

// or set multiple properties at once
mixpanel.get_group('company', 'mixpanel').set({
     'Location': '405 Howard',
     'Founded' : 2009,
});
// properties can be strings, integers, dates, or lists
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **prop** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and values. |
| **to** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | A value to set on the given property name |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.group.set_once
Set properties on a group, only if they do not yet exist. 
This will not overwrite previous group property values, unlike 
group.set().

### Usage:

```javascript
mixpanel.get_group('company', 'mixpanel').set_once('Location', '405 Howard');

// or set multiple properties at once
mixpanel.get_group('company', 'mixpanel').set_once({
     'Location': '405 Howard',
     'Founded' : 2009,
});
// properties can be strings, integers, lists or dates
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **prop** | <span class="mp-arg-type">Object or String</span></br></span><span class="mp-arg-required">required</span> | If a string, this is the name of the property. If an object, this is an associative array of names and values. |
| **to** | <span class="mp-arg-type"></span></br></span><span class="mp-arg-optional">optional</span> | A value to set on the given property name |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.group.unset
Unset properties on a group permanently.

### Usage:

```javascript
mixpanel.get_group('company', 'mixpanel').unset('Founded');
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **prop** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | The name of the property. |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.group.union
Merge a given list with a list-valued group property, excluding duplicate values.

### Usage:

```javascript
// merge a value to a list, creating it if needed
mixpanel.get_group('company', 'mixpanel').union('Location', ['San Francisco', 'London']);
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **list_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | Name of the property. |
| **values** | <span class="mp-arg-type">Array</span></br></span><span class="mp-arg-required">required</span> | Values to merge with the given property |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


<hr>
## mixpanel.group.remove
Remove a property from a group. The value will be ignored if doesn't exist.

### Usage:

```javascript
mixpanel.get_group('company', 'mixpanel').remove('Location', 'London');
```


| Argument | Type | Description |
| ------------- | ------------- | ----- |
| **list_name** | <span class="mp-arg-type">String</span></br></span><span class="mp-arg-required">required</span> | Name of the property. |
| **value** | <span class="mp-arg-type">Object</span></br></span><span class="mp-arg-required">required</span> | Value to remove from the given group property |
| **callback** | <span class="mp-arg-type">Function</span></br></span><span class="mp-arg-optional">optional</span> | If provided, the callback will be called after the tracking event |


