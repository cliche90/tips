# Tips

> Just Tips for development and env settings

## Troubleshooting

- loud "beep" during reboot/shutdown
	- on linux
	- on laptop
	- solution
		1. open `/etc/inputrc`
		2. uncomment `set bell-style none` 
		
## korean keyboard setting
- install `fcitx-hangul`
  ```bash
  $ sudo apt-get install fcitx-hangul
  ```

- install laguage support for hangul
  - System Settings > Language Support
  - select install button on popup
  - wait installing

- keyboard input method system
  - change 'IBus' to 'fcitx'

- Reboot

- On Right Top, click tray icon shaped keyboard
  - click > configure > + button
  - uncheck 'Only Show Current Language'
  - search 'Hangul'
  - add 'Hangul'

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
	
## Proxy

- docker proxy
	- docker application proxy setting
		- `/etc/systemd/system/docker.service.d/proxy.conf` file
		
			```bash
			[Service]
			Environment="HTTP_PROXY=http://proxy.com:8080/"
			Environment="HTTPS_PROXY=https://proxy.com:8080/"
			Environment="NO_PROXY=localhost,127.0.0.1"
			```
		- restart docker service
			```bash
			$ sudo systemctl start docker
			$ sudo service docker start
			```
	- docker client(instances) proxy setting
		- `~/.docker/config.json`
		
			```bash
			{
				"proxies": {
					"default": {
						"httpProxy": "http://proxy.com:8080/",
						"httpsProxy": "https://proxy.com:8080/",
						"noProxy": "*.example.com,localhost,127.0.0.1"
					}
				}
			}
			```
		
