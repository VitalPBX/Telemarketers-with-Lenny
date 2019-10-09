# Telemarketers-with-Lenny
Telemarketers are the worst. They have no souls. They feed off of the misery of others. No one likes them. Luckily, a nice British gentleman by the name of Lenny has come to save the day.

First, you will want to create the Lenny context in Asterisk. SSH into your VitalPBX and use your favorite editor to edit /etc/asterisk/ombutel/extensions__80_lenny.conf. Add the following lines of code:

<pre>
vi /etc/asterisk/ombutel/extensions__80_lenny.conf

[Lenny]
exten => talk,1,Set(i=${IF($["0${i}"="016"]?7:$[0${i}+1])})
same => n,ExecIf($[${i}=1]?MixMonitor(${UNIQUEID}.wav))
same => n,Playback(Lenny/Lenny${i})
same => n,BackgroundDetect(Lenny/backgroundnoise,1500)
</pre>

Then copy the audio file in /var/lib/asterisk/sounds/en/Lenny directory

