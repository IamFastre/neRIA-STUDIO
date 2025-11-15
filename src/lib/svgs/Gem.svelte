<svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
  <mask id="gem-mask">
    <rect
      id="gem-shape"
      x={0} y={0}
      rx={5} ry={5}
      width={50} height={50}
      fill="white"
    />
  </mask>
  <g id="gem" mask="url(#gem-mask)">
    <rect id="gem-bg"    x={0} y={0} width={50}  height={50} />
    <rect id="gem-glint" x={0} y={0} width={100} height={10} />

    <g id="gem-overlay">
      <rect id="gem-shade" x={0}  y={25} width={50}  height={25} />
      <rect id="gem-shade" x={25} y={25} width={25}  height={25} />
      <rect id="gem-hl"    x={0}  y={0}  width={25}  height={25} />
    </g>
  </g>
</svg>

<style lang="scss">
  @use "@/styles/utils.scss" as *;

  svg {
    @include size(min(35dvw, 25dvh));

    &:hover {
      scale: 0.9;

      #gem {
        #gem-glint {
          animation-play-state: running;
        }
      }
    }

    * {
      pointer-events: painted;
      transform-origin: center;
    }

    #gem {
      #gem-bg {
        fill: C(accent);
      }

      #gem-glint {
        fill: white;
        filter: blur(10px);
        animation: glint 2s ease-in-out infinite;
        animation-play-state: paused;
      }

      #gem-overlay {
        rotate: 45deg;
        scale: sqrt(2);

        #gem-hl    { fill: C(secondary); opacity: 0.15; }
        #gem-shade { fill: C(primary);   opacity: 0.075; }
      }
    }
  }

  @keyframes glint {
    0%   { transform: translateY(-70px); }
    20%  { transform: translateY(-10px); }
    80%  { transform: translateY(-10px); }
    100% { transform: translateY(70px);  }
  }
</style>
