{spawn, exec} = require 'child_process'

task 'watch', 'Build and watch the CoffeeScript source files', ->
  coffee = spawn 'coffee', ['-cw', '-o', 'lib', 'src']
  test   = spawn 'coffee', ['-cw', 'test']
  log = (d)-> console.log d.toString()
  coffee.stdout.on 'data', log
  test.stdout.on 'data', log

task 'build', 'Build minified file with uglify', ->
  console.log 'building...'

  coffee = exec 'coffee -c -o lib src', uglify
  log = (d)-> console.log d.toString()
  coffee.stdout.on 'data', log


uglify = ->
  console.log 'minifying...'
  exec 'uglifyjs -m -o jqconsole.min.js lib/jqconsole.js', (err, res)->
    if err
      console.error 'failed with', err
    else
      console.log 'build complete'
