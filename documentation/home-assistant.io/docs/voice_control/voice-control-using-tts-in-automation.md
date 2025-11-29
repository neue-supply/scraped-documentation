This procedure shows you how to create a text-to-speech actionActions are used in several places in Home Assistant. As part of a script or automation, actions define what is going to happen once a trigger is activated. In scripts, an action is called _sequence_.[ [Learn more]](https://www.home-assistant.io/docs/automation/action/). For this, we use our local text-to-speech engine, Piper, and the media player serviceThe term “service” in Home Assistant is used in the sense of an **information service**. For example, the municipal waste management service that provides entities for organic, paper, and packaging waste. In terms of functionality, the information service is like a device. It is called _service_ to avoid confusion, as it does not come with a piece of hardware.. Home Assistant can then speak to you over your media player as part of an automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/).
  1. Go to **[Settings> Automations & Scenes](https://my.home-assistant.io/redirect/automations)**, and select **Create automation**.
  2. Select **Create new automation** , then **Add action**.
  3. From the drop-down menu, search for or select **TTS: Speak**. 
  4. To use fully local text-to-speech processing, select **piper** from the **Choose entity** control. 
  5. Select the media player you want the automation to use.
  6. Enter the text you want to hear for this automation. 
  7. Your text-to-speech action is now ready to be used in your script or automation.
  8. Save your action.


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
