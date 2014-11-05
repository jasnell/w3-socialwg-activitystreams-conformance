Type:      Roundtrip Test

Condition: Language Map with multiple languages, no default language context

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content"

## Input(s)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo",
    "fr": "bar"
  }
}
```

## Output(s)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo",
    "fr": "bar"
  }
}
```

### Unacceptable Alternative(s)

While the following is legal according to JSON-LD, it is not legal for Activity Streams 2.0 because the context redefines the mapping of Activity Vocabulary terms.

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {
    "displayName_en": {
      "@id": "as:displayName",
      "@language": "en"
    },
    "displayName_fr": {
      "@id": "as:displayName",
      "@language": "fr"
    }
  }],
  "@id": "urn:example:1",
  "displayName_en": "foo",
  "displayNane_fr": "bar"
}
```

Likewise, while the following is legal JSON-LD, the serialization is non-obvious and MUST NOT be used in an Activity Streams 2.0 document. A Language Map MUST be used instead.

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": [
    {
      "@value": "foo", 
      "@language": "en"
    },
    {
      "@value": "bar", 
      "@language": "fr"
    }
  ]
}
```

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. "displayName" is a language map with two values: "foo" with language "en" and "bar" with language "fr"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization