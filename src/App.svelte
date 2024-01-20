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
		<div bind:this={targetDivs[0]} class="title">
			{#if isVisible[0]}
				<h1
					transition:fly={{
						delay: 600,
						duration: 800,
						x: -100,
						opacity: 0,
						easing: quintOut,
					}}
				>
					What's up!
				</h1>
				<h2
					transition:fly={{
						delay: 1000,
						duration: 800,
						x: -100,
						opacity: 0,
						easing: quintOut,
					}}
				>
					My name is <GenerateColorFullText input="Thinh Nguyen" />
				</h2>
			{/if}
		</div>
		<div bind:this={targetDivs[1]} class={"content"}>
			{#if isVisible[1]}
				<h3
					transition:fly={{
						delay: 1000,
						duration: 800,
						x: -100,
						opacity: 0,
						easing: quintOut,
					}}
				>
					This is under construction 👷🚧
				</h3>
				<h3
					transition:fly={{
						delay: 1200,
						duration: 800,
						x: -100,
						opacity: 0,
						easing: quintOut,
					}}
				>
					This is under construction 👷🚧
				</h3>
			{/if}
		</div>
	</section>
</main>

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
	main {
		height: 200%;
		z-index: 1;
	}

	header {
		height: 50%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	section {
		display: flex;
		align-items: center;
		flex-direction: column;
		margin-top: 3rem;
	}

	section div h1 {
		font-size: 3rem;
		margin: 0;
	}

	section div h2 {
		margin: 0;
	}

	section div.title {
		text-align: center;
	}

	section div.content {
		display: flex;
		justify-content: space-around;
		align-items: center;
		width: 100%;
	}

	section div.content:first-child {
		margin-right: 1rem;
	}
</style>
