the Activity Streams JSON-LD @context maps the prefix "as:" to the base URI "http://www.w3.org/ns/activitystreams#". This means that terms such as "as:Activity" are equivalent to the expanded form "http://www.w3.org/ns/activitystreams#Activity". In order to best illustrate that implementors must support both forms

## Equivalent Valid Inputs

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@type": "Application"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@type": "as:Application"
}
```

```json
{
  "@context": "http://asjsonld.mybluemix.net",
  "@type": "http://www.w3.org/ns/activitystreams#Application"
}
```

## Invalid Input

Invalid because the Application class is redefined

```json
{
  "@context": ["http://asjsonld.mybluemix.net",
    {"App": "as:Application"}],
  "@type": "App"
}
```