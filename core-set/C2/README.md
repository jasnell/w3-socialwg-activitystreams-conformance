Unless otherwise specified, all properties with date and time values must conform to the "date-time" production in [RFC3339], with an uppercase "T" character used to separate date and time, and an uppercase "Z" character in the absence of a numeric time zone offset. All such timestamps should be represented relative to Coordinated Universal Time (UTC).

## Valid Inputs

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "published": "2015-01-01T12:12:12Z"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:2",
  "published": "2015-01-01T12:12:12-08:00"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:3",
  "published": "2015-01-01T12:12:12.1234Z"
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#published> "2015-01-01T12:12:12Z"^^xsd:dateTime .
<urn:example:2> <http://www.w3.org/ns/activitystreams#published> "2015-01-01T12:12:12-08:00"^^xsd:dateTime .
<urn:example:3> <http://www.w3.org/ns/activitystreams#published> "2015-01-01T12:12:12.1234Z"^^xsd:dateTime .
```

## Invalid Inputs (invalid date formats)

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "published": "2015-01-01t12:12:12"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "published": "Fri, 09 Jan 2015 17:16:58 GMT"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "published": 1420823914
}
```