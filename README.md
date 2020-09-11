# geojson-extension

A JupyterLab extension for rendering GeoJSON

![demo](http://g.recordit.co/SsWJCpKIJy.gif)

## Requirements

* JupyterLab ^3.0
* Node.js >= 5

## Install

```bash
pip install jupyterlab_geojson
```

## Usage

To render GeoJSON output in IPython:

```python
from IPython.display import GeoJSON

GeoJSON({
    "type": "Feature",
    "geometry": {
        "type": "Point",
        "coordinates": [-118.4563712, 34.0163116]
    }
})
```

To use a specific tileset:

```python
GeoJSON(
    data={
        "type": "Feature",
        "geometry": {
            "type": "Point",
            "coordinates": [-118.4563712, 34.0163116]
        }
    }, url_template="https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token=[MAPBOX_ACCESS_TOKEN]",
    layer_options={
        "id": "mapbox.streets",
        "attribution" : '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
    }
)
```

To render GeoJSON on Mars:

```python
GeoJSON(
  data={
      "type": "Feature",
      "geometry": {
          "type": "Point",
          "coordinates": [11.8, -45.04]
      }
  }, url_template="http://s3-eu-west-1.amazonaws.com/whereonmars.cartodb.net/{basemap_id}/{z}/{x}/{y}.png",
  layer_options={
      "basemap_id": "celestia_mars-shaded-16k_global",
      "attribution" : "Celestia/praesepe",
      "tms": True,
      "minZoom" : 0,
      "maxZoom" : 5
  }
)
```

To render a `.geojson` or `.geo.json` file, simply open it.

## Contributing

### Install

The `jlpm` command is JupyterLab's pinned version of
[yarn](https://yarnpkg.com/) that is installed with JupyterLab. You may use
`yarn` or `npm` in lieu of `jlpm` below.

```bash
# Clone the repo to your local environment
git clone https://github.com/jupyterlab/geojson-extension.git
cd geojson-extension
# Install package in development mode
pip install -e .
# Rebuild extension Typescript source and extension after making changes
jlpm build:all
```

You can watch the jupyter-renderers directory and run JupyterLab in watch mode to watch for changes in the extension's source and automatically rebuild the extension and application.

```bash
# Run jupyterlab in watch mode in one terminal tab
jupyter lab --watch
# Watch the jupyter-renderers directory in another terminal tab
jlpm watch
```

### Uninstall

```bash
pip uninstall jupyterlab_geojson
jupyter labextension uninstall @jupyterlab/geojson-extension
```
