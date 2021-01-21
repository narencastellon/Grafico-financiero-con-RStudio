# Grafico-financiero-con-RStudio

---
title: "Gráficos Financieros"
author: "Naren Castellón"
date: "01/21/2021"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## **Gráficos**

En este apartado revisaremos como construir gráficos aparir de los datos financieros usando el paquete `quantmod`, que nos permitira poder importar eso datos a nuestra consola, además de brindarnos varios tipos de gráfico para poder analizarlo.

Quantmod dibuja buenos gráficos de los siguientes tipos comunes:

1. Línea
2. Barras
3. Candelas

Podemos usar `chartSeries()` y especificar los tipos directamente.

**Sintaxis:**

```{r eval=FALSE}
chartSeries(x,
           type = c("auto", "candlesticks", "matchsticks", "bars","line"), 
           subset = NULL,
           show.grid = TRUE, 
           name = NULL,
           time.scale = NULL,
           log.scale = FALSE,
           TA = 'addVo()',
           TAsep=';',
           line.type = "l",
           bar.type = "ohlc",
           theme = chartTheme("black"),
           layout = NA,
           major.ticks='auto', minor.ticks=TRUE,
           yrange=NULL,
           plot=TRUE,
           up.col,dn.col,color.vol = TRUE, multi.col = FALSE,
           ...)
```

## **Gráfico de líneas**

El gráfico de líneas muestra el precio de cierre de la acción.

El siguiente código muestra el precio de AMZN en 2020 mediante la opción de subconjunto . El tema de la opción está configurado para ser chartTheme ('blanco') ya que la opción predeterminada chartTheme ('negro').

```{r message=FALSE}
library(quantmod)
stocklist <- c("AAPL", "MSFT", "AMZN", "EBAY")
getSymbols(stocklist)
#GRAFICO
chartSeries(AMZN, lwd=10,
            type="line",
            subset="2020",
            theme=chartTheme("white"))
```

Además del gráfico de líneas en la parte superior, la parte inferior del gráfico es el volumen.

## **Gráfico de barras**

El gráfico de barras muestra el precio de cierre de apertura, máximo, mínimo, cierre y volumen de la acción. La parte superior de la barra es alta y la parte inferior de la barra es baja. El joystick izquierdo está abierto y el joystick derecho está cerca.

Si el cierre es más alto que abierto, la barra es de color verde. De lo contrario, es de color naranja. Por lo tanto, la coloración es fácil de ver en la pantalla, pero no es fácil para la impresión en blanco y negro.

El siguiente gráfico de barras muestra el precio de las acciones de AMZN de mayo a junio de 2020 mediante la opción de subconjunto .

```{r}
chartSeries(AMZN, 
            type="bar",show.grid = TRUE,
            subset='2020-05::2020-06',
            theme=chartTheme('white'))
```

## **Gráfico de velas**

Un gráfico de velas es muy similar a un gráfico de barras. También muestra el precio de cierre de apertura, máximo, mínimo, cierre y volumen de la acción.

La parte superior de un palo de vela es alta y la parte inferior de un palo de vela es baja. Los dos extremos del cuerpo de la vela están abiertos o cerrados, dependiendo de si la apertura es más alta que la cerrada, lo que también está representado por el color naranja (rojo, negro) o verde (blanco).

Si el cierre es más alto que abierto, la barra es de color verde. De lo contrario, es de color naranja.

El siguiente gráfico de velas muestra el precio de las acciones de AMZN solo en mayo.

```{r}
chartSeries(AMZN,
            type="candlesticks",
            subset='2020-12',show.grid = TRUE,
            up.col = 'white',
            down.col = 'black',
            theme=chartTheme('black'))
```

