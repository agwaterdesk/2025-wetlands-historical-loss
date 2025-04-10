<span class="legend-wrapper column"
  ><span class="legend-item"
    ><span class="original-wetlands-leg"></span> Equivalent area of 1780s wetlands</span
  ><span class="legend-item"
    ><span class="remaining-wetlands-leg"></span> Equivalent area of 1980s wetlands</span
  ></span
>

<style>
  span.legend-wrapper {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    margin: 0rem 0px 1rem;
    border-radius: 4px;

    &.column {
      flex-direction: column;
      align-items: flex-start;

      .legend-item {
        display: grid;
        grid-template-columns: 40px 1fr;
        align-items: center;
        justify-items: end;
        gap: 0.5rem;

        .original-wetlands-leg {
          width: 40px;
          height: 20px;
          background-color: #f1b82daa;
          border: 1px solid #f1b82d;
        }

        .remaining-wetlands-leg {
          width: 30px;
          height: 10px;
          background-color: #66666650;
          border: 1px solid #666666;
        }
      }
    }
  }
</style>
