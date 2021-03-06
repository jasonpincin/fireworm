Fireworm
========

Fireworm is a crawling file watcher.

Install
-------

    npm install fireworm

Usage
-----

    var fireworm = require('fireworm')

    // make a new file watcher
    var fw = fireworm('start_dir')

    // Add the files you want to watch for changes on (can be glob)
    fw.add('lib/**/*.js')
    fw.add('tests/**/*.js')

    // ignore some patterns
    fw.ignore('tests/dontcare/*.js')

    // register for the `change` event
    fw.on('change', function(filename){
        console.log(filename + ' just changed!')
    })

Why is this different from other file watchers?
-----------------------------------------------

Fireworm works by crawling and re-crawling the relevant directories when necessary. Because of this, it can detect newly created files, new files in newly created directories, re-created files, and even new files within re-created directories too - as long as the file matches the paths you are watching.
