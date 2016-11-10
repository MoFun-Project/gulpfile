##  gulpfile
# gulpfile文件
````
var gulp = require("gulp"),
    connect = require("gulp-connect");
gulp.task("default", ['localhost']);
gulp.task('localhost', function() {
    connect.server({
        root: './www/',
        port: 8090
    });
});
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

