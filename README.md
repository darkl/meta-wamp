meta-wamp
===================


Metadata for [WAMP](http://github.com/tavendo/WAMP) messages!

Whaaaat?
----------
Each file consists of metadata of a WAMP message, the data is formatted in [JSON Schema format](http://json-schema.org/).


Example
-------------

Below is the metadata of a REGISTER message.

```json
{
  "code": 64,
  "name": "REGISTER",
  "roles": [
    "dealer"
  ],
  "items": [
    {
      "title": "Request",
      "type": "integer"
    },
    {
      "title": "Options",
      "type": "object",
      "properties": {
        "disclose_caller": {
          "advanced_profile": true,
          "type": [
            "boolean"
          ]
        },
        "invoke": {
          "advanced_profile": true,
          "type": [
            "string"
          ]
        },
        "match": {
          "advanced_profile": true,
          "type": [
            "string"
          ]
        }
      }
    },
    {
      "title": "Procedure",
      "type": "string"
    }
  ],
  "minItems": 3,
  "maxItems": 3
}
```

As you can see this contains the message name ("REGISTERED"), message code (64), and the message arguments with their types. Note that the Options argument type, which is a schema, describes what properties does Options have ("disclose_caller" which is a boolean, "match" which is a string and "invoke" which is a string. It also indicates that these features are advanced profile features).

Why?
-------------

You might be wondering "what is this good for"? Well, this is useful for new WAMP implementations: when writing a WAMP implementation, it is a tedious work to type all WAMP contracts in the target language. It is also an error prone process.
Instead, you can write a script that aggregates all these schema types and generates matching contracts. That should take about the same amount of time, but will be more fun and should avoid bugs.
