---
title: "Primeira Visualização"
date: 2017-11-14T09:19:47-03:00
draft: false
---
# Titulo

* bla

<div id="vis" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec = {
     "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
    "data": {
        "url":"https://api.insa.gov.br/reservatorios/12172/monitoramento",
        "format": {
            "type": "json",
            "property": "volumes",
            "parse": {"DataInformacao": "utc:%d/%m/%Y"}
        }
    },
    "width": 680,
    "height": 290,
    "mark": "circle",
    "encoding": {
      "x": {
        "field": "DataInformacao",
        "timeUnit": "year",
        "type": "ordinal"
      },
      "y": {
        "field": "DataInformacao",
        "timeUnit": "month",
        "type": "ordinal"
        },
        "color": {"value": "#c49ed3"},

      "size": {
        "field": "Volume",
        "type": "quantitative",
        "aggregate": "mean"
      }
    }
};
vegaEmbed('#vis', spec).catch(console.warn);
</script>
