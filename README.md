
cartodb.js
==========

This library allows to embed you visualizations created with CartoDB in your map or website in a simple way.


quick start
===========

  1. add cartodb.js and css to your site (and google maps if you are using it):

    ```html

        <link rel="stylesheet" href="http://libs.cartocdn.com/cartodb.js/v2/themes/css/cartodb.css" />
        <!--[if lte IE 8]>
            <link rel="stylesheet" href="http://libs.cartocdn.com/cartodb.js/v2/themes/css/cartodb.ie.css" />
        <![endif]-->

        <script src="https://maps.googleapis.com/maps/api/js?sensor=false"></script>
        <script src="http://libs.cartocdn.com/cartodb.js/v2/cartodb.js"></script>

        <!-- use these links if you are using https -->
        <!--

        <link rel="stylesheet" href="https://d3voyrscnb0slx.cloudfront.net/cartodb.js/v2/themes/cartodb.css" />
        <!--[if lte IE 8]>
            <link rel="stylesheet" href="https://d3voyrscnb0slx.cloudfront.net/cartodb.js/v2/themes/css/cartodb.ie.css" />
        <![endif]-->

        <script src="https://d3voyrscnb0slx.cloudfront.net/cartodb.js/v2/cartodb.js"></script>
        -->
    ```


  2. create the map and add the layer 
  
    **gmaps**

    ```javascript

        // create google map
        var map;
        var mapOptions = {
          zoom: 7,
          center: new google.maps.LatLng(43, -68),
          mapTypeId: google.maps.MapTypeId.ROADMAP
        };
        map = new google.maps.Map(document.getElementById('map'),  mapOptions);

        // add the cartodb layer
        // you can find this url in CartoDB interface:
        // - go to map
        // - click on share
        // - API tab
        var layerUrl = 'http://examples-beta.cartodb.com/api/v1/viz/219/viz.json';
        cartodb.createLayer(map, layerUrl, function(layer) {
            map.overlayMapTypes.setAt(0, layer);
        });

    ```

    **leaflet**

    ```javascript
      var map = L.map('map').setView([0, 0], 3);

      // set a base layer 
      L.tileLayer('http://a.tile.stamen.com/toner/{z}/{x}/{y}.png', {
        attribution: 'stamen http://maps.stamen.com/'
      }).addTo(map);
      
      // add the cartodb layer
      var layerUrl = 'http://examples-beta.cartodb.com/api/v1/viz/219/viz.json';
      cartodb.createLayer(map, layerUrl, function(layer) {
        map.overlayMapTypes.setAt(0, layer);
      });
    ```



next steps
==========

  - see our [examples](https://github.com/CartoDB/cartodb.js/tree/develop/examples)
  - read the [API reference](https://github.com/CartoDB/cartodb.js/tree/develop/doc/API.md)
  - read our mailing list



how to build
============

    
    ```
    open test/SpecRunner.html
    make release
    ```


