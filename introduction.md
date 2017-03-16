# Searching events & places

Events & places can be searched from the following endpoint:

```
GET https://search.uitdatabank.be/offers/
```

The response body from this endpoint looks like this:

```js
{
  "@context": "http://www.w3.org/ns/hydra/context.jsonld",
  "@type": "PagedCollection",
  "itemsPerPage": 30,
  "totalItems": 12,
  "member": [
    {
      "@id": "http://udb-silex.dev/place/39e6d5ee-c3d6-453a-bcb5-4e6e0eaf7054",
      "@type": "Place"
    },
    {
      "@id": "http://udb-silex.dev/event/23017cb7-e515-47b4-87c4-780735acc942",
      "@type": "Event"
    },
    ...
  ]
}
```



