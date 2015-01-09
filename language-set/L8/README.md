Type:      Roundtrip Test

Condition: Multiple language sensitive properties with different languages

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content" (various combinations)

## Input(s)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayNameMap": {
    "en": "foo"
  },
  "titleMap": {
    "fr": "bar"
  }
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#displayName> "foo"@en .
<urn:example:1> <http://www.w3.org/ns/activitystreams#title> "bar"@fr .
```

## Output(s)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayNameMap": {
    "en": "foo"
  },
  "titleMap": {
    "fr": "bar"
  }
}
```

### Acceptable Alternative(s)

An implementation can choose to inject it's own default language context and serialize accordingly so long as per-field language context is preserved:

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "titleMap": {
    "fr": "bar"
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "fr"}],
  "@id": "urn:example:1",
  "displayNameMap": {
    "en": "foo"
  },
  "title": "bar"
}
```

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName" or "displayNameMap")
1. @id is identical to input
1. "displayName" value is "foo" with language "en"
1. "title" value is "bar" with language "fr"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization