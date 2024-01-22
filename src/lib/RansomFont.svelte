<script lang="ts">
	import { scale } from "svelte/transition";
	import RansomChar from "./RansomChar.svelte";
	import { quintOut } from "svelte/easing";
	import { onMount } from "svelte";

	export let input: string;

	let width: number;
	let fontSize = 3;

	let isVisible: boolean = false;
	let targetDiv: Element;

	const handleIntersection = (entries: any) => {
		entries.forEach((entry: any) => {
			isVisible = entry.isIntersecting;
			if (isVisible) observer.disconnect();
		});
	};

	const observer = new IntersectionObserver(handleIntersection, {
		threshold: 0.5,
	});

	onMount(() => {
		if(width < 590) {
			fontSize = (width / 590) * 3;
		}
		if(width) observer.observe(targetDiv);

		return () => observer.disconnect();
	});
</script>

<svelte:window bind:innerWidth={width}/>

{#each input.split(" ") as textArr, key}
	<span bind:this={targetDiv}>
		{#each textArr.split("") as text, key}
			{#if isVisible}
				<span
					id={key + text}
					class="char"
					in:scale={{
						delay: 250 + key * 100,
						duration: 800,
						easing: quintOut,
					}}
				>
					<RansomChar char={text} num={key} fontSize={fontSize} />
				</span>
			{/if}
		{/each}
	</span>
{/each}

<style>
	.char {
		display: inline-block;
		filter: drop-shadow(1rem 1rem 0.8rem rgba(74, 74, 74, 0.5));
		margin: 0.3rem;
	}

	span {
		text-align: center;
		margin-right: 4.32vw;
	}

	span:last-child {
		margin-right: 0;
	}

	@media only screen and (max-width: 1000px) {
		span {
			margin-right: 0;
			display: block;
		}

		span:last-child {
			margin-top: 1rem;
		}
	}
</style>
