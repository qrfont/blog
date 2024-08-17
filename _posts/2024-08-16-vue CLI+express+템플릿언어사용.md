# vue CLI 프로젝트 안에서 express 정적폴더 생성하고 템플릿 언어 ejs 사용법

## 예제
http://localhost:8080/dev/filelist 
클릭하면 해당폴더의 목록과 링크
```
\dev\sample\textstyle.html
\dev\sample\textstyle02.html
\dev\sample\textstyle03.html
\dev\sample\textstyle04.html
\dev\sample\textstyle05.html
```

## 사용 목적
- 로컬에서 다양한 웹서비스를 테스트할때 편리
- vue 빌드할때 public폴더처럼 빌드(카피)되지 않음
- public처럼 정적폴더 생성
- vue 안에서 express 서버가동하여 템플릿언어 ejs 를 사용할 수 있다
- ejs 템플릿 사용으로 개발한 파일목록과 링크가 자동생성된다


## 설정
- vue루트폴더 > npm install express ejs  설치
- vue.config.js 수정
- vu루트폴더> dev 폴더생성
- vue > dev > filelist.ejs 생성
- vue > npm run serve 서버실행
- 브라우저 > http://localhost:8080/dev/filelist
- 소스는 아래에 첨부

## 소스 첨부

### express.js
```
const express = require('express')
const fs = require('fs')
const path = require('path')

module.exports = function (app) {
  const directoryPath = path.join(__dirname, 'dev')

  // EJS 템플릿 엔진 설정
  app.set('views', directoryPath)
  app.set('view engine', 'ejs')

  // 정적 파일 제공 (dev 폴더)
  app.use('/dev', express.static(directoryPath))

  // 모든 하위 폴더를 포함한 HTML 파일 목록 생성
  function getHtmlFiles (dir, fileList = []) {
    const files = fs.readdirSync(dir)

    files.forEach(file => {
      const filePath = path.join(dir, file)
      const stat = fs.statSync(filePath)

      if (stat.isDirectory()) {
        // 디렉토리인 경우 재귀적으로 탐색
        getHtmlFiles(filePath, fileList)
      } else if (stat.isFile() && path.extname(file) === '.html') {
        // HTML 파일인 경우 목록에 추가
        fileList.push(filePath.replace(__dirname, '')) // 상대 경로로 변환
      }
    })

    return fileList
  }

  // EJS 파일을 렌더링하여 제공
  app.get('/dev/filelist', (req, res, next) => {
    try {
      const htmlFiles = getHtmlFiles(directoryPath)
      if (!res.headersSent) {
        res.render('filelist', { files: htmlFiles })
      }
    } catch (error) {
      if (!res.headersSent) {
        next(error)
      }
    }
  })
}
```

### vue.config.js 

```
const { defineConfig } = require('@vue/cli-service')
const devServerApp = require('./express')

module.exports = defineConfig({
  transpileDependencies: true,
  devServer: {
    onBeforeSetupMiddleware (devServer) {
      if (!devServer) {
        throw new Error('webpack-dev-server is not defined')
      }
      devServerApp(devServer.app)
    }
  }
})

```
### filelist.ejs
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>File List</title>
</head>
<body>
    <h1>Available Files</h1>
    <ul>
        <% files.forEach(file => { %>
            <li><a href="/dev/<%= file %>"><%= file %></a></li>
        <% }) %>
    </ul>
</body>
</html>

```

