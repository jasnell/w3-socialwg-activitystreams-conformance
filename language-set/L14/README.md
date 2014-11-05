Type:      Roundtrip Test
Condition: Child object overrides default language context with null

## Input(s)

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "object": {
    "@context": {
      "@language": null
    },
    "displayName": "bar"
  }
}
```

## Output(s)

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "object": {
    "@context": {
      "@language": null
    },
    "displayName": "bar"
  }
}
```

### Acceptable but Discouraged Alternative(s)

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo"
  },
  "object": {
    "@context": {
      "@language": null
    },
    "displayName": {
      "@value": "bar"
    }
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo"
  },
  "object": {
    "displayName": {
      "@value": "bar",
      "@language": null
    }
  }
}
```

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. containing object's "displayName" value is "foo" with language "en"
1. "object" value's "displayName" value is "bar" with language "fr"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization