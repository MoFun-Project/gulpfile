##  gulpfile
# gulpfile文件
````
var gulp = require('gulp');
var concat = require('gulp-concat');
var autoprefixer = require('gulp-autoprefixer');
var less =require('gulp-less');
var uglify  = require('gulp-uglify');
var connect = require('gulp-connect');
var cleanCss = require('gulp-clean-css');
var rev =require('gulp-rev');//md5加密
var inject = require('gulp-inject');//注入文件
var clean = require('gulp-clean');//清理文件
var sequence = require('gulp-sequence');//强制顺序执行文件

gulp.task('less',function(){
	return gulp.src('mofang/css/*.less')
			   .pipe(less())
			   .pipe(autoprefixer())
			   .pipe(concat('app.min.css'))
			   .pipe(cleanCss())
			   .pipe(gulp.dest('mofang/'))
	});
gulp.task('js',function(){
 return gulp.src(['mofang/config/*.js','mofang/controller/*.js'])
		.pipe(concat('app.min.js'))
		.pipe(uglify())
		.pipe(gulp.dest('mofang/'))
	});
gulp.task('localhost',function(){
 return	connect.server({
		root:'mofang/',
		port:8000
		})
	});
// gulp.task('rev',function(){
// 	return gulp.src(['app/app.min.js','app/app.min.css'])
// 				.pipe(rev())
// 				.pipe(gulp.dest('app/'))
// 				.pipe(rev.manifest())//记录的json
// 				.pipe(gulp.dest('app/'))
// 	})
// gulp.task('inject',function(){//将新生成的文件植入页面
// 	return gulp.src('app/index.html')
// 				.pipe(inject(gulp.src(['app/app-*.min.*']),{ignorePath:'app/',addRootSlash:false}))
// 				.pipe(gulp.dest('app/'))
// 	})

// gulp.task('clean',function(){
// 	return gulp.src('app/app-*.min.*')
// 		       .pipe(clean())
// 	})

// gulp.task('build',function(cb){
// 	return sequence('clean','rev','inject',cb)//按顺序执行
// 	})

gulp.task('myWatch',function(){
    	gulp.watch(['mofang/css/*.less'],['less']);
		gulp.watch(['mofang/config/*.js','mofang/controller/*.js'],['js']);
		// gulp.watch(['app/*.css','app/*.js'],['build']);
	});


gulp.task('default',['myWatch','localhost']);

````
## package.json
# package.json文件
````
{
  "name": "a",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "gulp": "^3.9.1",
    "gulp-autoprefixer": "^3.1.1",
    "gulp-clean": "^0.3.2",
    "gulp-clean-css": "^2.0.13",
    "gulp-concat": "^2.6.0",
    "gulp-connect": "^5.0.0",
    "gulp-inject": "^4.1.0",
    "gulp-less": "^3.1.0",
    "gulp-rev": "^7.1.2",
    "gulp-sequence": "^0.4.6",
    "gulp-uglify": "^2.0.0"
  }
}
````

