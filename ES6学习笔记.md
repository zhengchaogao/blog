#ES6

###工欲善其事必先利其器
目前es6无法直接在大部分浏览器中运行，需要先解析成es5语法。在构建中使用babelify + babel-preset-es2015。
```javascript
gulp.task('js', function() {
	browserify('./app/index.js')
				.transform('babelify', {presets: ['es2015']})
				.bundle()
				.on('error', function(err) {
					console.log(err.message);
					this.emit('end');
				})
				.pipe(source('bundle.js'))
				.pipe(gulp.dest('./build'))
				.pipe(reload({stream: true}));
});
```