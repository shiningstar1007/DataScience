#WSL2(Winodws Sub Linux) 설치

Windows에서 리눅스를 사용하기 위해서 MS가 WSL을 만들어서 지원합니다.  
일명 가상화 기술을 사용해서 리눅스를 사용할 수 있도록 해주는 기능입니다.  
Windows 10 Pro 커널빌드 2004 버전에서 지원함으로 OS 패치를 진행하면 됩니다.  

먼저 WSL을 설치 하기 위해서는 아래 MS 홈페이지에 가면 자세하게 나와 있습니다.  
https://docs.microsoft.com/ko-kr/windows/wsl/install-win10  

안에 내용대로 그대로 설치를 하고 진행하면 되는데...  
저는 Ubuntu-20.04 최신 버전을 설치하려고 하는데 문제가 발생했습니다.  
바로 설치가 안되는 문제였는데 에러 메시지가   
WslRegisterDistribution failed with error: 0x80370102 가 발생하였습니다.  
그래서 인터넷을 찾아보니 Hyper-하이퍼바이저 설치를 해야 하는데  
여기서 또 막히는게 설치를 하려고 제어판에서 Windows 기능 켜기/끄기 항목에 들어가서 보니  
[Hyper-V] -> [Hyper-V 플랫폼] -> [Hyper-V 하이퍼바이저] 가 비활성화 되어 있었습니다.  
그래서 찾아보니까 BIOS 설정에 들어가서 Virtualization을 Enabled 로 바꿔줘야 한다고 합니다.  

Intel CPU 는 Virtualization Technology(VT) 를 Enabled 로 설정해주면 되고  
AMD CPU 는 SVM Mode 를 Enabled 로 바꿔 주면 된다고 합니다.  

여기서 저는 AMD CPU라서 SVM Mode를 Enabled 해주려고 하는데  
메인보드가 MSI 보드라서 좀 삽을 열심히 펏습니다.  
그리고 위치를 찾았는데 OverClock 메뉴에 CPU Features에 보면 SVM Mode 가 있습니다.  
그 위치 찾느라 엄청 삽펏네요.   

아무튼 그걸 Enabled 해주고 리부팅을 하면 정상적으로 [Hyper-V 하이퍼바이저] 를 활성화 할 수 있습니다.  
그리고  [Hyper-V 하이퍼바이저]를 활성화 하고 난 뒤에 Ubuntu-20.04를 설치하니까   
정상적으로 설치가 완료 되는걸 확인하였습니다.  