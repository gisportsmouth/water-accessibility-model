# water-accessibility-model
Analyse household access to existing and proposed water sources using OpenStreetMap paths, terrain models, walking-time estimation and load-carriage energy metrics.

## Introduction
This code is designed to calculate the savings in terms of time, distance travelled and calories saved after installing new water sources in rural villages.

## Requirements
The input is a folder with one or more csv files, each representing water sources and household locations in a village. The csv file must have the following structure:
- ['Latitude', 'Longitude', 'Description']
- Lat/Lon in WGS1984 (EPSG:4326)
- Description must be WC Source n | Old Water Source n | Household Locations

## Python Environment

