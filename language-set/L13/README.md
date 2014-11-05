Type:      Roundtrip Test
Condition: Child object overrides default language context

## Input(s)

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "object": {
    "@context": {
      "@language": "fr"
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
      "@language": "fr"
    },
    "displayName": "bar"
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
    "@context": {
      "@language": "fr"
    },
    "displayName": {
      "fr": "bar"
    }
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net"],
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo"
  },
  "object": {
    "displayName": {
      "fr": "bar"
    }
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net"],
  "@id": "urn:example:1",
  "displayName": {
    "@value": "foo",
    "@language": "en"
  },
  "object": {
    "displayName": {
      "@value": "bar",
      "@language": "fr"
    }
  }
}
```

### Acceptable Alternative(s)

Implementations can choose to switch the default language context so long as per-field language context is preserved:

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "fr"}],
  "@id": "urn:example:1",
  "displayName": {
    "en": "foo"
  },
  "object": {
    "displayName": "bar"
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "fr"}],
  "@id": "urn:example:1",
  "displayName": {
    "@value": "foo",
    "@language": "en"
  },
  "object": {
    "displayName": "bar"
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