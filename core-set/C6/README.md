Previous versions of the Activity Streams format used the objectType property to identify the action type. The objectType property must not be used within an Activity Streams 2.0 document to represent object type.

## Valid

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "@type": "Application"
}
```

## Normalized

```turtle
<urn:example:1> a <http://www.w3.org/ns/activitystreams#Application> .
```

## Invalid

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@id": "urn:example:1",
  "objectType": "Application"
}
```