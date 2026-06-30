# Airfields

## Purpose

The `airfields` table stores airfields, glider sites and relevant alternate landing sites used by OpenGlide Decision Map.

Airfields are not only map objects.  
They may be home airfields, alternate destinations or landing options used in decision calculations.

## Geometry

Point

## Required fields

| Field | Type | Required | Description |
|---|---|---:|---|
| `airfield_id` | text | yes | Stable internal ID |
| `icao` | text | no | ICAO code if available |
| `name` | text | yes | Airfield name |
| `type` | text | yes | Type of airfield |
| `elevation_m` | integer | yes | Elevation in metres MSL |
| `country` | text | yes | Country code |
| `region_id` | text | no | Reference to region |
| `default_arrival_agl_m` | integer | yes | Default arrival height AGL |
| `default_glide_ratio` | integer | yes | Default decision glide ratio |
| `active` | boolean | yes | Whether the airfield is active |
| `remarks` | text | no | Notes |

## Field values

### `type`

Allowed values:

| Value | Meaning |
|---|---|
| `airfield` | General airfield |
| `glider_site` | Glider site |
| `military` | Military airfield |
| `heliport` | Heliport |
| `unknown` | Unknown or not yet classified |

## Example

| airfield_id | icao | name | type | elevation_m | country | default_arrival_agl_m | default_glide_ratio |
|---|---|---|---|---:|---|---:|---:|
| `ch_lszx` | `LSZX` | Schänis | `glider_site` | 416 | CH | 300 | 25 |
| `ch_lsze` | `LSZE` | Bad Ragaz | `airfield` | 493 | CH | 400 | 25 |
| `at_loih` | `LOIH` | Hohenems | `airfield` | 412 | AT | 400 | 30 |

## Design notes

Airfields may be used as:

- home airfield
- alternate airfield
- destination for decision rules
- reference point for generated glide areas

Calculated arrival heights are not stored here.  
Only default assumptions are stored.

Personal values are stored in `pilot_profiles`.
