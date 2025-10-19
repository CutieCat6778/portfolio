<script lang="ts">
	import { onMount } from "svelte";

	onMount(() => {
		const scrollText = document.getElementById('scroll-down');

		window.addEventListener('scroll', () => {
			// Calculate how far we've scrolled relative to the hero section
			const scrollY = window.scrollY;
			const heroHeight = window.innerHeight;

			// Fade out from 0 to heroHeight
			const opacity = Math.max(1 - scrollY / heroHeight, 0);
			scrollText.style.opacity = opacity;
		});
	})
</script>


<main class="w-full dark flex flex-col items-center">
	<section class="w-full min-h-screen flex flex-col justify-center items-center text-center sm:text-left relative">
		<div class="sm:w-[40rem] xl:w-[40vw]">
			<h1 class="text-[3rem] xl:text-[3vw] font-serif leading-10">
				Everyday is problem solving
			</h1>
			<h2 class="mt-4">
				<span class="font-bold text-[1rem] xl:text-[1vw] text-neutral-50 uppercase">
					Thinh Nguyen
				</span> – Student in Information Engineering in Germany
			</h2>
		</div>

		<p class="sm:w-[40rem] xl:w-[40vw] mt-4 px-2 sm:px-0 line-clamp-6">
			I build intelligent systems that bridge hardware and software — from sensors and embedded devices to full-stack applications. People know me for turning complex technical ideas into working, real-world solutions.
		</p>
		<h3 id="scroll-down" class="absolute bottom-0">Scroll down!</h3>
	</section>

	<section class="mt-[4vw] flex flex-col justify-center items-center">
		<img src="https://avatars.githubusercontent.com/u/51492960?v=4" class="w-[20rem] rounded-full"/>
		<h1 class="font-serif text-[2rem] xl:text-[2vw] text-center mt-4">Thinh Nguyen</h1>
		<p class="sm:w-[30rem] xl:w-[30vw] mt-4 px-2 sm:px-0 line-clamp-6 text-center">
			I’m {new Date().getFullYear() - 2006} years old, originally from Vietnam and currently living in Villingen-Schwenningen, Germany. I speak Vietnamese, German, Englisch, and Bulgarian fluently. Currently I'm stilling visting school and this is my final year to graduate. 
		</p>
	</section>

	<section class="w-full flex justify-center mt-12 px-4 sm:px-0">
		<div class="sm:w-[40rem] xl:w-[40vw] text-left">
			<h2 class="text-2xl font-serif mb-6">Contacts</h2>

			<div class="mb-6 pl-6">
				<h3 class="text-lg hover:underline">
					<a href="mailto:thinhnguyenhuuhung@gmail.com">
						• thinhnguyenhuuhung@gmail.com
					</a>
				</h3>
			</div>

			<div class="mb-6 pl-6">
				<h3 class="text-lg hover:underline">
					<a href="https://github.com/CutieCat6778">
						• github.com/CutieCat6778	
					</a>
				</h3>
			</div>

			<div class="mb-6 pl-6">
				<h3 class="text-lg hover:underline">
					<a href="http://linkedin.com/in/thinis.de">
						• linkedin.com/in/thinis.de	
					</a>
				</h3>
			</div>
		</div>
	</section>

	<section class="w-full flex justify-center mt-12 px-4 sm:px-0">
		<div class="sm:w-[40rem] xl:w-[40vw] text-left">
			<h2 class="text-2xl font-serif mb-6">Practical Experience</h2>

			<div class="mb-8">
				<a class="font-semibold text-lg hover:underline" href="https://github.com/orgs/FTS-SIA-HFU-24-25/repositories" target="_blank">
					Vital Tracking Vest, Furtwangen University • Project Manager / Developer ↗
				</a>
				<p class="text-sm text-neutral-400 mb-2">(09/2024) – (07/2025)</p>
				<p>
					I led a team in developing a vital-tracking vest that collects ECG data, body temperature, and movement data, sending it to a back-end server for analysis. The collected data is visualized in real time on a website. The project achieved an outstanding result and received a perfect score from the Abitur examiners as part of the “Special Academic Achievement” program.
				</p>
			</div>

			<div class="mb-8">
				<h3 class="font-semibold text-lg">
					Gleason GmbH, Eisenbach • Internship – System Administrator
				</h3>
				<p class="text-sm text-neutral-400 mb-2">(07/2022) – (08/2022)</p>
				<p>
					During my internship, I set up a monitoring server that tracks company servers. The system monitors disk usage, server status, and other key metrics, and automatically sends email notifications when irregularities occur to enable quick troubleshooting.
				</p>
			</div>

			<div>
				<h3 class="font-semibold text-lg">
					Helios Ventilatoren GmbH, VS-Schwenningen • Internship – DevOps
				</h3>
				<p class="text-sm text-neutral-400 mb-2">(07/2021) – (08/2021)</p>
				<p>
					I built a high-performance server with CPU, GPU, storage, and memory, and installed a Linux server distribution (Proxmox). I then configured Kubernetes and Docker to host a web server with a load balancer and reverse proxy. Additionally, I set up a firewall to protect against DDoS attacks and deployed the server via the company’s public IP address.
				</p>
			</div>
		</div>
	</section>

	<section class="w-full flex justify-center my-24 px-4 sm:px-0">
		<div class="sm:w-[40rem] xl:w-[40vw] text-left">
			<h2 class="text-2xl font-serif mb-6">Education</h2>

			<div class="mb-6">
				<h3 class="font-semibold text-lg">
					Abitur – Feintechnikschule, Villingen-Schwenningen, Germany
				</h3>
				<p class="text-sm text-neutral-400">(2023) – (2026)</p>
			</div>

			<div class="mb-6">
				<h3 class="font-semibold text-lg">
					Realschulabschluss – Bickebergschule, Villingen-Schwenningen, Germany
				</h3>
				<p class="text-sm text-neutral-400">(2019) – (2023)</p>
			</div>

			<div>
				<h3 class="font-semibold text-lg">
					Mittlere Reife – Sofia Mathematical Gymnasium, Sofia, Bulgaria
				</h3>
				<p class="text-sm text-neutral-400">(2017) – (2019)</p>
			</div>
		</div>
	</section>
</main>
