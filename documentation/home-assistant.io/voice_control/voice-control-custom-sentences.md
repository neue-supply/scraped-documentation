You may add your own sentences to the intent recognizer by either extending an [existing intent](https://developers.home-assistant.io/docs/intent_builtin/) or creating a new one. You may also [customize responses](https://www.home-assistant.io/voice_control/custom_sentences_yaml#customizing-responses) for existing intents.
## Prerequisites 
### Prerequisites 
You need a working Assist configuration. If you haven’t done so yet, check [Assist’s starting page](https://www.home-assistant.io/voice_control/) to get you ready with your setup.
### To add a custom sentence to trigger an automation 
This is the easiest method to get started with custom sentences for automations.
  1. Under **[Settings> Automations & Scenes](https://my.home-assistant.io/redirect/automations)**, in the bottom right corner, select **Create automation**.
  2. In the **Trigger** drop-down menu, select **Sentence**.
  3. Enter one or more sentences that you would like to trigger an automation.
     * Do not use punctuation.
     * You can add multiple sentences. They will then all trigger that automation. 
  4. To add a custom response, select **Add action**. Scroll all the way down and select **Other actions**.
     * Then, select **Set conversation response**. 
  5. In the text field, enter the response you want to hear from Assist and select **Save**.
     * You can also use [wildcards](https://www.home-assistant.io/docs/automation/trigger/#sentence-wildcards). For example, the trigger:
```
play {album} by {artist}
```

YAML
Copy
could have the response:
```
Playing {{ trigger.slots.album }} by {{ trigger.slots.artist }}
```

YAML
Copy
     * For more details, refer to [conversation response script action](https://www.home-assistant.io/docs/scripts/#respond-to-a-conversation).
  6. To test the automation, go to **Overview** and in the top right corner, open Assist.
     * Enter one of the sentences.
  7. If it did not work out, checkout the [troubleshooting](https://www.home-assistant.io/voice_control/troubleshooting/) section.
     * One of the causes could be that the device you’re targeting has not been exposed to Assist.
  8. Pick up your voice control device and speak the custom sentence.
     * Your automation should now be triggered.


### Setting up custom sentences in configuration.yaml 
To set up custom sentences in your configuration file follow [this tutorial](https://www.home-assistant.io/voice_control/custom_sentences_yaml/).
## Related devices and installation tutorials 
  * [$13 voice assistant for Home Assistant](https://www.home-assistant.io/voice_control/thirteen-usd-voice-remote/)
  * [S3-BOX-3 voice assistant](https://www.home-assistant.io/voice_control/s3_box_voice_assistant/)
  * [Assist for Apple](https://www.home-assistant.io/voice_control/apple/)
  * [Assist for Android](https://www.home-assistant.io/voice_control/android/)


## Related topics 
  * [ Conversation response script action ](https://www.home-assistant.io/docs/scripts/#respond-to-a-conversation)


## Related links 
  * [View existing intents](https://developers.home-assistant.io/docs/intent_builtin/)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
