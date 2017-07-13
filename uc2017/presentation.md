<!-- .slide: data-background="images/Picture1.png" -->

<div style="padding-top: 100px"/>


<!-- .slide: data-background="images/Picture1.png" -->

#  Building 3D GIS Applications with JavaScript

<br>

Javier Gutierrez and Janett Baresel

ESRI R&amp;D Center Zürich

---

<!-- .slide: data-background="images/Picture2.png" -->

## Building an App: New York

<img src="./images/ny-app.png" style="max-height: 600px; border:0; background: none; box-shadow: none;" />

---

<!-- .slide: data-background="images/Picture2.png" -->

## Creating a SceneView


<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
 var map = new Map({
   basemap: "dark-gray",
   ground: "world-elevation"
 });


 var view = new SceneView({
   container: "viewDiv",
   map: map,
   center: [-101.17, 21.78]
 });</code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/01-basics.html"></iframe>
  </div>
</div>




---

<!-- .slide: data-background="images/Picture2.png" -->

## Layers


**Supported in 2D and 3D**

| | |
| - | - |
| FeatureLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-FeatureLayer.html |
| GraphicsLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-GraphicsLayer.html |
| MapImageLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-MapImageLayer.html |
| ImageryLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-ImageryLayer.html |
| TileLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-TileLayer.html |
| VectorTileLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-VectorTileLayer.html |

<small >More layers coming soon</small>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Layers


**Supported in 3D only**

| | |
| - | - |
| SceneLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-SceneLayer.html |
| ElevationLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-ElevationLayer.html |
| IntegratedMeshLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-IntegratedMeshLayer.html |
| PointCloudLayer | https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-PointCloudLayer.html |


---


<!-- .slide: data-background="images/Picture2.png" -->

## Adding Layers

Layers can be added via the service url or the portal id


<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">


 var pcLayer = new PointCloudLayer({
   url: "https://..."
 });

 var sceneLayer = new SceneLayer({
   portalItem: {
     id: "2e0761b9a4274b8db52c4bf34356911e"
   }
 });

 map.add(sceneLayer);
 map.add(pcLayer);


       </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/02-basics.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->


## API widgets

<div style = "text-align: left; margin-left: 200px;">

- a number of ready-to-use widgets<br/>
- modular and easily added and positioned in the view<br/>
- separation of logic and view<br/>
- easy custom styling via themes and custom css<br/>
- guide to create custom widgets<br/>



<img src="./images/widgets.png" style="max-height: 600px; border:0; background: none; box-shadow: none;" />

</div>


---

<!-- .slide: data-background="images/Picture2.png" -->


## Adding a widget

Adding the layer list widget to toggle layer visbilities

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">

  view.then(function() {
    var layerList = new LayerList({
      view: view
    });

    view.ui.add(layerList, "top-right");
  });
         </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/03-widget.html"></iframe>
  </div>
</div>



---

<!-- .slide: data-background="images/Picture2.png" -->

## Adding a group layer

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">

    var groupLayer = new GroupLayer({
      title: "NY Layers",
      visibilityMode: "exclusive"
    });

    groupLayer.addMany([pcLayer, sceneLayer]);
    map.add(groupLayer);


       </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/02a-basics.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->


## Changing the time of day

environment allows changing shadows and the time of day

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
 view.environment = {
   lighting: {
     directShadowsEnabled: true,
     date:
       new Date("Sun Mar 15 2015 09:00:00 GMT/-0400 (EDT)")
   }
 };
         </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/03a-time.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Layer Symbology

- layers have renderers to define how they are visualized
- renderers: SimpleRenderer, ClassBreaksRenderer, UniqueValueRenderer

<img src="./images/renderers.png" style="max-height: 300px; border:0; background: none; box-shadow: none;" />

---

<!-- .slide: data-background="images/Picture2.png" -->

## Layer Symbology

Visual variables: define parameters for data-driven visualizations of numeric data

<img src="./images/helsinki.png" style="max-height: 300px; border:0; background: none; box-shadow: none;" />

---

<!-- .slide: data-background="images/Picture2.png" -->

## Layer Symbology

Create a SimpleRenderer, coloring all buildings the same

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
   sceneLayer.renderer = new SimpleRenderer({
     symbol: new MeshSymbol3D({
       symbolLayers:
        new Collection([
         new FillSymbol3DLayer({
           material: { color: "green" }
         })
       ])
     })
   });
         </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/04-smartmapping.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Layer Symbology

Create a SimpleRenderer, using visual variables
<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
   sceneLayer.renderer = new SimpleRenderer({
     symbol: new MeshSymbol3D({
       symbolLayers: new Collection([new FillSymbol3DLayer()]),
        visualVariables: [{
         type: "color",
         field: "CNSTRCT_YR",
         stops: [
           {
             color: [58,128,89,1],
             value: 1912,
             label: "< 1912"
           },
           {
             color: [155,191,133,1],
             value: 1925
           },
           ...
         ]
       }]
     })
   });
         </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/04a-smartmapping.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Layer Symbology

Create a PointCloudStretchRenderer for point cloud layer for the elevation attribute

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
   var newRenderer = new PointCloudStretchRenderer({
     field: "ELEVATION",
     stops: [{
       value: -1,
       color: [61, 51, 158]
     }, {
       value: 1,
       color: [73, 196, 196]
     }, {
       value: 5,
       color: [104, 196, 73]
     },
     ...
     ]
   });

   pcLayer.renderer = newRenderer;
         </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/05-pcl.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## hitTest & query elevation

- hitTest searches for graphics that intersect the specified screen coordinates
- ground can be queried for elevation at a given point

---

<!-- .slide: data-background="images/Picture2.png" -->

## Query Elevation
determine point in 3D scene from screen point

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
  view.on("click", function(screenPoint) {

     view.hitTest(screenPoint)
        .then(function(hit) {
          if (hit.results.length === 0) return;

          hitPoint = hit.results[0].mapPoint;
        });
     });
  }
  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/06-hitTest.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Query Elevation
query elevation for point in 3D scene

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
  view.on("click", function(screenPoint) {

     view.hitTest(screenPoint)
        .then(function(hit) {
          if (hit.results.length === 0) return;

          hitPoint = hit.results[0].mapPoint;
          return view.map.ground.queryElevation(hitPoint);
        })
        .then(function(elevationResult) {
          if (!elevationResult) return;

          var groundPoint = elevationResult.geometry;
          var distance = hitPoint.z - groundPoint.z;

          var graphics = createGraphics(hitPoint,
            groundPoint, distance);

          view.graphics.addMany(graphics);
        });
     });
  }
  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/ny/06a-hitTest.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Building an App: Lyon

<img src="./images/lyon-app.png" style="max-height: 600px; border:0; background: none; box-shadow: none;" />

---

<!-- .slide: data-background="images/Picture2.png" -->

## Building an App: Lyon

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
    var renderer = new UniqueValueRenderer({
      field: "Type",
      uniqueValueInfos: [{
        value: "Museum",
        symbol: createSymbol("Museum.png", "#D13470")
      }, {
        value: "Restaurant",
        symbol: createSymbol("Restaurant.png", "#F97C5A")
      }, {
        value: "Church",
        symbol: createSymbol("Church.png", "#884614")
      }, {
        value: "Hotel",
        symbol: createSymbol("Hotel.png", "#56B2D6")
      }, {
        value: "Park",
        symbol: createSymbol("Park.png", "#40C2B4")
      }]
    });

    var featLayer = new FeatureLayer({
      portalItem: {
        id: "6e76d897e09b47b6b68d8ba9a7b0c3d0"
      },
      renderer: renderer
    });
  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/01-basics.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Elevation Mode

 * `relative-to-scene` (new)
 * `relative-to-ground`, `absolute-height`, `on-the-ground`

<img src="./images/elevation-modes.jpg" style="max-height: 300px; border:0; background: none; box-shadow: none;" />


---

<!-- .slide: data-background="images/Picture2.png" -->

## New elevation mode: "relative-to-scene"

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
      var featLayer = new FeatureLayer({
       portalItem: {
         id: "6e76d897e09b47b6b68d8ba9a7b0c3d0"
       },
       renderer: renderer,
       elevationInfo: {
         mode: "relative-to-scene"
       }
     });
  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/02-relative.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Declutter

Number of overlapping points is reduced

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
      var featLayer = new FeatureLayer({
       portalItem: {
         id: "6e76d897e09b47b6b68d8ba9a7b0c3d0"
       },
       renderer: renderer,
       elevationInfo: {
         mode: "relative-to-scene"
       },
       featureReduction: {
         type: "selection"
       }
     });
  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/03-declutter.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## Improve Perspective

improve the sense of depth for 2D icons

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
      var featLayer = new FeatureLayer({
       portalItem: {
         id: "6e76d897e09b47b6b68d8ba9a7b0c3d0"
       },
       renderer: renderer,
       elevationInfo: {
         mode: "relative-to-scene"
       },
       featureReduction: {
         type: "selection"
       },
       screenSizePerspectiveEnabled: true
     });
  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/04-perspective.html"></iframe>
  </div>
</div>
---

<!-- .slide: data-background="images/Picture2.png" -->

## Callout Lines

Lift symbols above the ground for better visibility.

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
     new PointSymbol3D({
       symbolLayers: [...],

       verticalOffset: {
         screenLength: 40
       },

       callout: new LineCallout3D({
         color: "white",
         size: 2,
         border: {
           color: color
         }
       })
     });
  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/05-callout.html"></iframe>
  </div>
</div>

---

<!-- .slide: data-background="images/Picture2.png" -->

## 3D Models

use WebStyleSymbols to include 3d models in your scene.

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">

  new UniqueValueRenderer({
    field: "TYPE",
    uniqueValueInfos: [
    {
      value: "taxi",
      symbol: new WebStyleSymbol({
         name: "Taxi",
         styleName: "EsriRealisticTransportationStyle"
       })
    },
    ...
    ]
  })


  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/06-models.html"></iframe>
  </div>
</div>

<div style="font-size: 18px;display: inline;">Model gallery:</div>
https://developers.arcgis.com/javascript/latest/guide/esri-web-style-symbols/index.html

---

<!-- .slide: data-background="images/Picture2.png" -->

## Webscene loading

Loading a webscene by id

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">

  var map = new WebScene({
    portalItem: {
      id: "8b464fd68d87480486d36e8cbbc52ab9"
    }
  });


  var view = new SceneView({
    container: "viewDiv",
    map: map
  });


  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/07-webscene-load.html"></iframe>
  </div>
</div>

---


<!-- .slide: data-background="images/Picture2.png" -->

## Popups and webscene saving

Adding a custom popup template and saving the webscene

<div class="twos">
  <div class="snippet">
  <pre><code class="lang-js hljs javascript">
  featLayer.popupTemplate = new PopupTemplate({
      title: "{NAME}",
      content: "{ADDRESS}<br/>" +
      "Telephone: {TELEPHONE}<br/>" +
      "Website: {WEBSITE}<br/>"
    });
  });

  [...]

  var portal = new Portal({
    url: myPortalUrl,
    authMode: "immediate"
  });
  portal.load().then(function() {
    webscene.saveAs({
      title: "My Scene",
      portal: portal
    });
  });

  </code>
   </pre>
  <!--<svg data-play-frame="frame-auto-cast" class="play-code" viewBox="0 0 24 24"><path fill="#999" d="M12,20.14C7.59,20.14 4,16.55 4,12.14C4,7.73 7.59,4.14 12,4.14C16.41,4.14 20,7.73 20,12.14C20,16.55 16.41,20.14 12,20.14M12,2.14A10,10 0 0,0 2,12.14A10,10 0 0,0 12,22.14A10,10 0 0,0 22,12.14C22,6.61 17.5,2.14 12,2.14M10,16.64L16,12.14L10,7.64V16.64Z" /></svg>-->
  </div>
  <div class="snippet-preview">
    <iframe id="frame-auto-cast" data-src="./snippets/lyon/08-popup.html"></iframe>
  </div>
</div>

<div style="font-size: 18px;display: inline;">Final webscene:</div> http://arcg.is/1q0avT



