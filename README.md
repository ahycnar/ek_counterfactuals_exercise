# EK Counterfactuals

Quantitative implementation of Eaton and Kortum (2002) with trade imbalances,
solved by exact hat algebra.

## What this does

Derives the exact hat algebra system for the one-sector EK model augmented with
international transfers, calibrates it to 2014 WIOT bilateral trade flows for 41
countries, and computes the general equilibrium effects of a 10% increase in
Chinese productivity under two alternative numeraires for those transfers.

## Contents

- `ek_counterfactuals.Rmd` — derivation, code and write-up
- `ek_counterfactuals.pdf` — knitted output
- `data/bilateral_trade_country.csv` — bilateral trade flows, 2014 WIOT
- `data/country_list.csv` — 41 country codes
- `docs/CodingTask.pdf` — assignment

## Reproducing

1. Clone the repo and open `ek-counterfactuals.Rproj` in RStudio
2. Install dependencies: `install.packages(c("here", "tidyverse"))`
3. Knit `ek_counterfactuals.Rmd` 

Runs in under a minute.

## Method

The counterfactual is solved by iterating on excess labour demand,

    w_hat(b+1) = w_hat(b) + kappa * Z(w_hat(b))

with kappa = 0.5 and a tolerance of 1e-10. Both counterfactuals converge
monotonically in under 260 iterations. The US wage is the numeraire throughout.

Trade elasticity calibrated to theta = 4.

## Results

A 10% rise in Chinese productivity raises China's real wage by 2.4% and every
other country's by less than 0.02%. Mexico is the only country whose nominal
wage falls, reflecting competition with China in the US market. Gains elsewhere
scale with each country's initial import share from China.

Switching the transfer numeraire from the US wage to the Chinese wage
redistributes between deficit and surplus countries: the change in the real wage
correlates -0.98 with the income-to-spending ratio.

## Source

Data built from the 2014 WIOT, [WIOD 2016 Release](https://www.rug.nl/ggdc/valuechain/wiod/wiod-2016-release).

## Author

Aleksander Hycnar
