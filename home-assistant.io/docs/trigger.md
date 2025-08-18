---
title: "Trigger"
source_url: "https://www.home-assistant.io/docs/automation/trigger"
crawled_date: "2025-08-18"
domain: "home-assistant.io"
categories:
  - home-assistant-io
  - documentation
  - docs
tags:
  - documentation
  - scraped
---

# Trigger

> **Source:** [https://www.home-assistant.io/docs/automation/trigger](https://www.home-assistant.io/docs/automation/trigger)  
> **Domain:** home-assistant.io  
> **Last Updated:** 2025-08-18

Triggers are what starts the processing of an automationAutomations in Home
Assistant allow you to automatically respond to things that happen in and around
your home. rule. When of the automation’s triggers becomes true (trigger ), Home
Assistant will validate the , if any, and call the .

An automationAutomations in Home Assistant allow you to automatically respond to
things that happen in and around your home. can be triggered by an eventEvery
time something happens in Home Assistant, an event is fired. There are different
types of events, such as state change events, when an action was triggered, or
the time changed. All entities produce state change events. Every time a state
changes, a state change event is produced. Events can be used to trigger
automations or scripts. For example, you can trigger an automation when a light
is turned on, then a speaker turns on in that room. Events can also be used to
trigger actions in the frontend. For example, you can trigger an action when a
button is pressed., a certain entityAn entity represents a sensor, actor, or
function in Home Assistant. Entities are used to monitor physical properties or
to control other entities. An entity is usually part of a device or a service.
stateThe state holds the information of interest of an entity, for example, if a
light is on or off. Each entity has exactly one state and the state only holds
one value at a time. However, entities can store attributes related to that
state such as brightness, color, or a unit of measurement., at a given time, and
more. These can be specified directly or more flexible via templates. It is also
possible to specify multiple triggers for one automation.

  * [Multiple Entity IDs for the same Trigger](https://www.home-assistant.io/docs/automation/trigger#multiple-entity-ids-for-the-same-trigger)

All triggers can be assigned an optional . If the ID is omitted, it will instead
be set to the index of the trigger. The can be referenced from . The does not
have to be unique for each trigger, and it can be used to group similar triggers
for use later in the automation (i.e., several triggers of different types that
should all turn some entity on).

This video tutorial explains how trigger IDs work.

```

  
      event
       
       
      mqtt
       
       
      state  # This trigger will be assigned id="2"
      
         device_tracker.paulus
         device_tracker.anne_therese
       
```

There are two different types of variables available for triggers. Both work
like .

The first variant allows you to define variables that will be set when the
trigger fires. The variables will be able to use templates and have access to .

The second variant is setting variables that are available when attaching a
trigger when the trigger can contain templated values. These are defined using
the key at an automation level. These variables can only contain . The triggers
will not re-apply if the value of the template changes. Trigger variables are a
feature meant to support using blueprint inputs in triggers.

```

  
     example_event
  
      event
      # Able to use `trigger_variables`
       
      # These variables are evaluated and set when this trigger is triggered
      
         
```

An event trigger fires when an is being received. Events are the raw building
blocks of Home Assistant. You can match events on just the event name or also
require specific event data or context to be present.

Events can be fired by integrations or via the API. There is no limitation to
the types. A list of built-in events can be found .

```

  
      event
       
      
      
         happy
      
        
        # any of these will match
           
           
```

It is also possible to listen for multiple events at once. This is useful for
event that contain no, or similar, data and contexts.

It’s also possible to use in the , and options.

The , and templates are only evaluated when setting up the trigger, they will
not be reevaluated for every event.

```

  
     ABC
     ac
     on
  
      event
       "{{ 'MY_CUSTOM_EVENT_' ~ sub_event }}"
```

Fires when Home Assistant starts up or shuts down.

```

  
      homeassistant
      # Event can also be 'shutdown'
       start
```

Automations triggered by the event have 20 seconds to run, after which they are
stopped to continue with the shutdown.

Fires when a specific message is received on given MQTT topic. Optionally can
match on the payload being sent over the topic. The default payload encoding is
‘utf-8’. For images and other byte payloads use to disable payload decoding
completely.

The option can be combined with a to process the message received on the given
MQTT topic before matching it with the payload. The trigger in the example below
will trigger only when the message received on is valid JSON, with a key which
has the value .

It’s also possible to use in the and options.

The and templates are only evaluated when setting up the trigger, they will not
be re-evaluated for every incoming MQTT message.

```

  
     
     
     
  
      mqtt
       "{{ room ~ '/switch/' ~ node}}"
      
       "{{ 'state:' ~ value }}"
       
```

Fires when the numeric value of an entity’s state (or attribute’s value if using
the property, or the calculated value if using the property) a given threshold
(equal excluded). On state change of a specified entity, attempts to parse the
state as a number and fires if the value is changing from above to below or from
below to above the given threshold (equal excluded).

Crossing the threshold means that the trigger only fires if the state wasn’t
previously within the threshold. If the current state of your entity is and you
set the threshold to , the trigger would not fire if the state changed to e.g.
or because the threshold was never crossed. The state would first have to change
to e.g. and then to e.g. for the trigger to fire.

```

  
      numeric_state
       sensor.temperature
      # If given, will trigger when the value of the given attribute for the given entity changes..
       attribute_name
      # ..or alternatively, will trigger when the value given by this evaluated template changes.
       "{{ state.attributes.value - 5 }}"
      # At least one of the following required
       
       
      # If given, will trigger when the condition has been true for X time; you can also use days and milliseconds.
      
         
         
         
```

Listing above and below together means the numeric_state has to be between the
two values. In the example above, the trigger would fire a single time if a
numeric_state goes into the 17.1-24.9 range (above 17 and below 25). It will
only fire again, once it has left the defined range and enters it again.

When the option is specified the trigger is compared to the given instead of the
state of the entity.

More dynamic and complex calculations can be done with . The variable ‘state’ is
the of the entity specified by .

The state of the entity can be referenced like this:

```

  
      numeric_state
       sensor.temperature
       "{{ state.state | float * 9 / 5 + 32 }}"
       
```

Attributes of the entity can be referenced like this:

```

  
      numeric_state
       climate.kitchen
       "{{ state.attributes.current_temperature - state.attributes.temperature_set_point }}"
       
```

Number helpers ( entities), , , and entities that contain a numeric value, can
be used in the and thresholds. However, the comparison will only be made when
the entity specified in the trigger is updated. This would look like:

```

  
      numeric_state
       sensor.outside_temperature
      # Other entity ids can be specified for above and/or below thresholds
       sensor.inside_temperature
```

The can also be specified as like this:

```

  
      numeric_state
       sensor.temperature
      # At least one of the following required
       
       

      # If given, will trigger when condition has been for X time.
       
```

You can also use templates in the option.

```

  
      numeric_state
      
         sensor.temperature_1
         sensor.temperature_2
       
      
         
         
  
      persistent_notification.create
      
         
          {{ trigger.to_state.name }} too high for {{ trigger.for }}!
```

The template(s) will be evaluated when an entity changes as specified.

Use of the option will not survive Home Assistant restart or the reload of
automations. During restart or reload, automations that were awaiting the
trigger to pass, are reset.

If for your use case this is undesired, you could consider using the automation
to set an to the desired time and then use that as an automation trigger to
perform the desired actions at the set time.

In general, the state trigger fires when the state of any of given entities .
The behavior is as follows:

  * If only the is given, the trigger fires for state changes, even if only a state attribute changed.
  * If at least one of , , , or are given, the trigger fires on any matching state change, but not if only an attribute changed. 
    * To trigger on all state changes, but not on changed attributes, set at least one of , , , or to .
  * Use of the option doesn’t survive a Home Assistant restart or the reload of automations. 
    * During restart or reload, automations that were awaiting the trigger to pass, are reset.
    * If for your use case this is undesired, you could consider using the automation to set an to the desired time and then use that as an automation trigger to perform the desired actions at the set time.

The values you see in your overview will often not be the same as the actual
state of the entity. For instance, the overview may show when the underlying
entity is actually . You should check the state of the entity by checking the
states in the developer tool, under .

This automation triggers if either Paulus or Anne-Therese are home for one
minute.

```

  
      state
      
         device_tracker.paulus
         device_tracker.anne_therese
      
       
      
       
      # If given, will trigger when the condition has been true for X time; you can also use days and milliseconds.
      
         
         
         
```

It’s possible to give a list of states or states:

If you want to trigger on all state changes, but not on attribute changes, you
can to (this would also work by setting , , or to ):

```

  
      state
       vacuum.test
      to
```

If you want to trigger on all state changes specific ones, use or The and
options are the counter parts of and . They can be used to trigger on state
changes that are the specified state.

You cannot use and at the same time. The same applies to and .

When the option is specified, the trigger only fires when the specified
attribute . Changes to other attributes or state changes are ignored.

For example, this trigger only fires when the boiler has been heating for 10
minutes:

This trigger fires whenever the boiler’s attribute changes:

### Holding a state or attribute

You can use to have the state trigger only fire if the state holds for some
time.

This example fires, when the entity state changed to and holds that state for 30
seconds:

```

  
      state
       light.office
      # Must stay "on" for 30 seconds
       
       
```

When holding a state, changes to attributes are ignored. Changes to attributes
don’t cancel the hold time.

You can also fire the trigger when the state value changed from a specific
state, but hasn’t returned to that state value for the specified time.

This can be useful, e.g., checking if a media player hasn’t turned “off” for the
time specified, but doesn’t care about “playing” or “paused”.

```

  
      state
       media_player.kitchen
      # Not "off" for 30 minutes
       
       
```

Please note, that when using , and , only the value of the option is considered
for the time specified.

In this example, the trigger fires if the state value of the entity remains the
same for the time specified, regardless of the current state value.

```

  
      state
       media_player.kitchen
      # The media player remained in its current state for 1 hour
       
```

You can also use templates in the option.

```

  
      state
      
         device_tracker.paulus
         device_tracker.anne_therese
       
      
         
         
  
      lock.lock
      
         lock.my_place
```

The template(s) will be evaluated when an entity changes as specified.

Use quotes around your values for and to avoid the YAML parser from interpreting
values as booleans.

Fires when the sun is setting or rising, i.e., when the sun elevation reaches
0°.

An optional time offset can be given to have it fire a set time before or after
the sun event (e.g., 45 minutes before sunset). A negative value makes it fire
before sunrise or sunset, a positive value afterwards. The offset needs to be
specified in number of seconds, or in a hh:mm:ss format.

Since the duration of twilight is different throughout the year, it is
recommended to use instead of or with a time offset to trigger automations
during dusk or dawn.

```

  
      sun
      # Possible values: sunset, sunrise
       sunset
      # Optional time offset. This example will trigger 45 minutes before sunset.
       
```

Sometimes you may want more granular control over an automation than simply
sunset or sunrise and specify an exact elevation of the sun. This can be used to
layer automations to occur as the sun lowers on the horizon or even after it is
below the horizon. This is also useful when the “sunset” event is not dark
enough outside and you would like the automation to run later at a precise solar
angle instead of the time offset such as turning on exterior lighting. For most
automations intended to run during dusk or dawn, a number between 0° and -6° is
suitable; -4° is used in this example:

```

    "Exterior Lighting on when dark outside"
    
        numeric_state
         sun.sun
         elevation
        # Can be a positive or negative number
         
    
        switch.turn_on
        
           switch.exterior_lighting
```

If you want to get more precise, you can use this

Although the actual amount of light depends on weather, topography and land
cover, they are defined as:

  * Civil twilight: 0° > Solar angle > -6°
This is what is meant by twilight for the average person: Under clear weather
conditions, civil twilight approximates the limit at which solar illumination
suffices for the human eye to clearly distinguish terrestrial objects. Enough
illumination renders artificial sources unnecessary for most outdoor activities.

  * Nautical twilight: -6° > Solar angle > -12°
  * Astronomical twilight: -12° > Solar angle > -18°

A very thorough explanation of this is available in the Wikipedia article about
the

Fires when a is scanned. For example, a NFC tag is scanned using the Home
Assistant Companion mobile application.

Additionally, you can also only trigger if a card is scanned by a specific
device/scanner by setting the :

Or trigger on multiple possible devices for multiple tags:

Template triggers work by evaluating a when any of the recognized entities
change state. The trigger will fire if the state change caused the template to
render ‘true’ (a non-zero number or any of the strings , , , ) when it was
previously ‘false’ (anything else).

This is achieved by having the template result in a true boolean expression (for
example ) or by having the template render (example below).

With template triggers you can also evaluate attribute changes by using
is_state_attr (like `{{ is_state_attr('climate.living_room', 'away_mode', 'off')
}}`)

```

  
      template
       "{% if is_state('device_tracker.paulus', 'home') %}true{% endif %}"

      # If given, will trigger when template remains true for X time.
       
```

You can also use templates in the option.

```

  
      template
       
      
         
```

The template(s) will be evaluated when the becomes ‘true’.

Templates that do not contain an entity will be rendered once per minute.

Use of the option will not survive Home Assistant restart or the reload of
automations. During restart or reload, automations that were awaiting the
trigger to pass, are reset.

If for your use case this is undesired, you could consider using the automation
to set an to the desired time and then use that as an automation trigger to
perform the desired actions at the set time.

The time trigger is configured to fire once a day at a specific time, or at a
specific time on a specific date. There are three allowed formats:

A string that represents a time to fire on each day. Can be specified as or . If
the seconds are not specified, will be used.

```

  
      time
      # 24-hour time format. This trigger will fire at 3:32 PM
       
```

The entity ID of an .

Will fire at specified date & time.  
---  
Will fire at midnight on specified date.  
Will fire once a day at specified time.  
```

  
        state
         binary_sensor.motion
         
    
        climate.turn_on
        
           climate.office
        input_datetime.set_datetime
        
           input_datetime.turn_off_ac
        
           
            {{ (now().timestamp() + 2*60*60)
               | timestamp_custom('%Y-%m-%d %H:%M:%S') }}
  
        time
         input_datetime.turn_off_ac
    
        climate.turn_off
        
           climate.office
```

### Sensors of datetime device class

The Entity ID of a with the “timestamp” device class.

### Sensors of datetime device class with offsets

When the time is provided using a sensor of the timestamp device class, an
offset can be provided. This offset will be added to (or subtracted from when
negative) the sensor value.

For example, this trigger fires 5 minutes before the phone alarm goes off.

When using a positive offset the trigger might never fire. This is due to the
sensor changing before the offset is reached. For example, when using a phone
alarm as a trigger, the sensor value will change to the new alarm time when the
alarm goes off, which means this trigger will change to the new time as well.

Multiple times can be provided in a list. All formats can be intermixed.

It’s also possible to use for times.

```

  
    
       Alarm
      
        
    
       Hour
      
        
           
           

  
      alarm
      hour
  
      time
      
       "sensor.{{ my_alarm | slugify }}_time"
       
```

Time triggers can be filtered to fire only on specific days of the week using
the option. This allows you to create automations that only run on certain days,
such as weekdays or weekends.

  * A single weekday as a string: , , , , , , 
  * A list of weekdays using the expanded format

This example will turn on the lights only on Mondays at 8:00 AM:

This example will run a morning routine only on weekdays (Monday through Friday)
at 6:30 AM:

This example demonstrates a different wake-up time for weekends:

The option works with all time formats, including input datetime entities:

```

  
        time
         input_datetime.work_start_time
        
           
           
           
           
           
    
        notify.mobile_app
        
           
           
```

With the time pattern trigger, you can match if the hour, minute or second of
the current time matches a specific value. You can prefix the value with a to
match whenever the value is divisible by that number. You can specify to match
any value (when using the web interface this is required, the fields cannot be
left empty).

```

  
      time_pattern
      # Matches every hour at 5 minutes past whole
       

automation 2

  
      time_pattern
      # Trigger once per minute during the hour of 3
       
       

automation 3

  
      time_pattern
      # You can also match on interval. This will match every 5 minutes
       
```

Do not prefix numbers with a zero - using instead of for example will result in
errors.

Persistent notification triggers are fired when a is or that matches the
configuration options.

See the integration for more details on event triggers and the additional event
data available for use by an automation.

Webhook trigger fires when a web request is made to the webhook endpoint: . The
webhook endpoint is created automatically when you set it as the in an
automation trigger.

You can run this automation by sending an HTTP POST request to . Here is an
example using the command line program, with an example form data payload:

Webhooks support HTTP POST, PUT, HEAD, and GET requests; PUT requests are
recommended. HTTP GET and HEAD requests are not enabled by default but can be
enabled by adding them to the option. The request methods can also be configured
in the UI by clicking the settings gear menu button beside the Webhook ID.

By default, webhook triggers can only be accessed from devices on the same
network as Home Assistant or via option should be set to to allow webhooks to be
triggered directly via the internet. This option can also be configured in the
UI by clicking the settings gear menu button beside the Webhook ID.

Remember to use an HTTPS URL if you’ve secured your Home Assistant installation
with SSL/TLS.

Note that a given webhook can only be used in one automation at a time. That is,
only one automation trigger can use a specific webhook ID.

Payloads may either be encoded as form data or JSON. Depending on that, its data
will be available in an automation template as either or . URL query parameters
are also available in the template as .

Note that to use JSON encoded payloads, the header must be set to , e.g.:

```

 -X POST -H  -d  
```

Webhook endpoints don’t require authentication, other than knowing a valid
webhook ID. Security best practices for webhooks include:

  * Do not use webhooks to trigger automations that are destructive, or that can create safety issues. For example, do not use a webhook to unlock a lock, or open a garage door.
  * Treat a webhook ID like a password: use a unique, non-guessable value, and keep it secret.
  * Do not copy-and-paste webhook IDs from public sources, including blueprints. Always create your own.
  * Keep the option enabled for webhooks if access from the internet is not required.

Zone trigger fires when an entity is entering or leaving the zone. The entity
can be either a person, or a device_tracker. For zone automation to work, you
need to have setup a device tracker platform that supports reporting GPS
coordinates. This includes , the and the .

```

  
      zone
       person.paulus
       zone.home
      # Event is either enter or leave
       enter 
```

Geolocation trigger fires when an entity is appearing in or disappearing from a
zone. Entities that are created by a platform support reporting GPS coordinates.
Because entities are generated and removed by these platforms automatically, the
entity ID normally cannot be predicted. Instead, this trigger requires the
definition of a , which is directly linked to one of the Geolocation platforms.

This isn’t for use with entities. For those look above at the trigger.

```

  
      geo_location
       nsw_rural_fire_service_feed
       zone.bushfire_alert_zone
      # Event is either enter or leave
       enter 
```

Device triggers encompass a set of events that are defined by an integration.
This includes, for example, state changes of sensors as well as button events
from remotes. are set up through autodiscovery.

In contrast to state triggers, device triggers are tied to a device and not
necessarily an entity. To use a device trigger, set up an automation through the
browser frontend. If you would like to use a device trigger for an automation
that is not managed through the browser frontend, you can copy the YAML from the
trigger widget in the frontend and paste it into your automation’s trigger list.

Calendar trigger fires when a event starts or ends, allowing for much more
flexible automations than using the Calendar entity state which only supports a
single event start at a time.

An optional time offset can be given to have it fire a set time before or after
the calendar event (e.g., 5 minutes before event start).

```

  
      calendar
      # Possible values: start, end
       start
      
       calendar.light_schedule
      
       
```

See the integration for more details on event triggers and the additional event
data available for use by an automation.

A sentence trigger fires when matches a sentence from a voice assistant using
the default . Sentence triggers work with Home Assistant Assist. They will not
work with external conversation agents such as OpenAI or Google Generative AI
unless “Prefer handling commands locally” is enabled in the conversation agent
settings.

Sentences are allowed to use some basic like optional and alternative words. For
example, will match both “party time” and “it’s party time”.

```

  
      conversation
      
         
         
```

The sentences matched by this trigger will be:

Punctuation and casing are ignored, so “It’s PARTY TIME!!!” will also match.

  * [Adding a custom sentence to trigger an automation](https://www.home-assistant.io/voice_control/custom_sentences/#adding-a-custom-sentence-to-trigger-an-automation)

Adding one or more to your trigger sentences will capture any text at that point
in the sentence. A object will be [available in the trigger
data](https://www.home-assistant.io/docs/automation/templating#sentence). This
allows you to match sentences with variable parts, such as album/artist names or
a description of a picture.

For example, the sentence will match “play the white album by the beatles” and
have the following variables available in the action templates:

  * - “the white album”
  * - “the beatles”

Wildcards will match as much text as possible, which may lead to surprises:
“play day by day by taken by trees” will match as “day” and as “day by taken by
trees”. Including extra words in your template can help: `play {album} by artist
{artist}` can now correctly match “play day by day by artist taken by trees”.

It is possible to specify multiple triggers for the same rule. To do so just
prefix the first line of each trigger with a dash (-) and indent the next lines
accordingly. Whenever one of the triggers fires, processing of your automation
rule begins.

```

  
    
      time_pattern
       
      # our second trigger is the sunset
      sun
       sunset
```

## Multiple entity IDs for the same trigger

It is possible to specify multiple entities for the same trigger. To do so add
multiple entities using a nested list. The trigger will fire and start,
processing your automation each time the trigger is true for any entity listed.

Every individual trigger in an automation can be disabled, without removing it.
To do so, add to the trigger. For example:

```

# Example script with a disabled trigger

  
    # This trigger will not trigger, as it is disabled.
    # This automation does not run when the sun is set.
      
       sun
       sunset

    # This trigger will fire, as it is not disabled.
      time
       
```

Triggers can also be disabled based on limited templates or blueprint inputs.
These are only evaluated once when the automation is loaded.

```

  
    
       Boolean
      
        
    
       Number
      
        
           
           

  
      input_number

  
      sun
       sunrise
        input_boolean
      sun
       sunset
       "{{ _enable_number < 50 }}"
```

This feature requires Home Assistant version 2024.10 or later. If using this in
a blueprint, set the for the blueprint to at least this version. See the for
more details.

In some advanced cases (like for blueprints with trigger selectors), it may be
necessary to insert a second list of triggers into the main trigger list. This
can be done by adding a dictionary in the main trigger list with the sole key ,
and the value for that key contains a second list of triggers. These will then
be flattened into a single list of triggers. For example:

This blueprint automation can then be triggered either by the fixed manual_event
trigger, or additionally by any triggers selected in the trigger selector. This
is also applicable for action.

  * [ Adding a custom sentence to trigger an automation ](https://www.home-assistant.io/voice_control/custom_sentences/#adding-a-custom-sentence-to-trigger-an-automation)

####  **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.



---

## Additional Resources

- [home-assistant.io Documentation](https://home-assistant.io/docs)
- [Source Page](https://www.home-assistant.io/docs/automation/trigger)

---

*This page was automatically generated from home-assistant.io.*