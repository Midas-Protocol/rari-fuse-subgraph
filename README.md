# Midas's Fuse Subgraph
_Subgraph for Midas's Fuse pools_

### Quick Start
 - grab dependencies with `yarn`
 - run `yarn codegen` to generate up to date data formats if you modify subgraph.template.yaml or schema.graphql
 - update `config/config.json` with additional networks and startBlocks
 - `yarn deploy <NETWORK_NAME | "all> <GRAPH_API_KEY>` to build subgraph deploy to a network


### Parts Of This Repo
There are 3 Parts to this repo, the schema, the subgraph template yaml, and the mappings.
#### Schema
The schema is found in `schema.graphql`. this is where we define each type of entity in the subgraph, all of the attributes of that entity (including whether they are required or optional), and finnally the relationships between different types of entities
#### Subgraph.yaml
The `subgraph.template.yaml` file is where we define the base contracts that the subgraph will track. This is defined as a template to support cross-chain templating. In this case we only initially track `FusePoolDirectory`. From there we have event hooks setup to trigger specific mapping functions when a specific event is triggered on the the `FusePoolDirectory`, any monitored `Comptroller`, or any monitored `CToken`.

#### src/mappings/
Within the mappings directory we have a bunch of files each one containing functions which are triggered by a specific event as defined in the `subgraph.yaml`

