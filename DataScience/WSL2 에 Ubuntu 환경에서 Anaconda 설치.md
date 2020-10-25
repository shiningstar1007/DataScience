# WSL2 에 Ubuntu 환경에서 Anaconda 설치 

여러가지 과학 패키지들을 기본적으로 포함되어 있는 파이썬 배포판으로 Anaconda를 설치해야 합니다.  
그러면 머신러닝(Machine learning)이나 데이터 분석(Data analysis)를 조금 더 편하게 할 수 있습니다.  
장점으로는 가상 환경 구축에 유리하고 각종 머신러닝 라이브러리가 포함되어 있으며  
주피터 노트북(jupyter notebook)도 포함되어 있기 때문이다.  

WSL2 에 Ubuntu 를 설치 한 뒤 여기에 anaconda를 설치해보도록 하겠습니다.  
먼저 https://repo.anaconda.com/archive/ 에 접속하여 다운로드 받을 파일명을 확인합니다.  
저는 Anaconda3-2020.07-Linux-x86_64.sh 버전으로 설치를 진행하였습니다.  

그렇다면 우분투 접속한 뒤 아래 명령어를 실행하였습니다.  
xx$ wget https://repo.continuum.io/archive/Anaconda3-2020.07-Linux-x86_64.sh  

다운로드가 완료되면 다음은 아나콘다를 설치하였습니다.  
$bash Anaconda3-2020.07-Linux-x86_64.sh  

설치가 완료되면 폴더 권한을 변경해 줍니다.  
저는 귀찮아서 그냥 777로 줬습니다.  
chmod -R 777 /home/username  

그리고 난 뒤 $which python 를 실행해서  
/home/username/anaconda3/bin/python  
이 출력되면 되는데 출력되지 않을 경우에는  
vi 편집기를 실행해서 ~/.bashrc 파일을 열고 맨 마지막 줄에  
export PATH=/home/username/anaconda3/bin/$PATH 를 추가하고 저장 한 뒤  
source ~/.bashrc 를 실행하면 됩니다.  
이 후 conda list 명령을 실행해서 정상적으로 출력되는지를 확인하면 됩니다.  
