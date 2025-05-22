# pyInstaller_setup_exe
## pyInstaller
### 이 패키지는 1개의 실행 가능한 exe 파일을 만드는 것이다      
1. 기존 완성된 프로젝트에 pyInstaller를 설치 한다.
   ```
   pip install pyinstaller
   ```
   <img width="400" alt="image" src="https://github.com/user-attachments/assets/da112ce8-6320-47fc-801e-5979dcc46419" />

2. 터미널에서
   ```
   pyinstaller app.py
   ```
   여기서 app.py는 내가 실행 하려고 하는 파일의 이름 이다.
   
3. 결과는 dist 폴더에 저장 된다.   
   <img width="139" alt="image" src="https://github.com/user-attachments/assets/3ef787ad-7b28-4e6a-86b4-66efcaccb60c" />    
   간단하게 보이지만 실제로    
   _internal 폴더에는 정말 많은 파일들이 포함 되어 있다.    
   실제 만들어진 app.exe가 실행 되는데 필요한 부속 파일들이다.    

   <img width="122" alt="image" src="https://github.com/user-attachments/assets/76042284-3b20-4c49-af88-d8aaeca0e6d6" />

   이 모든 파일들을 1개의 exe 파일로 만들어야 한다.    
   현재 상태에서는 그렇다고 해서 프로그램이 실행이 되는것도 아니다.     
   이유는 필요한 res 폴더같은 부속 파일들이 dist 폴더에 없기 때문이다.
   res 폴더를 app.exe 가 있는 폴더에 복사 해 주면 실행 된다.    
   <img width="487" alt="image" src="https://github.com/user-attachments/assets/19cdb632-48d7-42d3-8ecd-b3c4442d882a" />

4. 이제 _internal 폴더를 포함 하는 1개의 exe 파일로 만들어 보자
   ```
   pyinstaller -F app.py
   ```
   기존에 있던 dist 폴더 아래의 app 폴더 전체를 지우고
   위 명령을 실행한뒤    
   app.exe가 dist 폴더에 바로 생기는 것을 확인
   res 폴더를 그곳에 복사 한다.

   <img width="431" alt="image" src="https://github.com/user-attachments/assets/faeed5cc-3103-4584-b07b-868a87e5de44" />

5. 실행 결과
   dist 폴더 내의 app.exe를 실행 하면 다음과 같은 결과를 볼수 있다
   <img width="491" alt="image" src="https://github.com/user-attachments/assets/296cad44-469b-4dd0-96fe-7f52632700f7" />
6. 완벽해 보이지만 하나의 애러가 있다.  그것은 터미널창 또는 Console 창이 보이는 것이다.      
7. 콘솔창을 안보이게 하는 것은 -w 옵션이다.
   ```
   pyinstaller -w -F app.py
   ```   
8. 1파일로 패키징이 된 폴더는 다음과 같다.
   <img width="419" alt="image" src="https://github.com/user-attachments/assets/29096aa8-d99f-4621-8ada-41c3489aea4b" />

9. 최종 실행 화면     
    <img width="206" alt="image" src="https://github.com/user-attachments/assets/6021ede7-3eb3-41ae-b488-e370bc9a865c" />

    
## installFactory 
### 배포용 setup_.exe 파일을 만드는 것이다. 

1. InstallFactory를 설치 한다.
2. 우리가 수정해야 하는 것은 다음 6개의 tab
   <img width="397" alt="image" src="https://github.com/user-attachments/assets/cf63bb97-786d-4a8e-baa5-bd2d55b9e5e0" />
   1) 첫번째 탭 일반     
<img width="397" alt="image" src="https://github.com/user-attachments/assets/1734b3dc-dda0-477b-9a58-dcc30871cfbc" />
   2) 두번째 탭 창
<img width="397" alt="image" src="https://github.com/user-attachments/assets/4b726a64-17ae-4323-93d6-65a1f6ae3923" />

   3) 세번째 탭 정보
설치시나 설치후 보여줄 특별한 내용이 없으므로 check out
<img width="397" alt="image" src="https://github.com/user-attachments/assets/231e8712-90c3-41d4-be8f-74cca62ebb2f" />

   4) 네번째 탭 단축아이콘
여기는 중요함.
프로그램이 설치된후에 바로가기 아이콘을 만드는 것     
기존에 있는것을 모두 삭제
<img width="397" alt="image" src="https://github.com/user-attachments/assets/2aaa1b28-200d-4c14-94a8-4c673ca117a5" />
필요한것만 추가 (예..프로그램 그룹에 1개/바탕화면에 1개)
프로그램 그룹     
<img width="377" alt="image" src="https://github.com/user-attachments/assets/e6438bb7-8a0a-47bc-bd64-b235fc264ace" />
  
바탕화면    
<img width="377" alt="image" src="https://github.com/user-attachments/assets/2182e771-f54c-434f-8007-244e6853eece" />

   5) 다섯번째 탭 제거
제어판-프로그램 추가/제거 에 삭제    
프로그램 그룹에 제거      
<img width="451" alt="image" src="https://github.com/user-attachments/assets/83493342-a390-4c65-a233-d437b11e08ac" />

   7) 여섯번째 실행
설치 프로그램이 실행 되고 난 후 실행 될 파일을 선택
또는 프로그램 설치 도중에 실행 해야만 하는 파일을 지정
<img width="397" alt="image" src="https://github.com/user-attachments/assets/2eda198c-30ce-4a00-96ac-9076659a3c38" />

### 만들기 

<img width="559" alt="image" src="https://github.com/user-attachments/assets/b5555ae4-7605-4f81-9dfc-563b1622a7bf" />

### 설치 실행 
<img width="959" alt="image" src="https://github.com/user-attachments/assets/1bc9aa3d-0038-4d75-84f3-df6d981442d4" />

### 바로가기로 실행 
<img width="358" alt="image" src="https://github.com/user-attachments/assets/8198cb03-c1d8-4d3d-b2c3-a89c563393ed" />

### 끝











   
   
      
      
 
   


   
   
   

   
