<script>
  import Window from "./components/Window.svelte";
  import Legend from "./components/Legend.svelte";
  import LossMap from "./components/LossMap.svelte";

  // Handle responsive iframes for embeds
  import pym from "pym.js";

  new pym.Child({
    polling: 500,
  });

  function getUrlParameter(name) {
    const params = new URLSearchParams(window.location.search);
    return params.get(name);
  }

  let includeCredit = getUrlParameter("credit") != "false";
</script>

<Window />
<!-- Outer div must have class 'chart-container' don't change -->
<div class="chart-container">
  <h1 class="headline">Visualizing the shrinking footprint of U.S. wetlands</h1>

  <p class="dek">
    More than half of U.S. wetlands have been drained, filled or altered. In the
    1780s, before widespread development and agricultural expansion, the <span
      class="original-wetlands">estimated extent of wetlands</span
    >
    was about 221 million acres, an area that would have stretched from northwest
    Nebraska to southeast Kentucky. Two centuries later, a 1980
    <span class="remaining-wetlands">estimate of remaining wetlands</span> was about
    103 million acres.
  </p>
  <Legend />
  <p class="sr-only">
    Map showing the equivalent land area of U.S. wetlands in the 1780s (in
    orange) and the 1980s (in gray), illustrating a dramatic reduction in
    wetland coverage over time. The comparison is centered over the Midwest,
    spanning from Nebraska to Kentucky.
  </p>

  <div id="g-viz">
    <LossMap />
  </div>

  {#if includeCredit}
    <div class="credit">
      Data: U.S. Fish and Wildlife Service; Graphic by Jared Whalen /
      <a target="_blank" href="https://agwaterdesk.org/">Ag & Water Desk</a><br/>
      <a
        href="https://www.mapbox.com/about/maps/"
        target="_blank"
        title="Mapbox"
        aria-label="Mapbox">© Mapbox</a
      >
      <a
        href="https://www.openstreetmap.org/copyright/"
        target="_blank"
        title="OpenStreetMap"
        aria-label="OpenStreetMap">© OpenStreetMap</a
      >
      <a
        class="mapbox-improve-map"
        href="https://apps.mapbox.com/feedback/?owner=startribune&amp;id=cm8hhq3e6017901s55dfi5dmn&amp;access_token=pk.eyJ1Ijoic3RhcnRyaWJ1bmUiLCJhIjoiY2sxYjRnNjdqMGtjOTNjcGY1cHJmZDBoMiJ9.St9lE8qlWR5jIjkPYd3Wqw#/-92.53/39.55/5.06"
        target="_blank"
        title="Improve this map"
        aria-label="Improve this map"
        rel="noopener nofollow">Improve this map</a
      >
      <a
        href="https://www.maxar.com/"
        target="_blank"
        title="Maxar"
        aria-label="Maxar">© Maxar</a
      >
    </div>
  {/if}
</div>

<style lang="scss">
  .chart-container {
    max-width: 800px;
    width: 100%;
    padding: 0.5rem;

    #g-viz {
      width: 100%;
    }

    .dek {
      span {
      }

      .original-wetlands {
        border-bottom: 2px solid var(--project-color-yellow);
        // border: 2px solid var(--project-color-yellow);
      }

      .remaining-wetlands {
        border-bottom: 2px solid #333333;
        // border: 2px solid #666;
      }
    }
  }
</style>
