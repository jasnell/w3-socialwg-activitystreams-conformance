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

There are some JSON-LD specific mechanisms that can be used but should be avoided. Example:

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

The string literal and language map forms are required for all consumers, while the other forms are optional. Compliant producers MUST only output either the string literal or language map form.

