## General notes for language-set tests

### JSON-LD "@language" inside the "@context" is used to set the "Default Language Context"

```json
{
  "@context": [
    "http://asjsonld.mybluemix.net",
    { "@language" : "en" }
  ],
  "displayName": "foo"
}
```

### Language-specific fields can take one of two basic forms: String Literal or Language Map

No langauge context:
```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "displayName": "foo"
}
```

String literal with default language context:
```json
{
  "@context": [
    "http://asjsonld.mybluemix.net", 
    { "@language": "en" }
  ],
  "displayName": "foo"
}
```

Language Map:
```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "displayName": {
    "en": "foo"
  }
}
```

There are some JSON-LD specific mechanisms that make it through the JSON-LD expansion algorithms ok but should be avoided in AS 2.0. Example:

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "displayName": {
    "@value": "foo",
    "@language": "en"
  }
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "displayName": [{
    "@value": "foo",
    "@language": "en"
  }]
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "displayName": ["foo"]
}
```

The string literal and language map forms are required for all consumers, while the other forms are optional. Compliant producers MUST only output either the string literal or language map form 

Note: there is an issue with JSON-LD here... which is set up to do one form OR the other, not either. We'll need to resolve this. One suggestion has been to use separately mapped terms... 

```json
{
  "@context": [
    "http://asjsonld.mybluemix.net", 
    {
      "displayNameMap": {
        "@id": "as:displayName",
        "@container": "@language"
      },
      "displayName": {
        "@id": "as:displayName",
        "@type": "xsd:string"
      }
    }
  ],
  "displayNameMap": {
    "en": "foo",
    "fr": "bar"
  },
  "displayName": "test"
}
```

Here, both "displayNameMap" and "displayName" map to as:displayName but the former is treated as a Language Map while the latter is a literal string. This is a workable solution that preserves backwards compatibility with AS 1.0 and makes the serialized output a bit more predictable. Non JSON-LD implementations would have to be aware, however, that the displayName could be expressed in one of two different ways ("displayName" or "displayNameMap"), which is less than ideal.

The same pattern would hold for each of the language sensitive fields: 

# title (literal string)
# titleMap (language map)
# summary (literal string)
# summaryMap (language map)
# content (literal string)
# contentMap (language map)
# displayName (literal string)
# displayNameMap (language map)


