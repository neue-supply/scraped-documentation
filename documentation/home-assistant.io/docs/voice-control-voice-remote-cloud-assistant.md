Before being able to use Assist, you need to configure it.
The simplest and most effective way to use Assist is to leverage the voice providers (for speech-to-text and text-to-speech) included in Home Assistant Cloud. This page will detail how to do just that.
If you are interested in setting up a fully local voice assistant, follow this procedure instead.
## Setting up a cloud Assist pipeline 
To have the fastest processing voice assistant experience, follow these steps:
  1. If you haven’t done this already, [enable Home Assistant Cloud](https://www.nabucasa.com/config/).
  2. As soon as you’re connected to Home Assistant Cloud, a voice assistant has been created for you.
     * This voice assistant is using text-to-speech and speech-to-text engines based on the region settings of your Home Assistant user.
  3. To view the settings, go to [**Settings** > **Voice assistants**](https://my.home-assistant.io/redirect/voice_assistants) and under **Assist** , select **Home Assistant Cloud**. 
     * **Troubleshooting** : If you do not see any assistants here, you are not using the [default configuration](https://www.home-assistant.io/integrations/default_config). In this case, you need to add the following to your `configuration.yaml` file:
```
# Example configuration.yaml entry
assist_pipeline:
```

YAML
Copy
  4. If the predefined language settings work for you, skip the next step.
  5. If you want to make some changes:
     * If you like, change the name. You can pick any name that is meaningful to you.
     * If you do not agree with the predefined language, select the language that you want to speak.
     * Under **Conversation agent** , select **Home Assistant**.
     * Under **Speech-to-text** , select the language you want to speak.
     * Under **Text-to-speech** , select the language you want Assist to use when speaking to you.
     * Depending on your language, you may be able to select different language variants.
  6. That’s it. You can now speak to your device, and the device can answer in the language you defined.


## Next steps 
Once Assist is configured, you can start using it. You can now talk through your device ([Android](https://www.home-assistant.io/voice_control/android/), [iOS](https://www.home-assistant.io/voice_control/apple/) or [Voice Preview edition](https://support.nabucasa.com/hc/en-us/categories/24451727188125-Home-Assistant-Voice-Preview-Edition).
To get the best out of the voice interaction, don’t forget to check the [best practices](https://www.home-assistant.io/voice_control/best_practices/).
## Related topics 
  * [ Best practices with assist ](https://www.home-assistant.io/voice_control/best_practices/)
  * [ Creating a local assistant ](https://www.home-assistant.io/voice_control/voice_remote_local_assistant/)
  * [ Exposing devices to assist ](https://www.home-assistant.io/voice_control/voice_remote_expose_devices/)


## Related links 
  * [Voice Preview Edition - Documentation](https://support.nabucasa.com/hc/en-us/categories/24451727188125-Home-Assistant-Voice-Preview-Edition)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
