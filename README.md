# Tips

> 개발 및 환경 설정에 대한 단순한 팁들입니다.

## Troubleshooting

- (LG 그램에 Ubuntu 설치 후) 재부팅/종료 시에 커다란 "beep"(비프음) 이 발생하는 경우
	- 리눅스(Ubuntu 기준) 설치
	- 노트북에(정확히는 LG 그램에)만 해당
	- 해결방법
		1. `ukuu`를 설치합니다.
			```bash
			$ sudo apt-add-repository -y ppa:teejee2008/ppa
			$ sudo apt update
			$ sudo apt install ukuu
			```
		2. `ukuu-gtk`를 실행합니다.
			```bash
			$ sudo ukuu-gtk
			```
		3. GUI 상에서 최신의 커널을 설치합니다.
		4. 재부팅을 합니다.
		
## zsh 및 테마 설치
- `zsh`를 설치합니다.
  ```bash
  $ sudo apt update
  $ sudo apt install -y zsh
  $ zsh --version
  ```
- `zsh`를 기본 쉘로 지정합니다.
  ```bash
  $ whereis zsh
  # zsh: /usr/bin/zsh ~~~
  $ sudo usermod -s /usr/bin/zsh $(whoami)
  ```
- 재부팅을 합니다.
- 새롭게 터미널을 열고, 숫자 `2` 를 누릅니다.
- `powerline`과 `powerline-fonts`을 설치합니다.
  ```bash
  $ sudo apt install -y powerline fonts-powerline
  ```
- `zsh-theme-powerlinelevel9k` 테마를 설치합니다.
  ```bash
  $ sudo apt install zsh-theme-powerlevel9k
  $ echo "source /usr/share/powerlevel9k/powerlevel9k.zsh-theme" >> ~/.zshrc
  ```
- `zsh-syntax-highligting`을 설치합니다.
  ```bash
  $ sudo apt install zsh-syntax-highlighting
  $ echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
  ```
- 다시 터미널을 엽니다.
- (설치되어있지 않다면) `git`을 설치합니다.
  ```bash
  $ sudo apt install -y git
  ```
- `oh-my-zsh`을 설치합니다.
  ```bash
  $ sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  ```
- `powerlevel9k` 테마를 활성화합니다.
  ```bash
  ~ echo "source /usr/share/powerlevel9k/powerlevel9k.zsh-theme" >> ~/.zshrc
  ~ echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
  ```
- 테마의 적용확인을 위해 `git`을 테스트 해 봅니다.
  ```bash
  $ mkdir git-test
  $ cd git-test
  $ git init
  ```

## 한글 키보드 설정
- `fcitx-hangul`를 설치합니다.
  ```bash
  $ sudo apt install fcitx-hangul
  ```

- 언어지원을 열어 언어팩을 설치합니다.
  - 시스템 설정 > 언어지원
  - 팝업이 뜨면 설치 버튼을 누릅니다.
  - 설치가 끝나길 기다립니다.

- 키보드 입력 방식 설정을 변경합니다.
  - 'IBus'에서 'fcitx'로 변경

- 재부팅을 합니다.

- 우측 상단의 키보드 모양의 트레이 아이콘을 클릭합니다.
  - 클릭 > 설정 > + 버튼
  - 아래쪽의 현재 사용중인 언어만 보이도록 하는 체크박스 옵션을 해제합니다.
  - 'Hangul'을 검색합니다.
  - 'Hangul'을 추가합니다.

## 리눅스에서의 터치패드 단축키
> (LG 그램을 기준으로)노트북에 Ubuntu 설치시 터치패드를 켜고 끄는 단축키가 제대로 작동하지 않을 경우에 적용합니다.

- `toggle-touchpad-with-linux` 프로젝트를 clone 합니다.
	```bash
	$ git clone https://github.com/cliche90/toggle-touchpad-with-linux
	```
- `toggle_touchpad` 파일을 원하는 위치에 놓습니다.
	```bash
	$ cd toggle-touchpad-with-linux
	$ mkdir ~/utils
	$ mv toggle_touchpad ~/utils
	```
- `toggle_touchpad` 파일에 실행 권한을 부여합니다.
	```bash
	$ sudo chmod +x toggle_touchpad
	```
- 단축키를 등록합니다.
	- 설정 > 키보드 > 키보드 단축키
	- `toggle_touchpad`를 실행하도록 단축키 추가

## 배터리 절약
- `tlp`를 설치합니다.
	```bash
	$ sudo apt install tlp tlp-rdw
	$ sudo tlp start
	```
	
## 프록시(Proxy)

- 도커 프록시(docker proxy)
	- docker 자체의 프록시 설정
		- `/etc/systemd/system/docker.service.d/proxy.conf` 파일
		
			```bash
			[Service]
			Environment="HTTP_PROXY=http://proxy.com:8080/"
			Environment="HTTPS_PROXY=https://proxy.com:8080/"
			Environment="NO_PROXY=localhost,127.0.0.1"
			```
		- docker 서비스 재시작
			```bash
			$ sudo systemctl start docker
			$ sudo service docker start
			```
	- docker 인스턴스 사이의 프록시 설정
		- `~/.docker/config.json` 파일
		
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
		
