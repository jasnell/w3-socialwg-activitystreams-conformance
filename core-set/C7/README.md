While all properties are optional, all Object instances should at least contain either displayName or displayNameMap.

## Valid

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@type": "Note",
  "displayName": "Test"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@type": "Note",
  "displayNameMap": {
    "en": "Foo",
    "sp": "Bar"
  }
}
```

## OK, but violates the SHOULD because of no displayName

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@type": "Note"
}
```
