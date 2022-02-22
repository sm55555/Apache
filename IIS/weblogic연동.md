### IIS & weblogic 연동

IIS의 첫 화면이다. 사이트에 우클릭해서 웹 사이트 추가를 눌러준다.

![image](https://user-images.githubusercontent.com/38831314/155096685-19c8be15-0136-4d0d-9235-10d45125c6e7.png)

사이트 추가를 해준다. 80번 포트를 사용하고 싶으면 Default Web Site를 지우거나 정지시킨다. 정지시킬 때는 응용 프로그램 풀에서도 정지시켜 주어야 한다.

![image](https://user-images.githubusercontent.com/38831314/155096755-a2d4f6fa-2c9a-489b-a1fd-d9fb3e7025f5.png)

IIS로 돌아가서 이전에 만든 가상 디렉토리 창에서 처리기 매핑을 찾는다.

![image](https://user-images.githubusercontent.com/38831314/155096861-538e2c14-2d70-43ee-9e95-5cc03e0db2e8.png)

스크립트 매핑을 클릭한다.

![image](https://user-images.githubusercontent.com/38831314/155096920-46d5f40c-2013-49d0-aa74-23cd7c7b8554.png)

위와 같이 입력해 준다. 실행 파일은 복붙해온 dll 파일들 중에서 찾는다.

그리고 요청 제한을 클린한다.

![image](https://user-images.githubusercontent.com/38831314/155096977-48992573-694d-4d5b-8b46-1367fabd8cb6.png)

![image](https://user-images.githubusercontent.com/38831314/155097012-20076872-fc46-465f-9a98-b5b96c83a47f.png)

![image](https://user-images.githubusercontent.com/38831314/155097041-ac6b3c7c-4d43-4f60-aad1-d11c6f0743a5.png)

위와 같이 설정해 준다. 그대로 확인-확인-예 해준다.

![image](https://user-images.githubusercontent.com/38831314/155097109-aaeb175f-4f02-4ea2-b063-9a0b5d92f104.png)

성공적으로 추가한 것을 볼 수 있다.

이외에도 생성해야 할 파일이 있다. dll파일을 복붙한 폴더로 이동한 후 아래와 같은 이름의 파일을 생성한다.

![image](https://user-images.githubusercontent.com/38831314/155097180-931b4422-f7aa-400f-981a-0557ae53eb7c.png)

![image](https://user-images.githubusercontent.com/38831314/155097618-a26e3367-6fcb-4789-bc6e-9c31b4482f16.png)



