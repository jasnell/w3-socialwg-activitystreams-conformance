Type:      Roundtrip Test

Condition: Multiple language sensitive properties with default language context "en"

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content" (various combinations)

## Input(s)

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "title": "bar"
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#displayName> "foo"@en .
<urn:example:1> <http://www.w3.org/ns/activitystreams#title> "bar"@en .
```

## Output(s)
```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "title": "bar"
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net"],
  "@id": "urn:example:1",
  "displayNameMap": {
    "en": "foo"
  },
  "titleMap": {
    "en": "bar"
  }
}
```

Note: the specific value of "@language" is insignificant in this test.

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName" or "displayNameMap")
1. @id is identical to input
1. There is no default language context specified in @context, the default language context is set to "en", or per-field language context is preserved using inline expansion.
1. "displayName" value is "foo" with language "en"
1. "title" value is "bar" with language "en"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization