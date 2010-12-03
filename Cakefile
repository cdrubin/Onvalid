
fs      = require 'fs'
path    = require 'path'
cp      = require 'child_process'

task 'minify', 'minify the source', ->
    proc = cp.spawn 'uglifyjs', ['-o', 'onvalid-min.js', 'onvalid.js']
    proc.on        'exit', (status) -> process.exit(1) if status != 0

task 'lint', 'run jslint over the source', ->
    proc = cp.spawn 'jsl', ['-conf', 'jsl.conf',
                            '-process', 'onvalid.js',]
    proc.stdout.on 'data', (buffer) -> console.log buffer.toString()
    proc.on        'exit', (status) -> process.exit(1) if status != 0

task 'test', 'run all unit tests', ->
    proc = cp.spawn 'expresso', ['onvalid.test.js', '-I', './',]
    proc.stderr.on 'data', (buffer) -> console.log buffer.toString()
    proc.on        'exit', (status) -> process.exit(1) if status != 0
