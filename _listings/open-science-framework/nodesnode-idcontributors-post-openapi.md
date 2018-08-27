---
swagger: "2.0"
x-collection-name: Open Science Framework
x-complete: 0
info:
  title: Open Science Framework Create a contributor
  description: |-
    Adds a contributor to a node, effectively creating a relationship between the node and a user.

    Contributors are users who can make changes to the node or, in the case of private nodes, have read access to the node.

    Contributors are categorized as either "bibliographic" or "non-bibliographic" contributors. From a permissions standpoint, both are the same, but bibliographic contributors are included in citations and are listed on the project overview page on the OSF, while non-bibliographic contributors are not.
    #### Permissions
    Only project administrators can add contributors to a node.
    #### Required
    A relationship object with a `data` key, containing the `users` type and valid user ID is required.

    All attributes describing the relationship between the node and the user are optional.
    #### Returns
    Returns a JSON object with a `data` key containing the representation of the new contributor, if the request is successful.

    If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
  contact:
    name: OSF
    url: https://osf.io/support
    email: support@osf.io
  version: "2.0"
host: test-api.osf.io
basePath: /v2
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /nodes/{node_id}/contributors/:
    get:
      summary: List all contributors
      description: |-
        A paginated list of the node's contributors, sorted by their index.

        Contributors are users who can make changes to the node or, in the case of private nodes, have read access to the node.

        Contributors are categorized as either "bibliographic" or "non-bibliographic". From a permissions standpoint, both are the same, but bibliographic contributors are included in citations and are listed on the project overview page on the OSF, while non-bibliographic contributors are not.

        Note that if an anonymous view_only key is being used to view the list of contributors, the user relationship will not be exposed and the contributor ID will be an empty string.

        #### Returns
        Returns a JSON object containing `data` and `links` keys.

        The `data` key contains an array of 10 contributors. Each resource in the array contains the full representation of the contributor, meaning additional requests to a contributor's detail view are not necessary. Additionally, the full representation of the user this contributor represents is automatically embedded within the `data` key of the response.

        The `links` key contains a dictionary of links that can be used for [pagination](#Introduction_pagination).
        #### Filtering
        You can optionally request that the response only include contributors that match your filters by utilizing the `filter` query parameter, e.g. https://api.osf.io/v2/nodes/y9jdt/contributors/?filter[bibliographic]=true.

        Contributors may be filtered by their `bibliographic` and `permission` attributes.
      operationId: nodes_contributors_list
      x-api-path-slug: nodesnode-idcontributors-get
      parameters:
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Contributors
    post:
      summary: Create a contributor
      description: |-
        Adds a contributor to a node, effectively creating a relationship between the node and a user.

        Contributors are users who can make changes to the node or, in the case of private nodes, have read access to the node.

        Contributors are categorized as either "bibliographic" or "non-bibliographic" contributors. From a permissions standpoint, both are the same, but bibliographic contributors are included in citations and are listed on the project overview page on the OSF, while non-bibliographic contributors are not.
        #### Permissions
        Only project administrators can add contributors to a node.
        #### Required
        A relationship object with a `data` key, containing the `users` type and valid user ID is required.

        All attributes describing the relationship between the node and the user are optional.
        #### Returns
        Returns a JSON object with a `data` key containing the representation of the new contributor, if the request is successful.

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
      operationId: nodes_contributors_create
      x-api-path-slug: nodesnode-idcontributors-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: node_id
        description: The unique identifier of the node
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
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