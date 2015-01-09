The serialized JSON form of an Activity Streams 2.0 document must be consistent with what would be produced by the standard JSON-LD 1.0 Processing Algorithms and API [JSON-LD-API] Compaction Algorithm using, at least, the normative JSON-LD @context definition provided here. Implementations may augment the provided @context with additional @context definitions but must not override or change the normative context. Implementations may also include in the serialized JSON document additional properties and values not defined in the JSON-LD @context with the understanding that any such properties will likely be unsupported and ignored by consuming implementations that use the standard JSON-LD algorithms. See the Extensibility section for more information on handling extensions within Activity Streams 2.0 documents.

## Valid

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": "Test",
  "published": "2015-01-01T12:12:12Z",
  "rating": 2.5
}
```

## Normalized

```turtle
<urn:example:1> <http://www.w3.org/ns/activitystreams#displayName> "Test" .
<urn:example:1> <http://www.w3.org/ns/activitystreams#published> "2015-01-01T12:12:12Z"^^xsd:dateTime .
<urn:example:1> <http://www.w3.org/ns/activitystreams#rating> "2.5"^^xsd:float .
```

## Output

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "displayName": "Test",
  "published": "2015-01-01T12:12:12Z",
  "rating": 2.5
}
```

## Invalid

Invalid because the core AS 2.0 properties are redefined
```json
{
  "@context": ["http://asjsonld.mybluemix.net",
    {
      "pubdate": "as:published",
      "name": "as:displayName"
    }],
  "@id": "urn:example:1",
  "name": "Test",
  "pubdate": "2015-01-01T12:12:12Z",
  "rating": 2.5
}
```