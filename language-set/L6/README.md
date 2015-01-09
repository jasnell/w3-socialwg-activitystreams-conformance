Type:      Roundtrip Test

Condition: Multiple Language-sensitive properties Undefined language context

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content"

## Input

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": "foo",
  "title": "bar"
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": null}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "title": "bar"
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#displayName> "foo" .
<urn:example:1> <http://www.w3.org/ns/activitystreams#title> "bar" .
```

## Output(s)
```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": "foo",
  "title": "bar"
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": null}],
  "@id": "urn:example:1",
  "displayName": "foo",
  "title": "bar"
}
```

Note: the specific value of "@language" is insignificant in this test.

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. There is no default language context specified in @context, the default language context is set to null, or specific language-sensitive values are excluded from the language context (see above).
1. "displayName" value is "foo"
1. "title" value is "bar"
1. There is no @language associated with the "displayName" or "title" values

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization