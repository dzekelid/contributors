---
swagger: "2.0"
x-collection-name: GitLab
x-complete: 0
info:
  title: GitLab Get Projects Repository Contributors
  version: 1.0.0
  description: Get projects repository contributors.
host: localhost:3000
basePath: /api
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /v3/projects/{id}/repository/contributors:
    get:
      summary: Get Projects Repository Contributors
      description: Get projects repository contributors.
      operationId: getV3ProjectsIdRepositoryContributors
      x-api-path-slug: v3projectsidrepositorycontributors-get
      parameters:
      - in: path
        name: id
        description: The ID of a project
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Repository
      - Contributors
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---