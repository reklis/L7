L7
======

A simple HL7 query language.

Usage
----

Given HL7:

    MSH|^~\&|REG|XYZ||XYZ|20050912110538||SIU^S12|4676115|P|2.3
    PID|||353966||SMITH^JOHN^^^^||19820707|F||C|108 MAIN STREET ^^ANYTOWN^TX^77777^^|HARV|(512)555-0170|||||00362103|123-45-6789||||||||||||
    SCH|1||||||NEW||||20050912110230^20050912110430||||||||||||||||||^^^^^^||3|
    PV1||O|SEROT|3|||1284^JOHNSON^MIKE^S.^^MD~|||SEROT||||1|||1284^JOHNSON^MIKE^S.^^ MD|SERIES|787672|B|||||||||N||||||||||||A|||20050912110230|||||| PV2|||HAND BRACE NEEDS REPAIRED|||||||||||20050912||||||||||A||20050725|||||O||||||
    NK1|0001|HULK^INCREDIBLE|M|123 FAKE ST^^OUTLAND^^00000|123456789||

And the javascript:

    parser = require('L7')

    message = parser.parse(hl7)
    version = message.query('MSH|12') // 2.3

    name = message.translate({
      familyName: 'PID|5^0'
      firstName: 'PID|5^1'
    }) // { "familyName": "McTest", "firstName": "Test" }

Installation
------------

    $ npm install L7

Development
-----------

  * [Twitter](http://twitter.com/wombleton)

Caveat
------

This package is in its infancy, use with caution.
