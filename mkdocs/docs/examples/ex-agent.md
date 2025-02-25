# Agent Examples

This example include agents (people and organizations) and their relationships.

![agent diagram reflecting the yaml below](../assets/examples/agent-rel.png)

``` yaml
# Example: Agents and Agent Relationships

'@context':
  - '@vocab': http://w3id.org/valueflows/ont/vf#
  - alice: https://alice.example/
    bob: https://bob.example/
    fablab: https://fablab.example/
    coop: https://coop.example/

'@graph':

  # Agents

  - '@id': https://alice.example/
    '@type': vf:Person
    name: Alice
    image: https://alice.example/avatar.png
    primaryLocation: https://somelocation.example
    note: Alice is a mechanical engineer who likes to work in the fablab.

  - '@id': https://bob.example/
    '@type': vf:Person
    name: Bob

  - '@id': https://fablab.example/
    '@type': vf:Organization
    name: Driftless Fablab

  - '@id': https://coop.example/
    '@type': vf:Organization
    name: Community Tool Lending Coop

  # Roles

  - '@id': fablab:52f0e212-3c4f-4d27-b345-5e964c135824
    '@type': AgentRelationshipRole
    roleLabel: is member of
    inverseRoleLabel: has member
    note: Both persons and organizations can be members of this fablab.

  - '@id': fablab:02b39a30-3e04-4305-9656-7f261aa63c84
    '@type': AgentRelationshipRole
    roleLabel: is supplier of
    inverseRoleLabel: is customer of

  - '@id': fablab:a25500e0-0106-43cd-8cbb-e74779488835
    '@type': AgentRelationshipRole
    roleLabel: mentors
    inverseRoleLabel: has mentor

  # Relationships

  - '@id': fablab:6b97b1be-8e07-44ac-82e5-214f1b2aaf33
    '@type': AgentRelationship
    subject: https://alice.example/
    relationship: fablab:52f0e212-3c4f-4d27-b345-5e964c135824 # member
    object: https://fablab.example/

  - '@id': fablab:a8236bbb-81e0-422d-9861-56d2417db0fb
    '@type': AgentRelationship
    subject: https://coop.example/
    relationship: fablab:02b39a30-3e04-4305-9656-7f261aa63c84 # trading partner
    object: https://fablab.example/
    note: The coop is a supplier of tools for the fablab.

  - '@id': fablab:6f438393-7f87-4914-806c-e23a4fd15e89
    '@type': AgentRelationship
    subject: https://alice.example/
    relationship: fablab:a25500e0-0106-43cd-8cbb-e74779488835 # mentor
    object: https://bob.example/
    inScopeOf: https://fablab.example/
    note: Alice mentors Bob at the fablab.
```
