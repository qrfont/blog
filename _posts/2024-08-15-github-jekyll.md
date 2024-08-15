---
layout: post
title: 깃허브 jekyll 프로젝트 생성
subtitle: 설치
categories: github
tags: [github, jekyll]
---

# Ruby 설치
### 권장 버전 
https://rubyinstaller.org/downloads/  
Ruby+Devkit 3.0.7-1 (x64)  
exe파일을 pc에서 보안차단할 경우 관리자로 실행(추가정보 더보기)
### error : 최신버전을 사용하면 bundle install에서 gem wdm 구문에서 에러가 발생


# Jekyll 설치
# Jekyll 프로젝트 생성
# 윈도우 터미널 또는 vscode 터미널을 열고 실행
c:\dir>jekyll new mysite  
c:\dir>cd mysite  
c:\dir> mysite > jekyll serve  
c:\dir> mysite > bundle install  
c:\dir> mysite > bundle exec jekyll serve  


### 크롬 브라우저 열고 나의 제킬 웹사이트 확인
http://localhost:4000 
### 포트 변경해서 실행
터미널 > jekyll serve --port 4001 
#gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
gem 'wdm', '~> 0.1.1', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
