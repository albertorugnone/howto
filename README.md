SIMPLY HOWTO
============
# Introduction
This is simply a set of how-to spreading in all field of technology that I usually touch.

# Gitbook
## How to build this book even if it is empty?

- clone howto repository
```
    git clone https://github.com/albertorugnone/howto.git
    cd howto/
```
- install packages:
```
npm -i -g
```
or
```
    npm -i gitbook-cli -g
```

- init gitbook repository

```    
    gitbook init
```

- install calibre 
```    
    brew update
    brew cask install calibre
```

- generate  book
```
    gitbook pdf . ./howto.pdf
```
or
```
    gitbook mobi . ./howto.mobi
```

# Ongoing work
- how to work locally using markdown in effective way
    - how to with [node-livereload](https://github.com/napcs/node-livereload)
    - how to with livereload  [gulp-livereload](https://www.npmjs.com/package/gulp-livereload)
    
- how to install docker on Mac and configure it properly

# Future work
We are at the really beginning. Infact this set of howto is quite empty :-)

The first step will be define the environment, then

- how to link this to a blog
- how to write a blog using markdown and then
- how to link this repository to a gitbook.

They are simple how that will be ready in the next release.




