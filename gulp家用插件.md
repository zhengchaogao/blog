#gulp插件介绍  
*提高生产力*
###gulp-postcss
postcss处理css爽歪歪，妈妈再也不用担心我不会用sass了。写法如下
```javascript
var postcss = require('gulp-postcss');

gulp.task('postcss', function() {
	//选择使用的插件
	var processor = [autoprefixer];
	gulp.src('./src/*.css')
		.pipe(postcss(processor))
		.pipe(gulp.dest('./dest'))
});
```
postcss常用插件：  
1. autoprefixer 自动添加浏览器前缀；    
2. postcss-import 合并@import css文件；  
3. cssnano 压缩代码，优化的插件合集；    
4. css-mqpacker 合并媒体查询@media；   
5. precss 预处理插件合集, 支持像SASS，合并@import；  
6. precss-bem 默认SUIT风格，可以改成BEM命名风格；    

*参考 http://www.w3cplus.com/blog/tags/516.html*   
###babel系列
babel提供了对新语法的解析，包括但不限于es6、es7、react。   
