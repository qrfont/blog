---
layout: post
title: 깃허브 jekyll 설치 프로젝트 생성
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
터미널> gem install bundler  
터미널> gem install jekyll  


# Jekyll 프로젝트 생성 (기본테마 설치됨 minimal)
c:> jekyll new mysite  
c:> cd mysite  (프로젝트 폴더로 이동)  
c:\dir> mysite > bundle exec jekyll serve  (권장 실행)
# Jekyll 나만의 테마 생성  
c:> jekyll new-theme mytheme    
c:> cd mytheme  

gemfiele 파일 생성  
jekyll-rara.gemspec 파일 생성  

c:mytheme> bundle install  
c:mytheme> bundle install  
c:mytheme> bundle exec jekyll serve  (실행)  



### 크롬 브라우저 열고 나의 제킬 웹사이트 확인
http://localhost:4000 
### 포트 변경해서 실행
터미널 > jekyll serve --port 4001 

### 플러그인 설치
프로젝트 폴더 > Gemfile 파일 열어서  
```
group :jekyll_plugins do
    gem "jekyll-feed", "~> 0.12"
    gem "jekyll-seo-tag", "~> 2.7"
    gem "jekyll-sitemap", "~> 1.4"
    gem "jekyll-paginate"  
    gem "jekyll-spaceship"  
  end
```
> bundle install
> 
### [TIP] jekyll 테마를 로컬컴에 다운로드후 VSCODE열기( zip파일 )
- jekyll 빈 프로젝트 생성
- 다운로드한 zip파일 안에 jekyll 테마와 버전정보를
- 새로 생성한 빈 프로젝트의 gem파일에 추가
- bundle install
- bundle exec serve 실행
- Http://localhost:4000/
  
### [TIP] 설치 
- 최신 루비버전은 설치중 에러가 날 확률이 높으므로 낮은버전 3.0 추천
- 제킬 실행시
- c:\dir> mysite > bundle exec jekyll serve  (권장 실행)  
~~c:> mysite > jekyll serve  (gem 버전오류 가능-비추)~~
