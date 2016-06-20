#gulp插件介绍  
*提高生产力*
###gulp-postcss
postcss处理css爽歪歪，妈妈再也不用担心我不回用sass了。写法如下
`
var postcss = require('gulp-postcss');

gulp.task('postcss', function() {
	//选择使用的插件
	var processor = [autoprefixer];
	gulp.src('./src/*.css')
		.pipe(postcss(processor))
		.pipe(gulp.dest('./dest'))
});
`