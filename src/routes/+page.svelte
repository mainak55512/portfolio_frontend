<script lang="ts">
	import { onMount } from 'svelte';
	import { env } from '$env/dynamic/public';
	interface Entity {
		name: string;
		description: string;
		path: string;
		tech: string;
		thumbnail: string;
	}
	interface Blog {
		title: string;
		url: string;
		thumbnail: string;
	}
	var entities: Entity[];
	var blogs: Blog[];
	onMount(async () => {
		let SERVER_URL = env.PUBLIC_SERVER_URL;
		// console.log('Server url: ' + SERVER_URL);
		var response_entity = await fetch(SERVER_URL + '/api/entities');
		const data_entity = await response_entity.json();
		entities = [...data_entity];
		var response_blog = await fetch(SERVER_URL + '/api/blogs');
		const data_blog = await response_blog.json();
		blogs = [...data_blog];
	});
</script>

<div>
	<span class="text-white/30">portfolio.whoAmI(</span>
	<div class="flex flex-col items-center">
		<img alt="Profile Picture" src="/resource/me.jpg" class="h-40 w-40 rounded-full" />
		<h1 class="mt-5 text-center text-5xl font-black text-white/70">Hi👋, I am Mainak!</h1>
		<div class="mt-5 h-50 w-200 text-center text-white/45">
			Results-driven ServiceNow Developer with hands-on expertise in JavaScript, UI Builder, Service
			Portal (AngularJS), and REST API integrations. Demonstrated success in designing intuitive
			user interfaces, automating workflows, and integrating third-party tools to streamline
			business processes. Committed to delivering high-performance, scalable, and user-centric
			ServiceNow solutions with a strong focus on system efficiency and user experience.
		</div>
	</div>
	<div class="flex flex-col items-end">
		<span class="text-right text-white/30">).then(resp &Rightarrow; &lcub;</span><br />
	</div>
	<span class="text-white/30">let getMyProjects = () &Rightarrow; &lcub;</span>

	<h1 class="mt-5 ml-5 text-left text-3xl font-black text-white/70">Projects</h1>

	<div class="grid grid-cols-4 gap-4">
		{#each entities as entity}
			<a
				class="isolate m-5 flex h-70 grow-1 flex-col rounded-xl bg-white/20 p-5 text-start text-white shadow-lg ring-1 ring-black/5 backdrop-blur-md"
				href={entity.path}
				target="_blank"
				rel="noopener noreferrer"
				data-sveltekit-reload
			>
				<div class="h-20">
					<div class="text-lg font-semibold">{entity.name}</div>
					<div class="text-xs text-white/50">{entity.description}</div>
				</div>
				<img alt={entity.name} src={entity.thumbnail} class="h-40 w-90 rounded-lg" />
			</a>
		{/each}
	</div>
	<span class="text-white/30">};</span><br />
	<span class="text-white/30">const my_blogs = &lcub;</span>
	<h1 class="mt-5 ml-5 text-left text-3xl font-black text-white/70">Blogs</h1>
	<div class="grid grid-cols-4 gap-4">
		{#each blogs as blog}
			<a
				class="isolate m-5 flex h-70 grow-1 flex-col rounded-xl bg-white/20 p-5 text-start text-white shadow-lg ring-1 ring-black/5 backdrop-blur-md"
				href={blog.url}
				target="_blank"
				rel="noopener noreferrer"
				data-sveltekit-reload
			>
				<div class="h-20">
					<div class="text-lg font-semibold">{blog.title}</div>
					<!-- <div class="text-xs text-white/50">{entity.description}</div> -->
				</div>
				<img alt={blog.title} src={blog.thumbnail} class="h-40 w-90 rounded-lg" />
			</a>
		{/each}
	</div>
	<div class="flex flex-col justify-center">
		<span class="text-right text-white/30">};</span><br />
	</div>
	<span class="text-white/30">return [</span>
	<div class="flex justify-center">
		<div class="flex flex-row">
			<a
				href="https://github.com/mainak55512"
				target="_blank"
				rel="noopener noreferrer"
				data-sveltekit-reload
				><img alt="placeholder" src="/resource/github.png" class="m-2 h-8 w-8 rounded-lg" /></a
			>
			<a
				href="https://www.linkedin.com/in/mainak-bhattacharjee-10773923a"
				target="_blank"
				rel="noopener noreferrer"
				data-sveltekit-reload
				><img alt="placeholder" src="/resource/linkedin.png" class="m-2 h-8 w-8 rounded-lg" /></a
			>
		</div>
	</div>
	<div class="flex flex-col justify-center">
		<span class="text-right text-white/30">]});</span>
	</div>
</div>
