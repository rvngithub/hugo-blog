---
title: "혼자 보려고 정리하는 Hugo 가이드"
date: 2021-06-01
categories: "Guide"
---
##### Github에서
1. 두개의 Repository 생성
    1. 발행할 블로그의 기본 데이터들을 올릴 Repository.(이름은 상관 없음=hugo-blog)
    2. Hugo에서 빌드할 때 자체적으로 변환을 거친 Public 폴더 안의 생성된 HTML 파일들을 올릴 Repository.  
    여기가 홈페이지가 되므로 **[깃헙 아이디=rvngithub].github.io** 로 생성.


##### 터미널에서
2. ```brew install hugo```
3. 블로그 폴더를 생성하고 싶은 로컬 디렉토리에서  
```hugo new site [폴더 이름(혹은 블로그 이름 등)=blog]```
4. ```cd blog```
5. 원하는 테마가 있다면 해당 테마 파일을 다운로드.  
대체로 해당 테마 제작자의 깃헙 페이지에 설명이 나와있으며  
본 테마의 경우  
```git submodule add https://github.com/austingebauer/devise.git themes/devise```  
테마 업데이트의 경우 ```git submodule update --remote themes/devise```
6. ```git init```  
```git remote add origin [1-1.에서 생성한 Repository 링크]```[^1]  
```git submodule add -b master [1-2.에서 생성한 Repository 링크] public```
7. ```hugo new post/[파일명].md``` 등으로 테스트 포스트 작성.
8. ```hugo server -D```[^2]
9. ```hugo -t [테마명=devise]``` or ```hugo -D```
10. ```cd public```  
```git add .```  
```git commit -m "[커밋 메세지]"```  
```git push origin master```[^3]
11. ```cd ..```  
```git add .```  
```git commit -m "[커밋 메세지]"```  
```git push origin master```[^4]

[^1]: 만약 remote origin이 이미 존재한다고 나온다면, git remote rm origin 으로 기존 remote origin 삭제
[^2]: 문서 속성이 draft: true 로 되어있는 경우에도 로컬호스트에서 확인이 가능
[^3]: 1-2.에서 만든 HTML 파일 등이 올라갈 Repository에 파일 push
[^4]: 1-1.에서 만든 Hugo 자체 소스 파일?등이 올라갈 Repository에 파일 push
