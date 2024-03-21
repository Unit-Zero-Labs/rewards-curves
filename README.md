## Brainstems Reward Curves

stems_monthly_emissions_rates.ipynb provides high level details on STEMS token monthly emissions
stems_node_reward_curve.ipynb provides more of the calculations behind individual node earnings, with simulations for different levels of reputation, utilization, and tokens staked

Reward Curves and Emission Formulas

## Monthly Emission Rates
The monthly emission rate is calculated based on the base annual emission, demand factor, and an offset.
NCM = max(min(demand_factor - offset, 1), -1)
base_monthly_emission = base_annual_emission / 12
monthly_emission = base_monthly_emission * (1 + NCM)

Where:
- NCM is the Network Computation Multiplier
- demand_factor is a factor that adjusts the base emission based on the total computational resources demanded from the network
- offset is an adjustment to the demand factor to calculate the NCM if necessary
- base_annual_emission is the total emissions to be distributed annually
- base_monthly_emission is the base monthly emission without multiplier
- monthly_emission is the adjusted monthly emission based on NCM


## Node Earnings
The earnings for an individual node are calculated using the following formula:
node_earnings = (M * (1 - U) * S) + (M * U * R)

Where:
- M is the base emission for the network, which is a pool of available tokens to be distributed monthly
- U is the network utilization rate, which reflects the proportion of nodes that are actively participating
- S is the individual node stake relative to the total network stake
- R is the individual node reputation score, normalized between 0 and 1


## Reputation Score
The reputation score for a node is calculated using the following formula:
active_ratio = days_deployed / total_days_in_month
revenue_score = sum(contributed_revenue[i] / num_nodes[i]) for i in deployments
reputation_score = active_ratio * revenue_score

Where:
- days_deployed is the number of days the node was actively deployed in the month
- total_days_in_month is the total number of days in the month
- contributed_revenue[i] is the revenue contributed by the node in deployment i
- num_nodes[i] is the total number of nodes in deployment i
- active_ratio is the ratio of days the node was active in the month
- revenue_score is the sum of the node's contributed revenue divided by the number of nodes in each deployment
- reputation_score is the product of the active ratio and revenue score, representing the node's overall reputation

