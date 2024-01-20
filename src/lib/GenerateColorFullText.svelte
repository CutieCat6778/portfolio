<script lang="ts">

    export let input: string;

    const colors = [
		"--color-red",
		"--color-green",
		"--color-blue",
		"--color-yellow",
	];

    function getColor(index: number): string {
        return colors[index % 4];
    }

</script>

{#each input.split("") as char, index}

    <span style="color:var({getColor(index)})" >
        {char}
    </span>

{/each}

<style>

    span {
        margin: 0;
        padding: 0;
        width: min-content;
        height: min-content;
    }

    span:first-child {
        margin-left: 0.2rem;
    }

</style>