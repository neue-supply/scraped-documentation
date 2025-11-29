Home Assistant comes with [built-in sentences](https://github.com/home-assistant/intents/tree/main/sentences) contributed by the community for [dozens of languages](https://developers.home-assistant.io/docs/voice/intent-recognition/supported-languages).
## Prerequisites 
  * The entities you want to control with Assist must be [exposed to Assist](https://www.home-assistant.io/voice_control/voice_remote_expose_devices/).
  * When using the names of entities or areas, make sure to use them exactly as they are defined in Home Assistant, or, [create an alias](https://www.home-assistant.io/voice_control/aliases/).


## Device control 
### Turning entities on and off 
  * _turn on the living room light_
  * _turn off ceiling fan_
  * _turn on the TV_
  * _lock all the doors_
  * _open the main door_


### Lights 
  * _Change kitchen lights brightness to 50%_
  * _Set bed light to green_
  * _set bed light brightness to 50%_
  * _set living room brightness to 50%_
  * _set brightness to 50%_
    * Uses area of voice satellite
  * _set kitchen lights to red_
  * _set lights to red_
    * Uses area of voice satellite
  * _turn on the lights in the living room_


### Covers 
  * _Close the garage door_
  * _Open kitchen window_
  * _Which curtains are closed_
  * _Set bedroom curtain to 50%_


### Scenes and scripts 
  * _Run stealth mode script_
  * _Activate dinner scene_
  * _Turn kitchen dinner scene on_


### Media player 
  * _next item on TV_
  * _next track_
  * _next track in office_
  * _previous track_
  * _previous track in office_
  * _skip song on the TV_
  * _skip track on the TV_
  * _skip to the next song on the TV_
  * _pause|resume_
    * pauses or resumes music on voice satellite or in current area
  * _pause|resume “area” music_
    * pauses or resumes music in area
  * _pause|resume “entity”_
    * pauses or resumes music on media player
  * _unpause TV_
  * _TV unpause_
  * _set TV volume to 90 percent_
  * _change the TV volume to 90_
  * _turn TV volume down to 90 percent_
  * _Mute my TV_
  * _Unmute the television_


### Vacuum 
  * _return rover to base_
  * _start rover_


### Lists 
  * _Add bread to my shopping list_
  * _Add decorating christmas tree to my december chores list_
    * needs a todo list name “december chores”
  * _add clean out garage to weekend list_
    * needs a todo list named “Weekend”


## Date and time 
  * _what time is it?_
  * _what’s the date?_


## Timers 
### Starting 
  * _set a timer for 5 minutes_
  * _5 minute timer_
  * _set a 20 minute timer for pizza_
  * _set a timer for 1 hour and 3 minutes_
    * Break it up into hours, minutes, and seconds instead of using a technical term like _set a timer for 63 minutes_.


### Cancelling 
  * _cancel timer_
    * can’t cancel multiple timers yet
  * _cancel 5 minute timer_
  * _cancel pizza timer_
  * _cancel kitchen timer_
    * Must have been set by a voice satellite in the kitchen


### Adding/Removing Time 
  * _add 5 minutes to pizza timer_
  * _add 5 minutes to kitchen timer_
  * _remove 1 minute from timer_
  * _remove 1 minute from 5 minute timer_


### Status 
  * _timer status_
  * _how much time is left on pizza timer?_
  * _how much time is left on kitchen timer?_
  * _how much time is left on 5 minute timer?_


To learn how to set this up, refer to the [ESP32-S3-Box-3B tutorial](https://www.home-assistant.io/voice_control/s3_box_voice_assistant/).
### Combining timers and device control to add a delay 
Unlike regular voice timers, delayed commands cannot be canceled or modified.
  * _Turn off the lights in the living room in 5 minutes_
  * _Pause TV in 10 minutes_
  * _Open the blinds in 5 minutes_


## Aborting 
  * _Nevermind_ : If you triggered the wake word by mistake and want to stop Home Assistant from listening


## Troubleshooting 
The list of supported sentences is constantly being updated for each language. There are so many possible sentences that they cannot be all listed here. To find out what works in your language, follow these steps.
  1. If the voice assistant doesn’t understand you, you may need to rephrase your sentence a bit. Or check if the entityAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/) or areaAn area in Home Assistant is a [logical grouping](https://www.home-assistant.io/docs/organizing/) of devices and entities that are meant to match areas (or rooms) in the physical world: your home. For example, the `living room` area groups devices and entities in your living room.[ [Learn more]](https://www.home-assistant.io/docs/organizing/areas/) name is correct for your environment.
  2. Take a look at the test sentences:
     * On GitHub, in the [tests](https://github.com/home-assistant/intents/tree/main/tests) folder, open the subfolder for your language.
     * Look through the test files to see the example sentences that have been tested.
     * The second part of the file name shows the intentIntent is a term used with voice assistants. The intent is what Home Assistant thinks you want it to do when it extracts a command from your voice or text utterance.[ [Learn more]](https://developers.home-assistant.io/docs/intent_builtin), the first part shows the domainEach integration in Home Assistant has a unique identifier: The domain. It is often shown as the first part (before the dot) of entity IDs.. For some domainsEach integration in Home Assistant has a unique identifier: The domain. It is often shown as the first part (before the dot) of entity IDs., such as covers, fans, and light, there are specific sentences. The other domainsEach integration in Home Assistant has a unique identifier: The domain. It is often shown as the first part (before the dot) of entity IDs. are covered by the generic _homeassistant__.
     * The screenshot below shows sentences used to test the command to turn on the lights. Note that _Living room_ here is just a place holder. It could be any areaAn area in Home Assistant is a [logical grouping](https://www.home-assistant.io/docs/organizing/) of devices and entities that are meant to match areas (or rooms) in the physical world: your home. For example, the `living room` area groups devices and entities in your living room.[ [Learn more]](https://www.home-assistant.io/docs/organizing/areas/) that you have in your home.
  3. View the sentence definition for the tests:
     * On GitHub, in the [sentences](https://github.com/home-assistant/intents/tree/main/sentences) folder, open the subfolder for your language.
     * Open the file of interest.
       * () mean alternative elements.
       * [] mean optional elements.
       * <> mean an expansion rule. To view these rules, search for `expansion_rules` in the [_common.yaml](https://github.com/home-assistant/intents/blob/main/sentences/en/_common.yaml) file.
       * The syntax is explained in detail in the [template sentence syntax documentation](https://developers.home-assistant.io/docs/voice/intent-recognition/template-sentence-syntax/).
  4. View the [sentence definition](https://github.com/home-assistant/intents/tree/main/sentences) for your language.
  5. View the [response definition](https://github.com/home-assistant/intents/tree/main/responses)
  6. If there are issues when asking for the weather forecast, check the [troubleshooting section](https://www.home-assistant.io/voice_control/troubleshooting/) to see common errors.


## More sentences 
You can extend the [built-in sentences](https://github.com/home-assistant/intents/tree/main/sentences) or [add your own](https://www.home-assistant.io/voice_control/custom_sentences) to trigger any action in Home Assistant.
## Related topics 
  * [ Create your own sentences ](https://www.home-assistant.io/voice_control/custom_sentences/)
  * [ Sentence troubleshooting ](https://www.home-assistant.io/voice_control/troubleshooting/)
  * [ Best practices with assist ](https://www.home-assistant.io/voice_control/best_practices/)


## Related links 
  * [Built-in sentence definitions](https://github.com/home-assistant/intents/tree/main/sentences)
  * [Built-in response definitions](https://github.com/home-assistant/intents/tree/main/responses)
  * [Template sentence syntax documentation](https://developers.home-assistant.io/docs/voice/intent-recognition/template-sentence-syntax/)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
