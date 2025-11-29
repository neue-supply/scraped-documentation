This tutorial will guide you to turn an ATOM Echo into a voice assistant. Pick up the tiny device to talk to your smart home. Issue commands and get responses!
## Prerequisites 
  * Home Assistant 2023.10 or later, installed with the Home Assistant Operating System. If you do not have Home Assistant installed yet, refer to the [installation page](https://www.home-assistant.io/installation/) for instructions.
  * [Home Assistant Cloud](https://www.home-assistant.io/voice_control/voice_remote_cloud_assistant/) or a manually configured [Assist Pipeline](https://www.home-assistant.io/voice_control/voice_remote_local_assistant)
  * Have [enabled a wake word](https://www.home-assistant.io/voice_control/install_wake_word_add_on/) for your voice assistant
  * The password to your 2.4 GHz Wi-Fi network
  * Chrome (or a Chromium-based browser like Edge) on desktop (not Android/iOS)
  * [M5Stack ATOM Echo Development Kit](https://shop.m5stack.com/products/atom-echo-smart-speaker-dev-kit?ref=NabuCasa)
  * USB-C cable to connect the ATOM Echo


## Installing the software onto the ATOM Echo 
Before you can use this device with Home Assistant, you need to install a bit of software on it.
  1. Make sure this page is opened in a Chromium-based browser on a desktop. It does not work on a tablet or phone.
     * Select the **Connect** button below. If your browser does not support web serial, you will see a warning instead of a button.
     * **For advanced users** : The configuration file is available on [GitHub](https://github.com/esphome/wake-word-voice-assistants/blob/main/m5stack-atom-echo/m5stack-atom-echo.yaml).
  2. To connect the ATOM Echo to your computer, follow these steps:
     * In the pop-up window, view the available ports.
     * Plug the USB-C cable into the ATOM Echo and connect it to your computer.
     * In the pop-up window, there should now appear a new entry. Select this USB serial port and select **Connect**.
     * **Troubleshooting** : If no new port shows, your system may be missing a driver. Close the pop-up window. 
       * In the dialog, select the CH342 driver, install it, then **Try again**. 
  3. Select **Install Voice Assistant** , then **Install**.
     * Once the installation is complete, select **Next**.
     * Add the ATOM Echo to your Wi-Fi: 
       * When prompted, select your network from the list and enter the credentials to your 2.4 GHz Wi-Fi network.
       * Select **Connect**.
       * The ATOM Echo now joined your network. Select **Add to Home Assistant**.
  4. This opens the **My** link to Home Assistant.
     * If you have not used My Home Assistant before, you will need to configure it. If your Home Assistant URL is not accessible on `http://homeassistant.local:8123`, replace it with the URL to your Home Assistant instance.
     * Open the link.
  5. Select **OK**.
  6. This starts the a wizard to customize the your voice assistant.
     * Follow the wizard steps to define the wake word and choose the voice.
     * When you are finished, select **Done**.
  7. Your ATOM Echo is connected to Home Assistant over Wi-Fi. You can now move it to any place in your home with a USB power supply.
  8. Congratulations! You can now voice control Home Assistant. Now give some commands.


## Controlling Home Assistant over the ATOM Echo 
  1. Say the wake word you configured. For example, use “OK, Nabu”. 
     * Wait for the LED to start blinking in blue.
  2. Say a [supported voice command](https://www.home-assistant.io/voice_control/builtin_sentences/). For example, _Turn off the light in the kitchen_. 
     * While you are speaking, the blue LED keeps pulsing.
     * Once the intent has been processed, the LED lights up in green and Home Assistant confirms the action. 
       * Make sure you’re using the area name exactly as you defined it in Home Assistant.
       * You can also ask a question, such as 
         * _Is the front door locked?_
         * _Which lights are on in the living room?_
  3. Your command is not supported? Add your own commands using [a sentence trigger](https://www.home-assistant.io/voice_control/custom_sentences/).
  4. You find ATOM Echo takes too long to start processing your command? 
     * Adjust the silence detection settings.
     * Go to [**Settings** > **Devices & services**](https://my.home-assistant.io/redirect/integrations) and select the **ESPHome** integration.
     * Under **M5Stack ATOM Echo** , select **1 device**. Under **Configuration** , change the **Finished speaking detection**.
     * This setting defines how much silence is needed for Assist to find you’re done speaking and it can start processing your command.


## Troubleshooting 
Are things not working as expected?
  * Checkout the [general troubleshooting section for Assist](https://www.home-assistant.io/voice_control/troubleshooting/).


## Removing the Wi-Fi credentials from the ATOM Echo 
If you no longer use the device or want to pass it on to someone else, you can remove the Wi-Fi credentials that are stored on the device.
  1. Make sure this page is opened in a Chromium-based browser on a desktop. It does not work on a tablet or phone.
     * Select the **Connect** button below. If your browser does not support web serial, you will see a warning instead of a button.
  2. To connect the ATOM Echo to your computer, follow these steps:
     * In the pop-up window, view the available ports.
     * Plug the USB-C cable into the ATOM Echo and connect it to your computer.
     * In the pop-up window, there should now appear a new entry. Select this USB serial port and select **Connect**.
  3. In the dialog, select **Erase user data**.
     * **Result** : Your Wi-Fi credentials are deleted from the device.
     * The firmware stays on the device.


## Related topics 
  * [ Create your own wake words ](https://www.home-assistant.io/voice_control/create_wake_word/)
  * [ Creating a cloud assistant ](https://www.home-assistant.io/voice_control/voice_remote_cloud_assistant/)
  * [ General troubleshooting section for assist ](https://www.home-assistant.io/voice_control/troubleshooting/)
  * [ Using a sentence trigger ](https://www.home-assistant.io/voice_control/custom_sentences/)
  * [ Access to your configuration files ](https://www.home-assistant.io/common-tasks/os/#configuring-access-to-files)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
