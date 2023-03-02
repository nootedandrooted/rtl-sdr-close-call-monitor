# rtl-sdr-close-call-monitor

This script uses an RTL-SDR device to detect peak signals on a user specified frequency range. The script can also make an automatic blacklist so that different sources of RF noise won't cause continuous false positives. This script can be used to monitor certain frequencies for a wide range of purposes such as: 

- In criminal investigations, a close-call RF signal monitor can be used to detect and track communication signals used by criminals. This can help law enforcement agencies gather intelligence and evidence, and even prevent future crimes from being committed. By analyzing the frequency and strength of signals emitted by communication devices, a close-call RF signal monitor can provide valuable insights into the movements and activities of suspects, allowing investigators to piece together a timeline of events and make informed decisions about how to proceed with a case.

- In military operations, a close-call RF signal monitor can be used to identify and track enemy communication signals, providing valuable intelligence for strategic decision-making.

- In scientific research, a close-call RF signal monitor can be used to collect and analyze data related to wireless communication systems, providing valuable insights for thesis projects and other research studies.


### Dependencies

This code requires the following dependencies to run:

    numpy
    rtlsdr
    playsound

These dependencies can be installed by running:

pip install -r requirements.txt

or

pip install numpy rtlsdr playsound

### Usage
Connect an RTL-SDR device to your computer.
    Open a terminal and navigate to the directory containing the python script.
    Run the script using `python3 name_of_the_script_here.py`.
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
        
   The script will then scan the specified frequency range until you interrupt it by pressing Ctrl+C). Any frequencies below the squelch level or that are    blacklisted will be skipped. Any other frequencies will play an audible alarm.
   
        
### More about an RTL-SDR here:
https://www.rtl-sdr.com/about-rtl-sdr/

It is important to know the basic capabilities of an RTL-SDR before using this script since you'll have to set different parameters correctly in order to have this script work as intented. 

License

This code is licensed under the GNU General Public License v3.0. See the LICENSE file for details.
