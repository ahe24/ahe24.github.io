---
title: "Install Jenkins!"
date: 2024-03-26 08:26:28 -0400
categories: Jenkins
---

## 루트 인증서 설치

Jenkins의 저장소 추가시 인증서 에러가 발생할 경우를 대비해 루트 인증서를 설치 합니다.

```bash
# yum -y install ca-certificates
```

![install ca-cert](<../assets/images/Pasted image 20240318080718.png>)

## 패키지 저장소 추가

이제 Jenkins의 패키지 저장소를 추가합니다.

```bash
# wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

![Jenkins의 패키지 저장소](<../assets/images/Pasted image 20240318081203.png>)

## GPG 키 추가

그런 다음 Jenkins GPG 키를 다음과 같이 추가 합니다.

```bash
# rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```

## JAVA 11 설치

Jenkins 최신 버전은 JAVA 11 이상에서 구동됨.

```bash
# curl -L https://corretto.aws/downloads/latest/amazon-corretto-11-x64-linux-jdk.rpm -o jdk11.rpm 

# yum install jdk11.rpm 
```

### 버전 확인

 ```bash
# java -version 
```

```log
 openjdk version "11.0.17" 2022-10-18 LTS OpenJDK Runtime Environment Corretto-11.0.17.8.1 (build 11.0.17+8-LTS) OpenJDK 64-Bit Server VM Corretto-11.0.17.8.1 (build 11.0.17+8-LTS, mixed mode)
```

## Jenkins My Admin user

csjo / c96..s

## SSH key gen for Jenkins account

```bash
$ sudo -u jenkins ssh-keygen
$ cp /var/lib/jenkins/.ssh/id_rsa.pub /home/git/.ssh/jenkins_id_rsa.pub
$ cd /home/git/.ssh/
$ cat jenkins_id_rsa.pub >> authorized_keys 
```

## Jenkins 설정

- Dashboard > Jenkins 관리 > Security
  
![alt text](<../assets/images/Pasted image 20240318155606.png>)
