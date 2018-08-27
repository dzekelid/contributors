swagger: "2.0"
x-collection-name: GitHub
x-complete: 1
info:
  title: GitHub
  version: 1.0.0
host: api.github.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /repos/{owner}/{repo}/contributors:
    get:
      summary: Get Repos Owner Repo Contributors
      description: Get list of contributors.
      operationId: get-list-of-contributors
      x-api-path-slug: reposownerrepocontributors-get
      parameters:
      - in: header
        name: Accept
        description: Is used to set specified media type
      - in: query
        name: access_token
        description: Your Github OAuth token
      - in: query
        name: anon
        description: Set to 1 or true to include anonymous contributors in results
      - in: path
        name: owner
        description: Name of repository owner
      - in: path
        name: repo
        description: Name of repository
      responses:
        200:
          description: OK
      tags:
      - Repos
      - Owner
      - Repo
      - Contributors
  /repos/{owner}/{repo}/stats/contributors:
    get:
      summary: Get Repos Owner Repo Stats Contributors
      description: Get contributors list with additions, deletions, and commit counts.
      operationId: get-contributors-list-with-additions-deletions-and-commit-counts
      x-api-path-slug: reposownerrepostatscontributors-get
      parameters:
      - in: header
        name: Accept
        description: Is used to set specified media type
      - in: query
        name: access_token
        description: Your Github OAuth token
      - in: path
        name: owner
        description: Name of repository owner
      - in: path
        name: repo
        description: Name of repository
      responses:
        200:
          description: OK
      tags:
      - Repos
      - Owner
      - Repo
      - Stats
      - Contributors