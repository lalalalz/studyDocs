# 우분투 SSH 설정

## 1. 우분투 SSH 설정

### 1.1. SSH Sever 설치
--------------------------------------------------------------------------------
  원격으로 접속할 PC의 Open SSH Server를 설치한다. 

``` terminal

	$ sudo apt update
	$ sudo apt install openssh-server

```

### 1.2. SSH Sever 실행 확인
--------------------------------------------------------------------------------
  SSH를 설치하면 자동으로 실행되며 다음 명령어를 통해 실행을 확인할 수 있다.

``` terminal

	$ sudo systemctl status ssh
	ssh.service - OpenBSD Secure Shell server
   	  Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
      Active: active (running) since Tue 2021-08-03 19:12:39 KST; 6h ago
        Docs: man:sshd(8)
              man:sshd_config(5)
    Main PID: 22984 (sshd)
      Tasks: 1 (limit: 19102)
     Memory: 8.9M
     CGroup: /system.slice/ssh.service
             └─22984 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups

```

### 1.3. SSH 작동원리
--------------------------------------------------------------------------------
  Secure Shell Protocol의 약어로 네트워크 프로토콜이다. 다른 인터넷 서비스 프로토콜보다 보안성이 뛰어나다는 특징을 가지고 있어 원격 제어 상황에서 사용할 수 있다. 

  SSH는 SSH-Sever에 접속할 때 비대칭키 방식을 사용하여 SSH-Client를 인증한다. 그렇게 인증이 된 후에는 대칭키 방식을 사용하여 메시지를 주고받는다. 이와 같은 절차들을 통해 보안성을 확보하는 것이다. 

  

