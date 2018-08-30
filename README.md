# Tips

> Just Tips for development and env settings

## Troubleshooting

- loud "beep" during reboot/shutdown
	- on linux
	- on laptop
	- solution
		1. open `/etc/inputrc`
		2. uncomment `set bell-style none` 

## Touchpad shortcut with linux

- clone toggle-touchpad-with-linux repo.
	```bash
	$ git clone https://github.com/cliche90/toggle-touchpad-with-linux
	```
- move `toggle_touchpad` file to somewhere
	```bash
	$ cd toggle-touchpad-with-linux
	$ mkdir ~/utils
	$ mv toggle_touchpad ~/utils
	```
- assign right to excute `toggle_touchpad` file
	```bash
	$ sudo chmod +x toggle_touchpad
	```
- register shortcut
	- Settings > Keyboard > Keyboard Shortcuts
	- Command `~/toggle_touchpad`

## Saving Battery

- install tlp
	```bash
	$ sudo apt install tlp tlp-rdw
	$ sudo tlp start
	```
