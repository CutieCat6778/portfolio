<script lang="ts">
	import { fly } from "svelte/transition";
	import { quintOut } from "svelte/easing";
	import { onMount } from "svelte";

	export let input: string;
	export let style: string = "";

	const colors = [
		"--color-red",
		"--color-green",
		"--color-blue",
		"--color-yellow",
	];

	function getColor(index: number): string {
		return colors[index % 4];
	}

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
		observer.observe(targetDiv);

		return () => observer.disconnect();
	});
</script>

<div bind:this={targetDiv}>
	{#each input.split("") as char, index}
		{#if isVisible}
			<span
				transition:fly={{
					x: -200,
					duration: 350,
					delay: 600 + index * 100,
                    opacity: 0,
					easing: quintOut,
				}}
				style="color:var({getColor(index)});opacity:{char == " " ? 0 : 1};{style}"
			>
				{char == " " ? "a" : char}
			</span>
		{/if}
	{/each}
</div>

<style>
	span {
		margin: 0;
		padding: 0;
		width: fit-content;
		height: fit-content;
	}

	span:first-child {
		margin-left: 0.2rem;
	}
</style>
