<script>
  import { windowWidth } from "../stores/global";
  import wetlandRectangles from "../data/wetland-rectangles.geo.json";

  // Check URL parameter
  const urlParams = new URLSearchParams(window.location.search);
  const useWebMap = urlParams.get("web") === "true";

  let width = $derived($windowWidth);
  let height = $derived(Math.round($windowWidth * 0.7));

  let imageUrl;

  if (useWebMap) {
    // console.log("using web map");
    // const style = "startribune/cm8hhq3e6017901s55dfi5dmn";

    // // Calculate the bounding box that encompasses both rectangles
    // const bbox = [
    //   -102, // West
    //   37, // South
    //   -83.06, // East
    //   42.00482129436723, // North
    // ];

    // $inspect(width, height);

    // // Create GeoJSON layer for original wetlands
    // const originalWetlands = {
    //   type: "Feature",
    //   properties: {
    //     fill: "#f1b82d",
    //     "fill-opacity": 0.6,
    //     stroke: "#f1b82d",
    //     "stroke-width": 2,
    //   },
    //   geometry: wetlandRectangles.features[0].geometry,
    // };

    // // Create GeoJSON layer for remaining wetlands
    // const remainingWetlands = {
    //   type: "Feature",
    //   properties: {
    //     fill: "#333333",
    //     "fill-opacity": 0.4,
    //     stroke: "#333333",
    //     "stroke-width": 2,
    //   },
    //   geometry: wetlandRectangles.features[1].geometry,
    // };

    // // Construct the overlay parameter
    // const geojsonOverlay = encodeURIComponent(
    //   JSON.stringify({
    //     type: "FeatureCollection",
    //     features: [originalWetlands, remainingWetlands],
    //   })
    // );

    // // Construct the Mapbox Static Image URL
    // const baseUrl = "https://api.mapbox.com/styles/v1";
    // const token = import.meta.env.VITE_MAPBOX_TOKEN;

    // imageUrl = `${baseUrl}/${style}/static/geojson(${geojsonOverlay})/[${bbox.join(",")}]/${width}x${height}?padding=50&attribution=false&logo=false&access_token=${token}`;
  } else {
    imageUrl = "assets/map-750x525.jpeg";
  }
</script>

<div class="map-container">
  <img
    src={imageUrl}
    alt="Map showing historical wetland loss in the United States"
    {width}
    {height}
  />
</div>

<style>
  .map-container {
    position: relative;
    width: 100%;
    max-width: 800px;
    margin: 0 auto;
  }

  img {
    width: 100%;
    height: auto;
    display: block;
  }

  .legend {
    position: absolute;
    bottom: 20px;
    right: 20px;
    background: white;
    padding: 10px;
    border-radius: 4px;
    box-shadow: 0 1px 4px rgba(0, 0, 0, 0.2);
  }

  .legend-item {
    display: flex;
    align-items: center;
    margin: 5px 0;
  }

  .color-box {
    width: 20px;
    height: 20px;
    margin-right: 8px;
    border: 1px solid #ccc;
  }

  .color-box.original {
    background-color: rgba(84, 134, 135, 0.3);
  }

  .color-box.remaining {
    background-color: rgba(51, 51, 51, 0.3);
    border-style: dashed;
  }
</style>
