---
layout: post
title: jekyll zip 로컬에서 실행 (zip 다운로드)
subtitle: 설치법
categories: github
tags: [github, jekyll]
---

# 로컬에서 실행하기
- github.com 에서 'JEKYLL theme' 검색후
- 'fork'하여 나의 레포지토리로 추가
- 레포지토리 zip 다운로드
- ruby 설치
- jekyll 설치
- 다운로드 한 jekyll 폴더 선택후 vscode로 열기
- vscode > 메뉴 > 터미널 실행
- Gemfile 설정
- _config.yml 설정 - 아래 문구 추가
    exclude:
  - .github


### 에러 처리
```
bundle exec jekyll serve
fatal: not a git repository (or any of the parent directories): .git
Configuration file: C:/WEBSERVER/GITHUB-BLOG/_config.yml
  Jekyll Spaceship: 🚀 Jekyll-Spaceship 0.10.2
  Jekyll Spaceship: 🎉 A Jekyll plugin to provide powerful supports.
```
