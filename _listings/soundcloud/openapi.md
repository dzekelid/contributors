---
swagger: "2.0"
x-collection-name: SoundCloud
x-complete: 1
info:
  title: Sound Cloud
  description: access-host-upload-and-comment-on-audio-
  version: 1.0.0
host: api.soundcloud.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /groups/{group_id}/contributors.json:
    get:
      summary: Get Groups Contributors
      description: Returns a collection of contributors of the group with group id
      operationId: getGroupsGroupContributors.json
      x-api-path-slug: groupsgroup-idcontributors-json-get
      parameters:
      - in: query
        name: consumer_key
      responses:
        200:
          description: OK
      tags:
      - Groups
      - Contributors
  /groups/{group_id}/contributors.{format}:
    get:
      summary: Get Groups Contributors. Format
      description: Returns a collection of contributors of the group with group id
      operationId: getGroupsGroupContributors.Format
      x-api-path-slug: groupsgroup-idcontributors-format-get
      parameters:
      - in: query
        name: consumer_key
        description: Access, host, upload, and comment on audio
      - in: query
        name: playlist_id
        description: Access, host, upload, and comment on audio
      responses:
        200:
          description: OK
      tags:
      - Groups
      - Contributors
      - ""
      - Format
---