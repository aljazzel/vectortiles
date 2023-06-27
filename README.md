{
    "version": 8,
    "name": "Example: Add traffic data",
    "metadata": {
        "mapbox:type": "default",
        "mapbox:origin": "navigation-night-v1",
        "mapbox:sdk-support": {
            "js": "1.6.0",
            "android": "8.3.0",
            "ios": "5.3.0"
        },
        "mapbox:autocomposite": true,
        "mapbox:groups": {
            "Road network, traffic-and-closures": {
                "name": "Road network, traffic-and-closures",
                "collapsed": false
            },
            "Transit, transit-labels": {
                "name": "Transit, transit-labels",
                "collapsed": false
            },
            "Administrative boundaries, admin": {
                "name": "Administrative boundaries, admin",
                "collapsed": false
            },
            "Land & water, built": {
                "name": "Land & water, built",
                "collapsed": false
            },
            "Transit, bridges": {
                "name": "Transit, bridges",
                "collapsed": false
            },
            "Transit, surface": {
                "name": "Transit, surface",
                "collapsed": false
            },
            "Land & water, land": {
                "name": "Land & water, land",
                "collapsed": false
            },
            "Road network, bridges": {
                "name": "Road network, bridges",
                "collapsed": false
            },
            "Road network, tunnels": {
                "name": "Road network, tunnels",
                "collapsed": false
            },
            "Road network, road-labels": {
                "name": "Road network, road-labels",
                "collapsed": false
            },
            "Buildings, built": {
                "name": "Buildings, built",
                "collapsed": false
            },
            "Natural features, natural-labels": {
                "name": "Natural features, natural-labels",
                "collapsed": false
            },
            "Road network, surface": {
                "name": "Road network, surface",
                "collapsed": false
            },
            "Place labels, place-labels": {
                "name": "Place labels, place-labels",
                "collapsed": false
            },
            "Transit, ferries": {
                "name": "Transit, ferries",
                "collapsed": false
            },
            "Transit, elevated": {
                "name": "Transit, elevated",
                "collapsed": false
            },
            "Point of interest labels, poi-labels": {
                "name": "Point of interest labels, poi-labels",
                "collapsed": false
            },
            "Road network, tunnels-case": {
                "name": "Road network, tunnels-case",
                "collapsed": false
            },
            "Transit, built": {
                "name": "Transit, built",
                "collapsed": false
            },
            "Road network, surface-icons": {
                "name": "Road network, surface-icons",
                "collapsed": false
            },
            "Land & water, water": {
                "name": "Land & water, water",
                "collapsed": false
            },
            "Transit, ferry-aerialway-labels": {
                "name": "Transit, ferry-aerialway-labels",
                "collapsed": false
            }
        }
    },
    "center": [
        -73.97691118502598,
        40.739245872266025
    ],
    "zoom": 12.06364458144697,
    "bearing": 0,
    "pitch": 0,
    "sources": {
        "mapbox://mapbox.mapbox-traffic-v1": {
            "url": "mapbox://mapbox.mapbox-traffic-v1",
            "type": "vector"
        },
        "mapbox://mapbox.mapbox-incidents-v1": {
            "url": "mapbox://mapbox.mapbox-incidents-v1",
            "type": "vector"
        },
        "composite": {
            "url": "mapbox://mapbox.mapbox-streets-v8,mapbox.mapbox-terrain-v2",
            "type": "vector"
        }
    },
    "sprite": "mapbox://sprites/examples/ck7pbezoo07661ioxtn6qsmuw/13fdt7tomawgskr0xq9vd3iq1",
    "glyphs": "mapbox://fonts/examples/{fontstack}/{range}.pbf",
    "layers": [
        {
            "id": "land",
            "type": "background",
            "layout": {},
            "paint": {
                "background-color": "hsl(60, 0%, 99%)"
            },
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, land"
            }
        },
        {
            "id": "landcover",
            "type": "fill",
            "source": "composite",
            "source-layer": "landcover",
            "maxzoom": 7,
            "layout": {},
            "paint": {
                "fill-color": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "snow",
                    "hsl(60, 0%, 100%)",
                    "hsl(82, 28%, 92%)"
                ],
                "fill-opacity": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    2,
                    0.3,
                    7,
                    0
                ],
                "fill-antialias": false
            },
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, land"
            }
        },
        {
            "minzoom": 5,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, land"
            },
            "filter": [
                "==",
                [
                    "get",
                    "class"
                ],
                "national_park"
            ],
            "type": "fill",
            "source": "composite",
            "id": "national-park",
            "paint": {
                "fill-color": "hsl(100, 50%, 84%)",
                "fill-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    0,
                    6,
                    0.5,
                    10,
                    0.5
                ]
            },
            "source-layer": "landuse_overlay"
        },
        {
            "minzoom": 5,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, land"
            },
            "filter": [
                "match",
                [
                    "get",
                    "class"
                ],
                [
                    "park",
                    "airport",
                    "glacier",
                    "pitch",
                    "sand"
                ],
                true,
                "cemetery",
                true,
                "school",
                true,
                "hospital",
                true,
                "parking",
                [
                    "step",
                    [
                        "zoom"
                    ],
                    false,
                    15,
                    true
                ],
                false
            ],
            "type": "fill",
            "source": "composite",
            "id": "landuse",
            "paint": {
                "fill-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "park",
                        "hsl(100, 50%, 84%)",
                        "airport",
                        "hsl(260, 1%, 100%)",
                        "cemetery",
                        "hsl(82, 16%, 90%)",
                        "glacier",
                        "hsl(197, 88%, 98%)",
                        "hospital",
                        "hsl(320, 22%, 96%)",
                        "pitch",
                        "hsl(100, 51%, 79%)",
                        "sand",
                        "hsl(100, 38%, 98%)",
                        "school",
                        "hsl(35, 23%, 90%)",
                        "parking",
                        "hsl(60, 87%, 94%)",
                        "hsl(60, 2%, 94%)"
                    ],
                    16,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "park",
                        "hsl(100, 50%, 84%)",
                        "airport",
                        "hsl(260, 15%, 98%)",
                        "cemetery",
                        "hsl(82, 16%, 90%)",
                        "glacier",
                        "hsl(197, 88%, 98%)",
                        "hospital",
                        "hsl(320, 48%, 98%)",
                        "pitch",
                        "hsl(100, 51%, 79%)",
                        "sand",
                        "hsl(100, 38%, 98%)",
                        "school",
                        "hsl(35, 23%, 90%)",
                        "parking",
                        "hsl(60, 87%, 94%)",
                        "hsl(60, 2%, 94%)"
                    ]
                ],
                "fill-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    0,
                    6,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "glacier",
                        0.5,
                        1
                    ]
                ]
            },
            "source-layer": "landuse"
        },
        {
            "minzoom": 15,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, land"
            },
            "filter": [
                "==",
                [
                    "get",
                    "class"
                ],
                "pitch"
            ],
            "type": "line",
            "source": "composite",
            "id": "pitch-outline",
            "paint": {
                "line-color": "hsl(82, 29%, 95%)"
            },
            "source-layer": "landuse"
        },
        {
            "id": "waterway",
            "type": "line",
            "source": "composite",
            "source-layer": "waterway",
            "minzoom": 8,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    11,
                    "round"
                ],
                "line-join": "round"
            },
            "paint": {
                "line-color": "hsl(197, 98%, 78%)",
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.3
                    ],
                    [
                        "zoom"
                    ],
                    9,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "canal",
                            "river"
                        ],
                        0.1,
                        0
                    ],
                    20,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "canal",
                            "river"
                        ],
                        8,
                        3
                    ]
                ],
                "line-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    8,
                    0,
                    8.5,
                    1
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, water"
            }
        },
        {
            "id": "water",
            "type": "fill",
            "source": "composite",
            "source-layer": "water",
            "layout": {},
            "paint": {
                "fill-color": "hsl(197, 98%, 78%)"
            },
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, water"
            }
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, built"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "Polygon"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "land"
                ]
            ],
            "type": "fill",
            "source": "composite",
            "id": "land-structure-polygon",
            "paint": {
                "fill-color": "hsl(60, 0%, 99%)"
            },
            "source-layer": "structure"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "land-and-water",
                "mapbox:group": "Land & water, built"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "land"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "land-structure-line",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.99
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.75,
                    20,
                    40
                ],
                "line-color": "hsl(60, 0%, 99%)"
            },
            "source-layer": "structure"
        },
        {
            "minzoom": 11,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, built"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "Polygon"
                ],
                [
                    "match",
                    [
                        "get",
                        "type"
                    ],
                    [
                        "runway",
                        "taxiway",
                        "helipad"
                    ],
                    true,
                    false
                ]
            ],
            "type": "fill",
            "source": "composite",
            "id": "aeroway-polygon",
            "paint": {
                "fill-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    "hsl(260, 8%, 91%)",
                    16,
                    "hsl(260, 20%, 93%)"
                ],
                "fill-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    11,
                    0,
                    11.5,
                    1
                ]
            },
            "source-layer": "aeroway"
        },
        {
            "minzoom": 9,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, built"
            },
            "filter": [
                "==",
                [
                    "geometry-type"
                ],
                "LineString"
            ],
            "type": "line",
            "source": "composite",
            "id": "aeroway-line",
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    "hsl(260, 8%, 91%)",
                    16,
                    "hsl(260, 20%, 93%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    9,
                    [
                        "match",
                        [
                            "get",
                            "type"
                        ],
                        "runway",
                        1,
                        0.5
                    ],
                    18,
                    [
                        "match",
                        [
                            "get",
                            "type"
                        ],
                        "runway",
                        80,
                        20
                    ]
                ]
            },
            "source-layer": "aeroway"
        },
        {
            "minzoom": 15,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "buildings",
                "mapbox:group": "Buildings, built"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "type"
                    ],
                    "building:part"
                ],
                [
                    "==",
                    [
                        "get",
                        "underground"
                    ],
                    "false"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "building-outline",
            "paint": {
                "line-color": "hsl(60, 0%, 89%)",
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.75,
                    20,
                    3
                ],
                "line-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0,
                    16,
                    1
                ]
            },
            "source-layer": "building"
        },
        {
            "minzoom": 15,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "buildings",
                "mapbox:group": "Buildings, built"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "type"
                    ],
                    "building:part"
                ],
                [
                    "==",
                    [
                        "get",
                        "underground"
                    ],
                    "false"
                ]
            ],
            "type": "fill",
            "source": "composite",
            "id": "building",
            "paint": {
                "fill-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    "hsl(60, 0%, 95%)",
                    16,
                    "hsl(60, 0%, 95%)"
                ],
                "fill-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0,
                    16,
                    1
                ],
                "fill-outline-color": "hsl(60, 0%, 89%)"
            },
            "source-layer": "building"
        },
        {
            "minzoom": 15,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "track",
                        "secondary_link",
                        "tertiary_link",
                        "service"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-minor-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.75,
                    18,
                    1.5
                ],
                "line-color": "hsl(230, 1%, 72%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "track",
                        1,
                        0.5
                    ],
                    18,
                    10,
                    22,
                    75
                ],
                "line-dasharray": [
                    3,
                    3
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "maxzoom": 14,
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-street-low-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.5,
                    14,
                    2
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-street-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.5,
                    18,
                    2
                ],
                "line-color": "hsl(230, 1%, 72%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-dasharray": [
                    3,
                    3
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 12,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-secondary-tertiary-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    2
                ],
                "line-color": "hsl(230, 1%, 72%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    28,
                    22,
                    200
                ],
                "line-dasharray": [
                    3,
                    3
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 10,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-primary-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(230, 1%, 72%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1.125,
                    18,
                    32,
                    22,
                    225
                ],
                "line-dasharray": [
                    3,
                    3
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-major-link-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-dasharray": [
                    3,
                    3
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-motorway-trunk-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ],
                "line-dasharray": [
                    3,
                    3
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels-case"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "construction"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-construction-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-dasharray": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "literal",
                        [
                            0.4,
                            0.8
                        ]
                    ],
                    15,
                    [
                        "literal",
                        [
                            0.3,
                            0.6
                        ]
                    ],
                    16,
                    [
                        "literal",
                        [
                            0.2,
                            0.3
                        ]
                    ],
                    17,
                    [
                        "literal",
                        [
                            0.2,
                            0.25
                        ]
                    ],
                    18,
                    [
                        "literal",
                        [
                            0.15,
                            0.15
                        ]
                    ]
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-major-link-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(50, 82%, 85%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "track",
                        "secondary_link",
                        "tertiary_link",
                        "service"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-minor-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "track",
                        1,
                        0.5
                    ],
                    18,
                    10,
                    22,
                    75
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-street-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.5,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-secondary-tertiary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    28,
                    22,
                    200
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-primary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1.125,
                    18,
                    32,
                    22,
                    225
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, tunnels"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "tunnel-motorway-trunk-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ],
                "line-color": "hsl(50, 82%, 85%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 8,
            "layout": {
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    14,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, ferries"
            },
            "filter": [
                "==",
                [
                    "get",
                    "type"
                ],
                "ferry"
            ],
            "type": "line",
            "source": "composite",
            "id": "ferry",
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    "hsl(206, 91%, 71%)",
                    17,
                    "hsl(231, 91%, 71%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.5,
                    20,
                    1
                ],
                "line-dasharray": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "literal",
                        [
                            1,
                            0
                        ]
                    ],
                    13,
                    [
                        "literal",
                        [
                            12,
                            4
                        ]
                    ]
                ]
            },
            "source-layer": "road"
        },
        {
            "id": "ferry-auto",
            "type": "line",
            "source": "composite",
            "source-layer": "road",
            "filter": [
                "==",
                [
                    "get",
                    "type"
                ],
                "ferry_auto"
            ],
            "layout": {
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    14,
                    "round"
                ]
            },
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    "hsl(206, 91%, 71%)",
                    17,
                    "hsl(231, 91%, 71%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.5,
                    20,
                    1
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, ferries"
            }
        },
        {
            "minzoom": 15,
            "layout": {
                "icon-image": "turning-circle-outline",
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.06,
                    22,
                    1.4
                ],
                "icon-allow-overlap": true,
                "icon-ignore-placement": true,
                "icon-padding": 0,
                "icon-rotation-alignment": "map"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "Point"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "turning_circle",
                        "turning_loop"
                    ],
                    true,
                    false
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "turning-feature-outline-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "track",
                        "secondary_link",
                        "tertiary_link",
                        "service"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-minor-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.75,
                    18,
                    1.5
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "track",
                        1,
                        0.5
                    ],
                    18,
                    10,
                    22,
                    75
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 11,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    14,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    14,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "maxzoom": 14,
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-street-low-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.5,
                    14,
                    2
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    13,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    13,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-street-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.5,
                    18,
                    2
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 12,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-secondary-tertiary-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    2
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    28,
                    22,
                    200
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 12,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-primary-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1.125,
                    18,
                    32,
                    22,
                    225
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 11,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    13,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    13,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-major-link-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-motorway-trunk-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "construction"
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-construction-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(230, 10%, 92%)",
                "line-dasharray": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "literal",
                        [
                            0.4,
                            0.8
                        ]
                    ],
                    15,
                    [
                        "literal",
                        [
                            0.3,
                            0.6
                        ]
                    ],
                    16,
                    [
                        "literal",
                        [
                            0.2,
                            0.3
                        ]
                    ],
                    17,
                    [
                        "literal",
                        [
                            0.2,
                            0.25
                        ]
                    ],
                    18,
                    [
                        "literal",
                        [
                            0.15,
                            0.15
                        ]
                    ]
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 11,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    13,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    13,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-major-link-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(50, 92%, 80%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "track",
                        "secondary_link",
                        "tertiary_link",
                        "service"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-minor-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "track",
                        1,
                        0.5
                    ],
                    18,
                    10,
                    22,
                    75
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "link",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-tunnel-link-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 65%, 75%)",
                    "moderate",
                    "hsl(35, 85%, 70%)",
                    "heavy",
                    "hsl(0, 85%, 85%)",
                    "severe",
                    "hsl(340, 45%, 75%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0,
                    15,
                    3.5,
                    18,
                    7
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 15,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "service"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-tunnel-minor-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.75,
                    18,
                    7,
                    22,
                    18
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 65%, 75%)",
                    "moderate",
                    "hsl(35, 85%, 70%)",
                    "heavy",
                    "hsl(0, 85%, 85%)",
                    "severe",
                    "hsl(340, 45%, 75%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    1,
                    18,
                    7,
                    22,
                    30
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 14,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-street-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.5,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "street"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-tunnel-street-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 65%, 75%)",
                    "moderate",
                    "hsl(35, 85%, 70%)",
                    "heavy",
                    "hsl(0, 85%, 85%)",
                    "severe",
                    "hsl(340, 45%, 75%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    1,
                    18,
                    6,
                    22,
                    30
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 8,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    11,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    11,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-secondary-tertiary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    0.175,
                    10,
                    0.75,
                    18,
                    28,
                    22,
                    200
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-tunnel-secondary-tertiary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    7
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 65%, 75%)",
                    "moderate",
                    "hsl(35, 85%, 70%)",
                    "heavy",
                    "hsl(0, 85%, 85%)",
                    "severe",
                    "hsl(340, 45%, 75%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    1,
                    15,
                    3,
                    18,
                    7,
                    22,
                    60
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 6,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    11,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    11,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-primary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1.125,
                    18,
                    32,
                    22,
                    225
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-tunnel-primary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 65%, 75%)",
                    "moderate",
                    "hsl(35, 85%, 70%)",
                    "heavy",
                    "hsl(0, 85%, 85%)",
                    "severe",
                    "hsl(340, 45%, 75%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    1,
                    18,
                    10,
                    22,
                    80
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 5,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "maxzoom": 13,
            "filter": [
                "all",
                [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "==",
                        [
                            "get",
                            "class"
                        ],
                        "motorway"
                    ],
                    6,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "motorway",
                            "trunk"
                        ],
                        true,
                        false
                    ]
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-motorway-trunk-case-low-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 6,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-tunnel-major-link-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 65%, 75%)",
                    "moderate",
                    "hsl(35, 85%, 70%)",
                    "heavy",
                    "hsl(0, 85%, 85%)",
                    "severe",
                    "hsl(340, 45%, 75%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0,
                    15,
                    3.5,
                    18,
                    7
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 5,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    8,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    8,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-motorway-trunk-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ],
                "line-color": "hsl(50, 92%, 80%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-tunnel-motorway-trunk-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    1,
                    13,
                    4,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 65%, 75%)",
                    "moderate",
                    "hsl(35, 85%, 70%)",
                    "heavy",
                    "hsl(0, 85%, 85%)",
                    "severe",
                    "hsl(340, 45%, 75%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    0,
                    9,
                    1,
                    15,
                    3,
                    18,
                    7,
                    22,
                    80
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "major_rail",
                        "minor_rail"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-rail",
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    13,
                    "hsl(75, 5%, 90%)",
                    16,
                    "hsl(230, 0%, 71%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.5,
                    20,
                    1
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, surface"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "major_rail",
                        "minor_rail"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "road-rail-tracks",
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    13,
                    "hsl(75, 5%, 90%)",
                    16,
                    "hsl(230, 0%, 71%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    4,
                    20,
                    8
                ],
                "line-dasharray": [
                    0.1,
                    15
                ],
                "line-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    13.75,
                    0,
                    14,
                    1
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 16,
            "layout": {
                "icon-image": "level-crossing",
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    16,
                    0.25,
                    22,
                    1
                ],
                "icon-allow-overlap": true
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface-icons"
            },
            "filter": [
                "==",
                [
                    "get",
                    "class"
                ],
                "level_crossing"
            ],
            "type": "symbol",
            "source": "composite",
            "id": "level-crossing-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "icon-image": "turning-circle",
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.05,
                    22,
                    1.5
                ],
                "icon-allow-overlap": true,
                "icon-ignore-placement": true,
                "icon-padding": 0,
                "icon-rotation-alignment": "map"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, surface-icons"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "Point"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "turning_circle",
                        "turning_loop"
                    ],
                    true,
                    false
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "turning-feature-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "track",
                        "secondary_link",
                        "tertiary_link",
                        "service"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-minor-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.75,
                    18,
                    1.5
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "track",
                        1,
                        0.5
                    ],
                    18,
                    10,
                    22,
                    75
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "maxzoom": 14,
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-street-low-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.5,
                    14,
                    2
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-street-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.5,
                    18,
                    2
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 12,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-secondary-tertiary-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    2
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    28,
                    22,
                    200
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 12,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-primary-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1.125,
                    18,
                    32,
                    22,
                    225
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "<=",
                    [
                        "get",
                        "layer"
                    ],
                    1
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-major-link-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "<=",
                    [
                        "get",
                        "layer"
                    ],
                    1
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-motorway-trunk-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "construction"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-construction-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(230, 8%, 85%)",
                "line-dasharray": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "literal",
                        [
                            0.4,
                            0.8
                        ]
                    ],
                    15,
                    [
                        "literal",
                        [
                            0.3,
                            0.6
                        ]
                    ],
                    16,
                    [
                        "literal",
                        [
                            0.2,
                            0.3
                        ]
                    ],
                    17,
                    [
                        "literal",
                        [
                            0.2,
                            0.25
                        ]
                    ],
                    18,
                    [
                        "literal",
                        [
                            0.15,
                            0.15
                        ]
                    ]
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "<=",
                    [
                        "get",
                        "layer"
                    ],
                    1
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-major-link-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(50, 92%, 80%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "track",
                        "secondary_link",
                        "tertiary_link",
                        "service"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-minor-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        "track",
                        1,
                        0.5
                    ],
                    18,
                    10,
                    22,
                    75
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "street",
                        "street_limited",
                        "primary_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-street-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.5,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": [
                    "step",
                    [
                        "zoom"
                    ],
                    "butt",
                    11,
                    "round"
                ],
                "line-join": [
                    "step",
                    [
                        "zoom"
                    ],
                    "miter",
                    11,
                    "round"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-secondary-tertiary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    28,
                    22,
                    200
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-primary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1.125,
                    18,
                    32,
                    22,
                    225
                ],
                "line-color": "hsl(230, 10%, 92%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "<=",
                    [
                        "get",
                        "layer"
                    ],
                    1
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-motorway-trunk-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ],
                "line-color": "hsl(50, 92%, 80%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    ">=",
                    [
                        "get",
                        "layer"
                    ],
                    2
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-major-link-2-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    0.75,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    ">=",
                    [
                        "get",
                        "layer"
                    ],
                    2
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-motorway-trunk-2-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.2
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    2
                ],
                "line-color": "hsl(50, 77%, 65%)",
                "line-gap-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    ">=",
                    [
                        "get",
                        "layer"
                    ],
                    2
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-major-link-2-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0.75,
                    14,
                    2,
                    18,
                    20,
                    22,
                    175
                ],
                "line-color": "hsl(50, 92%, 80%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-cap": "round",
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    ">=",
                    [
                        "get",
                        "layer"
                    ],
                    2
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-motorway-trunk-2-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1.25,
                    18,
                    32,
                    22,
                    225
                ],
                "line-color": "hsl(50, 92%, 80%)"
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "major_rail",
                        "minor_rail"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-rail",
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    13,
                    "hsl(75, 5%, 90%)",
                    16,
                    "hsl(230, 0%, 71%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.5,
                    20,
                    1
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, bridges"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "major_rail",
                        "minor_rail"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "bridge-rail-tracks",
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    13,
                    "hsl(75, 5%, 90%)",
                    16,
                    "hsl(230, 0%, 71%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    4,
                    20,
                    8
                ],
                "line-dasharray": [
                    0.1,
                    15
                ],
                "line-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    13.75,
                    0,
                    14,
                    1
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ],
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "link",
                        "primary_link"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-link-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 70%, 60%)",
                    "moderate",
                    "hsl(35, 100%, 50%)",
                    "heavy",
                    "hsl(0, 100%, 65%)",
                    "severe",
                    "hsl(340, 60%, 35%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0,
                    15,
                    3.5,
                    18,
                    7
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 15,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "service"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-minor-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.75,
                    18,
                    7,
                    22,
                    18
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 70%, 60%)",
                    "moderate",
                    "hsl(35, 100%, 50%)",
                    "heavy",
                    "hsl(0, 100%, 65%)",
                    "severe",
                    "hsl(340, 60%, 35%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    1,
                    18,
                    7,
                    22,
                    30
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 13,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "street"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-street-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 70%, 60%)",
                    "moderate",
                    "hsl(35, 100%, 50%)",
                    "heavy",
                    "hsl(0, 100%, 65%)",
                    "severe",
                    "hsl(340, 60%, 35%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    1,
                    18,
                    7,
                    22,
                    60
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 8,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-secondary-tertiary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 70%, 60%)",
                    "moderate",
                    "hsl(35, 100%, 50%)",
                    "heavy",
                    "hsl(0, 100%, 65%)",
                    "severe",
                    "hsl(340, 60%, 35%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    1,
                    15,
                    3,
                    18,
                    7,
                    22,
                    60
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 6,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "primary"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-primary-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 70%, 60%)",
                    "moderate",
                    "hsl(35, 100%, 50%)",
                    "heavy",
                    "hsl(0, 100%, 65%)",
                    "severe",
                    "hsl(340, 60%, 35%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    1,
                    18,
                    10,
                    22,
                    80
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 6,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-major-link-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    1,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 70%, 60%)",
                    "moderate",
                    "hsl(35, 100%, 50%)",
                    "heavy",
                    "hsl(0, 100%, 65%)",
                    "severe",
                    "hsl(340, 60%, 35%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    0,
                    15,
                    3.5,
                    18,
                    7
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 5,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "maxzoom": 13,
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-motorway-trunk-case-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    2,
                    13,
                    7,
                    18,
                    10
                ],
                "line-color": "hsl(60, 0%, 100%)",
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    0,
                    9,
                    1,
                    15,
                    3,
                    18,
                    7
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 5,
            "layout": {
                "line-round-limit": 1.5,
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "!=",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "has",
                    "congestion"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-traffic-v1",
            "id": "traffic-bridge-road-motorway-trunk-navigation",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    1,
                    13,
                    4,
                    18,
                    7,
                    22,
                    22
                ],
                "line-color": [
                    "match",
                    [
                        "get",
                        "congestion"
                    ],
                    "low",
                    "hsl(120, 70%, 60%)",
                    "moderate",
                    "hsl(35, 100%, 50%)",
                    "heavy",
                    "hsl(0, 100%, 65%)",
                    "severe",
                    "hsl(340, 60%, 35%)",
                    "hsla(0, 0%, 0%, 0)"
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    0,
                    9,
                    1,
                    15,
                    3,
                    18,
                    7,
                    22,
                    80
                ]
            },
            "source-layer": "traffic"
        },
        {
            "minzoom": 16,
            "layout": {
                "icon-image": "level-crossing",
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    16,
                    0.25,
                    22,
                    1
                ],
                "icon-allow-overlap": true
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "==",
                [
                    "get",
                    "class"
                ],
                "level_crossing"
            ],
            "type": "symbol",
            "source": "composite",
            "id": "traffic-level-crossing-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "symbol-placement": "line",
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    400,
                    18,
                    600,
                    22,
                    1200
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    "oneway-small",
                    17,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited"
                        ],
                        "oneway-large",
                        "oneway-small"
                    ],
                    18,
                    "oneway-large"
                ],
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.25,
                    20,
                    1
                ],
                "icon-rotation-alignment": "map"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "==",
                    [
                        "get",
                        "oneway"
                    ],
                    "true"
                ],
                [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "street",
                            "street_limited",
                            "tertiary"
                        ],
                        true,
                        false
                    ],
                    16,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited",
                            "primary_link",
                            "secondary_link",
                            "tertiary_link",
                            "service",
                            "track"
                        ],
                        true,
                        false
                    ]
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "traffic-tunnel-oneway-arrow-blue-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "symbol-placement": "line",
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    400,
                    18,
                    600,
                    22,
                    1200
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    "oneway-white-small",
                    17,
                    "oneway-white-large"
                ],
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.4,
                    20,
                    1
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "tunnel"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "motorway_link",
                        "trunk",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "get",
                        "oneway"
                    ],
                    "true"
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "traffic-tunnel-oneway-arrow-white-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "symbol-placement": "line",
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    400,
                    18,
                    600,
                    22,
                    1200
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    "oneway-small",
                    17,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited"
                        ],
                        "oneway-large",
                        "oneway-small"
                    ],
                    18,
                    "oneway-large"
                ],
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.25,
                    20,
                    1
                ],
                "icon-rotation-alignment": "map"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "oneway"
                    ],
                    "true"
                ],
                [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited"
                        ],
                        true,
                        false
                    ],
                    16,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited",
                            "primary_link",
                            "secondary_link",
                            "tertiary_link",
                            "service",
                            "track"
                        ],
                        true,
                        false
                    ]
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "traffic-road-oneway-arrow-blue-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "symbol-placement": "line",
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    400,
                    18,
                    600,
                    22,
                    1200
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    "oneway-white-small",
                    17,
                    "oneway-white-large"
                ],
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.4,
                    20,
                    1
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "oneway"
                    ],
                    "true"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk",
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "match",
                    [
                        "get",
                        "structure"
                    ],
                    [
                        "none",
                        "ford"
                    ],
                    true,
                    false
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "traffic-road-oneway-arrow-white-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "symbol-placement": "line",
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    400,
                    18,
                    600,
                    22,
                    1200
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    "oneway-small",
                    17,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited"
                        ],
                        "oneway-large",
                        "oneway-small"
                    ],
                    18,
                    "oneway-large"
                ],
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.25,
                    20,
                    1
                ],
                "icon-rotation-alignment": "map"
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "==",
                    [
                        "get",
                        "oneway"
                    ],
                    "true"
                ],
                [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited"
                        ],
                        true,
                        false
                    ],
                    16,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "primary",
                            "secondary",
                            "tertiary",
                            "street",
                            "street_limited",
                            "primary_link",
                            "secondary_link",
                            "tertiary_link",
                            "service",
                            "track"
                        ],
                        true,
                        false
                    ]
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "traffic-bridge-oneway-arrow-blue-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 15,
            "layout": {
                "symbol-placement": "line",
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    400,
                    18,
                    600,
                    22,
                    1200
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    "oneway-white-small",
                    17,
                    "oneway-white-large"
                ],
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    0.45,
                    20,
                    1
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "structure"
                    ],
                    "bridge"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk",
                        "motorway_link",
                        "trunk_link"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "get",
                        "oneway"
                    ],
                    "true"
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "traffic-bridge-oneway-arrow-white-navigation",
            "paint": {},
            "source-layer": "road"
        },
        {
            "minzoom": 8,
            "layout": {
                "line-join": "round",
                "line-round-limit": 1.5
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "type"
                    ],
                    "full"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-incidents-v1",
            "id": "incident-closure-lines-navigation",
            "paint": {
                "line-color": "hsl(60, 0%, 100%)",
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    1,
                    18,
                    7,
                    22,
                    12
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    1,
                    18,
                    10,
                    22,
                    20
                ]
            },
            "source-layer": "closures"
        },
        {
            "minzoom": 8,
            "layout": {
                "line-join": "round",
                "line-round-limit": 1.5
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "type"
                    ],
                    "full"
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "line",
            "source": "mapbox://mapbox.mapbox-incidents-v1",
            "id": "incident-closure-line-highlights-navigation",
            "paint": {
                "line-color": "hsl(60, 0%, 40%)",
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    0.6,
                    18,
                    4.2,
                    22,
                    6
                ],
                "line-offset": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    12,
                    1,
                    18,
                    10,
                    22,
                    20
                ],
                "line-dasharray": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "literal",
                        [
                            1,
                            0
                        ]
                    ],
                    14,
                    [
                        "literal",
                        [
                            1,
                            1
                        ]
                    ]
                ]
            },
            "source-layer": "closures"
        },
        {
            "minzoom": 8,
            "layout": {
                "icon-image": "road-closure",
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    0.15,
                    18,
                    0.6,
                    22,
                    1
                ],
                "icon-allow-overlap": true
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "type"
                    ],
                    "endpoint:full"
                ],
                [
                    "match",
                    [
                        "geometry-type"
                    ],
                    [
                        "LineString",
                        "Point"
                    ],
                    true,
                    false
                ]
            ],
            "type": "symbol",
            "source": "mapbox://mapbox.mapbox-incidents-v1",
            "id": "incident-endpoints-navigation",
            "paint": {},
            "source-layer": "closures"
        },
        {
            "minzoom": 8,
            "layout": {
                "icon-image": "road-closure",
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    5,
                    0.15,
                    18,
                    0.6,
                    22,
                    1
                ],
                "icon-allow-overlap": true
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, traffic-and-closures"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "type"
                    ],
                    "startpoint:full"
                ],
                [
                    "match",
                    [
                        "geometry-type"
                    ],
                    [
                        "LineString",
                        "Point"
                    ],
                    true,
                    false
                ]
            ],
            "type": "symbol",
            "source": "mapbox://mapbox.mapbox-incidents-v1",
            "id": "incident-startpoints-navigation",
            "paint": {},
            "source-layer": "closures"
        },
        {
            "minzoom": 12,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, elevated"
            },
            "filter": [
                "==",
                [
                    "get",
                    "class"
                ],
                "aerialway"
            ],
            "type": "line",
            "source": "composite",
            "id": "aerialway",
            "paint": {
                "line-color": "hsl(230, 0%, 71%)",
                "line-width": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    14,
                    0.5,
                    20,
                    1
                ]
            },
            "source-layer": "road"
        },
        {
            "id": "admin-1-boundary-bg",
            "type": "line",
            "source": "composite",
            "source-layer": "admin",
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "admin_level"
                    ],
                    1
                ],
                [
                    "==",
                    [
                        "get",
                        "maritime"
                    ],
                    "false"
                ],
                [
                    "match",
                    [
                        "get",
                        "worldview"
                    ],
                    [
                        "all",
                        "US"
                    ],
                    true,
                    false
                ]
            ],
            "layout": {
                "line-join": "bevel"
            },
            "paint": {
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    8,
                    "hsl(60, 0%, 99%)",
                    16,
                    "hsl(250, 100%, 100%)"
                ],
                "line-width": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    3.75,
                    12,
                    5.5
                ],
                "line-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    0,
                    8,
                    0.75
                ],
                "line-dasharray": [
                    1,
                    0
                ],
                "line-translate": [
                    0,
                    0
                ],
                "line-blur": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    0,
                    8,
                    3
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "admin-boundaries",
                "mapbox:group": "Administrative boundaries, admin"
            }
        },
        {
            "minzoom": 1,
            "layout": {},
            "metadata": {
                "mapbox:featureComponent": "admin-boundaries",
                "mapbox:group": "Administrative boundaries, admin"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "admin_level"
                    ],
                    0
                ],
                [
                    "==",
                    [
                        "get",
                        "maritime"
                    ],
                    "false"
                ],
                [
                    "match",
                    [
                        "get",
                        "worldview"
                    ],
                    [
                        "all",
                        "US"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "admin-0-boundary-bg",
            "paint": {
                "line-width": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    3.5,
                    10,
                    8
                ],
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    "hsl(60, 0%, 99%)",
                    8,
                    "hsl(250, 100%, 100%)"
                ],
                "line-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    0,
                    4,
                    0.5
                ],
                "line-translate": [
                    0,
                    0
                ],
                "line-blur": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    0,
                    10,
                    2
                ]
            },
            "source-layer": "admin"
        },
        {
            "id": "admin-1-boundary",
            "type": "line",
            "source": "composite",
            "source-layer": "admin",
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "admin_level"
                    ],
                    1
                ],
                [
                    "==",
                    [
                        "get",
                        "maritime"
                    ],
                    "false"
                ],
                [
                    "match",
                    [
                        "get",
                        "worldview"
                    ],
                    [
                        "all",
                        "US"
                    ],
                    true,
                    false
                ]
            ],
            "layout": {
                "line-join": "round",
                "line-cap": "round"
            },
            "paint": {
                "line-dasharray": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "literal",
                        [
                            2,
                            0
                        ]
                    ],
                    7,
                    [
                        "literal",
                        [
                            2,
                            2,
                            6,
                            2
                        ]
                    ]
                ],
                "line-width": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    0.75,
                    12,
                    1.5
                ],
                "line-opacity": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    2,
                    0,
                    3,
                    1
                ],
                "line-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    "hsl(250, 53%, 75%)",
                    7,
                    "hsl(250, 90%, 85%)"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "admin-boundaries",
                "mapbox:group": "Administrative boundaries, admin"
            }
        },
        {
            "minzoom": 1,
            "layout": {
                "line-join": "round",
                "line-cap": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "admin-boundaries",
                "mapbox:group": "Administrative boundaries, admin"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "admin_level"
                    ],
                    0
                ],
                [
                    "==",
                    [
                        "get",
                        "disputed"
                    ],
                    "false"
                ],
                [
                    "==",
                    [
                        "get",
                        "maritime"
                    ],
                    "false"
                ],
                [
                    "match",
                    [
                        "get",
                        "worldview"
                    ],
                    [
                        "all",
                        "US"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "admin-0-boundary",
            "paint": {
                "line-color": "hsl(250, 90%, 80%)",
                "line-width": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    0.5,
                    10,
                    2
                ],
                "line-dasharray": [
                    10,
                    0
                ]
            },
            "source-layer": "admin"
        },
        {
            "minzoom": 1,
            "layout": {
                "line-join": "round"
            },
            "metadata": {
                "mapbox:featureComponent": "admin-boundaries",
                "mapbox:group": "Administrative boundaries, admin"
            },
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "disputed"
                    ],
                    "true"
                ],
                [
                    "==",
                    [
                        "get",
                        "admin_level"
                    ],
                    0
                ],
                [
                    "==",
                    [
                        "get",
                        "maritime"
                    ],
                    "false"
                ],
                [
                    "match",
                    [
                        "get",
                        "worldview"
                    ],
                    [
                        "all",
                        "US"
                    ],
                    true,
                    false
                ]
            ],
            "type": "line",
            "source": "composite",
            "id": "admin-0-boundary-disputed",
            "paint": {
                "line-color": "hsl(250, 90%, 80%)",
                "line-width": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    0.5,
                    10,
                    2
                ],
                "line-dasharray": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "literal",
                        [
                            3.25,
                            3.25
                        ]
                    ],
                    6,
                    [
                        "literal",
                        [
                            2.5,
                            2.5
                        ]
                    ],
                    7,
                    [
                        "literal",
                        [
                            2,
                            2.25
                        ]
                    ],
                    8,
                    [
                        "literal",
                        [
                            1.75,
                            2
                        ]
                    ]
                ]
            },
            "source-layer": "admin"
        },
        {
            "minzoom": 13,
            "layout": {
                "text-size": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "motorway",
                            "trunk",
                            "primary",
                            "secondary",
                            "tertiary"
                        ],
                        13,
                        [
                            "motorway_link",
                            "trunk_link",
                            "primary_link",
                            "secondary_link",
                            "tertiary_link",
                            "street",
                            "street_limited"
                        ],
                        10.4,
                        8.450000000000001
                    ],
                    18,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "motorway",
                            "trunk",
                            "primary",
                            "secondary",
                            "tertiary"
                        ],
                        20.8,
                        [
                            "motorway_link",
                            "trunk_link",
                            "primary_link",
                            "secondary_link",
                            "tertiary_link",
                            "street",
                            "street_limited"
                        ],
                        18.2,
                        16.900000000000002
                    ],
                    22,
                    [
                        "match",
                        [
                            "get",
                            "class"
                        ],
                        [
                            "motorway",
                            "trunk",
                            "primary",
                            "secondary",
                            "tertiary"
                        ],
                        65,
                        [
                            "motorway_link",
                            "trunk_link",
                            "primary_link",
                            "secondary_link",
                            "tertiary_link",
                            "street",
                            "street_limited"
                        ],
                        52,
                        39
                    ]
                ],
                "text-max-angle": 30,
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    150,
                    18,
                    450,
                    22,
                    1500
                ],
                "text-font": [
                    "DIN Pro Regular",
                    "Arial Unicode MS Regular"
                ],
                "symbol-placement": "line",
                "text-padding": 1,
                "text-rotation-alignment": "map",
                "text-pitch-alignment": "viewport",
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-letter-spacing": 0.01
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, road-labels"
            },
            "filter": [
                "step",
                [
                    "zoom"
                ],
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk",
                        "primary",
                        "secondary",
                        "tertiary"
                    ],
                    true,
                    false
                ],
                15.25,
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk",
                        "primary",
                        "secondary",
                        "tertiary",
                        "street"
                    ],
                    true,
                    false
                ],
                16,
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk",
                        "primary",
                        "secondary",
                        "tertiary",
                        "street",
                        "street_limited"
                    ],
                    true,
                    false
                ],
                16.5,
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "pedestrian",
                        "golf",
                        "ferry",
                        "aerialway",
                        "path"
                    ],
                    false,
                    true
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "road-label-navigation",
            "paint": {
                "text-color": "hsl(0, 0%, 15%)",
                "text-halo-color": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "motorway",
                        "trunk"
                    ],
                    "hsla(60, 5%, 100%, 0.75)",
                    "hsl(230, 10%, 92%)"
                ],
                "text-halo-width": 1,
                "text-halo-blur": 1
            },
            "source-layer": "road"
        },
        {
            "minzoom": 6,
            "layout": {
                "text-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    14,
                    22,
                    26
                ],
                "icon-image": [
                    "concat",
                    [
                        "get",
                        "shield"
                    ],
                    "-",
                    [
                        "to-string",
                        [
                            "get",
                            "reflen"
                        ]
                    ]
                ],
                "icon-rotation-alignment": "viewport",
                "text-max-angle": 38,
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    11,
                    150,
                    14,
                    200,
                    16,
                    400,
                    17,
                    500,
                    18,
                    500,
                    22,
                    1200
                ],
                "text-font": [
                    "DIN Pro Bold",
                    "Arial Unicode MS Bold"
                ],
                "symbol-placement": [
                    "step",
                    [
                        "zoom"
                    ],
                    "point",
                    11,
                    "line"
                ],
                "text-rotation-alignment": "viewport",
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    0.5,
                    13,
                    0.5,
                    22,
                    1
                ],
                "text-field": [
                    "get",
                    "ref"
                ],
                "text-letter-spacing": 0.05
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, road-labels"
            },
            "filter": [
                "all",
                [
                    "has",
                    "reflen"
                ],
                [
                    "<=",
                    [
                        "get",
                        "reflen"
                    ],
                    6
                ],
                [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "==",
                        [
                            "geometry-type"
                        ],
                        "Point"
                    ],
                    11,
                    [
                        ">",
                        [
                            "get",
                            "len"
                        ],
                        5000
                    ],
                    12,
                    [
                        ">",
                        [
                            "get",
                            "len"
                        ],
                        2500
                    ],
                    13,
                    [
                        ">",
                        [
                            "get",
                            "len"
                        ],
                        1000
                    ],
                    14,
                    true
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "road-number-shield-navigation",
            "paint": {
                "text-color": [
                    "match",
                    [
                        "get",
                        "shield_text_color"
                    ],
                    "white",
                    "hsl(0, 0%, 100%)",
                    "yellow",
                    "hsl(50, 100%, 70%)",
                    "orange",
                    "hsl(25, 100%, 75%)",
                    "blue",
                    "hsl(230, 57%, 44%)",
                    "hsl(230, 18%, 13%)"
                ]
            },
            "source-layer": "road"
        },
        {
            "minzoom": 14,
            "layout": {
                "text-field": [
                    "get",
                    "ref"
                ],
                "text-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    14,
                    22,
                    26
                ],
                "text-font": [
                    "DIN Pro Bold",
                    "Arial Unicode MS Bold"
                ],
                "icon-image": [
                    "concat",
                    "motorway-exit-",
                    [
                        "to-string",
                        [
                            "get",
                            "reflen"
                        ]
                    ]
                ],
                "icon-size": [
                    "interpolate",
                    [
                        "exponential",
                        1.5
                    ],
                    [
                        "zoom"
                    ],
                    6,
                    0.5,
                    13,
                    0.5,
                    22,
                    1
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "road-network",
                "mapbox:group": "Road network, road-labels"
            },
            "filter": [
                "all",
                [
                    "has",
                    "reflen"
                ],
                [
                    "<=",
                    [
                        "get",
                        "reflen"
                    ],
                    9
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "road-exit-shield-navigation",
            "paint": {
                "text-color": "hsl(0, 0%, 100%)"
            },
            "source-layer": "motorway_junction"
        },
        {
            "minzoom": 15,
            "layout": {
                "text-size": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    10,
                    8.450000000000001,
                    18,
                    16.900000000000002
                ],
                "text-max-angle": 30,
                "text-font": [
                    "DIN Pro Regular",
                    "Arial Unicode MS Regular"
                ],
                "symbol-placement": "line",
                "text-padding": 1,
                "text-rotation-alignment": "map",
                "text-pitch-alignment": "viewport",
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-letter-spacing": 0.01
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, ferry-aerialway-labels"
            },
            "filter": [
                "match",
                [
                    "get",
                    "class"
                ],
                "aerialway",
                true,
                "ferry",
                true,
                false
            ],
            "type": "symbol",
            "source": "composite",
            "id": "ferry-aerialway-label",
            "paint": {
                "text-color": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "ferry",
                    "hsl(197, 66%, 58%)",
                    "hsl(0, 0%, 15%)"
                ],
                "text-halo-color": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "ferry",
                    "hsl(197, 98%, 78%)",
                    "hsla(60, 5%, 100%, 0.75)"
                ],
                "text-halo-width": 1,
                "text-halo-blur": 1
            },
            "source-layer": "road"
        },
        {
            "minzoom": 13,
            "layout": {
                "text-font": [
                    "DIN Pro Italic",
                    "Arial Unicode MS Regular"
                ],
                "text-max-angle": 30,
                "symbol-spacing": [
                    "interpolate",
                    [
                        "linear",
                        1
                    ],
                    [
                        "zoom"
                    ],
                    15,
                    250,
                    17,
                    400
                ],
                "text-size": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    13,
                    12,
                    18,
                    16
                ],
                "symbol-placement": "line",
                "text-pitch-alignment": "viewport",
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "natural-features",
                "mapbox:group": "Natural features, natural-labels"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "canal",
                        "river",
                        "stream"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "waterway-label",
            "paint": {
                "text-color": "hsl(197, 66%, 57%)"
            },
            "source-layer": "natural_label"
        },
        {
            "minzoom": 4,
            "layout": {
                "text-size": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        19.8,
                        5,
                        13.200000000000001
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        19.8,
                        13,
                        13.200000000000001
                    ]
                ],
                "text-max-angle": 30,
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-font": [
                    "DIN Pro Medium",
                    "Arial Unicode MS Regular"
                ],
                "symbol-placement": "line-center",
                "text-pitch-alignment": "viewport"
            },
            "metadata": {
                "mapbox:featureComponent": "natural-features",
                "mapbox:group": "Natural features, natural-labels"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "glacier",
                        "landform"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ],
                [
                    "<=",
                    [
                        "get",
                        "filterrank"
                    ],
                    0
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "natural-line-label",
            "paint": {
                "text-halo-width": 0.5,
                "text-halo-color": "hsl(60, 5%, 100%)",
                "text-halo-blur": 0.5,
                "text-color": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "hsl(236, 1%, 58%)",
                        5,
                        "hsl(236, 6%, 48%)"
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "hsl(236, 1%, 58%)",
                        13,
                        "hsl(236, 6%, 48%)"
                    ]
                ]
            },
            "source-layer": "natural_label"
        },
        {
            "minzoom": 4,
            "layout": {
                "text-size": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        19.8,
                        5,
                        13.200000000000001
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        19.8,
                        13,
                        13.200000000000001
                    ]
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "concat",
                        [
                            "get",
                            "maki"
                        ],
                        "-11"
                    ],
                    15,
                    [
                        "concat",
                        [
                            "get",
                            "maki"
                        ],
                        "-15"
                    ]
                ],
                "text-font": [
                    "DIN Pro Medium",
                    "Arial Unicode MS Regular"
                ],
                "text-offset": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        [
                            "literal",
                            [
                                0,
                                0
                            ]
                        ],
                        5,
                        [
                            "literal",
                            [
                                0,
                                0.75
                            ]
                        ]
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        [
                            "literal",
                            [
                                0,
                                0
                            ]
                        ],
                        13,
                        [
                            "literal",
                            [
                                0,
                                0.75
                            ]
                        ]
                    ]
                ],
                "text-anchor": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "center",
                        5,
                        "top"
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "center",
                        13,
                        "top"
                    ]
                ],
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "natural-features",
                "mapbox:group": "Natural features, natural-labels"
            },
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "dock",
                        "glacier",
                        "landform",
                        "water_feature",
                        "wetland"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "Point"
                ],
                [
                    "<=",
                    [
                        "get",
                        "filterrank"
                    ],
                    0
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "natural-point-label",
            "paint": {
                "icon-opacity": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        0,
                        5,
                        1
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        0,
                        13,
                        1
                    ]
                ],
                "text-halo-color": "hsl(60, 5%, 100%)",
                "text-halo-width": 0.5,
                "text-halo-blur": 0.5,
                "text-color": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "hsl(236, 1%, 58%)",
                        5,
                        "hsl(236, 6%, 48%)"
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "hsl(236, 1%, 58%)",
                        13,
                        "hsl(236, 6%, 48%)"
                    ]
                ]
            },
            "source-layer": "natural_label"
        },
        {
            "id": "water-line-label",
            "type": "symbol",
            "metadata": {
                "mapbox:featureComponent": "natural-features",
                "mapbox:group": "Natural features, natural-labels"
            },
            "source": "composite",
            "source-layer": "natural_label",
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "bay",
                        "ocean",
                        "reservoir",
                        "sea",
                        "water"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "LineString"
                ]
            ],
            "layout": {
                "text-size": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        24,
                        6,
                        18,
                        12,
                        12
                    ],
                    10,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        18,
                        9,
                        12
                    ],
                    18,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        18,
                        9,
                        16
                    ]
                ],
                "text-max-angle": 30,
                "text-letter-spacing": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "ocean",
                    0.25,
                    [
                        "sea",
                        "bay"
                    ],
                    0.15,
                    0
                ],
                "text-font": [
                    "DIN Pro Italic",
                    "Arial Unicode MS Regular"
                ],
                "symbol-placement": "line-center",
                "text-pitch-alignment": "viewport",
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ]
            },
            "paint": {
                "text-color": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "bay",
                        "ocean",
                        "sea"
                    ],
                    "hsl(197, 94%, 58%)",
                    "hsl(197, 66%, 57%)"
                ]
            }
        },
        {
            "id": "water-point-label",
            "type": "symbol",
            "source": "composite",
            "source-layer": "natural_label",
            "filter": [
                "all",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "bay",
                        "ocean",
                        "reservoir",
                        "sea",
                        "water"
                    ],
                    true,
                    false
                ],
                [
                    "==",
                    [
                        "geometry-type"
                    ],
                    "Point"
                ]
            ],
            "layout": {
                "text-line-height": 1.3,
                "text-size": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    7,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        24,
                        6,
                        18,
                        12,
                        12
                    ],
                    10,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        18,
                        9,
                        12
                    ]
                ],
                "text-font": [
                    "DIN Pro Italic",
                    "Arial Unicode MS Regular"
                ],
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-letter-spacing": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "ocean",
                    0.25,
                    [
                        "bay",
                        "sea"
                    ],
                    0.15,
                    0.01
                ],
                "text-max-width": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "ocean",
                    4,
                    "sea",
                    5,
                    [
                        "bay",
                        "water"
                    ],
                    7,
                    10
                ]
            },
            "paint": {
                "text-color": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    [
                        "bay",
                        "ocean",
                        "sea"
                    ],
                    "hsl(197, 94%, 58%)",
                    "hsl(197, 66%, 57%)"
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "natural-features",
                "mapbox:group": "Natural features, natural-labels"
            }
        },
        {
            "minzoom": 6,
            "layout": {
                "text-size": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        19.8,
                        5,
                        13.200000000000001
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        19.8,
                        13,
                        13.200000000000001
                    ]
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "concat",
                        [
                            "get",
                            "maki"
                        ],
                        "-11"
                    ],
                    15,
                    [
                        "concat",
                        [
                            "get",
                            "maki"
                        ],
                        "-15"
                    ]
                ],
                "text-font": [
                    "DIN Pro Medium",
                    "Arial Unicode MS Regular"
                ],
                "text-offset": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        [
                            "literal",
                            [
                                0,
                                0
                            ]
                        ],
                        5,
                        [
                            "literal",
                            [
                                0,
                                0.75
                            ]
                        ]
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        [
                            "literal",
                            [
                                0,
                                0
                            ]
                        ],
                        13,
                        [
                            "literal",
                            [
                                0,
                                0.75
                            ]
                        ]
                    ]
                ],
                "text-anchor": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "center",
                        5,
                        "top"
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        "center",
                        13,
                        "top"
                    ]
                ],
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "point-of-interest-labels",
                "mapbox:group": "Point of interest labels, poi-labels"
            },
            "filter": [
                "let",
                "densityByClass",
                [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "education",
                    1,
                    "landmark",
                    2,
                    "medical",
                    1,
                    "motorist",
                    3,
                    "park_like",
                    1,
                    0
                ],
                [
                    "<=",
                    [
                        "get",
                        "filterrank"
                    ],
                    [
                        "case",
                        [
                            "<",
                            0,
                            [
                                "var",
                                "densityByClass"
                            ]
                        ],
                        [
                            "+",
                            [
                                "step",
                                [
                                    "zoom"
                                ],
                                0,
                                16,
                                1,
                                17,
                                2
                            ],
                            [
                                "var",
                                "densityByClass"
                            ]
                        ],
                        [
                            "var",
                            "densityByClass"
                        ]
                    ]
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "poi-label",
            "paint": {
                "icon-opacity": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        0,
                        5,
                        1
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        0,
                        13,
                        1
                    ]
                ],
                "text-halo-color": [
                    "match",
                    [
                        "get",
                        "class"
                    ],
                    "park_like",
                    "hsl(100, 55%, 100%)",
                    "education",
                    "hsl(35, 35%, 100%)",
                    "medical",
                    "hsl(320, 53%, 100%)",
                    "hsl(60, 5%, 100%)"
                ],
                "text-halo-width": 0.5,
                "text-halo-blur": 0.5,
                "text-color": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        [
                            "match",
                            [
                                "get",
                                "class"
                            ],
                            "food_and_drink",
                            "hsl(232, 13%, 71%)",
                            "park_like",
                            "hsl(99, 100%, 33%)",
                            "education",
                            "hsl(35, 24%, 54%)",
                            "medical",
                            "hsl(320, 24%, 62%)",
                            "hsl(236, 1%, 58%)"
                        ],
                        5,
                        [
                            "match",
                            [
                                "get",
                                "class"
                            ],
                            "food_and_drink",
                            "hsl(232, 20%, 54%)",
                            "park_like",
                            "hsl(99, 100%, 22%)",
                            "education",
                            "hsl(35, 60%, 34%)",
                            "medical",
                            "hsl(320, 32%, 52%)",
                            "hsl(236, 6%, 48%)"
                        ]
                    ],
                    17,
                    [
                        "step",
                        [
                            "get",
                            "sizerank"
                        ],
                        [
                            "match",
                            [
                                "get",
                                "class"
                            ],
                            "food_and_drink",
                            "hsl(232, 13%, 71%)",
                            "park_like",
                            "hsl(99, 100%, 33%)",
                            "education",
                            "hsl(35, 24%, 54%)",
                            "medical",
                            "hsl(320, 24%, 62%)",
                            "hsl(236, 1%, 58%)"
                        ],
                        13,
                        [
                            "match",
                            [
                                "get",
                                "class"
                            ],
                            "food_and_drink",
                            "hsl(232, 20%, 54%)",
                            "park_like",
                            "hsl(99, 100%, 22%)",
                            "education",
                            "hsl(35, 60%, 34%)",
                            "medical",
                            "hsl(320, 32%, 52%)",
                            "hsl(236, 6%, 48%)"
                        ]
                    ]
                ]
            },
            "source-layer": "poi_label"
        },
        {
            "id": "airport-label",
            "type": "symbol",
            "source": "composite",
            "source-layer": "airport_label",
            "minzoom": 8,
            "layout": {
                "text-line-height": 1.1,
                "text-size": [
                    "step",
                    [
                        "get",
                        "sizerank"
                    ],
                    19.8,
                    9,
                    13.200000000000001
                ],
                "icon-image": [
                    "step",
                    [
                        "get",
                        "sizerank"
                    ],
                    [
                        "concat",
                        [
                            "get",
                            "maki"
                        ],
                        "-15"
                    ],
                    9,
                    [
                        "concat",
                        [
                            "get",
                            "maki"
                        ],
                        "-11"
                    ]
                ],
                "text-font": [
                    "DIN Pro Medium",
                    "Arial Unicode MS Regular"
                ],
                "text-offset": [
                    0,
                    0.75
                ],
                "text-rotation-alignment": "viewport",
                "text-anchor": "top",
                "text-field": [
                    "step",
                    [
                        "get",
                        "sizerank"
                    ],
                    [
                        "coalesce",
                        [
                            "get",
                            "name_en"
                        ],
                        [
                            "get",
                            "name"
                        ]
                    ],
                    15,
                    [
                        "get",
                        "ref"
                    ]
                ],
                "text-letter-spacing": 0.01,
                "text-max-width": 9
            },
            "paint": {
                "text-color": "hsl(260, 30%, 71%)",
                "text-halo-color": "hsl(260, 20%, 100%)",
                "text-halo-width": 1
            },
            "metadata": {
                "mapbox:featureComponent": "transit",
                "mapbox:group": "Transit, transit-labels"
            }
        },
        {
            "minzoom": 10,
            "layout": {
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-transform": "uppercase",
                "text-font": [
                    "DIN Pro Bold",
                    "Arial Unicode MS Bold"
                ],
                "text-letter-spacing": [
                    "match",
                    [
                        "get",
                        "type"
                    ],
                    "suburb",
                    0.15,
                    0.1
                ],
                "text-max-width": 7,
                "text-padding": 3,
                "text-size": [
                    "interpolate",
                    [
                        "cubic-bezier",
                        0.5,
                        0,
                        1,
                        1
                    ],
                    [
                        "zoom"
                    ],
                    11,
                    [
                        "match",
                        [
                            "get",
                            "type"
                        ],
                        "suburb",
                        14.3,
                        13.65
                    ],
                    15,
                    [
                        "match",
                        [
                            "get",
                            "type"
                        ],
                        "suburb",
                        22.1,
                        20.8
                    ]
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "place-labels",
                "mapbox:group": "Place labels, place-labels"
            },
            "maxzoom": 15,
            "filter": [
                "all",
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "settlement_subdivision"
                ],
                [
                    "<=",
                    [
                        "get",
                        "filterrank"
                    ],
                    3
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "settlement-subdivision-label",
            "paint": {
                "text-halo-color": "hsla(60, 5%, 100%, 0.75)",
                "text-halo-width": 1,
                "text-color": "hsl(210, 10%, 39%)",
                "text-halo-blur": 0.5
            },
            "source-layer": "place_label"
        },
        {
            "layout": {
                "text-line-height": 1.1,
                "text-size": [
                    "interpolate",
                    [
                        "cubic-bezier",
                        0.2,
                        0,
                        0.9,
                        1
                    ],
                    [
                        "zoom"
                    ],
                    3,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        15.600000000000001,
                        9,
                        14.3,
                        10,
                        13.65,
                        12,
                        12.35,
                        14,
                        11.05,
                        16,
                        8.450000000000001,
                        17,
                        5.2
                    ],
                    13,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        32.5,
                        9,
                        29.900000000000002,
                        10,
                        27.3,
                        11,
                        24.7,
                        12,
                        23.400000000000002,
                        13,
                        22.1,
                        15,
                        19.5
                    ]
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "case",
                        [
                            "==",
                            [
                                "get",
                                "capital"
                            ],
                            2
                        ],
                        "border-dot-13",
                        [
                            "step",
                            [
                                "get",
                                "symbolrank"
                            ],
                            "dot-11",
                            9,
                            "dot-10",
                            11,
                            "dot-9"
                        ]
                    ],
                    8,
                    ""
                ],
                "text-font": [
                    "DIN Pro Regular",
                    "Arial Unicode MS Regular"
                ],
                "text-justify": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "text_anchor"
                        ],
                        [
                            "left",
                            "bottom-left",
                            "top-left"
                        ],
                        "left",
                        [
                            "right",
                            "bottom-right",
                            "top-right"
                        ],
                        "right",
                        "center"
                    ],
                    8,
                    "center"
                ],
                "text-offset": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "capital"
                        ],
                        2,
                        [
                            "match",
                            [
                                "get",
                                "text_anchor"
                            ],
                            "bottom",
                            [
                                "literal",
                                [
                                    0,
                                    -0.3
                                ]
                            ],
                            "bottom-left",
                            [
                                "literal",
                                [
                                    0.3,
                                    -0.1
                                ]
                            ],
                            "left",
                            [
                                "literal",
                                [
                                    0.45,
                                    0.1
                                ]
                            ],
                            "top-left",
                            [
                                "literal",
                                [
                                    0.3,
                                    0.1
                                ]
                            ],
                            "top",
                            [
                                "literal",
                                [
                                    0,
                                    0.3
                                ]
                            ],
                            "top-right",
                            [
                                "literal",
                                [
                                    -0.3,
                                    0.1
                                ]
                            ],
                            "right",
                            [
                                "literal",
                                [
                                    -0.45,
                                    0
                                ]
                            ],
                            "bottom-right",
                            [
                                "literal",
                                [
                                    -0.3,
                                    -0.1
                                ]
                            ],
                            [
                                "literal",
                                [
                                    0,
                                    -0.3
                                ]
                            ]
                        ],
                        [
                            "match",
                            [
                                "get",
                                "text_anchor"
                            ],
                            "bottom",
                            [
                                "literal",
                                [
                                    0,
                                    -0.25
                                ]
                            ],
                            "bottom-left",
                            [
                                "literal",
                                [
                                    0.2,
                                    -0.05
                                ]
                            ],
                            "left",
                            [
                                "literal",
                                [
                                    0.4,
                                    0.05
                                ]
                            ],
                            "top-left",
                            [
                                "literal",
                                [
                                    0.2,
                                    0.05
                                ]
                            ],
                            "top",
                            [
                                "literal",
                                [
                                    0,
                                    0.25
                                ]
                            ],
                            "top-right",
                            [
                                "literal",
                                [
                                    -0.2,
                                    0.05
                                ]
                            ],
                            "right",
                            [
                                "literal",
                                [
                                    -0.4,
                                    0.05
                                ]
                            ],
                            "bottom-right",
                            [
                                "literal",
                                [
                                    -0.2,
                                    -0.05
                                ]
                            ],
                            [
                                "literal",
                                [
                                    0,
                                    -0.25
                                ]
                            ]
                        ]
                    ],
                    8,
                    [
                        "literal",
                        [
                            0,
                            0
                        ]
                    ]
                ],
                "text-anchor": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "get",
                        "text_anchor"
                    ],
                    8,
                    "center"
                ],
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-max-width": 7
            },
            "metadata": {
                "mapbox:featureComponent": "place-labels",
                "mapbox:group": "Place labels, place-labels"
            },
            "maxzoom": 15,
            "filter": [
                "all",
                [
                    "<=",
                    [
                        "get",
                        "filterrank"
                    ],
                    2
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "settlement"
                ],
                [
                    "step",
                    [
                        "zoom"
                    ],
                    true,
                    8,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        11
                    ],
                    10,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        12
                    ],
                    11,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        13
                    ],
                    12,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        15
                    ],
                    13,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        11
                    ],
                    14,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        13
                    ]
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "settlement-minor-label",
            "paint": {
                "text-color": "hsl(210, 10%, 0%)",
                "text-halo-color": "hsl(60, 5%, 100%)",
                "text-halo-width": 1,
                "text-halo-blur": 1
            },
            "source-layer": "place_label"
        },
        {
            "layout": {
                "text-line-height": 1.1,
                "text-size": [
                    "interpolate",
                    [
                        "cubic-bezier",
                        0.2,
                        0,
                        0.9,
                        1
                    ],
                    [
                        "zoom"
                    ],
                    8,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        25.2,
                        9,
                        23.799999999999997,
                        10,
                        21
                    ],
                    15,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        39.199999999999996,
                        9,
                        36.4,
                        10,
                        32.199999999999996,
                        11,
                        29.4,
                        12,
                        28,
                        13,
                        26.599999999999998,
                        15,
                        22.4
                    ]
                ],
                "icon-image": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "case",
                        [
                            "==",
                            [
                                "get",
                                "capital"
                            ],
                            2
                        ],
                        "border-dot-13",
                        [
                            "step",
                            [
                                "get",
                                "symbolrank"
                            ],
                            "dot-11",
                            9,
                            "dot-10",
                            11,
                            "dot-9"
                        ]
                    ],
                    8,
                    ""
                ],
                "text-font": [
                    "DIN Pro Medium",
                    "Arial Unicode MS Regular"
                ],
                "text-justify": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "text_anchor"
                        ],
                        [
                            "left",
                            "bottom-left",
                            "top-left"
                        ],
                        "left",
                        [
                            "right",
                            "bottom-right",
                            "top-right"
                        ],
                        "right",
                        "center"
                    ],
                    8,
                    "center"
                ],
                "text-offset": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "capital"
                        ],
                        2,
                        [
                            "match",
                            [
                                "get",
                                "text_anchor"
                            ],
                            "bottom",
                            [
                                "literal",
                                [
                                    0,
                                    -0.3
                                ]
                            ],
                            "bottom-left",
                            [
                                "literal",
                                [
                                    0.3,
                                    -0.1
                                ]
                            ],
                            "left",
                            [
                                "literal",
                                [
                                    0.45,
                                    0.1
                                ]
                            ],
                            "top-left",
                            [
                                "literal",
                                [
                                    0.3,
                                    0.1
                                ]
                            ],
                            "top",
                            [
                                "literal",
                                [
                                    0,
                                    0.3
                                ]
                            ],
                            "top-right",
                            [
                                "literal",
                                [
                                    -0.3,
                                    0.1
                                ]
                            ],
                            "right",
                            [
                                "literal",
                                [
                                    -0.45,
                                    0
                                ]
                            ],
                            "bottom-right",
                            [
                                "literal",
                                [
                                    -0.3,
                                    -0.1
                                ]
                            ],
                            [
                                "literal",
                                [
                                    0,
                                    -0.3
                                ]
                            ]
                        ],
                        [
                            "match",
                            [
                                "get",
                                "text_anchor"
                            ],
                            "bottom",
                            [
                                "literal",
                                [
                                    0,
                                    -0.25
                                ]
                            ],
                            "bottom-left",
                            [
                                "literal",
                                [
                                    0.2,
                                    -0.05
                                ]
                            ],
                            "left",
                            [
                                "literal",
                                [
                                    0.4,
                                    0.05
                                ]
                            ],
                            "top-left",
                            [
                                "literal",
                                [
                                    0.2,
                                    0.05
                                ]
                            ],
                            "top",
                            [
                                "literal",
                                [
                                    0,
                                    0.25
                                ]
                            ],
                            "top-right",
                            [
                                "literal",
                                [
                                    -0.2,
                                    0.05
                                ]
                            ],
                            "right",
                            [
                                "literal",
                                [
                                    -0.4,
                                    0.05
                                ]
                            ],
                            "bottom-right",
                            [
                                "literal",
                                [
                                    -0.2,
                                    -0.05
                                ]
                            ],
                            [
                                "literal",
                                [
                                    0,
                                    -0.25
                                ]
                            ]
                        ]
                    ],
                    8,
                    [
                        "literal",
                        [
                            0,
                            0
                        ]
                    ]
                ],
                "text-anchor": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "get",
                        "text_anchor"
                    ],
                    8,
                    "center"
                ],
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-max-width": 7
            },
            "metadata": {
                "mapbox:featureComponent": "place-labels",
                "mapbox:group": "Place labels, place-labels"
            },
            "maxzoom": 15,
            "filter": [
                "all",
                [
                    "<=",
                    [
                        "get",
                        "filterrank"
                    ],
                    2
                ],
                [
                    "==",
                    [
                        "get",
                        "class"
                    ],
                    "settlement"
                ],
                [
                    "step",
                    [
                        "zoom"
                    ],
                    false,
                    8,
                    [
                        "<",
                        [
                            "get",
                            "symbolrank"
                        ],
                        11
                    ],
                    10,
                    [
                        "<",
                        [
                            "get",
                            "symbolrank"
                        ],
                        12
                    ],
                    11,
                    [
                        "<",
                        [
                            "get",
                            "symbolrank"
                        ],
                        13
                    ],
                    12,
                    [
                        "<",
                        [
                            "get",
                            "symbolrank"
                        ],
                        15
                    ],
                    13,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        11
                    ],
                    14,
                    [
                        ">=",
                        [
                            "get",
                            "symbolrank"
                        ],
                        13
                    ]
                ]
            ],
            "type": "symbol",
            "source": "composite",
            "id": "settlement-major-label",
            "paint": {
                "text-color": "hsl(210, 10%, 0%)",
                "text-halo-color": "hsl(60, 5%, 100%)",
                "text-halo-width": 1,
                "text-halo-blur": 1
            },
            "source-layer": "place_label"
        },
        {
            "minzoom": 3,
            "layout": {
                "text-size": [
                    "interpolate",
                    [
                        "cubic-bezier",
                        0.85,
                        0.7,
                        0.65,
                        1
                    ],
                    [
                        "zoom"
                    ],
                    4,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        12,
                        6,
                        11.4,
                        7,
                        10.799999999999999
                    ],
                    9,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        28.799999999999997,
                        6,
                        21.599999999999998,
                        7,
                        16.8
                    ]
                ],
                "text-transform": "uppercase",
                "text-font": [
                    "DIN Pro Bold",
                    "Arial Unicode MS Bold"
                ],
                "text-field": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        [
                            "coalesce",
                            [
                                "get",
                                "name_en"
                            ],
                            [
                                "get",
                                "name"
                            ]
                        ],
                        5,
                        [
                            "coalesce",
                            [
                                "get",
                                "abbr"
                            ],
                            [
                                "get",
                                "name_en"
                            ],
                            [
                                "get",
                                "name"
                            ]
                        ]
                    ],
                    5,
                    [
                        "coalesce",
                        [
                            "get",
                            "name_en"
                        ],
                        [
                            "get",
                            "name"
                        ]
                    ]
                ],
                "text-letter-spacing": 0.15,
                "text-max-width": 6
            },
            "metadata": {
                "mapbox:featureComponent": "place-labels",
                "mapbox:group": "Place labels, place-labels"
            },
            "maxzoom": 9,
            "filter": [
                "==",
                [
                    "get",
                    "class"
                ],
                "state"
            ],
            "type": "symbol",
            "source": "composite",
            "id": "state-label",
            "paint": {
                "text-color": "hsl(210, 10%, 0%)",
                "text-halo-color": "hsl(60, 5%, 100%)",
                "text-halo-width": 1
            },
            "source-layer": "place_label"
        },
        {
            "minzoom": 1,
            "layout": {
                "icon-image": "",
                "text-field": [
                    "coalesce",
                    [
                        "get",
                        "name_en"
                    ],
                    [
                        "get",
                        "name"
                    ]
                ],
                "text-line-height": 1.1,
                "text-max-width": 6,
                "text-font": [
                    "DIN Pro Medium",
                    "Arial Unicode MS Regular"
                ],
                "text-offset": [
                    "literal",
                    [
                        0,
                        0
                    ]
                ],
                "text-justify": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "match",
                        [
                            "get",
                            "text_anchor"
                        ],
                        [
                            "left",
                            "bottom-left",
                            "top-left"
                        ],
                        "left",
                        [
                            "right",
                            "bottom-right",
                            "top-right"
                        ],
                        "right",
                        "center"
                    ],
                    7,
                    "center"
                ],
                "text-size": [
                    "interpolate",
                    [
                        "cubic-bezier",
                        0.2,
                        0,
                        0.7,
                        1
                    ],
                    [
                        "zoom"
                    ],
                    1,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        15.399999999999999,
                        4,
                        12.6,
                        5,
                        11.2
                    ],
                    9,
                    [
                        "step",
                        [
                            "get",
                            "symbolrank"
                        ],
                        39.199999999999996,
                        4,
                        30.799999999999997,
                        5,
                        29.4
                    ]
                ]
            },
            "metadata": {
                "mapbox:featureComponent": "place-labels",
                "mapbox:group": "Place labels, place-labels"
            },
            "maxzoom": 10,
            "filter": [
                "==",
                [
                    "get",
                    "class"
                ],
                "country"
            ],
            "type": "symbol",
            "source": "composite",
            "id": "country-label",
            "paint": {
                "icon-opacity": [
                    "step",
                    [
                        "zoom"
                    ],
                    [
                        "case",
                        [
                            "has",
                            "text_anchor"
                        ],
                        1,
                        0
                    ],
                    7,
                    0
                ],
                "text-color": "hsl(210, 10%, 0%)",
                "text-halo-color": [
                    "interpolate",
                    [
                        "linear"
                    ],
                    [
                        "zoom"
                    ],
                    2,
                    "hsla(60, 5%, 100%, 0.75)",
                    3,
                    "hsl(60, 5%, 100%)"
                ],
                "text-halo-width": 1.25
            },
            "source-layer": "place_label"
        }
    ],
    "created": "2020-03-12T22:19:48.414Z",
    "modified": "2020-03-13T21:05:45.679Z",
    "id": "ck7pbezoo07661ioxtn6qsmuw",
    "owner": "examples",
    "visibility": "public",
    "protected": false,
    "draft": false
}
