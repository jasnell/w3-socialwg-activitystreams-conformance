Type:      Roundtrip Test

Condition: Child object overrides default language context

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content"

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

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#displayName> "foo"@en .
<urn:example:1> <http://www.w3.org/ns/activitystreams#object> _:c14n0 .
_:c14n0 <http://www.w3.org/ns/activitystreams#displayName> "bar"@fr .
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
  "displayNameMap": {
    "en": "foo"
  },
  "object": {
    "@context": {
      "@language": "fr"
    },
    "displayNameMap": {
      "fr": "bar"
    }
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net"],
  "@id": "urn:example:1",
  "displayNameMap": {
    "en": "foo"
  },
  "object": {
    "displayNameMap": {
      "fr": "bar"
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
  "displayNameMap": {
    "en": "foo"
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