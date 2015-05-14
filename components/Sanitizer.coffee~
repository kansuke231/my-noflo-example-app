noflo = require "noflo"
sanitizer = require "sanitizer"

class Sanitizer extends noflo.Component

  description: "This component takes a string, sanitize it and output 
                a clean string"

  constructor: ->
    @inPorts =
      in: new noflo.Port()
    @outPorts =
      out: new noflo.Port()

    @inPorts.in.on "data", (str) =>
      @str = str

    @inPorts.in.on "disconnect", =>
      @outPorts.out.send(sanitizer.sanitize(@str))
      @outPorts.out.disconnect()
      @str = null # maybe delete this

exports.getComponent = -> new Sanitizer
