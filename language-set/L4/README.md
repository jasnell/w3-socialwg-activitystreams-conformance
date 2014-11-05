Type:      Roundtrip Test

Condition: Language Map with "en":"foo"

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content"

## Input(s)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo"
  }
}
```

## Output(s)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": {
    "@value": "foo", 
    "@language": "en"
  }
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo"
  }
}
```

### Acceptable Alternative

An implementation MAY inject it's own default language context and serialize accordingly.

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": "foo"
}
```

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. "displayName" value is "foo" with language "en"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization