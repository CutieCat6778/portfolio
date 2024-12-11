<main class="w-full flex items-center flex-col">
	<nav class="py-2 flex justify-between dark:bg-neutral-800 bg-neutral-300">
		<li class="w-1/3 list-none">
			Portfolio
		</li>
		<li class="list-none">
			<a href="#about">About</a>
		</li>
		<li class="list-none">
			<a href="#experience">Experience</a>
		</li>
		<li class="list-none">
			<a href="#contact">Contact</a>
		</li>
	</nav>
	<header class="flex h-[16rem] items-center justify-between">
		<div class="w-1/2 flex flex-col items-center">
			<div>
				<h1 class="inline sm:mr-1 md:mr-2">Thinh Nguyen</h1>
				<span>
					{new Date().getUTCFullYear()-2006}
				</span>
				<div class="mt-1 text-[0.8rem] dark:text-neutral-200 text-neutral-700 pl-2">
					<li class="flex items-center">
						<svg class="fill-black dark:fill-neutral-200 mr-1" aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true">
							<path d="M8 .25a.75.75 0 0 1 .673.418l1.882 3.815 4.21.612a.75.75 0 0 1 .416 1.279l-3.046 2.97.719 4.192a.751.751 0 0 1-1.088.791L8 12.347l-3.766 1.98a.75.75 0 0 1-1.088-.79l.72-4.194L.818 6.374a.75.75 0 0 1 .416-1.28l4.21-.611L7.327.668A.75.75 0 0 1 8 .25Zm0 2.445L6.615 5.5a.75.75 0 0 1-.564.41l-3.097.45 2.24 2.184a.75.75 0 0 1 .216.664l-.528 3.084 2.769-1.456a.75.75 0 0 1 .698 0l2.77 1.456-.53-3.084a.75.75 0 0 1 .216-.664l2.24-2.183-3.096-.45a.75.75 0 0 1-.564-.41L8 2.694Z"></path>
						</svg>
						Software Developer
					</li>
					<li class="flex items-center">
						<svg class="fill-black dark:fill-neutral-200 mr-1" color="#fff" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m12.596 11.596-3.535 3.536a1.5 1.5 0 0 1-2.122 0l-3.535-3.536a6.5 6.5 0 1 1 9.192-9.193 6.5 6.5 0 0 1 0 9.193Zm-1.06-8.132v-.001a5 5 0 1 0-7.072 7.072L8 14.07l3.536-3.534a5 5 0 0 0 0-7.072ZM8 9a2 2 0 1 1-.001-3.999A2 2 0 0 1 8 9Z"></path></svg>
						Germany
					</li>
					<a href="mailto:thinh@thinis.de" class="flex items-center">
						<svg class="fill-black dark:fill-neutral-200 mr-1" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="M1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25v-8.5C0 2.784.784 2 1.75 2ZM1.5 12.251c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25V5.809L8.38 9.397a.75.75 0 0 1-.76 0L1.5 5.809v6.442Zm13-8.181v-.32a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25v.32L8 7.88Z"></path></svg>
						thinh@thinis.de
					</a>
				</div>
			</div>
		</div>
		<div class="w-1/2 flex justify-center">
			<img class="rounded-lg w-[150px] h-[150px]" src="/profile.jpg" alt="Thinh Nguyen" />
		</div>
	</header>
	<section class="flex flex-col">
		<div>
			<h2 id="about">Short about me</h2>
			<p class="prose-sm mt-1">
				Hi there, my name is Thinh. I'm borned in Ha Tinh, Vietnam. 
				When I was 9 year old, my family moved to Bulgaria and then 
				we stayed there for 4 years. After that, we moved to Germany 
				and I'm currently living there. 	
				<br/>
				I started programming since 5 grade and now I'm going to a specialized
				school that focus on IT. I'm also a photographer and I love to take pictures
				and save the momments
			</p>
			<div class="w-full mt-2">
				<img class="rounded-md w-[500px] h-[300px] object-cover" src="/banner.webp" alt="Thinh Nguyen" />
			</div>
		</div>
		<div class="-mx-4 px-4 py-6 mt-6 bg-neutral-900 text-white dark:bg-neutral-100 dark:text-neutral-800">
			<h2>Programming Languages</h2>
			<div class="w-full flex">
				<div class="w-1/3 text-sm pl-10 mt-2">
					<li>GoLang</li>
					<li>JavaScript</li>
				</div>
				<div class="w-1/3 text-sm pl-10 mt-2">
					<li>TypeScript</li>
					<li>Java</li>
				</div>
			</div>
		</div>
		<div class="mt-6">
			<h2 id="experience">Experience</h2>
			<div class="w-full flex justify-between">
				<div class="text-sm pl-4 mt-2">
					<li class="font-medium"><span class="px-1 mr-1 bg-black text-white rounded-sm dark:bg-neutral-200 dark:text-black font-bold">Intern</span> System Administrator at Gleason Cutting Tools GmbH</li>
					<p class="mt-2 prose-sm text-[0.8rem] pl-2 mb-2">
						As an intern, I gained valuable insights into company development processes by setting up a server to monitor others. It tracks disk usage, server status, and statistics, sending email alerts for irregularities to ensure prompt issue resolution.
					</p>
					<li class="font-medium"><span class="px-1 mr-1 bg-black text-white rounded-sm dark:bg-neutral-200 dark:text-black font-bold">Intern</span> System ADministrator at Helios Ventilatoren GmbH</li>
					<p class="mt-2 prose-sm text-[0.8rem] pl-2 mb-2">
						I built a server with a CPU, GPU, and storage, installed Linux, Kubernetes, and Docker, and configured a web server with a load balancer, reverse proxy, and DDoS protection.
					</p>
				</div>
			</div>
		</div>
	</section>
	<footer class="flex justify-center py-4">
		<div class="flex justify-between w-1/2">
			<a href="https://github.com/CutieCat6778">Github</a>
			<a href="https://stackoverflow.com/users/12344712">Stackoverflow</a>
			<a href="https://linkedin.com/in/thinisde">LinkedIn</a>
		</div>
	</footer>
</main>
