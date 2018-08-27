---
swagger: "2.0"
x-collection-name: Open Science Framework
x-complete: 0
info:
  title: Open Science Framework Retrieve a contributor
  description: |-
    Retrieves the details of a contributor on this registration.

    #### Returns
    Returns a JSON object with a `data` key containing the representation of the requested contributor, if the request is successful.

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
  /nodes/{node_id}/contributors/{user_id}/:
    delete:
      summary: Delete a contributor
      description: |-
        Removes a contributor from a node. This request only removes the relationship between the node and the user, it does not delete the user itself.

        A node must always have at least one admin, and attempting to remove the only admin from a node will result in a **400 Bad Request** response.
        #### Permissions
        A user can remove themselves as a node contributor. Otherwise, only project administrators can remove contributors.
        #### Returns
        If the request is successful, no content is returned.

        If the request is unsuccessful, a JSON object with an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
      operationId: nodes_contributors_delete
      x-api-path-slug: nodesnode-idcontributorsuser-id-delete
      parameters:
      - in: path
        name: node_id
        description: The unique identifier of the node
      - in: path
        name: user_id
        description: The unique identifier of the user
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Contributors
      - User
    get:
      summary: Retrieve a contributor
      description: |-
        Retrieves the details of a given contributor.

        Contributors are users who can make changes to the node or, in the case of private nodes, have read access to the node.

        Contributors are categorized as either "bibliographic" or "non-bibliographic". From a permissions standpoint, both are the same, but bibliographic contributors are included in citations and are listed on the project overview page on the OSF, while non-bibliographic contributors are not.
        #### Returns
        Returns a JSON object with a `data` key containing the representation of the requested contributor, if the request is successful.

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
      operationId: nodes_contributors_read
      x-api-path-slug: nodesnode-idcontributorsuser-id-get
      parameters:
      - in: path
        name: node_id
        description: The unique identifier of the node
      - in: path
        name: user_id
        description: The unique identifier of the user
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Contributors
      - User
    patch:
      summary: Update a contributor
      description: |-
        Updates a contributor by setting the values of the attributes specified in the request body. Any unspecified attributes will be left unchanged.

        Contributors can be updated with either a **PUT** or **PATCH** request. Since this endpoint has no mandatory attributes, PUT and PATCH are functionally the same.
        #### Permissions
        Only project administrators can update the contributors on a node.
        #### Returns
        Returns a JSON object with a `data` key containing the new representation of the updated contributor, if the request is successful.

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.

        If the given user is not already in the contributor list, a 404 Not Found error will be returned. A node must always have at least one admin, and any attempt to downgrade the permissions of a sole admin will result in a 400 Bad Request error.
      operationId: nodes_contributors_partial_update
      x-api-path-slug: nodesnode-idcontributorsuser-id-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: node_id
        description: The unique identifier of the node
      - in: path
        name: user_id
        description: The unique identifier of the user
      responses:
        200:
          description: OK
      tags:
      - Nodes
      - Node
      - Contributors
      - User
  /registrations/{registration_id}/contributors/:
    get:
      summary: List all contributors
      description: |-
        A paginated list of all contributors on this registration.
        The returned contributors are sorted by their index.

        Contributors are users who can make changes to the registration or, in the case of private registration, have read access to the registration.

        Contributors are categorized as either "bibliographic" or "non-bibliographic". From a permissions standpoint, both are the same, but bibliographic contributors are included in citations and are listed in the contributors list on the OSF, while non-bibliographic contributors are not.

        Note that if an anonymous view_only key is being used to view the list of contributors, the user relationship will not be exposed and the contributor ID will be an empty string.

        #### Returns
        Returns a JSON object containing `data` and `links` keys.

        The `data` key contains an array of up to 10 contributors. Each resource in the array contains the full representation of the contributor. Additionally, the full representation of the user this contributor represents is automatically embedded within the `data` key of the response.

        The `links` key contains a dictionary of links that can be used for [pagination](#Introduction_pagination).
        #### Filtering
        You can optionally request that the response only include contributors that match your filters by utilizing the `filter` query parameter, e.g. https://api.osf.io/v2/registrations/wu3a4/contributors/?filter[bibliographic]=true.

        Contributors may be filtered by their `bibliographic` and `permission` attributes.
      operationId: registrations_contributors_list
      x-api-path-slug: registrationsregistration-idcontributors-get
      parameters:
      - in: path
        name: registration_id
        description: The unique identifier of the registration
      responses:
        200:
          description: OK
      tags:
      - Registrations
      - Registration
      - Contributors
  /registrations/{registration_id}/contributors/{user_id}/:
    get:
      summary: Retrieve a contributor
      description: |-
        Retrieves the details of a contributor on this registration.

        #### Returns
        Returns a JSON object with a `data` key containing the representation of the requested contributor, if the request is successful.

        If the request is unsuccessful, an `errors` key containing information about the failure will be returned. Refer to the [list of error codes](#Introduction_error_codes) to understand why this request may have failed.
      operationId: registrations_contributors_read
      x-api-path-slug: registrationsregistration-idcontributorsuser-id-get
      parameters:
      - in: path
        name: registration_id
        description: The unique identifier of the registration
      - in: path
        name: user_id
        description: The unique identifier of the user
      responses:
        200:
          description: OK
      tags:
      - Registrations
      - Registration
      - Contributors
      - User
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