Type:      Roundtrip Test

Condition: Inherited default language context

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content"

## Input(s)

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "object": {
    "displayName": "foo"
  }
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#object> _:c14n0 .
_:c14n0 <http://www.w3.org/ns/activitystreams#displayName> "foo"@en .
```

## Output(s)

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "object": {
    "displayName": "foo"
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "id": "urn:example:1",
  "object": {
    "displayNameMap": {
      "en": "foo"
    }
  }
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "id": "urn:example:1",
  "object": {
    "displayNameMap": {
      "en": "foo"
    }
  }
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "id": "urn:example:1",
  "object": {
    "@context": {"@language": "en"}
    "displayNameMap": {
      "en": "foo"
    }
  }
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "id": "urn:example:1",
  "object": {
    "@context": {"@language": "en"}
    "displayName": "foo"
  }
}
```


## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. object value's "displayName" value is "foo" with language "en"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization