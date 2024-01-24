<script lang="ts">
	export let char: string;
	export let num: number;
	export let fontSize: number = 3;

	const colors = [
		"--color-red",
		"--color-green",
		"--color-blue",
		"--color-yellow",
	];

	console.log(fontSize)

	const fonts = [
		"--font-1",
		"--font-2",
		"--font-3",
		"--font-4",
		"--font-5",
		"--font-6",
		"--font-7",
		"--font-7",
		"--font-9",
	];

	function getBackgroundColor() {
		if (char == " ") return;
		const index = num % colors.length;
		const style = `var(${colors[index]})`;
		return style;
	}

	function getFontFamily() {
		if (char == " ") return;
		const index = num % colors.length;
		const style = `var(${fonts[index]})`;
		return style;
	}

	function getRandomNumberInRange(
		min: number,
		max: number,
		defaultNumber: number,
	) {
		const adjustedMin = Math.max(0.01, min);
		const adjustedMax = Math.min(2.0, max);
		const randomNumber =
			adjustedMin +
			Math.random() * (adjustedMax - adjustedMin);
		return randomNumber + defaultNumber;
	}

	function getRandomAngle(min: number, max: number): string {
		const randomAngle =
			Math.random() * (max - min) + min * (Math.random() < 0.3 ? 1 : -1);

		return randomAngle.toFixed(1);
	}

	function getClipPath(): string {
		const shapes = [
			"polygon(0 7%, 82% 2%, 100% 100%, 0% 100%)",
			"polygon(0 0, 100% 4%, 89% 100%, 0% 100%)",
			"polygon(20% 0, 100% 0%, 89% 100%, 0% 100%)",
			"polygon(3% 6%, 98% 0, 85% 50%, 90% 100%, 0% 100%)",
			"polygon(4% 0, 70% 0, 98% 31%, 90% 100%, 0% 100%)",
			"polygon(0 5%, 94% 0, 88% 22%, 100% 100%, 0% 100%)",
			"polygon(100% 0%, 90% 37%, 100% 100%, 0 100%, 0% 50%, 11% 0)",
            "polygon(85% 0, 100% 100%, 10% 100%, 0 19%)",
            "polygon(100% 0, 100% 100%, 0 100%, 25% 13%)",
            "polygon(50% 0%, 90% 0, 100% 75%, 74% 100%, 0 100%, 0 0)",
            "polygon(46% 0, 100% 1%, 100% 100%, 20% 100%, 0% 50%)",
            "polygon(26% 0, 100% 18%, 100% 100%, 12% 100%, 0% 50%)",
            "polygon(11% 0, 100% 4%, 100% 100%, 0 100%, 17% 51%)"
		];
		return shapes[Math.round(Math.random() * shapes.length - 1)];
	}

	function getRandomFontWeight() {
		return (Math.round(Math.random() * 3) + 6) * 100;
	}

	const backgroundColor = getBackgroundColor();
	const angle = getRandomAngle(10, 20);
	const clipPath = getClipPath();
	const fontFamily = getFontFamily();
	const fontS = getRandomNumberInRange(0, 5, fontSize);
	const fontWeight = getRandomFontWeight();
</script>

<span
	style="background-color: {backgroundColor};height: {fontSize * 2.33}rem;width: {fontSize * 1.33}rem;{Math.random() < 0.5
		? `transform: rotate(${angle}deg)`
		: null};clip-path: {clipPath}"
>
	<h1 style="font-family: {fontFamily};font-size: {fontS}rem;font-weight: {fontWeight}">
		{char}
	</h1>
</span>

<style>
	span {
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 0rem;
	}
	h1 {
		margin: 0;
		padding: 0;
		color: #000;
	}
</style>
