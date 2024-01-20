<script lang="ts">
	import RansomFont from "./lib/RansomFont.svelte";
	import { onMount } from "svelte";
	import { fly } from "svelte/transition";
	import { quintOut } from "svelte/easing";
	import GenerateColorFullText from "./lib/GenerateColorFullText.svelte";

	let text = "HELLO WORLD!";

	let isVisible: boolean[] = [];
	let targetDivs: Element[] = [];

	const handleIntersection = (entries: any) => {
		entries.forEach((entry: any, index: number) => {
			if (isVisible[index]) return;
			isVisible[index] = entry.isIntersecting;
		});
	};

	const observer = new IntersectionObserver(handleIntersection, {
		threshold: 0.5,
	});

	onMount(() => {
		for (let targetDiv of targetDivs) {
			console.log(targetDivs);
			observer.observe(targetDiv);
		}

		return () => observer.disconnect();
	});

	console.log(isVisible);
</script>

<main>
	<header>
		<RansomFont input={text} />
	</header>

	<section>
		<div bind:this={targetDivs[0]} class={"content"}>
			{#if isVisible[0]}
				<h3
					class="first-h3"
					transition:fly={{
						delay: 1000,
						duration: 800,
						x: -100,
						opacity: 0,
						easing: quintOut,
					}}
				>
					I'm a self-taught web developer who's been working with
					JavaScript for over four years. It's my go-to language, and
					I've used it extensively in various projects that you can
					check out on my <a href="https://github.com/CutieCat6778">GitHub</a>.<br/><br/>
					If you want to contact to me, you can email to <a href="mailto:contact@thinis.de">contact@thinis.de</a>
				</h3>
				<img
					src="/2.png"
					alt="1.png"
					transition:fly={{
						delay: 1600,
						duration: 800,
						x: -100,
						opacity: 0,
						easing: quintOut,
					}}
				/>
			{/if}
		</div>
	</section>
</main>

<div class="background"></div>

<svg id="filter" style="display: none;opacity: 0.5;">
	<filter id="noise">
		<feTurbulence baseFrequency="0.6" />
		<feColorMatrix
			in="colorNoise"
			type="matrix"
			values=".33 .33 .33 0 0 .33 .33 .33 0 0 .33 .33 .33 0 0 0 0 0 0.66 0"
		/>
		<feComposite operator="in" in2="SourceGraphic" result="monoNoise" />
		<feBlend in="SourceGraphic" in2="monoNoise" mode="multiply" />
	</filter>
</svg>

<svg id="filter" style="display: none;opacity: 0.5;">
	<filter id="wavy2">
		<feTurbulence x="0" y="0" baseFrequency="0.02" numOctaves="5" seed="1"
		></feTurbulence>
		<feDisplacementMap in="SourceGraphic" scale="5" />
	</filter>
</svg>

<style>
	div.background {
		height: 200%;
		width: 100%;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		position: absolute;
		background-color: #111;
		z-index: -1;
		filter: url("#noise");
	}

	main {
		height: 200%;
	}

	header {
		height: 50%;
		display: flex;
		justify-content: center;
		align-items: center;
		filter: url("#noise");
	}

	section {
		display: flex;
		align-items: center;
		flex-direction: column;
		margin-top: 3rem;
	}

	section div.content {
		display: flex;
		justify-content: space-around;
		align-items: center;
		width: 100%;
		margin-top: 3rem;
		background-color: var(--color-red2);
		width: 80%;
		padding-top: 1rem;
		border-radius: 1rem;
		box-shadow: 0rem 0rem 3rem 1rem #1a1a1a;
	}

	div.content h3.first-h3 {
		margin-right: 1rem;
		max-width: 50%;
		filter: url("#noise");
		font-size: 1.4rem;
		font-family: "Times New Roman", Times, serif;
	}

	a {
		color: var(--font-color);
	}

	div.content img {
		filter: none;
		z-index: 1;
	}
</style>
