

## Data Tidying

* Set all names to the format: `Id|host_species|geoloc|genotype|cdate`. If some data field is not available, use '\*'. You can work with csv or .fasta, doesn't matter which (because it's easy to convert from one to the other anyway). Use backslashes as a secondary delimiter, such as for locations which have higher resolution data like country and street number, e.g. `19977|*|Singapore\KimChuanRd|D1GIII_13_EW19|2014`
* Some of the dates are delimited by underscores or backslashes. Convert these delimiters to hyphens, i.e. 2010-10-28
* Standardize location names: check that there aren't multiple ways to spell the same location, e.g. standardize "Hong Kong", "HongKong", "Hongkong" or "Hong_Kong"...etc.
* Remove special characters. Try to keep only "|", "\_", either of the slashes, or "-".
* Some of the Singaporean sequences have the week in there, e.g. The second last field, `EW03`, in  `03683|Singapore|HillsideDr|D2CosmoIndian|13|EW03|2013`. This means that the sequence was collected in week 3 (out of 52 in a year) Get an estimate of the month of when this week occured, and add that to the collection date (e.g. week 3 is in january, so we add the month to the cdate: `2013-01`)

## Files

Under `data`:

* <dx_cdh>.fas: balanced by country+year, where oversized subpopulations got downsampled using `cd-hit` with `-c 1.0`.
