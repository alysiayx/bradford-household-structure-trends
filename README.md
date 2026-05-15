# Bradford Household Trends

This repository explores how household composition and household size have changed in Bradford across the 2001, 2011 and 2021 Censuses.

The work brings together household data downloaded from Nomis, cleans and standardises the files, and prepares them for comparison across time. The main focus is on producing comparable ward-level figures, while also keeping Bradford-wide and England-level figures for context.

The analysis currently covers two themes:

- household composition
- household size

## What this project does

The workflow:

- standardises column names across census years;
- tidies geography type labels so they are easier to compare;
- maps LSOA-level data to 2025 ward boundaries;
- reallocates LSOA counts to wards using split weights where an LSOA falls into more than one ward;
- keeps non-LSOA records, such as Bradford / local authority district and England totals, unchanged;
- harmonises household composition categories so that 2001, 2011 and 2021 can be compared more easily;
- calculates counts and percentages for each geography and census year;
- creates basic charts to explore trends over time;
- exports both long and wide versions of the data for further analysis or visualisation.

## Household composition

Household composition categories are not identical across the three Census years, so a manually curated mapping file is used to align them into a more consistent set of categories.

Some categories are also split into broader and more detailed levels, such as `main_category`, `sub_category1`, and `sub_category2`. This makes it easier to look at both high-level patterns and more detailed breakdowns.

## Household size

Household size categories are more consistent across the three Census years, so they do not need the same level of category harmonisation.

The same geography processing is applied: LSOA-level records are mapped to 2025 wards, ward-level counts are recalculated, and percentages are calculated within each geography and year.

One small adjustment is made for 2021: the `0 people in household` category is removed, as it contains zero households.

## Mapping LSOAs to wards

Some LSOAs are split across more than one 2025 ward. In those cases, the household counts are distributed using the split weights in the lookup table.

For example, if an LSOA is split equally across three wards, one third of the count for each household category is assigned to each ward. The weighted values are then summed to create the final ward-level estimates.

## Outputs

The project produces cleaned household composition and household size datasets, including:

- long-format files for analysis;
- wide-format files for visualisation tools such as Flourish;
- ward-level estimates for 2025 ward boundaries;
- Bradford / local authority district and England-level comparison data.
