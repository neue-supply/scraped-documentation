---
title: "Documentation"
source: "https://www.home-assistant.io/docs/automation/trigger"
domain: "home-assistant.io"
scraped_at: "2025-08-18T03:48:27.028Z"
---

# Documentation

<html>
<!--<![endif]--><head>
    <title>Automation Trigger - Home Assistant</title>
    </head>

  <body>
    <header>
      



<div>
  <div>
    <div>
      <a href="/">
        </a>
      <a href="/blog/2025/08/06/release-20258/" title="Latest version 2025.8.2 released August 15, 2025">
        2025.8.2
      </a>
    </div>

    <div>
      <nav>
        <input>
        <ul>
          <li><a href="/installation/">Getting started</a></li>
          <li>
            <a href="/docs/">Documentation </a>
            <ul>
              <li><a href="/installation/"></a></li>
              <li><a href="/docs/automation/"></a></li>
              <li><a href="/dashboards/"></a></li>
              <li><a href="/voice_control/"></a></li>
              <li><a href="/docs/organizing/"></a></li>
              <li><a href="/docs/energy/"></a></li>
              <li><a href="/docs/configuration/"></a></li>
            </ul>
          </li>
          <li><a href="/integrations/">Integrations</a></li>
          <li><a href="/blog/">Blog</a></li>
          <li><a href="/help/">Need help?</a></li>
          <li>
            <div><button><span><span>Search</span></span><span><kbd>K</kbd></span></button></div>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</div>

    </header>

    <div>

      

      <div>
        <div>

          <aside>
                <section>
                  <div>
                    <ul>
<li>
<a href="#trigger-id">Trigger ID</a>
<ul>
<li><a href="#video-tutorial">Video tutorial</a></li>
</ul>
</li>
<li><a href="#trigger-variables">Trigger variables</a></li>
<li><a href="#event-trigger">Event trigger</a></li>
<li><a href="#home-assistant-trigger">Home Assistant trigger</a></li>
<li><a href="#mqtt-trigger">MQTT trigger</a></li>
<li><a href="#numeric-state-trigger">Numeric state trigger</a></li>
<li>
<a href="#state-trigger">State trigger</a>
<ul>
<li><a href="#examples">Examples</a></li>
<li><a href="#triggering-on-attribute-changes">Triggering on attribute changes</a></li>
<li><a href="#holding-a-state-or-attribute">Holding a state or attribute</a></li>
</ul>
</li>
<li>
<a href="#sun-trigger">Sun trigger</a>
<ul>
<li><a href="#sunset--sunrise-trigger">Sunset / Sunrise trigger</a></li>
<li><a href="#sun-elevation-trigger">Sun elevation trigger</a></li>
</ul>
</li>
<li><a href="#tag-trigger">Tag trigger</a></li>
<li><a href="#template-trigger">Template trigger</a></li>
<li>
<a href="#time-trigger">Time trigger</a>
<ul>
<li><a href="#time-string">Time string</a></li>
<li><a href="#input-datetime">Input datetime</a></li>
<li><a href="#sensors-of-datetime-device-class">Sensors of datetime device class</a></li>
<li><a href="#sensors-of-datetime-device-class-with-offsets">Sensors of datetime device class with offsets</a></li>
<li><a href="#multiple-times">Multiple times</a></li>
<li><a href="#limited-templates">Limited templates</a></li>
<li><a href="#weekday-filtering">Weekday filtering</a></li>
</ul>
</li>
<li><a href="#time-pattern-trigger">Time pattern trigger</a></li>
<li><a href="#persistent-notification-trigger">Persistent notification trigger</a></li>
<li>
<a href="#webhook-trigger">Webhook trigger</a>
<ul>
<li><a href="#webhook-data">Webhook data</a></li>
<li><a href="#webhook-security">Webhook security</a></li>
</ul>
</li>
<li><a href="#zone-trigger">Zone trigger</a></li>
<li><a href="#geolocation-trigger">Geolocation trigger</a></li>
<li><a href="#device-triggers">Device triggers</a></li>
<li><a href="#calendar-trigger">Calendar trigger</a></li>
<li>
<a href="#sentence-trigger">Sentence trigger</a>
<ul>
<li><a href="#related-topic">Related topic</a></li>
<li><a href="#sentence-wildcards">Sentence wildcards</a></li>
</ul>
</li>
<li><a href="#multiple-triggers">Multiple triggers</a></li>
<li><a href="#multiple-entity-ids-for-the-same-trigger">Multiple entity IDs for the same trigger</a></li>
<li><a href="#disabling-a-trigger">Disabling a trigger</a></li>
<li><a href="#merging-lists-of-triggers">Merging lists of triggers</a></li>
<li><a href="#related-topics">Related topics</a></li>
</ul>
                  </div>
                </section>
              </aside> 

          
          <div>
          

            
              <article>
  
  <header>
    
    
      <div>
        <a href="/">Home</a>
        
          
            
            ▸ <a href="/docs/">Documentation</a>
          
        
          
            
            ▸ <a href="/docs/automation/">Automation</a>
          
        
          
            ▸ 
          
        
      </div>
    
    <h1>
      
        Automation Trigger
      
    </h1>
  </header>
  
  
  <p>Triggers are what starts the processing of an <span>automation<span>Automations in Home Assistant allow you to automatically respond to things that happen in and around your home.<a href="/docs/automation/"> [Learn more]</a></span></span> rule. When <em>any</em> of the automation’s triggers becomes true (trigger <em>fires</em>), Home Assistant will validate the <a href="/docs/automation/condition/">conditions</a>, if any, and call the <a href="/docs/automation/action/">action</a>.</p>
<p>An <span>automation<span>Automations in Home Assistant allow you to automatically respond to things that happen in and around your home.<a href="/docs/automation/"> [Learn more]</a></span></span> can be triggered by an <span>event<span>Every time something happens in Home Assistant, an event is fired. There are different types of events, such as state change events, when an action was triggered, or the time changed. All entities produce state change events. Every time a state changes, a state change event is produced. Events can be used to trigger automations or scripts. For example, you can trigger an automation when a light is turned on, then a speaker turns on in that room. Events can also be used to trigger actions in the frontend. For example, you can trigger an action when a button is pressed.<a href="/docs/configuration/events/"> [Learn more]</a></span></span>, a certain <span>entity<span>An entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.<a href="/docs/configuration/entities_domains/"> [Learn more]</a></span></span> <span>state<span>The state holds the information of interest of an entity, for example, if a light is on or off. Each entity has exactly one state and the state only holds one value at a time. However, entities can store attributes related to that state such as brightness, color, or a unit of measurement.<a href="/docs/configuration/state_object/"> [Learn more]</a></span></span>, at a given time, and more. These can be specified directly or more flexible via templates. It is also possible to specify multiple triggers for one automation.</p>
<ul>
<li><a href="#trigger-id">Trigger ID</a></li>
<li><a href="#trigger-variables">Trigger variables</a></li>
<li><a href="#event-trigger">Event trigger</a></li>
<li><a href="#home-assistant-trigger">Home Assistant trigger</a></li>
<li><a href="#mqtt-trigger">MQTT trigger</a></li>
<li><a href="#numeric-state-trigger">Numeric state trigger</a></li>
<li><a href="#state-trigger">State trigger</a></li>
<li><a href="#sun-trigger">Sun trigger</a></li>
<li><a href="#tag-trigger">Tag trigger</a></li>
<li><a href="#template-trigger">Template trigger</a></li>
<li><a href="#time-trigger">Time trigger</a></li>
<li><a href="#time-pattern-trigger">Time pattern trigger</a></li>
<li><a href="#persistent-notification-trigger">Persistent notification trigger</a></li>
<li><a href="#webhook-trigger">Webhook trigger</a></li>
<li><a href="#zone-trigger">Zone trigger</a></li>
<li><a href="#geolocation-trigger">Geolocation trigger</a></li>
<li><a href="#device-triggers">Device triggers</a></li>
<li><a href="#calendar-trigger">Calendar trigger</a></li>
<li><a href="#sentence-trigger">Sentence trigger</a></li>
<li><a href="#multiple-triggers">Multiple triggers</a></li>
<li><a href="#multiple-entity-ids-for-the-same-trigger">Multiple Entity IDs for the same Trigger</a></li>
<li><a href="#disabling-a-trigger">Disabling a trigger</a></li>
<li><a href="#merging-lists-of-triggers">Merging lists of triggers</a></li>
</ul>
<h2>Trigger ID <a href="#trigger-id"></a>
</h2>
<p>All triggers can be assigned an optional <code>id</code>. If the ID is omitted, it will instead be set to the index of the trigger. The <code>id</code> can be referenced from <a href="/docs/scripts/conditions/#trigger-condition">trigger conditions and actions</a>. The <code>id</code> does not have to be unique for each trigger, and it can be used to group similar triggers for use later in the automation (i.e., several triggers of different types that should all turn some entity on).</p>
<h3>Video tutorial <a href="#video-tutorial"></a>
</h3>
<p>This video tutorial explains how trigger IDs work.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> event
      <span>event_type</span><span>:</span> <span>"MY_CUSTOM_EVENT"</span>
      <span>id</span><span>:</span> <span>"custom_event"</span>
    <span>-</span> <span>trigger</span><span>:</span> mqtt
      <span>topic</span><span>:</span> <span>"living_room/switch/ac"</span>
      <span>id</span><span>:</span> <span>"ac_on"</span>
    <span>-</span> <span>trigger</span><span>:</span> state  <span># This trigger will be assigned id="2"</span>
      <span>entity_id</span><span>:</span>
        <span>-</span> device_tracker.paulus
        <span>-</span> device_tracker.anne_therese
      <span>to</span><span>:</span> <span>"home"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Trigger variables <a href="#trigger-variables"></a>
</h2>
<p>There are two different types of variables available for triggers. Both work like <a href="/integrations/script/#variables">script level variables</a>.</p>
<p>The first variant allows you to define variables that will be set when the trigger fires. The variables will be able to use templates and have access to <a href="/docs/automation/templating#available-trigger-data">the <code>trigger</code> variable</a>.</p>
<p>The second variant is setting variables that are available when attaching a trigger when the trigger can contain templated values. These are defined using the <code>trigger_variables</code> key at an automation level. These variables can only contain <a href="/docs/configuration/templating/#limited-templates">limited templates</a>. The triggers will not re-apply if the value of the template changes. Trigger variables are a feature meant to support using blueprint inputs in triggers.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>trigger_variables</span><span>:</span>
    <span>my_event</span><span>:</span> example_event
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> event
      <span># Able to use `trigger_variables`</span>
      <span>event_type</span><span>:</span> <span>"{{ my_event }}"</span>
      <span># These variables are evaluated and set when this trigger is triggered</span>
      <span>variables</span><span>:</span>
        <span>name</span><span>:</span> <span>"{{ trigger.event.data.name }}"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Event trigger <a href="#event-trigger"></a>
</h2>
<p>An event trigger fires when an <a href="/docs/configuration/events/">event</a> is being received. Events are the raw building blocks of Home Assistant. You can match events on just the event name or also require specific event data or context to be present.</p>
<p>Events can be fired by integrations or via the API. There is no limitation to the types. A list of built-in events can be found <a href="/docs/configuration/events/">here</a>.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> event
      <span>event_type</span><span>:</span> <span>"MY_CUSTOM_EVENT"</span>
      <span># optional</span>
      <span>event_data</span><span>:</span>
        <span>mood</span><span>:</span> happy
      <span>context</span><span>:</span>
        <span>user_id</span><span>:</span>
        <span># any of these will match</span>
          <span>-</span> <span>"MY_USER_ID"</span>
          <span>-</span> <span>"ANOTHER_USER_ID"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>It is also possible to listen for multiple events at once. This is useful for
event that contain no, or similar, data and contexts.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> event
      <span>event_type</span><span>:</span>
        <span>-</span> automation_reloaded
        <span>-</span> scene_reloaded</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>It’s also possible to use <a href="/docs/configuration/templating/#limited-templates">limited templates</a> in the <code>event_type</code>, <code>event_data</code> and <code>context</code> options.</p>
<div>
  <div>
<p>The <code>event_type</code>, <code>event_data</code> and <code>context</code> templates are only evaluated when setting up the trigger, they will not be reevaluated for every event.</p>
  </div>
</div>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>trigger_variables</span><span>:</span>
    <span>sub_event</span><span>:</span> ABC
    <span>node</span><span>:</span> ac
    <span>value</span><span>:</span> on
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> event
      <span>event_type</span><span>:</span> <span>"{{ 'MY_CUSTOM_EVENT_' ~ sub_event }}"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Home Assistant trigger <a href="#home-assistant-trigger"></a>
</h2>
<p>Fires when Home Assistant starts up or shuts down.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> homeassistant
      <span># Event can also be 'shutdown'</span>
      <span>event</span><span>:</span> start</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<div>
  <div>
<p>Automations triggered by the <code>shutdown</code> event have 20 seconds to run, after which they are stopped to continue with the shutdown.</p>
  </div>
</div>
<h2>MQTT trigger <a href="#mqtt-trigger"></a>
</h2>
<p>Fires when a specific message is received on given MQTT topic. Optionally can match on the payload being sent over the topic. The default payload encoding is ‘utf-8’. For images and other byte payloads use <code>encoding: ''</code> to disable payload decoding completely.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> mqtt
      <span>topic</span><span>:</span> <span>"living_room/switch/ac"</span>
      <span># Optional</span>
      <span>payload</span><span>:</span> <span>"on"</span>
      <span>encoding</span><span>:</span> <span>"utf-8"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>The <code>payload</code> option can be combined with a <code>value_template</code> to process the message received on the given MQTT topic before matching it with the payload.
The trigger in the example below will trigger only when the message received on <code>living_room/switch/ac</code> is valid JSON, with a key <code>state</code> which has the value <code>"on"</code>.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> mqtt
      <span>topic</span><span>:</span> <span>"living_room/switch/ac"</span>
      <span>payload</span><span>:</span> <span>"on"</span>
      <span>value_template</span><span>:</span> <span>"{{ value_json.state }}"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>It’s also possible to use <a href="/docs/configuration/templating/#limited-templates">limited templates</a> in the <code>topic</code> and <code>payload</code> options.</p>
<div>
  <div>
<p>The <code>topic</code> and <code>payload</code> templates are only evaluated when setting up the trigger, they will not be re-evaluated for every incoming MQTT message.</p>
  </div>
</div>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>trigger_variables</span><span>:</span>
    <span>room</span><span>:</span> <span>"living_room"</span>
    <span>node</span><span>:</span> <span>"ac"</span>
    <span>value</span><span>:</span> <span>"on"</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> mqtt
      <span>topic</span><span>:</span> <span>"{{ room ~ '/switch/' ~ node}}"</span>
      <span># Optional</span>
      <span>payload</span><span>:</span> <span>"{{ 'state:' ~ value }}"</span>
      <span>encoding</span><span>:</span> <span>"utf-8"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Numeric state trigger <a href="#numeric-state-trigger"></a>
</h2>
<p>Fires when the numeric value of an entity’s state (or attribute’s value if using the <code>attribute</code> property, or the calculated value if using the <code>value_template</code> property) <strong>crosses</strong> a given threshold (equal excluded). On state change of a specified entity, attempts to parse the state as a number and fires if the value is changing from above to below or from below to above the given threshold (equal excluded).</p>
<div>
  <div>
<p>Crossing the threshold means that the trigger only fires if the state wasn’t previously within the threshold.
If the current state of your entity is <code>50</code> and you set the threshold to <code>below: 75</code>, the trigger would not fire if the state changed to e.g. <code>49</code> or <code>72</code> because the threshold was never crossed. The state would first have to change to e.g. <code>76</code> and then to e.g. <code>74</code> for the trigger to fire.</p>
  </div>
</div>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> numeric_state
      <span>entity_id</span><span>:</span> sensor.temperature
      <span># If given, will trigger when the value of the given attribute for the given entity changes..</span>
      <span>attribute</span><span>:</span> attribute_name
      <span># ..or alternatively, will trigger when the value given by this evaluated template changes.</span>
      <span>value_template</span><span>:</span> <span>"{{ state.attributes.value - 5 }}"</span>
      <span># At least one of the following required</span>
      <span>above</span><span>:</span> <span>17</span>
      <span>below</span><span>:</span> <span>25</span>
      <span># If given, will trigger when the condition has been true for X time; you can also use days and milliseconds.</span>
      <span>for</span><span>:</span>
        <span>hours</span><span>:</span> <span>1</span>
        <span>minutes</span><span>:</span> <span>10</span>
        <span>seconds</span><span>:</span> <span>5</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<div>
  <div>
<p>Listing above and below together means the numeric_state has to be between the two values.
In the example above, the trigger would fire a single time if a numeric_state goes into the 17.1-24.9 range (above 17 and below 25). It will only fire again, once it has left the defined range and enters it again.</p>
  </div>
</div>
<p>When the <code>attribute</code> option is specified the trigger is compared to the given <code>attribute</code> instead of the state of the entity.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> numeric_state
      <span>entity_id</span><span>:</span> climate.kitchen
      <span>attribute</span><span>:</span> current_temperature
      <span>above</span><span>:</span> <span>23</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>More dynamic and complex calculations can be done with <code>value_template</code>. The variable ‘state’ is the <a href="/docs/configuration/state_object">state object</a> of the entity specified by <code>entity_id</code>.</p>
<p>The state of the entity can be referenced like this:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> numeric_state
      <span>entity_id</span><span>:</span> sensor.temperature
      <span>value_template</span><span>:</span> <span>"{{ state.state | float * 9 / 5 + 32 }}"</span>
      <span>above</span><span>:</span> <span>70</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>Attributes of the entity can be referenced like this:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> numeric_state
      <span>entity_id</span><span>:</span> climate.kitchen
      <span>value_template</span><span>:</span> <span>"{{ state.attributes.current_temperature - state.attributes.temperature_set_point }}"</span>
      <span>above</span><span>:</span> <span>3</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>Number helpers (<code>input_number</code> entities), <code>number</code>, <code>sensor</code>, and <code>zone</code> entities
that contain a numeric value, can be used in the <code>above</code> and <code>below</code> thresholds.
However, the comparison will only be made when the entity specified in the trigger is updated. This would look like:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> numeric_state
      <span>entity_id</span><span>:</span> sensor.outside_temperature
      <span># Other entity ids can be specified for above and/or below thresholds</span>
      <span>above</span><span>:</span> sensor.inside_temperature</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>The <code>for:</code> can also be specified as <code>HH:MM:SS</code> like this:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> numeric_state
      <span>entity_id</span><span>:</span> sensor.temperature
      <span># At least one of the following required</span>
      <span>above</span><span>:</span> <span>17</span>
      <span>below</span><span>:</span> <span>25</span>

      <span># If given, will trigger when condition has been for X time.</span>
      <span>for</span><span>:</span> <span>"01:10:05"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>You can also use templates in the <code>for</code> option.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> numeric_state
      <span>entity_id</span><span>:</span>
        <span>-</span> sensor.temperature_1
        <span>-</span> sensor.temperature_2
      <span>above</span><span>:</span> <span>80</span>
      <span>for</span><span>:</span>
        <span>minutes</span><span>:</span> <span>"{{ states('input_number.high_temp_min')|int }}"</span>
        <span>seconds</span><span>:</span> <span>"{{ states('input_number.high_temp_sec')|int }}"</span>
  <span>actions</span><span>:</span>
    <span>-</span> <span>action</span><span>:</span> persistent_notification.create
      <span>data</span><span>:</span>
        <span>message</span><span>:</span> <span>&gt;</span><span>
          {{ trigger.to_state.name }} too high for {{ trigger.for }}!</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>The <code>for</code> template(s) will be evaluated when an entity changes as specified.</p>
<div>
  <div>
<p>Use of the <code>for</code> option will not survive Home Assistant restart or the reload of automations. During restart or reload, automations that were awaiting <code>for</code> the trigger to pass, are reset.</p>
<p>If for your use case this is undesired, you could consider using the automation to set an <a href="/integrations/input_datetime"><code>input_datetime</code></a> to the desired time and then use that <a href="/integrations/input_datetime"><code>input_datetime</code></a> as an automation trigger to perform the desired actions at the set time.</p>
  </div>
</div>
<h2>State trigger <a href="#state-trigger"></a>
</h2>
<p>In general, the state trigger fires when the state of any of given entities <strong>changes</strong>. The behavior is as follows:</p>
<ul>
<li>If only the <code>entity_id</code> is given, the trigger fires for <strong>all</strong> state changes, even if only a state attribute changed.</li>
<li>If at least one of <code>from</code>, <code>to</code>, <code>not_from</code>, or <code>not_to</code> are given, the trigger fires on any matching state change, but not if only an attribute changed.
<ul>
<li>To trigger on all state changes, but not on changed attributes, set at least one of <code>from</code>, <code>to</code>, <code>not_from</code>, or <code>not_to</code> to <code>null</code>.</li>
</ul>
</li>
<li>Use of the <code>for</code> option doesn’t survive a Home Assistant restart or the reload of automations.
<ul>
<li>During restart or reload, automations that were awaiting <code>for</code> the trigger to pass, are reset.</li>
<li>If for your use case this is undesired, you could consider using the automation to set an <a href="/integrations/input_datetime"><code>input_datetime</code></a> to the desired time and then use that <a href="/integrations/input_datetime"><code>input_datetime</code></a> as an automation trigger to perform the desired actions at the set time.</li>
</ul>
</li>
</ul>
<div>
  <div>
<p>The values you see in your overview will often not be the same as the actual state of the entity. For instance, the overview may show <code>Connected</code> when the underlying entity is actually <code>on</code>. You should check the state of the entity by checking the states in the developer tool, under <a href="https://my.home-assistant.io/redirect/developer_states"><strong>Developer Tools</strong> &gt; <strong>States</strong></a>.</p>
  </div>
</div>
<h3>Examples <a href="#examples"></a>
</h3>
<p>This automation triggers if either Paulus or Anne-Therese are home for one minute.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span>
        <span>-</span> device_tracker.paulus
        <span>-</span> device_tracker.anne_therese
      <span># Optional</span>
      <span>from</span><span>:</span> <span>"not_home"</span>
      <span># Optional</span>
      <span>to</span><span>:</span> <span>"home"</span>
      <span># If given, will trigger when the condition has been true for X time; you can also use days and milliseconds.</span>
      <span>for</span><span>:</span>
        <span>hours</span><span>:</span> <span>0</span>
        <span>minutes</span><span>:</span> <span>1</span>
        <span>seconds</span><span>:</span> <span>0</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>It’s possible to give a list of <code>from</code> states or <code>to</code> states:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> vacuum.test
      <span>from</span><span>:</span>
        <span>-</span> <span>"cleaning"</span>
        <span>-</span> <span>"returning"</span>
      <span>to</span><span>:</span> <span>"error"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>If you want to trigger on all state changes, but not on attribute changes, you can <code>to</code> to <code>null</code> (this would also work by setting <code>from</code>, <code>not_from</code>, or <code>not_to</code> to <code>null</code>):</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> vacuum.test
      to<span>:</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>If you want to trigger on all state changes <em>except</em> specific ones, use <code>not_from</code> or <code>not_to</code>  The <code>not_from</code> and <code>not_to</code> options are the counter parts of <code>from</code> and <code>to</code>. They can be used to trigger on state changes that are <strong>not</strong> the specified state.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> vacuum.test
      <span>not_from</span><span>:</span>
        <span>-</span> <span>"unknown"</span>
        <span>-</span> <span>"unavailable"</span>
      <span>to</span><span>:</span> <span>"on"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>You cannot use <code>from</code> and <code>not_from</code> at the same time. The same applies to <code>to</code> and <code>not_to</code>.</p>
<h3>Triggering on attribute changes <a href="#triggering-on-attribute-changes"></a>
</h3>
<p>When the <code>attribute</code> option is specified, the trigger only fires
when the specified attribute <strong>changes</strong>. Changes to other attributes or
state changes are ignored.</p>
<p>For example, this trigger only fires when the boiler has been heating for 10 minutes:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> climate.living_room
      <span>attribute</span><span>:</span> hvac_action
      <span>to</span><span>:</span> <span>"heating"</span>
      <span>for</span><span>:</span> <span>"00:10:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>This trigger fires whenever the boiler’s <code>hvac_action</code> attribute changes:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> climate.living_room
      <span>attribute</span><span>:</span> hvac_action</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Holding a state or attribute <a href="#holding-a-state-or-attribute"></a>
</h3>
<p>You can use <code>for</code> to have the state trigger only fire if the state holds for some time.</p>
<p>This example fires, when the entity state changed to <code>"on"</code> and holds that
state for 30 seconds:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> light.office
      <span># Must stay "on" for 30 seconds</span>
      <span>to</span><span>:</span> <span>"on"</span>
      <span>for</span><span>:</span> <span>"00:00:30"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>When holding a state, changes to attributes are ignored. Changes to attributes
don’t cancel the hold time.</p>
<p>You can also fire the trigger when the state value changed from a specific
state, but hasn’t returned to that state value for the specified time.</p>
<p>This can be useful, e.g., checking if a media player hasn’t turned “off” for
the time specified, but doesn’t care about “playing” or “paused”.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> media_player.kitchen
      <span># Not "off" for 30 minutes</span>
      <span>from</span><span>:</span> <span>"off"</span>
      <span>for</span><span>:</span> <span>"00:30:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>Please note, that when using <code>from</code>, <code>to</code> and <code>for</code>, only the value of the
<code>to</code> option is considered for the time specified.</p>
<p>In this example, the trigger fires if the state value of the entity remains the
same for <code>for</code> the time specified, regardless of the current state value.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span> media_player.kitchen
      <span># The media player remained in its current state for 1 hour</span>
      <span>for</span><span>:</span> <span>"01:00:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>You can also use templates in the <code>for</code> option.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span>
        <span>-</span> device_tracker.paulus
        <span>-</span> device_tracker.anne_therese
      <span>to</span><span>:</span> <span>"home"</span>
      <span>for</span><span>:</span>
        <span>minutes</span><span>:</span> <span>"{{ states('input_number.lock_min')|int }}"</span>
        <span>seconds</span><span>:</span> <span>"{{ states('input_number.lock_sec')|int }}"</span>
  <span>actions</span><span>:</span>
    <span>-</span> <span>action</span><span>:</span> lock.lock
      <span>target</span><span>:</span>
        <span>entity_id</span><span>:</span> lock.my_place</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>The <code>for</code> template(s) will be evaluated when an entity changes as specified.</p>
<div>
  <div>
<p>Use quotes around your values for <code>from</code> and <code>to</code> to avoid the YAML parser from interpreting values as booleans.</p>
  </div>
</div>
<h2>Sun trigger <a href="#sun-trigger"></a>
</h2>
<h3>Sunset / Sunrise trigger <a href="#sunset--sunrise-trigger"></a>
</h3>
<p>Fires when the sun is setting or rising, i.e., when the sun elevation reaches 0°.</p>
<p>An optional time offset can be given to have it fire a set time before or after the sun event (e.g.,  45 minutes before sunset). A negative value makes it fire before sunrise or sunset, a positive value afterwards. The offset needs to be specified in number of seconds, or in a hh:mm:ss format.</p>
<div>
  <div>
<p>Since the duration of twilight is different throughout the year, it is recommended to use <a href="/docs/automation/trigger/#sun-elevation-trigger">sun elevation triggers</a> instead of <code>sunset</code> or <code>sunrise</code> with a time offset to trigger automations during dusk or dawn.</p>
  </div>
</div>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> sun
      <span># Possible values: sunset, sunrise</span>
      <span>event</span><span>:</span> sunset
      <span># Optional time offset. This example will trigger 45 minutes before sunset.</span>
      <span>offset</span><span>:</span> <span>"-00:45:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Sun elevation trigger <a href="#sun-elevation-trigger"></a>
</h3>
<p>Sometimes you may want more granular control over an automation than simply sunset or sunrise and specify an exact elevation of the sun. This can be used to layer automations to occur as the sun lowers on the horizon or even after it is below the horizon. This is also useful when the “sunset” event is not dark enough outside and you would like the automation to run later at a precise solar angle instead of the time offset such as turning on exterior lighting. For most automations intended to run during dusk or dawn, a number between 0° and -6° is suitable; -4° is used in this example:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>alias</span><span>:</span> <span>"Exterior Lighting on when dark outside"</span>
    <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> numeric_state
        <span>entity_id</span><span>:</span> sun.sun
        <span>attribute</span><span>:</span> elevation
        <span># Can be a positive or negative number</span>
        <span>below</span><span>:</span> <span>-4.0</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> switch.turn_on
        <span>target</span><span>:</span>
          <span>entity_id</span><span>:</span> switch.exterior_lighting</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>If you want to get more precise, you can use this <a href="https://gml.noaa.gov/grad/solcalc/">solar calculator</a>, which will help you estimate what the solar elevation will be at any specific time. Then from this, you can select from the defined twilight numbers.</p>
<p>Although the actual amount of light depends on weather, topography and land cover, they are defined as:</p>
<ul>
<li>
<p>Civil twilight: 0° &gt; Solar angle &gt; -6°</p>
<p>This is what is meant by twilight for the average person: Under clear weather conditions, civil twilight approximates the limit at which solar illumination suffices for the human eye to clearly distinguish terrestrial objects. Enough illumination renders artificial sources unnecessary for most outdoor activities.</p>
</li>
<li>
<p>Nautical twilight: -6° &gt; Solar angle &gt; -12°</p>
</li>
<li>
<p>Astronomical twilight: -12° &gt; Solar angle &gt; -18°</p>
</li>
</ul>
<p>A very thorough explanation of this is available in the Wikipedia article about the <a href="https://en.wikipedia.org/wiki/Twilight">Twilight</a>.</p>
<h2>Tag trigger <a href="#tag-trigger"></a>
</h2>
<p>Fires when a <a href="/integrations/tag">tag</a> is scanned. For example, a NFC tag is
scanned using the Home Assistant Companion mobile application.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> tag
      <span>tag_id</span><span>:</span> A7<span>-</span>6B<span>-</span>90<span>-</span>5F</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>Additionally, you can also only trigger if a card is scanned by a specific
device/scanner by setting the <code>device_id</code>:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> tag
      <span>tag_id</span><span>:</span> A7<span>-</span>6B<span>-</span>90<span>-</span>5F
      <span>device_id</span><span>:</span> 0e19cd3cf2b311ea88f469a7512c307d</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>Or trigger on multiple possible devices for multiple tags:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> tag
      <span>tag_id</span><span>:</span>
        <span>-</span> <span>"A7-6B-90-5F"</span>
        <span>-</span> <span>"A7-6B-15-AC"</span>
      <span>device_id</span><span>:</span>
        <span>-</span> 0e19cd3cf2b311ea88f469a7512c307d
        <span>-</span> d0609cb25f4a13922bb27d8f86e4c821</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Template trigger <a href="#template-trigger"></a>
</h2>
<p>Template triggers work by evaluating a <a href="/docs/configuration/templating/">template</a> when any of the recognized entities change state. The trigger will fire if the state change caused the template to render ‘true’ (a non-zero number or any of the strings <code>true</code>, <code>yes</code>, <code>on</code>, <code>enable</code>) when it was previously ‘false’ (anything else).</p>
<p>This is achieved by having the template result in a true boolean expression (for example <code>{{ is_state('device_tracker.paulus', 'home') }}</code>) or by having the template render <code>true</code> (example below).</p>
<p>With template triggers you can also evaluate attribute changes by using is_state_attr (like <code>{{ is_state_attr('climate.living_room', 'away_mode', 'off') }}</code>)</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> template
      <span>value_template</span><span>:</span> <span>"{% if is_state('device_tracker.paulus', 'home') %}true{% endif %}"</span>

      <span># If given, will trigger when template remains true for X time.</span>
      <span>for</span><span>:</span> <span>"00:01:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>You can also use templates in the <code>for</code> option.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> template
      <span>value_template</span><span>:</span> <span>"{{ is_state('device_tracker.paulus', 'home') }}"</span>
      <span>for</span><span>:</span>
        <span>minutes</span><span>:</span> <span>"{{ states('input_number.minutes')|int(0) }}"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>The <code>for</code> template(s) will be evaluated when the <code>value_template</code> becomes ‘true’.</p>
<p>Templates that do not contain an entity will be rendered once per minute.</p>
<div>
  <div>
<p>Use of the <code>for</code> option will not survive Home Assistant restart or the reload of automations. During restart or reload, automations that were awaiting <code>for</code> the trigger to pass, are reset.</p>
<p>If for your use case this is undesired, you could consider using the automation to set an <a href="/integrations/input_datetime"><code>input_datetime</code></a> to the desired time and then use that <a href="/integrations/input_datetime"><code>input_datetime</code></a> as an automation trigger to perform the desired actions at the set time.</p>
  </div>
</div>
<h2>Time trigger <a href="#time-trigger"></a>
</h2>
<p>The time trigger is configured to fire once a day at a specific time, or at a specific time on a specific date. There are three allowed formats:</p>
<h3>Time string <a href="#time-string"></a>
</h3>
<p>A string that represents a time to fire on each day. Can be specified as <code>HH:MM</code> or <code>HH:MM:SS</code>. If the seconds are not specified, <code>:00</code> will be used.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> time
      <span># 24-hour time format. This trigger will fire at 3:32 PM</span>
      <span>at</span><span>:</span> <span>"15:32:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Input datetime <a href="#input-datetime"></a>
</h3>
<p>The entity ID of an <a href="/integrations/input_datetime/">input datetime</a>.</p>
<table>
<thead>
<tr>
<th>has_date</th>
<th>has_time</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>true</code></td>
<td><code>true</code></td>
<td>Will fire at specified date &amp; time.</td>
</tr>
<tr>
<td><code>true</code></td>
<td><code>false</code></td>
<td>Will fire at midnight on specified date.</td>
</tr>
<tr>
<td><code>false</code></td>
<td><code>true</code></td>
<td>Will fire once a day at specified time.</td>
</tr>
</tbody>
</table>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> state
        <span>entity_id</span><span>:</span> binary_sensor.motion
        <span>to</span><span>:</span> <span>"on"</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> climate.turn_on
        <span>target</span><span>:</span>
          <span>entity_id</span><span>:</span> climate.office
      <span>-</span> <span>action</span><span>:</span> input_datetime.set_datetime
        <span>target</span><span>:</span>
          <span>entity_id</span><span>:</span> input_datetime.turn_off_ac
        <span>data</span><span>:</span>
          <span>datetime</span><span>:</span> <span>&gt;</span><span>
            {{ (now().timestamp() + 2*60*60)
               | timestamp_custom('%Y-%m-%d %H:%M:%S') }}</span>
  <span>-</span> <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span> input_datetime.turn_off_ac
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> climate.turn_off
        <span>target</span><span>:</span>
          <span>entity_id</span><span>:</span> climate.office</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Sensors of datetime device class <a href="#sensors-of-datetime-device-class"></a>
</h3>
<p>The Entity ID of a <a href="/integrations/sensor/">sensor</a> with the “timestamp” device class.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span> sensor.phone_next_alarm
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> light.turn_on
        <span>target</span><span>:</span>
          <span>entity_id</span><span>:</span> light.bedroom</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Sensors of datetime device class with offsets <a href="#sensors-of-datetime-device-class-with-offsets"></a>
</h3>
<p>When the time is provided using a sensor of the timestamp device class, an offset can be provided. This offset will be added to (or subtracted from when negative) the sensor value.</p>
<p>For example, this trigger fires 5 minutes before the phone alarm goes off.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span>
          <span>entity_id</span><span>:</span> sensor.phone_next_alarm
          <span>offset</span><span>:</span> <span>-</span><span>00:05:00</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> light.turn_on
        <span>target</span><span>:</span>
          <span>entity_id</span><span>:</span> light.bedroom</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<div>
  <div>
<p>When using a positive offset the trigger might never fire. This is due to the sensor changing before the offset is reached. For example, when using a phone alarm as a trigger, the sensor value will change to the new alarm time when the alarm goes off, which means this trigger will change to the new time as well.</p>
  </div>
</div>
<h3>Multiple times <a href="#multiple-times"></a>
</h3>
<p>Multiple times can be provided in a list. All formats can be intermixed.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> time
      <span>at</span><span>:</span>
        <span>-</span> input_datetime.leave_for_work
        <span>-</span> <span>"18:30:00"</span>
        <span>-</span> <span>entity_id</span><span>:</span> sensor.bus_arrival
          <span>offset</span><span>:</span> <span>"-00:10:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Limited templates <a href="#limited-templates"></a>
</h3>
<p>It’s also possible to use <a href="/docs/configuration/templating/#limited-templates">limited templates</a> for times.</p>
<div><div><div>
<pre><code><span>blueprint</span><span>:</span>
  <span>input</span><span>:</span>
    <span>alarm</span><span>:</span>
      <span>name</span><span>:</span> Alarm
      <span>selector</span><span>:</span>
        <span>text</span><span>:</span>
    <span>hour</span><span>:</span>
      <span>name</span><span>:</span> Hour
      <span>selector</span><span>:</span>
        <span>number</span><span>:</span>
          <span>min</span><span>:</span> <span>0</span>
          <span>max</span><span>:</span> <span>24</span>

  <span>trigger_variables</span><span>:</span>
    <span>my_alarm</span><span>:</span> <span>!input</span> alarm
    <span>my_hour</span><span>:</span> <span>!input</span> hour
  <span>trigger</span><span>:</span>
    <span>-</span> <span>platform</span><span>:</span> time
      <span>at</span><span>:</span>
      <span>-</span> <span>"sensor.{{ my_alarm | slugify }}_time"</span>
      <span>-</span> <span>"{{ my_hour }}:30:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Weekday filtering <a href="#weekday-filtering"></a>
</h3>
<p>Time triggers can be filtered to fire only on specific days of the week using the <code>weekday</code> option. This allows you to create automations that only run on certain days, such as weekdays or weekends.</p>
<p>The <code>weekday</code> option accepts:</p>
<ul>
<li>A single weekday as a string: <code>"mon"</code>, <code>"tue"</code>, <code>"wed"</code>, <code>"thu"</code>, <code>"fri"</code>, <code>"sat"</code>, <code>"sun"</code>
</li>
<li>A list of weekdays using the expanded format</li>
</ul>
<h4>Single weekday <a href="#single-weekday"></a>
</h4>
<p>This example will turn on the lights only on Mondays at 8:00 AM:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span> <span>"08:00:00"</span>
        <span>weekday</span><span>:</span> <span>"mon"</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> light.turn_on
        <span>target</span><span>:</span>
          <span>entity_id</span><span>:</span> light.bedroom</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h4>Multiple weekdays <a href="#multiple-weekdays"></a>
</h4>
<p>This example will run a morning routine only on weekdays (Monday through Friday) at 6:30 AM:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span> <span>"06:30:00"</span>
        <span>weekday</span><span>:</span>
          <span>-</span> <span>"mon"</span>
          <span>-</span> <span>"tue"</span>
          <span>-</span> <span>"wed"</span>
          <span>-</span> <span>"thu"</span>
          <span>-</span> <span>"fri"</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> script.morning_routine</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h4>Weekend example <a href="#weekend-example"></a>
</h4>
<p>This example demonstrates a different wake-up time for weekends:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>alias</span><span>:</span> <span>"Weekday alarm"</span>
    <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span> <span>"06:30:00"</span>
        <span>weekday</span><span>:</span>
          <span>-</span> <span>"mon"</span>
          <span>-</span> <span>"tue"</span>
          <span>-</span> <span>"wed"</span>
          <span>-</span> <span>"thu"</span>
          <span>-</span> <span>"fri"</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> script.weekday_morning

  <span>-</span> <span>alias</span><span>:</span> <span>"Weekend alarm"</span>
    <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span> <span>"08:00:00"</span>
        <span>weekday</span><span>:</span>
          <span>-</span> <span>"sat"</span>
          <span>-</span> <span>"sun"</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> script.weekend_morning</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h4>Combined with input datetime <a href="#combined-with-input-datetime"></a>
</h4>
<p>The <code>weekday</code> option works with all time formats, including input datetime entities:</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>-</span> <span>triggers</span><span>:</span>
      <span>-</span> <span>trigger</span><span>:</span> time
        <span>at</span><span>:</span> input_datetime.work_start_time
        <span>weekday</span><span>:</span>
          <span>-</span> <span>"mon"</span>
          <span>-</span> <span>"tue"</span>
          <span>-</span> <span>"wed"</span>
          <span>-</span> <span>"thu"</span>
          <span>-</span> <span>"fri"</span>
    <span>actions</span><span>:</span>
      <span>-</span> <span>action</span><span>:</span> notify.mobile_app
        <span>data</span><span>:</span>
          <span>title</span><span>:</span> <span>"Work Day!"</span>
          <span>message</span><span>:</span> <span>"Time to start working"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Time pattern trigger <a href="#time-pattern-trigger"></a>
</h2>
<p>With the time pattern trigger, you can match if the hour, minute or second of the current time matches a specific value. You can prefix the value with a <code>/</code> to match whenever the value is divisible by that number. You can specify <code>*</code> to match any value (when using the web interface this is required, the fields cannot be left empty).</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> time_pattern
      <span># Matches every hour at 5 minutes past whole</span>
      <span>minutes</span><span>:</span> <span>5</span>

automation 2<span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> time_pattern
      <span># Trigger once per minute during the hour of 3</span>
      <span>hours</span><span>:</span> <span>"3"</span>
      <span>minutes</span><span>:</span> <span>"*"</span>

automation 3<span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> time_pattern
      <span># You can also match on interval. This will match every 5 minutes</span>
      <span>minutes</span><span>:</span> <span>"/5"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<div>
  <div>
<p>Do not prefix numbers with a zero - using <code>'01'</code> instead of <code>'1'</code> for example will result in errors.</p>
  </div>
</div>
<h2>Persistent notification trigger <a href="#persistent-notification-trigger"></a>
</h2>
<p>Persistent notification triggers are fired when a <code>persistent_notification</code> is <code>added</code> or <code>removed</code> that matches the configuration options.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> persistent_notification
      <span>update_type</span><span>:</span>
        <span>-</span> added
        <span>-</span> removed
      <span>notification_id</span><span>:</span> invalid_config</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>See the <a href="/integrations/persistent_notification/">Persistent Notification</a> integration for more details on event triggers and the additional event data available for use by an automation.</p>
<h2>Webhook trigger <a href="#webhook-trigger"></a>
</h2>
<p>Webhook trigger fires when a web request is made to the webhook endpoint: <code>/api/webhook/&lt;webhook_id&gt;</code>. The webhook endpoint is created automatically when you set it as the <code>webhook_id</code> in an automation trigger.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> webhook
      <span>webhook_id</span><span>:</span> <span>"some_hook_id"</span>
      <span>allowed_methods</span><span>:</span>
        <span>-</span> POST
        <span>-</span> PUT
      <span>local_only</span><span>:</span> <span>true</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>You can run this automation by sending an HTTP POST request to <code>http://your-home-assistant:8123/api/webhook/some_hook_id</code>. Here is an example using the <strong>curl</strong> command line program, with an example form data payload:</p>
<div><div><div>
<pre><code><span>curl</span> -X POST -d <span>'key=value&amp;key2=value2'</span> <a href="https://your-home-assistant:8123/api/webhook/some_hook_id">https://your-home-assistant:8123/api/webhook/some_hook_id</a></code></pre>
<div>
<div><span>Bash</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>Webhooks support HTTP POST, PUT, HEAD, and GET requests; PUT requests are recommended. HTTP GET and HEAD requests are not enabled by default but can be enabled by adding them to the <code>allowed_methods</code> option. The request methods can also be configured in the UI by clicking the settings gear menu button beside the Webhook ID.</p>
<p>By default, webhook triggers can only be accessed from devices on the same network as Home Assistant or via <a href="https://www.nabucasa.com/config/webhooks/">Nabu Casa Cloud webhooks</a>. The <code>local_only</code> option should be set to <code>false</code> to allow webhooks to be triggered directly via the internet. This option can also be configured in the UI by clicking the settings gear menu button beside the Webhook ID.</p>
<p>Remember to use an HTTPS URL if you’ve secured your Home Assistant installation with SSL/TLS.</p>
<p>Note that a given webhook can only be used in one automation at a time. That is, only one automation trigger can use a specific webhook ID.</p>
<h3>Webhook data <a href="#webhook-data"></a>
</h3>
<p>Payloads may either be encoded as form data or JSON. Depending on that, its data will be available in an automation template as either <code>trigger.data</code> or <code>trigger.json</code>. URL query parameters are also available in the template as <code>trigger.query</code>.</p>
<p>Note that to use JSON encoded payloads, the <code>Content-Type</code> header must be set to <code>application/json</code>, e.g.:</p>
<div><div><div>
<pre><code><span>curl</span> -X POST -H <span>"Content-Type: application/json"</span> -d <span>'{ "key": "value" }'</span> <a href="https://your-home-assistant:8123/api/webhook/some_hook_id">https://your-home-assistant:8123/api/webhook/some_hook_id</a></code></pre>
<div>
<div><span>Bash</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h3>Webhook security <a href="#webhook-security"></a>
</h3>
<p>Webhook endpoints don’t require authentication, other than knowing a valid webhook ID. Security best practices for webhooks include:</p>
<ul>
<li>Do not use webhooks to trigger automations that are destructive, or that can create safety issues. For example, do not use a webhook to unlock a lock, or open a garage door.</li>
<li>Treat a webhook ID like a password: use a unique, non-guessable value, and keep it secret.</li>
<li>Do not copy-and-paste webhook IDs from public sources, including blueprints. Always create your own.</li>
<li>Keep the <code>local_only</code> option enabled for webhooks if access from the internet is not required.</li>
</ul>
<h2>Zone trigger <a href="#zone-trigger"></a>
</h2>
<p>Zone trigger fires when an entity is entering or leaving the zone. The entity can be either a person, or a device_tracker. For zone automation to work, you need to have setup a device tracker platform that supports reporting GPS coordinates. This includes <a href="/integrations/gpslogger/">GPS Logger</a>, the <a href="/integrations/owntracks/">OwnTracks platform</a> and the <a href="/integrations/icloud/">iCloud platform</a>.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> zone
      <span>entity_id</span><span>:</span> person.paulus
      <span>zone</span><span>:</span> zone.home
      <span># Event is either enter or leave</span>
      <span>event</span><span>:</span> enter <span># or "leave"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Geolocation trigger <a href="#geolocation-trigger"></a>
</h2>
<p>Geolocation trigger fires when an entity is appearing in or disappearing from a zone. Entities that are created by a <a href="/integrations/geo_location/">Geolocation</a> platform support reporting GPS coordinates.
Because entities are generated and removed by these platforms automatically, the entity ID normally cannot be predicted. Instead, this trigger requires the definition of a <code>source</code>, which is directly linked to one of the Geolocation platforms.</p>
<div>
  <div>
<p>This isn’t for use with <code>device_tracker</code> entities. For those look above at the <code>zone</code> trigger.</p>
  </div>
</div>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> geo_location
      <span>source</span><span>:</span> nsw_rural_fire_service_feed
      <span>zone</span><span>:</span> zone.bushfire_alert_zone
      <span># Event is either enter or leave</span>
      <span>event</span><span>:</span> enter <span># or "leave"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Device triggers <a href="#device-triggers"></a>
</h2>
<p>Device triggers encompass a set of events that are defined by an integration. This includes, for example, state changes of sensors as well as button events from remotes.
<a href="/integrations/device_trigger.mqtt/">MQTT device triggers</a> are set up through autodiscovery.</p>
<p>In contrast to state triggers, device triggers are tied to a device and not necessarily an entity.
To use a device trigger, set up an automation through the browser frontend.
If you would like to use a device trigger for an automation that is not managed through the browser frontend, you can copy the YAML from the trigger widget in the frontend and paste it into your automation’s trigger list.</p>
<h2>Calendar trigger <a href="#calendar-trigger"></a>
</h2>
<p>Calendar trigger fires when a <a href="/integrations/calendar/">Calendar</a> event starts or ends, allowing
for much more flexible automations than using the Calendar entity state which only supports a single
event start at a time.</p>
<p>An optional time offset can be given to have it fire a set time before or after the calendar event (e.g., 5 minutes before event start).</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> calendar
      <span># Possible values: start, end</span>
      <span>event</span><span>:</span> start
      <span># The calendar entity_id</span>
      <span>entity_id</span><span>:</span> calendar.light_schedule
      <span># Optional time offset</span>
      <span>offset</span><span>:</span> <span>"-00:05:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>See the <a href="/integrations/calendar/">Calendar</a> integration for more details on event triggers and the
additional event data available for use by an automation.</p>
<h2>Sentence trigger <a href="#sentence-trigger"></a>
</h2>
<p>A sentence trigger fires when <a href="/voice_control/">Assist</a> matches a sentence from a voice assistant using the default <a href="/integrations/conversation/">conversation agent</a>. Sentence triggers work with Home Assistant Assist. They will not work with external conversation agents such as OpenAI or Google Generative AI unless “Prefer handling commands locally” is enabled in the conversation agent settings.</p>
<p>Sentences are allowed to use some basic <a href="https://developers.home-assistant.io/docs/voice/intent-recognition/template-sentence-syntax/#sentence-templates-syntax">template syntax</a> like optional and alternative words. For example, <code>[it's ]party time</code> will match both “party time” and “it’s party time”.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> conversation
      <span>command</span><span>:</span>
        <span>-</span> <span>"[it's ]party time"</span>
        <span>-</span> <span>"happy (new year|birthday)"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>The sentences matched by this trigger will be:</p>
<ul>
<li>party time</li>
<li>it’s party time</li>
<li>happy new year</li>
<li>happy birthday</li>
</ul>
<p>Punctuation and casing are ignored, so “It’s PARTY TIME!!!” will also match.</p>
<h3>Related topic <a href="#related-topic"></a>
</h3>
<ul>
<li><a href="/voice_control/custom_sentences/#adding-a-custom-sentence-to-trigger-an-automation">Adding a custom sentence to trigger an automation</a></li>
</ul>
<h3>Sentence wildcards <a href="#sentence-wildcards"></a>
</h3>
<p>Adding one or more <code>{lists}</code> to your trigger sentences will capture any text at that point in the sentence. A <code>slots</code> object will be <a href="/docs/automation/templating#sentence">available in the trigger data</a>.
This allows you to match sentences with variable parts, such as album/artist names or a description of a picture.</p>
<p>For example, the sentence <code>play {album} by {artist}</code> will match “play the white album by the beatles” and have the following variables available in the action templates:</p>
<ul>
<li>
<code>{{ trigger.slots.album }}</code> - “the white album”</li>
<li>
<code>{{ trigger.slots.artist }}</code> - “the beatles”</li>
</ul>
<p>Wildcards will match as much text as possible, which may lead to surprises: “play day by day by taken by trees” will match <code>album</code> as “day” and <code>artist</code> as “day by taken by trees”.
Including extra words in your template can help: <code>play {album} by artist {artist}</code> can now correctly match “play day by day by artist taken by trees”.</p>
<h2>Multiple triggers <a href="#multiple-triggers"></a>
</h2>
<p>It is possible to specify multiple triggers for the same rule. To do so just prefix the first line of each trigger with a dash (-) and indent the next lines accordingly. Whenever one of the triggers fires, processing of your automation rule begins.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span># first trigger</span>
    <span>-</span> <span>trigger</span><span>:</span> time_pattern
      <span>minutes</span><span>:</span> <span>5</span>
      <span># our second trigger is the sunset</span>
    <span>-</span> <span>trigger</span><span>:</span> sun
      <span>event</span><span>:</span> sunset</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Multiple entity IDs for the same trigger <a href="#multiple-entity-ids-for-the-same-trigger"></a>
</h2>
<p>It is possible to specify multiple entities for the same trigger. To do so add multiple entities using a nested list. The trigger will fire and start, processing your automation each time the trigger is true for any entity listed.</p>
<div><div><div>
<pre><code><span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> state
      <span>entity_id</span><span>:</span>
        <span>-</span> sensor.one
        <span>-</span> sensor.two
        <span>-</span> sensor.three</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Disabling a trigger <a href="#disabling-a-trigger"></a>
</h2>
<p>Every individual trigger in an automation can be disabled, without removing it.
To do so, add <code>enabled: false</code> to the trigger. For example:</p>
<div><div><div>
<pre><code><span># Example script with a disabled trigger</span>
<span>automation</span><span>:</span>
  <span>triggers</span><span>:</span>
    <span># This trigger will not trigger, as it is disabled.</span>
    <span># This automation does not run when the sun is set.</span>
    <span>-</span> <span>enabled</span><span>:</span> <span>false</span>
      <span>trigger</span><span>:</span> sun
      <span>event</span><span>:</span> sunset

    <span># This trigger will fire, as it is not disabled.</span>
    <span>-</span> <span>trigger</span><span>:</span> time
      <span>at</span><span>:</span> <span>"15:32:00"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>Triggers can also be disabled based on limited templates or blueprint inputs. These are only evaluated once when the automation is loaded.</p>
<div><div><div>
<pre><code><span>blueprint</span><span>:</span>
  <span>input</span><span>:</span>
    <span>input_boolean</span><span>:</span>
      <span>name</span><span>:</span> Boolean
      <span>selector</span><span>:</span>
        <span>boolean</span><span>:</span>
    <span>input_number</span><span>:</span>
      <span>name</span><span>:</span> Number
      <span>selector</span><span>:</span>
        <span>number</span><span>:</span>
          <span>min</span><span>:</span> <span>0</span>
          <span>max</span><span>:</span> <span>100</span>

  <span>trigger_variables</span><span>:</span>
    <span>_enable_number</span><span>:</span> <span>!input</span> input_number

  <span>triggers</span><span>:</span>
    <span>-</span> <span>trigger</span><span>:</span> sun
      <span>event_type</span><span>:</span> sunrise
      <span>enabled</span><span>:</span> <span>!input</span> input_boolean
    <span>-</span> <span>trigger</span><span>:</span> sun
      <span>event_type</span><span>:</span> sunset
      <span>enabled</span><span>:</span> <span>"{{ _enable_number &lt; 50 }}"</span></code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<h2>Merging lists of triggers <a href="#merging-lists-of-triggers"></a>
</h2>
<div>
  <div>
<p>This feature requires Home Assistant version 2024.10 or later. If using this in a blueprint, set the <code>min_version</code> for the blueprint to at least this version. See the <a href="/docs/blueprint/schema/#min_version">blueprint schema documentation</a> for more details.</p>
  </div>
</div>
<p>In some advanced cases (like for blueprints with trigger selectors), it may be necessary to insert a second list of triggers into the main trigger list. This can be done by adding a dictionary in the main trigger list with the sole key <code>triggers</code>, and the value for that key contains a second list of triggers. These will then be flattened into a single list of triggers. For example:</p>
<div><div><div>
<pre><code><span>blueprint</span><span>:</span>
  <span>name</span><span>:</span> Nested Trigger Blueprint
  <span>domain</span><span>:</span> automation
  <span>input</span><span>:</span>
    <span>usertrigger</span><span>:</span>
      <span>selector</span><span>:</span>
        <span>trigger</span><span>:</span>

<span>triggers</span><span>:</span>
  <span>-</span> <span>trigger</span><span>:</span> event
    <span>event_type</span><span>:</span> manual_event
  <span>-</span> <span>triggers</span><span>:</span> <span>!input</span> usertrigger</code></pre>
<div>
<div><span>YAML</span></div>
<div><button>Copy</button></div>
</div>
</div></div></div>
<p>This blueprint automation can then be triggered either by the fixed manual_event trigger, or additionally by any triggers selected in the trigger selector. This is also applicable for <code>wait_for_trigger</code> action.</p>


  

<div>
  <h2>Related topics<a href="#related-topics"></a>
</h2>
  <ul>
    
    
    
    
    
    <li>
      <a href="/voice_control/custom_sentences/#adding-a-custom-sentence-to-trigger-an-automation">
        Adding a custom sentence to trigger an automation
      </a>
    </li>
    </ul>
</div>


  
<div>
  <h4>
<b> Help us improve our documentation</b><a href="#feedback_section"></a>
</h4>
  Suggest an edit to this page, or provide/view feedback for this page.
  <div>
    <ul>
    <li><a href="https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/automation/trigger.markdown" title="Edit this page"></a></li>
    
    <li><a href="https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&amp;url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fautomation%2Ftrigger%2F&amp;version=2025.8.2&amp;labels=current" title="Provide feedback on this page"></a></li>
    <li><a href="https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&amp;q=%22%2Fdocs%2Fautomation%2Ftrigger%2F%22&amp;in=body" title="View given feedback for this page"></a></li>
    
  </ul>
  </div>
</div>


</article>

            
          </div>


          
            
              <aside>
            
            <div>
  




  <section>
  <div>
    <ul>
      <li>
        <a href="/docs/">Overview </a>
        |
        <a href="/faq/">FAQ </a>
        |
        <a href="/docs/glossary/">Glossary </a>
      </li>

      <li>
  <a href="/docs/automation/">Automations </a>
  
  <ul>
    <li>
      <a href="/docs/automation/basics/">Basic automations </a>
      
      <ul>
        <li><a href="/docs/automation/using_blueprints/">Using automation blueprints </a></li>
        <li><a href="/docs/automation/editor/">Editor </a></li>
        <li><a href="/docs/automation/trigger/">Triggers </a></li>
        <li><a href="/docs/automation/condition/">Conditions </a></li>
        <li><a href="/docs/automation/action/">Actions </a></li>
        <li><a href="/docs/automation/modes/">Run modes </a></li>
        <li><a href="/docs/automation/services/">Automation actions </a></li>
        <li><a href="/docs/automation/templating/">Templates </a></li>
        <li><a href="/docs/automation/yaml/">YAML </a></li>
        <li><a href="/docs/automation/troubleshooting/">Troubleshooting automation </a></li>
      </ul>
      
    </li>
    <li>
      <a href="/docs/scene/">Scenes </a>
      
    </li>
    <li>
      <a href="/docs/blueprint/">Blueprints </a>
      
    </li>
    <li>
      <a href="/docs/scripts/">Scripts </a>
      
    </li>
  </ul>
  
</li>

<li>
  <a href="/dashboards">Dashboards </a>
  
</li>

<li>
  <a href="/voice_control/">Voice assistants </a>
  
</li>

<li>
  <a href="/docs/organizing/">Organization </a>
  
</li>

<li>
  <a href="/docs/energy/">Home energy management </a>
  
</li>

<li>
  <a href="/common-tasks/general/">Common tasks </a>
  
</li>

<li>
  <a href="/docs/configuration/">Advanced configuration </a>
  
</li>

<li>
  <a href="/docs/authentication/">Authentication </a>
  
</li>

<li>
  <a href="/docs/backend/">Backend </a>
  
</li>

<li>
  <a href="/docs/tools/">Tools and helpers </a>
  
</li>

<li>
  <a href="https://companion.home-assistant.io/docs">iOS and Android apps </a>
</li>

<li>
  <a href="/integrations/mqtt">MQTT </a>
  
</li>

<li>
  <ul>
    <li><a href="https://support.nabucasa.com/hc/en-us/categories/24638797677853-Home-Assistant-Green">Home Assistant Green </a></li>
    <li><a href="https://support.nabucasa.com/hc/en-us/categories/24734620813469">Home Assistant Connect ZBT-1 </a></li>
    <li><a href="https://support.nabucasa.com/hc/en-us/categories/28669861145885">Home Assistant Connect ZWA-2 </a></li>
    <li><a href="https://support.nabucasa.com/hc/en-us/categories/24734575925149-Home-Assistant-Yellow">Home Assistant Yellow </a></li>
    <li><a href="https://support.nabucasa.com/hc/en-us/categories/24451727188125-Home-Assistant-Voice-Preview-Edition">Home Assistant Voice Preview Edition </a></li>
  </ul>
</li>

    </ul>
  </div>
</section>



  <section>
        <div>
          <ul>
<li>
<a href="#trigger-id">Trigger ID</a>
<ul>
<li><a href="#video-tutorial">Video tutorial</a></li>
</ul>
</li>
<li><a href="#trigger-variables">Trigger variables</a></li>
<li><a href="#event-trigger">Event trigger</a></li>
<li><a href="#home-assistant-trigger">Home Assistant trigger</a></li>
<li><a href="#mqtt-trigger">MQTT trigger</a></li>
<li><a href="#numeric-state-trigger">Numeric state trigger</a></li>
<li>
<a href="#state-trigger">State trigger</a>
<ul>
<li><a href="#examples">Examples</a></li>
<li><a href="#triggering-on-attribute-changes">Triggering on attribute changes</a></li>
<li><a href="#holding-a-state-or-attribute">Holding a state or attribute</a></li>
</ul>
</li>
<li>
<a href="#sun-trigger">Sun trigger</a>
<ul>
<li><a href="#sunset--sunrise-trigger">Sunset / Sunrise trigger</a></li>
<li><a href="#sun-elevation-trigger">Sun elevation trigger</a></li>
</ul>
</li>
<li><a href="#tag-trigger">Tag trigger</a></li>
<li><a href="#template-trigger">Template trigger</a></li>
<li>
<a href="#time-trigger">Time trigger</a>
<ul>
<li><a href="#time-string">Time string</a></li>
<li><a href="#input-datetime">Input datetime</a></li>
<li><a href="#sensors-of-datetime-device-class">Sensors of datetime device class</a></li>
<li><a href="#sensors-of-datetime-device-class-with-offsets">Sensors of datetime device class with offsets</a></li>
<li><a href="#multiple-times">Multiple times</a></li>
<li><a href="#limited-templates">Limited templates</a></li>
<li><a href="#weekday-filtering">Weekday filtering</a></li>
</ul>
</li>
<li><a href="#time-pattern-trigger">Time pattern trigger</a></li>
<li><a href="#persistent-notification-trigger">Persistent notification trigger</a></li>
<li>
<a href="#webhook-trigger">Webhook trigger</a>
<ul>
<li><a href="#webhook-data">Webhook data</a></li>
<li><a href="#webhook-security">Webhook security</a></li>
</ul>
</li>
<li><a href="#zone-trigger">Zone trigger</a></li>
<li><a href="#geolocation-trigger">Geolocation trigger</a></li>
<li><a href="#device-triggers">Device triggers</a></li>
<li><a href="#calendar-trigger">Calendar trigger</a></li>
<li>
<a href="#sentence-trigger">Sentence trigger</a>
<ul>
<li><a href="#related-topic">Related topic</a></li>
<li><a href="#sentence-wildcards">Sentence wildcards</a></li>
</ul>
</li>
<li><a href="#multiple-triggers">Multiple triggers</a></li>
<li><a href="#multiple-entity-ids-for-the-same-trigger">Multiple entity IDs for the same trigger</a></li>
<li><a href="#disabling-a-trigger">Disabling a trigger</a></li>
<li><a href="#merging-lists-of-triggers">Merging lists of triggers</a></li>
<li><a href="#related-topics">Related topics</a></li>
</ul>
        </div>
      </section>
</div>

          </aside>
          
        </div>
      </div>

      <footer>
        <div>
  <div>
    <div>
      <div>
        <div>
          <div>
            <img src="/images/footer-logo-text.svg" height="146" alt="Home Assistant" width="300">
          </div>
          <p>
            Home Assistant is a project from the <a href="https://www.openhomefoundation.org/">Open Home Foundation</a>, sponsored by <a href="https://www.nabucasa.com/">Nabu Casa</a>.
          </p>
        </div>

        <div>
          <h3>Join us and contribute!</h3>
          <ul>
            <li><a href="https://github.com/home-assistant/">GitHub repo </a></li>
            <li><a href="https://developers.home-assistant.io">Developers Portal </a></li>
            <li><a href="https://design.home-assistant.io">Design Portal </a></li>
            <li><a href="https://data.home-assistant.io">Data Science Portal </a></li>
            <li><a href="https://community.home-assistant.io">Community Forum </a></li>
            <li><a href="https://creators.home-assistant.io/">Creator Network </a></li>
            <li><a href="https://works-with.home-assistant.io/">Works With Home Assistant </a></li>
            <li><a href="/help/reporting_issues/">Reporting issues</a></li>
          </ul>
          <h3>System status</h3>
          <ul>
            <li>
              <a href="https://alerts.home-assistant.io">Integration Alerts </a>
            </li>
            <li><a href="/security/">Security Alerts</a></li>
            <li>
              <a href="https://status.home-assistant.io">System Status </a>
            </li>
          </ul>
        </div>

        <div>
          <h3>Companion apps</h3>
          <ul>
            <li><a href="https://apps.apple.com/us/app/home-assistant/id1099568401">iOS and Apple devices</a></li>
            <li><a href="https://play.google.com/store/apps/details?id=io.homeassistant.companion.android">Android and Wear OS</a></li>
            <li><a href="https://companion.home-assistant.io/">...and more!</a></li>
          </ul>
          <h3>Governance</h3>
          <ul>
            <li><a href="/privacy/">Privacy Notices</a></li>
            <li><a href="/developers/cla/">Contributor License Agreement</a></li>
            <li><a href="/tos/">Terms of Service</a></li>
            <li><a href="/code_of_conduct/">Code of Conduct</a></li>
            <li><a href="/developers/credits/">Credits</a></li>
            <li><a href="/developers/license/">License</a></li>
          </ul>
        </div>

        <div>

          <h3>Follow us</h3>
          <p><a href="https://newsletter.openhomefoundation.org/#/portal">Sign up for our newsletter </a></p>
          <div>
            <a href="https://youtube.com/@home_assistant" title="YouTube"></a>
            <a href="https://reddit.com/r/homeassistant" title="Reddit"></a>
            <a href="https://github.com/home-assistant/home-assistant" title="GitHub"></a>
            <br>
            <a href="https://fosstodon.org/@homeassistant" title="Mastodon"></a>
            <a href="https://bsky.app/profile/home-assistant.io" title="Bluesky"></a>
            <a href="https://x.com/home_assistant" title="X"></a>
            <br>
            <a href="https://www.facebook.com/homeassistantio" title="Facebook"></a>
            <a href="https://www.instagram.com/homeassistant/" title="Instagram"></a>
            <a href="https://www.linkedin.com/company/home-assistant" title="LinkedIn"></a>
          </div>

          <div>
            <p>
              For partnership inquiries please check out <a href="https://works-with.home-assistant.io/">Works With Home Assistant</a>. For media, get in touch <a href="mailto:media@openhomefoundation.org">here</a>. For other questions, you can contact us <a href="mailto:hello@home-assistant.io">here</a> (No technical support!)
            </p>
            <p>
              Website powered by <a href="https://jekyllrb.com/">Jekyll</a><br>
              Originally based on the <a href="https://github.com/coogie/oscailte">Oscailte theme</a>
            </p>
            <a href="https://www.netlify.com">
              <img src="/images/frontpage/netlify.svg" alt="Deploys by Netlify Badge" width="114" height="51">
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

      </footer>

    </div>
    </body>
</html>

---
*Scraped from: https://www.home-assistant.io/docs/automation/trigger*