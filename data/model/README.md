# Hydrodynamic-model output

`near_bottom_currents_model_2011_2012.csv.gz` – hourly near-bottom currents from a
three-dimensional hydrodynamic model of the Gulf of Eilat/Aqaba (December 2011 –
November 2012), extracted at the model grid cells nearest to the 18 study stations
(100, 200 and 300 m, inside and outside Eilat, Shlomo and Princess Canyons; see
Table S3 of the article). The file is a gzip-compressed CSV (8,760 hourly rows per
station); R (`readr::read_csv`) reads it directly, and it can be opened with any
unzip tool.

| Column | Description |
|---|---|
| `DateTime` | date and time, `dd/mm/yyyy HH:MM` (UTC) |
| `Canyon`, `Location` | canyon and position (`In` / `Out`) |
| `Iteration` | model time step |
| `Station` | station name |
| `StationLatitude`, `StationLongitude` | target station position (decimal degrees) |
| `ModelLatitude`, `ModelLongitude` | centre of the model grid cell (decimal degrees) |
| `TargetDepth_m` | target depth of the station (m) |
| `BottomDepth_m` | depth of the centre of the extraction cell (m): the deepest vertical cell of the water column that is at least half wet (`hFacC` ≥ 0.5); the model seabed lies 0–20 m deeper (0–25 m below 250 m). Not the model bottom depth |
| `U_cm_s`, `V_cm_s`, `W_cm_s` | velocity along the model grid axes and vertical velocity (cm s⁻¹). The model grid is rotated so that its y axis runs along the gulf (bearing 16.5° east of north): `U` is the across-gulf and `V` the along-gulf component, **not** east and north. Script 2 rotates them to east (u = U cos 16.5° + V sin 16.5°) and north (v = −U sin 16.5° + V cos 16.5°) |
| `Speed_cm_s` | horizontal current speed (cm s⁻¹) |
| `DirectionTo_deg` | direction toward which the current flows, relative to the model grid (add 16.5° for the geographic bearing) |

The 100-m stations are named after the mooring sites (e.g. `Eilat Canyon - inside`;
`Solomon` = Shlomo Canyon).

Model layers are 20 m thick between 50 and 250 m and 30 m thick between 250 and 550 m.
The run is forced by 3-hourly WRF winds for the actual period 1 December 2011 – 29 November 2012
(MITgcm configuration of Biton and Gildor 2011; no tidal forcing).
