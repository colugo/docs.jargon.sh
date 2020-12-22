# Docsify Boilerplate Homepage

> Hey congrats, you are a one step ahead of building your own docs-site/ blog :tada:

[![Made with Docsify](https://img.shields.io/badge/made_with-docsify.js-blue.svg)](https://docsify.js.org/)

## What is this boilerplate all about?
```jargon
c:ANZIC
i:mock.mock:mock as party
i:mock.mock:mock1 as fake
---
Organisation:
 ^abn:Numeric
 industryClassification:Code(ANZIC)[]
 name:OrganisationName
 foo:party.fake
 bar:fake.fake
 coo:not.fake

OrganisationName:
 name:Text[]
```

```jargon

---
Entity
 ^identifIier:Text
 values:ValueObject[]
 aggregate:Aggregate
 
 
ValueObject
 notAnIdentifier:Text
 
Aggregate
 getsIdentifiersFrom:Entity
```

Get the right tool to get started on writing documentation for your app/ service or your own blog.

?> This boilerplate will give you ready made and customizable code, ready to deploy

## Requirements

- Local Development(Any one of following would suffice the need)
  - NodeJS with `yarn` or `npm` for local host
  - Any local server that can host files
  - VS Code live host
- Deployment
  - Netlify or gh-pages or other as per your preferences

---

Made in :heart: with Docsify
