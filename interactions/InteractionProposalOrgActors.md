# Proposal for interaction between Organizations and Actors service
This should eventually be converted to an OpenAPI spec file.

## Interaction

1. Client application runs `POST /actors '{ "name": "Some name", "organization": { "id": 1234 } }` to create a new actor
2. Actors service generates unique ID for the new actor. For this example let's say it's 5678
3. Actors service runs `POST /organizations/members '{ "organizationId": 1234, "actorId": 5678 }'`
4. [implementation details specific to organizations service]
5. Organizations service returns a code of 402 (Payment Required) if there are too many actors in the organization for the current payment plan. Otherwise it returns 200
6. Actors service takes appropriate action based on the response
