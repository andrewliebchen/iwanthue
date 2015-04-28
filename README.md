# iWantHue API
[iWantHue](https://github.com/medialab/iwanthue) is a palette generator for scientists. This module intends to be a handy port of the original tool for inclusion in other projects.

## Installation
Install iWantHueAPI with NPM:
```
npm install iwanthue-api
```

## Example
```
var iWantHue = require('iwanthue-api');

// Generate a color palette
var colors = iWantHue().generate(
  7,                   // Number of colors to generate
  function(color){     // This function filters valid colors...
    var hcl = color.hcl();
    return hcl[0]>=0 && hcl[0]<=360 && // ...for a specific range of hues
           hcl[1]>=0 && hcl[1]<=3 &&
           hcl[2]>=0 && hcl[2]<=1.5;
  },
  false,               // Use Force Vector (for k-Means, use true)
  50                   // Color steps (quality)
);

// Sort colors by differentiation
var sortedColors = iWantHue().diffSort(colors);
```

## iWantHue Theory
iWantHue aims to distributing colors evenly, in a perceptively coherent space,
constrained by user-friendly settings, and to generate high quality custom palettes.

More can be found [here](http://tools.medialab.sciences-po.fr/iwanthue/theory.php).

## Original tool
If you're looking for the original tool, and a ton of great information, visit http://tools.medialab.sciences-po.fr/iwanthue/index.php.
