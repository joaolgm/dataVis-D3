---
title: "Visualizações sobre o Açude de Boqueirão"
date: 2017-11-14T09:19:47-03:00
draft: false
---
# Açude de Boqueirão

#### Com os dados coletados sobre o açude de boqueirão desde o ano de 1990 até a atualidade é possível perceber que o nível de água variou bastante, também pode-se notar que existe alguns padrões entre um período de seca e outro, além de mudanças repentinas no aumento do volume das águas.

<div id="meanVolume" width=300></div>

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
vegaEmbed('#meanVolume', spec).catch(console.warn);
</script>

* O tamanho dos círculos mostra a média de volume de água em milhões de metros cúbicos e as coordenadas horizontal e vertical identificam os anos e meses que foram coletados os dados, respectivamente. É possível fazer uma comparação entre as secas de 1999 e 2016.

<div>
<div id="raining" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec2 = {
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
    "mark": "point",
    "encoding": {
      "x": {"field": "DataInformacao","timeUnit": "year", "type": "ordinal"},
      "y": {"field": "VolumePercentual","type": "quantitative", "aggregate": "mean"},
      "color": {"value": "#c49ed3"}
  }
};
vegaEmbed('#raining', spec2).catch(console.warn);
</script>

* A coordenada horizontal mostra os anos que os dados foram coletados e a vertical a média do volume percentual. É possível perceber facilmente que em alguns anos o volume de chuvas foi bastante elevado.

<div id="pattern" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec3 = {
     "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
    "data": {
        "url":"https://api.insa.gov.br/reservatorios/12172/monitoramento",
        "format": {
            "type": "json",
            "property": "volumes",
            "parse": {"DataInformacao": "utc:%d/%m/%Y"}
        }
    },
     "vconcat": [{
    "width": 680,
    "height": 290,
    "mark": "area",
    "encoding": {
      "x": {
        "field": "DataInformacao",
        "type": "temporal",
        "scale": {"domain": {"selection": "brush"}},
        "axis": {"title": ""}
      },
      "y": {"field": "Volume","type": "quantitative"},
      "color": {"value": "#c49ed3"}
    }
  }, {
    "width": 490,
    "height": 90,
    "mark": "area",
    "selection": {
      "brush": {"type": "interval", "encodings": ["x"]}
    },
    "encoding": {
      "x": {
        "field": "DataInformacao",
        "type": "temporal",
        "axis": {"format": "%Y"}
      },
      "y": {
        "field": "Volume",
        "type": "quantitative",
        "axis": {"tickCount": 5, "grid": false}
      },
      "color": {"value": "#c49ed3"}
    }
  }]
};
vegaEmbed('#pattern', spec3).catch(console.warn);
</script>

* A coordenada vertical mostra o volume em milhões de metros cúbicos e a horizontal mostra os dias que foram coletados os dados, dando assim uma visão geral da situação do açude.
