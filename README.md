# Lightning-Network-Limitations

This repository is a collection of Notebooks and papers that investigate the technical limitations that exist in Bitcoin's Lightning Network Protocol with respect to its ability to scale payments. 
A lot of this is work in progress and many models depend on assumptions that can be justifiably questioned. 
Thus I encourage you to be cautious in case you use these result to draw conclusions. 

## A Mathematical theory of payment channel networks
The main document that this respository contains is a research paper titled: [a mathematical theory of payment channel networks](https://github.com/renepickhardt/Lightning-Network-Limitations/blob/paper/Limits%20of%20two%20party%20channels/paper/a%20mathematical%20theory%20of%20payment%20channel%20networks.pdf). Its contributions are:

* Providing a model and [Integer Linear Program](https://en.wikipedia.org/wiki/Integer_programming) for feasible wealth distributions of users on the lightning network given a channel graph.
* A general formular that estimates the upper bound of payment bandwidth for LN payments (currently section 4.4. of the paper) This was also [discussed during the 2024 Lighting Network Developer summit](https://delvingbitcoin.org/t/ln-summit-2024-notes-summary-commentary/1198) 
* A method to estimate how likely it is that payments are infeasible. This was also [discussed on delving bitcoin](https://delvingbitcoin.org/t/estimating-likelihood-for-lightning-payments-to-be-in-feasible/973) and in the [bitcoin optech newsletter](https://bitcoinops.org/en/newsletters/2024/06/28/).
* A proof that the number of circulations on the liquidity graph is equivalent to the number of equivalent states on the polytope of liquidity states given that two states are equivalent if they yield the same wealth distribution
* The conclusions that two party channels put (potentially too) strong constraints to the ability of liquidity to flow between peers of the network.

## Notebooks & Studies
* We investigate how [economic rational behaviour of nodes relates to the distribution of liquidity](https://github.com/renepickhardt/Lightning-Network-Limitations/blob/sidiropoulos_counter_example/Limits%20of%20two%20party%20channels/Estimating%20Liquidity%20State%20given%20Fees%20and%20Network%20Topologies.ipynb). This notebook in particular states that for any lightning network channel graph besides a spanning tree all channels are expected to be depleted. This goes hand and in hand with [prior research](https://github.com/gr-g/ln-steady-state-model/issues/1) (which operated under different assumptions) and seems to be a rather strong argument for the emergence of hub and spoke models (as one can understand the [results from other researchers](https://pubsonline.informs.org/doi/10.1287/mnsc.2023.03872))
* A follow up studies if the [selfish sending behavior of nodes leads to the same global optimization problem](https://github.com/renepickhardt/Lightning-Network-Limitations/blob/sidiropoulos_counter_example/Limits%20of%20two%20party%20channels/Selfish%20Sending%20yields%20Almost%20solution%20to%20Global%20Fee%20Potential%20Optimization.ipynb). The provided evidence seems to give justification to study the above global optimization problem.
* We studied how the [max flow of liquidity limits the network's ability to conduct payments](https://github.com/renepickhardt/Lightning-Network-Limitations/blob/main/likelihood-of-payment-possability/An%20upper%20Bound%20for%20the%20Probability%20to%20be%20able%20to%20successfully%20conduct%20a%20Payment%20on%20the%20Lightning%20Network.ipynb). This research was [independently verified by other community members](https://stacker.news/items/412708). This study gives an intuitive approach to some of the more abstract results of the mathematical theory of payment channel networks as it quantifies probabilities with which payments between arbitrary peers can occur.
* We provide [explicit code for the ILP that can be used to compute if a wealth distribution is feasible](https://github.com/renepickhardt/Lightning-Network-Limitations/pull/2) on the lightning network.
* We have a [random walk based simulation](https://github.com/renepickhardt/Lightning-Network-Limitations/blob/main/Limits%20of%20two%20party%20channels/A%20Mathematical%20Theory%20of%20Payment%20Channel%20Networks.ipynb) with an approximation to the ILP that hints that multi party channel's may lead to better reliability than two party channels. 

## Limitations on this work

Often we lack precise data to run experiments. Thus we often make simplifying assumptions. We believe the methodology in this research can be used with better assumptions to draw more precise conclusions. For example rather often we assume uniform distribution of payment pairs to arrive at some number. Yet the assumption that payment pairs are uniformly distributed is almost certainly always wrong which is way the actual number derrived in a model is not particularly expressiv. 

Despite peers looking at this stuff and providing feedback there is obviously no guarantee that the models themselves are reasonable and without flaws.

## Acknowledgements: 
The work is sponsored through a [long term support grant from OpenSats](https://opensats.org/blog/rene-pickhardt-receives-lts-grant) and through [individual patreons](https://www.patreon.com/renepickhardt).
