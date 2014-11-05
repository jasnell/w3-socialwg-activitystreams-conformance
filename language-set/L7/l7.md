Type:      Roundtrip Test
Condition: Multiple languages with default language context

## Input

```json
{
  "@context": [
    "http://asjsonld.mybluemix.net", 
    { "@language": "en" }
  ],
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
  "@context": [
    "http://asjsonld.mybluemix.net", 
    { "@language": "en" }
  ],
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo",
    "fr": "bar"
  }
}
```

## Acceptable Alternative

It is also acceptable for an implementation to drop the default language context so long as per-field language context is preserved using "inline-expansion"

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

Note: the specific value of "@language" is insignificant in this test.

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. There is a default language context or per-field language-context is preserved using "inline-expansion"
1. "displayName" is a language map with two values: "foo" with language "en" and "bar" with language "fr"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization