# Sustainability assessment visualization contest

**Deadline pushed back to February 19, 2023**

Visualization of life cycle assessment information could be significantly improved. Visualization of input data, calculation results, and interpretation algorithms helps us understand what we can say, how strongly we can believe it, and where we should prioritize future work. We invite entries on visualization schemes, graph layouts, and interactive programs; All forms of visualization are acceptable.

We have provided examples of the types of visualization used in life cycle assessment in the [examples directory](https://github.com/Depart-de-Sentier/visualization-contest-2022/tree/main/examples).

## Example data

We have provided example data drawn from the open [US EEIO table](https://github.com/USEPA/USEEIO), and [available here (115MB download)](https://files.brightway.dev/visualization_example_data.zip). The US EEIO can be thought of as a graph, with nodes and edges. In this perspective, the edges trace the flow of money through industries (industries buy inputs from other industries), and of mass or energy as the economy interacts with the natural world (industries releases pollution and consume natural resources).

The code to create the example data is given in the notebook [`Visualization fixtures creation.ipynb`](https://github.com/Depart-de-Sentier/visualization-contest-2022/blob/main/Visualization%20fixtures%20creation.ipynb).

The example data has the following files and file structure:

* `useeio_nodes.csv`: Metadata on the products and nodes provided in the database. The integer ids in this file are used consistently in all other data files.
* `useeio_edges.csv`: Edges are between two nodes in the database and represent the consumption of inputs or the releases of emissions relative to one dollar of that industry's production. For example, the second data line in this file tells us that there is an edge of 0.00133 USD from `State and local government enterprises` to `Frozen food; at manufacturer`. These edges are in relation to the production amount of the target node (`Frozen food; at manufacturer`) - the first data line tells us that the production amount is 1 USD.
* `useeio_product_scores.csv`: A list of the total environmental impact of consuming one dollar of each product in the US EEIO for 19 impact categories. The unit is dependent on the impact category, see the US EEIO repo for details.
* `useeio_technsophere_matrix.csv` and `useeio_biosphere_matrix.csv`: If we transform our graph edges into a matrix, we would the technosphere matrix (flows between industries) and the biosphere matrix (flows to or from the natural world). In the technosphere matrix, consumption is negative and production is positive; in the biosphere matrix, everything is positive, even consumption of natural resources (yes, we know...). In these files, the `row_id` and `col_id` refer to the ids given in `useeio_nodes.csv`.
* `products`: Folder given more detail on the source of impacts for all products and all impact categories. The folder names are id numbers; each file is for one impact category, and gives the inputs which are directly responsible for the highest impact. By directly responsible, we mean the processes which produce actual emissions or consume resources, not the supply chain which induces these effects. In the categorized matrix, rows are biosphere flows (emissions and resources), and columns are processes.
* `characterization`: Characterization matrices for the different impact categories which list the relative impact of emissions (e.g. methane has more global warming potential than CO2)
* `graphs`: Graph traversal results for four impact categories and five products each which show *how* impacts can flow down the supply chain. The data format [is explained in the documentation](https://github.com/brightway-lca/brightway2-calc/blob/master/bw2calc/graph_traversal.py#L253).

If you have questions, please [create an issue](https://github.com/Depart-de-Sentier/visualization-contest-2022/issues/new), give it the label "question", and tag @cmutel and @tngTUDOR in the question text.

## Prize fund

The prize fund is €2000, sponsored by the [ecoinvent association](https://ecoinvent.org/). Thanks a lot!

* First place: €1000
* Second place: €500
* Third place: €250 (2 awards)

## Rules

* Entries must be submitted by 12:00 UTC on February 19, 2023
* Entries can be from individuals or teams. Teams must nominate one member to receive the prize money.
* Entries are submitted by creating a [new issue in the contest repository](https://github.com/Depart-de-Sentier/visualization-contest-2022/issues) with the label `entry`. Entries must include links to the visualization, the code used to create the visualization, and a video presenting the visualization.
* Entries must include linked source code with an open license. Entry code licensed using the GPL or AGPL are not eligible for prizes.
* Entries must be complete software programs which consume one of the example datasets or other LCA/MFA/Industrial Ecology data. Please provide a link if not using the data provided. Installation instructions must be provided if needed.
* Prizes will be awarded by a committee of ecoinvent association staff, Départ de Sentier members, and graphic design professionals.
* Monetary prizes can only be awarded to participants in countries reachable via either a SWIFT transaction or via Wise.com. The organizing committee reserves the right to cancel monetary prizes in cases where the award of such prizes would pose legal or reputational risks.
