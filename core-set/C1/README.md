"When serialized, absent properties are represented by either (a) setting the property value to null, or (b) by omitting the property declaration altogether at the option of the publisher; these representations are semantically equivalent. If a property has an array value, the absence of any items in that array must be represented by omitting the property entirely or by setting the value to null. The appropriate interpretation of an omitted or explicitly null value is that no value has been assigned as opposed to the view that the given value is empty or nil."

## Equivalent Inputs

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "title": "Foo"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "displayName": null,
  "title": "Foo"
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#title> "Foo" .
```

## Output

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "title": "Foo"
}
```

## Invalid Output

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "title": "Foo",
  "displayName": []
}
```

