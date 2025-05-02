# Qubesfetch
custom fetch scripts for QubesOS

# Instructions

1. Download the qubesfetch script (make sure you are in the home directory)

`wget https://raw.githubusercontent.com/tillay/qubefetch/refs/heads/main/qubesfetch&&chmod +x qubesfetch`

2. Download the fetchinfo.sh script

`wget https://raw.githubusercontent.com/tillay/qubefetch/refs/heads/main/fetchinfo.sh&&chmod +x ~/fetchinfo.sh`

3. Move fetchinfo.sh script into dom0

`qvm-run --pass-io <qube-you-downloaded-in> 'cat ~/fetchinfo.sh' > fetchinfo.sh`

4. Make a keyboard shortcut to reload dom0-only fetch infos (and bind it to something)

`/home/<your-dom0-user>/fetchinfo.sh personal school work`

To use:

1. press the keybind to get dom0 fetch infos

2. Wait a few seconds for dom0 to interface with less trusted qubes

3. run qubesfetch shell script

4. gaze at your pretty system

![screenshot](https://raw.githubusercontent.com/tillay8/qubesfetch/refs/heads/main/screenshot.png)

## Bonus: Script to take screenshot on Qubes

1. Make sure xclip is installed in target qube(s)

2. Put this shell script in dom0 home directory and chmod it

3. Make keyboard shortcut through GUI's to run `/home/<username>/screenshot.sh <target-qube>` 

```
QUBE=$1
SCREENSHOT="/home/$USER/screenshot.png"
INCOMING='/home/user/QubesIncoming/dom0/screenshot.png'
xfce4-screenshooter -r -s $SCREENSHOT
qvm-move-to-vm $QUBE $SCREENSHOT
qvm-run --pass-io $QUBE -- 'xclip -selection clipboard -t image/png -i '$INCOMING' &&rm '$INCOMING''
```
