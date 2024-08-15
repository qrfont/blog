---
layout: post
title: 깃허브 jekyll 프로젝트 생성
subtitle: 설치
categories: github
tags: [github, jekyll]
---

# Ruby 설치
### 권장 버전 
[https://rubyinstaller.org/downloads/  ](https://rubyinstaller.org/downloads/)
Ruby+Devkit 3.0.7-1 (x64)  
exe파일을 pc에서 보안차단할 경우 관리자로 실행(추가정보 더보기)
설치중 cmd.exe가 자동실행  ==> 3 - MSYS2 and MINGW development toolchain 엔터
터미널 닫기
### error : 최신버전을 사용하면 bundle install에서 gem wdm 구문에서 에러가 발생


# Jekyll 설치
어떤폴더 터미널> gem install bundler
어떤폴더 터미널> gem install jekyll

# Jekyll 프로젝트 생성
c:> jekyll new mysite  
c:> cd mysite  
c:\dir> mysite > bundle exec jekyll serve  (권장 실행)
~~c:> mysite > jekyll serve  (gem 버전오류 가능-비추)~~

### 크롬 브라우저 열고 나의 제킬 웹사이트 확인
http://localhost:4000 
### 포트 변경해서 실행
터미널 > jekyll serve --port 4001 
#gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
gem 'wdm', '~> 0.1.1', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
