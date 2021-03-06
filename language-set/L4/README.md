Type:      Roundtrip Test

Condition: Default language context

Repeat Test for each of the language sensitive core properties: "displayName", "title", "summary", "content"

## Input

```json
{
  "@context": [
    "http://asjsonld.mybluemix.net", 
    { "@language": "en" }
  ],
  "@id": "urn:example:1",
  "displayName": "foo"
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#displayName> "foo"@en .
```

## Output(s)
```json
{
  "@context": [
    "http://asjsonld.mybluemix.net", 
    { "@language": "en" }
  ],
  "@id": "urn:example:1",
  "displayName": "foo"
}
```

## Acceptable Alternatives

The following alternative outputs use "inline expansion" of the default language context.

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayNameMap": {
    "en": "foo"
  }
}
```

Note: the specific value of "@language" is insignificant in this test.

## Success Conditions

1. Activity Vocabulary Terms are serialized without a prefix (as: or otherwise)
1. Activity Vocabulary Terms MUST NOT be redefined in the output context (e.g. "http://www.w3.org/ns/activitystreams#displayName" MUST be mapped to "displayName")
1. @id is identical to input
1. The default language context is "en" or per-field language context is preserved using "inline-expansion"
1. "displayName" value is "foo" with language "en"

## Parameters

1. Ordering of properties in output or input is insignificant, implementations are not required to preserve order

## Reference

1. http://www.w3.org/TR/json-ld/#string-internationalization