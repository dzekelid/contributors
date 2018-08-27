swagger: "2.0"
x-collection-name: Medium
x-complete: 1
info:
  title: Medium.com
  description: mediums-unofficial-api-documentation-using-openapi-specification--official-apiofficial-api-document-can-also-be-viewed-for-most-up-to-date-api-spec-at-httpsgithub-commediummediumapidocshttpsgithub-commediummediumapidocs-developer-blog--welcome-to-the-medium-apihttpsmedium-comblogwelcometothemediumapi3418f956552
  termsOfService: https://medium.com/@feerst/2b405a832a2f
  contact:
    name: Hossain Khan
    url: https://github.com/amardeshbd/medium-api-specification
  version: 1.0.0
host: api.medium.com
basePath: /v1
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /publications/{publicationId}/contributors:
    get:
      summary: Contributors of Publication
      description: This endpoint returns a list of contributors for a given publication.
        In other words, a list of Medium users who are allowed to publish under a
        publication, as well as a description of their exact role in the publication
        (for now, either an editor or a writer).
      operationId: publications.publicationId.contributors.get
      x-api-path-slug: publicationspublicationidcontributors-get
      parameters:
      - in: path
        name: publicationId
        description: A unique identifier for the publication
      responses:
        200:
          description: OK
      tags:
      - Publications
      - Publication
      - Contributors