---
layout: post
title:  "Sass(Syntactically Awesome StyleSheets) 설치"
date:   2017-02-03
categories: [Sass]
comments: true
tags: [Sass]
---

- Sass 설치
  - node-sass
  - gulp-sass

<!--more-->

---

### node-sass
#### 컴파일 1회

```sh
$ npm install node-sass --global
```

#### 폴더 내 파일 변화
```sh
$ node-sass sass/style.scss css/style.css
```

#### 지속적 컴파일 관찰 명령어
```sh
$ node-sass -w sass/ -o css/
```

#### Sourcemap 설정
```sh
$ node-sass -w sass -o css --source-map css
```

#### CSS output style (nested | expanded | compact | compressed)
```sh
$ node-sass -w sass -o css --output-style expanded --source-map css
```
- nested (여러줄 출력)
- expanded (여러줄 출력)
- compact (한줄 출력)
- compressed (압축 출력)

---

### [gulp-sass](https://www.npmjs.com/package/gulp-sass)
#### Install

```sh
$ npm install gulp-sass --save-dev
```

#### Basic Usage (gulpfile.js)

```js
  'use strict';

  var gulp        = require('gulp'),
      sourcemaps  = require('gulp-sourcemaps'),
      sass        = require('gulp-sass');

  gulp.task('sass', function () {
    return gulp.src('sass/**/*.{sass,scss}')
    .pipe(sourcemaps.init())
    .pipe(sass({outputStyle: 'expanded'}).on('error', sass.logError))
    .pipe(sourcemaps.write())
    .pipe(gulp.dest('css'));
  });

  gulp.task('sass:watch', function () {
    gulp.watch('sass/**/*.{sass,scss}', ['sass']);
  });
```
