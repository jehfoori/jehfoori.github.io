---
layout: ../../layouts/CaseStudy.astro
title: "UC-Lavatory: Campus restroom reviews"
category: Web development · UCLA CS35L
summary: A five-person course project combining a campus map and restroom reviews in a React, Express, and MySQL application. My work focused on the interactive map and review interface.
role: Map and frontend contributor
period: September–December 2022
team: Five-person team
tools: [JavaScript, React, React Leaflet, GeoLib, Axios, Express, MySQL]
evidence:
  - label: Team repository
    url: https://github.com/james-zhng/UC-LAvatory
  - label: Nearest-building lookup implementation
    url: https://github.com/james-zhng/UC-LAvatory/commit/90312f9
  - label: Review-page interface improvements
    url: https://github.com/james-zhng/UC-LAvatory/commit/700c5aa
note: An earlier course project developed for local use. Source code and contribution history are available; there is no live demo.
---

## The application

Our five-person team built UC-Lavatory to help students find campus restrooms and read reviews by building. The application combined an interactive React Leaflet map, building-specific review pages, and a form for submitting ratings and comments.

The team’s full-stack application used React for the interface, an Express API for requests, and MySQL for persistent review data. Users could browse reviews, filter by floor and restroom category, sort by rating or date, and view average ratings. My contribution centered on the map and frontend; teammates handled most backend development.

## My contribution

- Built the interactive campus map with building markers and popups, then corrected marker behavior and adjusted the map layout.
- Added a movable marker that users positioned by clicking the map, with a popup showing the nearest mapped building and its distance.
- Used GeoLib for distance calculations and corrected a coordinate issue affecting the results.
- Added date information to review submissions and adjusted frontend API URLs to accommodate the team’s local server setup.
- Reworked the building review page’s layout and styling, alongside improvements to the review listing page.

## Finding a nearby building

The map used a shared dataset of campus building coordinates. When a user selected a location, the interface compared it with the mapped buildings and displayed the closest one and its distance. This was a lookup from a user-selected point, rather than live location tracking or walking directions.

The feature connected map interactions, coordinate data, distance calculations, and React state. It also gave me practice debugging a result that could look plausible on screen while using incorrect coordinate values.

## Project context

UC-Lavatory was an early team web-development project. It gave me experience contributing features to a shared application, integrating frontend requests with the team’s API, and refining an interface as other components changed.

The repository preserves the final team code and my contributions, including interface work completed after the locally saved December 1 snapshot. The application was developed for local use and would need maintenance before being offered as a public service.
