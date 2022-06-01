# Full Text Country Code Lookup!

This module is a clone of [country-code-lookup](https://www.npmjs.com/package/country-code-lookup) with one main difference; You can misspell country names and still get results.

To achieve this, we use [string-similarity](https://www.npmjs.com/package/string-similarity) to search for the most likely result and return that.

# But Why?

Sometimes country data is fetched from different forms with different spellings. For example, I was writing an app that seeks to map IP Data in Geo Map using [chartjs-chart-geo](https://github.com/sgratzl/chartjs-chart-geo) (ChartJs). 

The data used to render the world map is fetched from this [Countries GeoJSON]('https://unpkg.com/world-atlas/countries-50m.json'). Now the trouble is that the GeoJSON contains country names such as "British Virgin Is.". This entry cannot be found unless we use some **full text search** capabilities to match it to "British Virgin Islands".

___
Everything else is as in the original **country-code-lookup** module.


# Country Code Lookup

A node.js module to look up countries by various country codes.

Supported codes:

* FIPS 10-4 codes (2 digits)
* ISO 3166 (2 digits)
* ISO 3166 (3 digits)
* ISO 3166 (numbers)
* Internet codes

## Installation

```
$ npm install country-code-lookup
```

## Usage

```js
const lookup = require('country-code-lookup')

// search by FIPS
lookup.byFips('UK')

// search by ISO
lookup.byIso('GB')
lookup.byIso('GBR')
lookup.byIso(826)

// search by internet code
lookup.byInternet('UK')

// search by country name
// NOTE: Full text search only applies for 'byCountry' search
lookup.byCountry('United Kingdom')

// get an array of all countries
lookup.countries
```

Searching for a country will return either null, or a country object:

```js
{ continent: 'Europe',
  region: 'Western Europe',
  country: 'United Kingdom',
  capital: 'London',
  fips: 'UK',
  iso2: 'GB',
  iso3: 'GBR',
  isoNo: '826',
  internet: 'UK' }
````

## Useful Links

ISO 2 and 3 digit country codes: https://www.iban.com/country-codes

## License

MIT
