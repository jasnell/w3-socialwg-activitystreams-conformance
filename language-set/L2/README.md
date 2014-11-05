Type:      Roundtrip Test
Condition: Value object with @language = null

## Input(s)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": {
    "@value": "foo"
  }
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": {
    "@value": "foo",
    "@language": null
  }
}
```

## Output(s)
```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": "foo"
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": null}],
  "@id": "urn:example:1",
  "displayName": "foo"
}
```

### Acceptable but discouraged Output

The following output(s) define a default language context for the document but use a JSON-LD trick to specifically indicate that the default does not apply to "displayName". While this is legal, it is non-obvious and SHOULD be avoided.

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": {
    "@value": "foo"
  }
}
```

```json
{
  "@context": ["http://asjsonld.mybluemix.net", {"@language": "en"}],
  "@id": "urn:example:1",
  "displayName": {
    "@value": "foo",
    "@language": null
  }
}
```

Note: the specific value of "@language" is insignificant in this test.

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. There is no default language context specified in @context, the default language context is set to null, or specific language-sensitive values are excluded from the language context (see above).
1. "displayName" value is "foo"
1. There is no @language associated with the "displayName" value

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization