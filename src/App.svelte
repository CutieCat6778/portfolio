<script lang="ts">

	import RansomFont from "./lib/RansomFont.svelte";

	let text = "HELLO WORLD!";


</script>

<main>

	<RansomFont input={text}/>
</main>

<div class="background"></div>

<style>

	main {
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.background {
		filter: url("#noise");
		width: 100%;
		height: 100%;
		position: absolute;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
		background-color: #111;
		z-index: -1;
	}

</style>

<svg id="filter" style="display: none;opacity: 0.5;">
    <filter id="noise">
      <feTurbulence baseFrequency="0.6" />
      <feColorMatrix in="colorNoise" type="matrix" values=".33 .33 .33 0 0 .33 .33 .33 0 0 .33 .33 .33 0 0 0 0 0 0.66 0"/>
      <feComposite operator="in" in2="SourceGraphic" result="monoNoise"/>
      <feBlend in="SourceGraphic" in2="monoNoise" mode="multiply" />
    </filter>
  </svg>

<svg  id="filter" style="display: none;opacity: 0.5;">
	<filter id="wavy2">
		<feTurbulence x="0" y="0" baseFrequency="0.02" numOctaves="5" seed="1"></feTurbulence>
		<feDisplacementMap in="SourceGraphic" scale="2" />
	</filter>
</svg>