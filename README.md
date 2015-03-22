# Placeholder for WeatherUndergroud Go API

[![GoDoc](https://godoc.org/github.com/Vertikar/weatherunderground?status.svg)](https://godoc.org/github.com/Vertikar/weatherunderground) [![Build Status](https://travis-ci.org/Vertikar/weatherunderground.svg?branch=master)](https://travis-ci.org/Vertikar/weatherunderground)

Placeholder Go (golang) package for use with www.wunderground.com/s API.

For more detail about the library and its features, reference your local godoc once installed.

Contributions welcome!

## Features

### Current Weather Conditions

- By City
- By City,St (State)
- By City,Co (Country)
- By City ID
- By Longitude and Latitude

## Forecast

For a given number of days.

- By City
- By City,St (State)
- By City,Co (Country)
- By City ID
- By Longitude and Latitude

### Access to Condition Codes and Icons

- Thunderstorms
- Drizzle
- Rain
- Snow
- Atmosphere
- Clouds
- Extreme
- Additional

### Data Available in Multiple Measurement Systems

- Fahrenheit (OpenWeatherMap API - imperial)
- Celcius (OpenWeatherMap API - metric)
- Kelvin (OpenWeatherMap API - internal)

## Historical Conditions

- ...still in the works...

## Installation

```bash
go get github.com/briandowns/openweathermap
```

## Examples

There are a few full examples in the examples directory that can be referenced.  1 is a command line application and 1 is a simple web application.

```Go
package main

import (
    "log"
    "fmt"

	// Shortening the import reference name seems to make it a bit easier
    owm "github.com/briandowns/openweathermap"
)

func main() {
    w, err := owm.NewCurrent("F") // fahrenheit (imperial)
    if err != nil {
        log.Fatalln(err)
    }

    w.CurrentByName("Phoenix")
    fmt.Println(w)
}
```

### Current Conditions in metric by location name

```Go
func main() {
    w, err := owm.NewCurrent("C") // celsius (metric)
    if err != nil {
        log.Fatalln(err)
    }

    w.CurrentByName("Phoenix,AZ")
    fmt.Println(w)
}
```

### Forecast Conditions in imperial by coordinates

```Go
func main() {
    w, err := owm.NewForecast("F")
    if err != nil {
        log.Fatalln(err)
    }

    w.DailyByCoordinates(
    		&Coordinates{
    			Longitude: -112.07,
    			Latitude: 33.45,
    		},
    )
    fmt.Println(w)
}
```

### Current conditions in metric by location ID

```Go
func main() {
    w, err := owm.NewCurrent("C")
    if err != nil {
        log.Fatalln(err)
    }

    w.CurrentByID(2172797)
    fmt.Println(w)
}
```
