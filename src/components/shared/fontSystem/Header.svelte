<h1>
  <slot />
</h1>

<style>
  h1 {
    font-weight: 700;
    font-size: 26px;
    line-height: 38px;
    color: hsl(120, 100%, 97%);
    background: url("/images/glitter.gif");
    animation: filter-animation 4s infinite;
  }

  @keyframes filter-animation {
    0% {
      filter: hue-rotate(0deg);
    }

    50% {
      filter: hue-rotate(360deg);
    }

    100% {
      filter: hue-rotate(0deg);
    }
  }
</style>
