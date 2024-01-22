<script lang="ts">
	import RansomFont from "./lib/RansomFont.svelte";
	import { onMount } from "svelte";
	import { fly, scale } from "svelte/transition";
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
</script>

<main>
	<header>
		<div>
			<a href="/" class="link">THINH NGUYEN</a>
			<h4>
				A PORTFOLIO MADE BY <a href="https://svelte.dev">SVELTE</a>,
				<a href="https://vitejs.dev">VITE</a>
				AND <a href="https://bun.sh">BUN</a>
			</h4>
			<a href="mailto:contact@thinis.de" class="link">CONTACT</a>
		</div>
		<div>
			<RansomFont input={text} />
		</div>
		<div>
			<a href="https://thinis.de" class="link"> thinis.de </a>
			<h4>SCROLL DOWN TO VIEW MORE</h4>
			<a href="https://github.com/CutieCat6778/portfolio" class="link"> SOURCE </a>
		</div>
	</header>

	<section>
		<div bind:this={targetDivs[0]} class={"content"}>
			{#if isVisible[0]}
				<div class="content-text">
					<div class="action-menu">
						<span></span>
						<span></span>
						<span></span>
					</div>
					<div
						class="note-window"
						transition:scale={{
							delay: 1000,
							duration: 800,
							opacity: 0,
							easing: quintOut,
						}}
					>
						<div class="action-menu">
							<span></span>
							<span></span>
							<span></span>
						</div>
						<h3 class="first-h3">
							I'm a self-taught web developer who's been working
							with Typescript and GoLang for over four years. It's
							my go-to language, and I've used it extensively in
							various projects that you can check out on my <a
								href="https://github.com/CutieCat6778">GitHub</a
							>.<br /><br />
							If you want to contact to me, you can email to
							<a href="mailto:contact@thinis.de"
								>contact@thinis.de</a
							>
						</h3>
					</div>
					<div style="opacity:0;">a</div>
				</div>
				<img
					src="/2.png"
					alt="1.png"
					transition:fly={{
						delay: 600,
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

<svg id="filter2" style="display: none;opacity: 0.5;">
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
		widows: 100%;
	}

	header {
		height: 50%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		filter: url("#noise");
		flex-direction: column;
		widows: 100%;
		padding-left: 1rem;
		padding-right: 1rem;
	}

	header > div {
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		text-align: center;
	}

	header > div:nth-child(2) {
		justify-content: center;
	}

	header > div:last-child > a:first-child {
		font-family: "Libre Barcode 128", system-ui;
		text-decoration: none;
		font-size: 4rem;
		width: fit-content;
	}

	header > div:last-child > a:last-child {
		font-size: 1.6rem;
		text-decoration: none;
		width: fit-content;
	}

	section {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 50%;
	}

	section > div.content {
		display: flex;
		justify-content: center;
		align-items: flex-end;
		margin-top: 3rem;
		background-color: var(--color-red2);
		width: 80%;
		height: 80%;
		border-radius: 1rem;
		box-shadow: 0rem 0rem 3rem 1rem #1a1a1a;
		position: relative;
	}

	div.content-text {
		height: 100%;
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
	}

	div.action-menu {
		display: flex;
		justify-content: flex-start;
		align-items: center;
		order: 0;
		width: 90%;
		margin-top: 0.8rem;
		padding-left: 1rem;
		height: min-content;
		margin-right: auto;
	}

	div.action-menu > span {
		height: 1rem;
		width: 1rem;
		display: flex;
		justify-content: center;
		align-items: center;
		color: #111;
		font-family: "Courier New", Courier, monospace;
		border-radius: 100%;
		opacity: 0.6;
		box-shadow: 0rem 0rem 1rem 0.1rem #111111ce;
	}

	div.action-menu > span:hover {
		opacity: 1;
	}

	div.action-menu > span:first-child {
		background-color: var(--color-green);
		margin-right: 0.3rem;
	}

	div.action-menu > span:nth-child(2) {
		background-color: var(--color-red);
		margin-right: 0.3rem;
	}

	div.action-menu > span:last-child {
		background-color: var(--color-yellow);
	}

	h3.first-h3 {
		margin-right: 1rem;
		max-width: 40vw;
		font-size: 1.2rem;
		font-family: "Times New Roman", Times, serif;
		text-align: left;
		border-radius: 1rem;
		padding-left: 5%;
	}

	div.note-window {
		background-color: var(--color-yellow2);
		border-radius: 1rem;
		box-shadow: 0.5rem 0.5rem 1rem 0.3rem #11111148;
		z-index: 1;
		width: 100%;
		margin-left: 1rem;
		max-width: 40rem;
	}

	a {
		color: var(--font-color);
		
	}
	
	a.link {
		text-decoration: none;
		font-size: 1.5rem;
		font-weight: bold;
	}

	div.content > img {
		filter: none;
		padding-top: 1rem;
	}

	@media only screen and (max-width: 1280px) {
		h3.first-h3 {
			padding-left: 1rem;
			padding-right: 1rem;
		}

		header > div:nth-child(2) {
			flex-direction: column;
		}

		header > div a.link {
			display: none;
		}

		header > div {
			justify-content: center;
			align-items: center;
		}

		section > div.content {
			width:98%;
			height: 70%;
		}

		section > div.content > div.content-text {
			width: 100%;
			align-items: center;
			justify-content: space-between;
			margin-left: 0;
			z-index: 1;
			height: 100%;
		}

		section > div.content > div.content-text:last-child {
			display: none;
		}

		section > div.content > div.content-text > div.note-window {
			width: 90%;
			background-color: rgb(136, 123, 67, 0.95);
		}
	}

	@media only screen and (max-width: 870px) {
		div.content > img {
			display: none;
		}

		div.content > div.content-text > div.note-window {
			margin-top: 0;
			margin: 0;
		}

		div.content > div.content-text > div.note-window > h3.first-h3 {
			text-align: center;
			max-width: 90%;
		}
	}

	@media only screen and (max-width: 480px) {
		header > div h4 {
			font-size: 0.8rem;
		}

		h3.first-h3 {
			max-width: 90%;
		}
	}
</style>
