How to about markdown
=====================

#How to set gulp to have a live reloading of markdown file

```
    var gulp = require('gulp'),
        livereload = require('gulp-livereload');

    gulp.task('reload', function(){
        livereload();
    })

    gulp.task('watch', function() {

        livereload.listen();
        gulp.watch(['**/*.md', 
            '!gulpfile.js', 
            '!*.pdf',
            '!*.mobi', 
            '!*.sublime-project', 
            '!*.sublime-workspace',
            '!.gitignore'], ['reload']);
    });
```

other usuful package https://www.npmjs.com/package/st
## Resources
- [Best way to filter files in gulp watch](http://stackoverflow.com/questions/21605592/best-way-to-filter-files-in-gulp-watch)
- [gulp-livereload](https://www.npmjs.com/package/gulp-livereload)
- [static server example](https://github.com/vohof/gulp-livereload/blob/master/examples/static-server.js)

#How to resize image

These example are valid for some markdown implementation. In general is better to use HTML. 

**esample**:

<img src="./images/sonarqbe_homepage_addproject.png" alt="SonarQBe Home Page" style="width: 748px;"/>

##how to set width and heigh

**esample**:

![](./pic/pic1_50.png =100x20)

##how to set only width

**esample**:

![](./pic/pic1_50.png =250x)


##Resources
- [How to change image size markdown](http://stackoverflow.com/questions/14675913/how-to-change-image-size-markdown)



