---
name: Medium
x-slug: medium
description: Medium is an online publishing platform founded by Twitter co-founder
  Evan Williams in August 2012. The platform has evolved into a hybrid of non-professional
  contributions and professional, paid contributions, an example of social journalism.
image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/medium-logo.png
x-kinRank: "8"
x-alexaRank: "0"
tags: Contributors
created: "2018-08-27"
modified: "2018-08-27"
url: https://raw.githubusercontent.com/streamdata-gallery-topics/contributors/master/_listings/medium/apis.md
specificationVersion: "0.14"
apis:
- name: Medium.com - Contributors of Publication
  x-api-slug: publicationspublicationidcontributors-get
  description: This endpoint returns a list of contributors for a given publication.
    In other words, a list of Medium users who are allowed to publish under a publication,
    as well as a description of their exact role in the publication (for now, either
    an editor or a writer).
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/medium-logo.png
  humanURL: https://medium.com/
  baseURL: https://api.medium.com//v1
  tags: Blogging, Communications, Stack Network, Media, API Provider, API Service
    Provider, SDIO Syndication, Profiles, General Data, Relative Data
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/contributors/master/_listings/medium/publicationspublicationidcontributors-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/contributors/master/_listings/medium/publicationspublicationidcontributors-get-openapi.md
x-common:
- type: x-api-gallery
  url: http://mattermost.api.gallery.streamdata.io
- type: x-api-stack
  url: http://medium.stack.network
- type: x-github
  url: https://github.com/Medium
- type: x-transparency-report
  url: https://medium.com/transparency-report
- type: x-twitter
  url: https://twitter.com/Medium
- type: x-website
  url: https://medium.com/
include: []
maintainers:
- FN: Kin Lane
  x-twitter: apievangelist
  email: info@apievangelist.com
---