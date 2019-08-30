# Samsung Android 기기에서 Linux 사용하기  

> **세 줄 요약**
> 1) 삼성 안드로이드 제품에 Linux를 설치하고 사용할 수 있음.  
> 2) 그런데 비공식 노가다가 조금 필요함.  
> 3) anaconda + jupyter lab (Google Drive 연동, GitHub 연동) 까지 성공함.


삼성이 자사의 Android 기기에서 Linux를 사용할 수 있는 환경을 제공합니다. `Dex`환경을 이용한 것이기 때문에 아래에 설명드릴 기술은 삼성 안드로이드(폰, 태블릿)에서만 작동되며, 그것도 비교적 최신 모델에 한해 기능이 제공됩니다.    
`VScode`와 `IntelliJ`가 탑재되어 있는 것을 보면 어디서든 개발을 하고자 하는 이들을 노린 것으로 보입니다.  
[`Linux on Dex`](https://www.linuxondex.com/)가 그 이름으로, 상세한 정보는 [공식 홈페이지](https://www.linuxondex.com/)와 [Gaiar Baimuratov의 포스팅](https://towardsdatascience.com/pydata-stack-in-your-pocket-literally-73662c20d18e)을 통해 확인하기 바랍니다.  
본 글에서는 필자의 설치 과정을 공유합니다.

- **공식 홈페이지에는 없는 오류**와 **Gaiar의 포스팅과는 다른 상황**이 있어 다소의 구글링을 필요로 했습니다.  
- Linux Image 압축 해제 후의 용량이 11 GB를 넘으니 감안하도록 합시다.  

![Linux on Dex](images/lod01.png)


### 1. 지원 기기  
본인의 기기가 지원 대상인지 확인합니다.  
필자는 태블릿(Galaxy Tab S4)에 설치했습니다.    

<p align="center">
  <img src="https://github.com/jehyunlee/texts/blob/master/Linux_on_Dex/images/lod02.png">
</p>
<br>  

### 2. `Linux on Dex` App 설치  
* **2019년 8월 30일 현재 `Google Play`에서 `Linux on Dex` 앱을 찾을 수 없습니다**  
별도의 링크를 이용하여 apk 파일을 다운받고 설치합니다. (<a href='https://drive.google.com/open?id=10Ku57itmXIy2gnzWu7VKj8RlMcIFH9vm'>Download Link</a>)  
<br>  
  
### 3. Linux Image File 다운로드 및 압축해제    
삼성에서 Ubuntu 16.04 Xenial 기반 Image를 제공합니다.  
* **2019년 8월 30일 현재 [공식 링크](https://webview.linuxondex.com/)에서 다운로드 오류가 발생합니다**  
* Android에서는 다운로드 중 조용히 종료되고,  
* Windows에서는 다운로드 중 `취소됨` 메시지와 함께 다운로드가 중단됩니다.  

#### 3.1. Download  
필자는 다른 리눅스 환경(윈도 노트북의 WSL)에서 wget 명령어를 이용해 다운받았습니다.  
용량이 약 4 GB 정도 됩니다.  

```bash
$ wget https://webview.linuxondex.com/016/xenial-gnome-with-IJ-GI016.zip
```

![Image Download](images/lod03.png)  
<br>  

#### 3.2. Transfer to Tablet PC
그리고 Tablet으로의 전송을 위해 Google Drive에 업로드했습니다.  
이 글을 보시는 여러분은 제 구글드라이브에서 다운받으셔도 좋습니다. (<a href='https://drive.google.com/open?id=1rZfguyO664sjDlp340rQQXEVBHgY-oWB'>Link</a>)  

#### 3.3. Image Mount
다운받은 이미지의 압축을 해제한 후, `Linux on Dex` app을 실행하고 압축을 해제한 image를 불러옵니다.  
아래 화면에서 왼쪽 아래 반쯤 가린, 주황색 + 모양 버튼을 누르고 이미지 파일을 선택합니다.  
아직 Image를 올리지 않았으므로 오른쪽은 비어있을 것이지만, 이미지를 마운트하면 아래 사진과 같이 바뀝니다.  

![Image Mount](images/lod11.jpg)  
<br> 

### 4. 실행
위 사진에서 오른쪽에 있는 주황색 RUN을 클릭하면 GUI mode가 기본값으로 실행됩니다.  
Terminal mode를 원하시는 분은 아래에 조그맣게 있는 Terminal mode를 클릭하시면 됩니다.  
기본 sudo password는 `secret`입니다.   
GUI 모드로 실행하시면, 아래와 같은 화면을 보실 수 있습니다.  

![Image Mount](images/lod05.jpg)  
<br>  

`VS Code`와 `Intelli J`가 기본으로 설치되어 있음을 볼 수 있다.

![Dev tools](images/lod06.jpg)  
<br>  

Text mode를 선택하면 GUI가 없는 터미널로 실행할 수도 있다.  
아래 그림은 `midnight commander`를 설치하여 실행한 모습이다. 
![text mode](images/lod07.jpg)  
<br>  

### 5. 업데이트  
<a href='https://www.linuxondex.com/'>공식 홈페이지</a>에 따르면, 터미널을 실행하거나 텍스트 모드로 로그인 한 후, 리눅스 이미지를 아래와 같은 명령어를 사용하여 업데이트하라고 한다.  
* **그런데 다 잘 되다가 마지막 줄에서 에러가 난다. 아직 원인을 못찾았다.**  

```bash
$ sudo -S wget -O - https://www.linuxondex.com/lodapt/keyFile | sudo apt-key add -

$ sudo su
# sudo -S printf "deb http://www.linuxondex.com/lodapt/ /\n" >> /etc/apt/sources.list

# exit

$ sudo -S apt update
$ sudo -S apt install linux-on-dex lod-daemon
//If you have a message about changing the Configuration file, please enter 'Y'.
```

linux-on-dex의 lod-daemon에 문제가 있는 것으로 판단되어 아래와 같이 리눅스 일반 명령을 실행했으나, Permission Error 메시지와 함께 더 이상 진행이 되지 않는다. 치명적인 오류는 아닌 것 같고 단순히 업데이트가 되지 않은 듯.  

```bash
sudo apt-get upgrade
```
![upgrade](images/lod09.png)  
<br>  

* 이후 추가적인 구글링을 통해 conda 설치까지 성공.  
* 상세한 정보는 이후 8/30 야간에 업데이트 예정임.  


![conda upgrade](images/lod10.png)  
<br>  
