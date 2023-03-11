# rtl-sdr-close-call-monitor

These scripts use an RTL-SDR device to detect peak signals on a user specified frequency range. The scripts can also make an automatic blacklist so that different sources of RF noise won't cause continuous false positives. There are three scripts provided as examples. The scripts can be used to monitor and log certain frequencies for a wide range of purposes such as: 

- In criminal investigations, a close-call RF signal monitor can be used to detect and track communication signals used by criminals. This can help law enforcement agencies gather intelligence and evidence, and even prevent future crimes from being committed. By analyzing the frequency and strength of signals emitted by communication devices, a close-call RF signal monitor can provide valuable insights into the movements and activities of suspects, allowing investigators to piece together a timeline of events and make informed decisions about how to proceaed with a case.

- In military operations, a close-call RF signal monitor can be used to identify and track enemy communication signals, providing valuable intelligence for strategic decision-making.

- In scientific research, a close-call RF signal monitor can be used to collect and analyze data related to wireless communication systems, providing valuable insights for thesis projects and other research studies.


### Dependencies

This code requires the following dependencies to run:

    numpy
    rtlsdr
    playsound
    requests

These dependencies can be installed by running:

pip install -r requirements.txt

or

pip install numpy rtlsdr playsound

### Usage

Connect an RTL-SDR device to your computer.
    Open a terminal and navigate to the directory containing the python script.
    Choose a script that you want to use.

   Run the monitor with sound script using `python3 monitor_with_sound.py` or run the CSV logging script using `python3 csv_logging.py` (ThingsBoard and JSON loggin in the end of this section)

   The script will prompt you to enter various options:
    
   `Sample rate`: choose between the default value of 2.56MHz or a custom value (in Hz).
        
   `Frequency correction`: choose between the default value of 18 PPM or a custom value (in PPM).
        
   `Gain`: choose between the default value of 30dB or a custom value (in dB).
        
   `Start frequency`: the frequency to start scanning from (in Hz).
        
   `End frequency`: the frequency to stop scanning at (in Hz).
        
   `Number of samples`: choose between the default value of 2^16 or a custom value (in the format of x**xx).
        
   `Squelch level`: the threshold for the squelch level, i.e., the level below which a signal is considered to be noise.
        
   `Blacklist frequencies manually`: whether or not to manually blacklist frequencies. If yes, enter the frequency to blacklist (in MHz).
        
   `Scan time for automated frequency blacklisting`: choose between the default value of 60 seconds or a custom value (in seconds).
        
   The script will then scan the specified frequency range until you interrupt it by pressing Ctrl+C). Any frequencies below the squelch level or that are    blacklisted will be skipped. Any other frequencies will play an audible alarm in the sound script and in CSV logging script a line will be written to      the CSV file.

For ThingsBoard and JSON logging:

   Run `python3 thingsboard_and_json_logging.py`
   
   The usage is the same as the other scripts but the script will also ask for `access token of the ThingsBoard server`, `ip address of the ThingsBoard server` and `port of the ThingsBoard server`.

   The script will then scan the specified frequency range until you interrupt it by pressing Ctrl+C). Any frequencies below the squelch level or that are    blacklisted will be skipped. Any other frequencies will be sent to the ThingsBoard server and a line will be written to the JSON file.

How to install ThingsBoard:

   https://thingsboard.io/docs/user-guide/install/installation-options/
        
### More about RTL-SDR

https://www.rtl-sdr.com/about-rtl-sdr/

It is important to know the basic capabilities of an RTL-SDR before using this script since you'll have to set different parameters correctly in order to have this script work as intented. 

### Raspberry pi 4

Install rtl-sdr package:
`sudo apt install rtl-sdr`

Download rtl-sdr.rules file from the official repository:
`sudo wget -O /etc/udev/rules.d/rtl-sdr.rules https://raw.githubusercontent.com/osmocom/rtl-sdr/master/rtl-sdr.rules`

Reload udev rules by running the following command:
`sudo udevadm control --reload-rules`

Unplug and plug back in the RTL-SDR device.

Install the GStreamer library and its Python bindings:
`sudo apt-get install gstreamer1.0-plugins-good gstreamer1.0-tools python3-gi python3-gst-1.0`

Make sure that the GST_PLUGIN_PATH and LD_LIBRARY_PATH environment variables are set:
`export GST_PLUGIN_PATH=/usr/lib/gstreamer-1.0:/usr/lib/arm-linux-gnueabihf/gstreamer-1.0`
`export LD_LIBRARY_PATH=/usr/lib/gstreamer-1.0:/usr/lib/arm-linux-gnueabihf/gstreamer-1.0`


### Sound file

The sound file: "warning.wav" is from a royalty-free source: https://bigsoundbank.com/detail-2381-aerospace-beep-2.html.

### Contributing

If you would like to contribute to this project, feel free to submit a pull request or open an issue.

### License

This code is licensed under the GNU General Public License v3.0. See the LICENSE file for details.
