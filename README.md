# 내 프로필을 클라우드에!

## 👨🏻‍💻프로젝트 간단요약

프로필 웹페이지를 AWS S3의 정적 웹 호스팅 기능을 활용하여 배포한다.

- 서비스 시연영상
    
    https://drive.google.com/file/d/1OmAZWIfnzAhOO8aObmUSjLGKkhJLrZxu/view?usp=drive_link
    

---

## 🙋🏻나는 무엇을 했는가?
    

1. html 웹페이지 제작하였습니다.



2. AWS 환경에서 정적 웹을 배포하였습니다.
    - Architecture
      <img src="https://github.com/it-mnm/profile/assets/137988290/e67e9fbe-1e4a-4e35-8c7c-3e2e1568f5bf">
        
        
    - 배포된 사진
        - S3(React 웹)
            <img src="https://github.com/it-mnm/profile/assets/137988290/eab31aeb-7dea-4e99-a00d-e6fa7061aa7d">
            
            
        
    

---

## 📖나는 무엇을 배웠는가?

1. S3는 단순히 저장소 역할을 하는 것을 넘어서 **정적 웹을 호스팅 할 수 있다는 것을 알았다.** 
2. 보안을 위해 https 통신을 하도록 만들었는데, 이를 위해서는 보안 인증서가 필요하다. AWS에서는 클라이언트의 https 통신을 이루기 위해서는 **반드시 인증서를 버지니아 북부에 위치시켜야한다.** 또한 CloudFront를 이용하여 그 인증서를 국내에서 빠르게 이용할 수 있도록 만들어야 한다.

---

## ➕앞으로 무엇을 더 보완할 수 있는가?

1. 코드가 수정되었을때 일일히 손으로 S3에 옮겨서 배포하는 것은 매우 불편한 과정이다. 따라서 git action 등을 통해 **자동 배포를 구현하는 것이 좋을 듯 하다.**
2. 정적 웹 호스팅이 완료되었으니, 백엔드 서버를 연결해보거나, 시각화도구(ex - Tableau)를 웹에 띄워보는 것도 해볼 수 있을 것이다.
3. 추후에 NFS를 이용하는 파일관리와 S3를 이용하여 하는 파일관리의 **속도차이를 비교해보고싶다.**
