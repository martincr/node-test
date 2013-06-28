Examples taken from:
https://devcenter.heroku.com/articles/nodejs

Uses:
http://expressjs.com/

Browse to:
http://127.0.0.1:5000

Branch: Heroku

https://github.com/passy/generator-heroku
sudo npm install -g yo
npm install -g generator-heroku
yo heroku

Do you want a separate git repository in dist/? (Y/n) n
   create heroku/Procfile
   create heroku/server.js
   create heroku/distpackage.json
Please add this copy task rule to your Gruntfile:
    copy: {
        dist: {
            files: [{
                expand: true,
                dest: '<%= yeoman.dist %>',
                cwd: 'heroku',
                src: '*',
                rename: function (dest, src) {
                    var path = require('path');
                    if (src === 'distpackage.json') {
                        return path.join(dest, 'package.json');
                    }
                    return path.join(dest, src);
                }
            }]
        }
    }

You're all set! Now run
  heroku apps:create
and push your dist directory with
  git subtree push --prefix dist heroku master
