---
title: "Primeira Visualização"
date: 2017-11-14T09:19:47-03:00
draft: false
---

{
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
}
