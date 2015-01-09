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
  "displayNameMap": {
    "en": "foo"
  }
}
```

There are some JSON-LD specific mechanisms that make it through the JSON-LD expansion algorithms ok but are not legal in AS 2.0. Example:

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

The string literal and language map forms are required for all consumers. Compliant producers MUST only output either the string literal or language map form 


