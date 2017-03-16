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
    {
      "@id": "http://udb-silex.dev/event/6157b74e-600a-4a05-a2dc-c65137192a15",
      "@type": "Event"
    },
    {
      "@id": "http://udb-silex.dev/place/fb43ae3d-d297-4c4a-8479-488fc028c8c8",
      "@type": "Place"
    },
    {
      "@id": "http://udb-silex.dev/place/16aa260e-c861-4fa0-b38d-f5840a7ac8d1",
      "@type": "Place"
    },
    {
      "@id": "http://udb-silex.dev/place/a1b3a9d8-ef08-46eb-8984-c7d3012bbb5a",
      "@type": "Place"
    },
    {
      "@id": "http://udb-silex.dev/place/a6b0ab58-67a5-496a-8ef8-ac2da14828c2",
      "@type": "Place"
    },
    {
      "@id": "http://udb-silex.dev/place/8cc3b0d4-bc97-4c17-b3d4-072ccc58b242",
      "@type": "Place"
    },
    {
      "@id": "http://udb-silex.dev/event/02ca9526-f7d6-4338-80fe-88a346fdd118",
      "@type": "Event"
    },
    {
      "@id": "http://udb-silex.dev/place/179c89c5-dba4-417b-ae96-62e7a12c2405",
      "@type": "Place"
    },
    {
      "@id": "http://udb-silex.dev/event/441a5831-a65e-44fa-81ef-5c47e9c57a05",
      "@type": "Event"
    },
    {
      "@id": "http://udb-silex.dev/event/d8cac5d6-c2b5-4c8d-b730-d9801a920c89",
      "@type": "Event"
    }
  ]
}
```



