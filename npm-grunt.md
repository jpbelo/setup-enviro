update homebrew and install node (npm is inside)
```
brew update
brew install node
```

make sure it's installed - check versions
```
node -v
npm -v
```

install grunt command line interface globally
```
npm install -g grunt-cli
```

**(now, inside the project folder)**

initialize npm to create jackage.json
``npm init``

install grunt for the project (-S for adding the dependencies)

``npm install -S grunt``

create the Gruntfile.js file

``touch Gruntfile.js``


## usefull grunt plugins:
1. concat - ``npm install grunt-contrib-concat --save-dev``
2. watch - ``npm install grunt-contrib-watch --save-dev``
3. stylus - ``npm install grunt-contrib-stylus --save-dev``
4. qunit - ``npm install grunt-contrib-qunit --save-dev``
5. jshint - ``npm install grunt-contrib-jshint --save-dev``

Just compile the main.styl and have the other styl files required inside the styl file in the order you want.
The watch tracks all of them but allways compiles from the main.styl file.

```
module.exports = function (grunt) {

  grunt.initConfig({
    watch: {
      scripts: {
        files: ['assets/scripts/*.js'],
        tasks: ['concat:js'],
      },
      styles: {
        files: ['assets/styles/*.styl'],
        tasks: ['stylus'],
      },
    },
    concat: {
      js: {
        src: ['assets/scripts/*.js'],
        dest: 'build/scripts.js',
      },
    },
    stylus: {
      compile: {
        options: {
          paths: ['assets/styles'],
        },
        files: {
          'build/styles.css': 'assets/styles/main.styl',
        },
      },
    },
    qunit: {
      files: ['test/**/*.html']
    },
    jshint: {
      files: ['Gruntfile.js', 'src/**/*.js', 'test/**/*.js'],
      options: {
        globals: {
          jQuery: true,
          console: true,
          module: true,
          document: true
        }
      }
    },

  });

  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-contrib-concat');
  grunt.loadNpmTasks('grunt-contrib-stylus');
  
  grunt.loadNpmTasks('grunt-contrib-jshint');
  grunt.loadNpmTasks('grunt-contrib-qunit');
  
  grunt.registerTask('default', ['stylus', 'concat', 'watch']);

  grunt.registerTask('test', ['jshint', 'qunit']);

};
```
