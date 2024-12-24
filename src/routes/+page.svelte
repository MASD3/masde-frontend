<script lang="ts">
	import MainHeader from "../components/MainHeader.svelte";
	import ProjectCard from "../components/ProjectCard.svelte";
	import AuthorCard from "../components/AuthorCard.svelte";

	let projects = [
		{ title: "Authorization for MASD3", owner: "Kazuya", description: "A cool project by Kazuya", link: "projects/authorization" },
		{ title: "Project 2", owner: "Kohta", description: "A cool project by Kohta", link: "https://google.com" },
		{ title: "Project Display Page", owner: "Owen", description: "A cool project by Owen", link: "projects/DisplayPage" },
		{ title: "Filler project 2", owner: "Owen", description: "A cool project by Owen", link: "https://google.com" },
		{ title: "Filler project 3", owner: "Owen", description: "A cool project by Owen", link: "https://google.com" },
		{ title: "Filler project 4", owner: "Owen", description: "A cool project by Owen", link: "https://google.com" },
		{ title: "Filler project 5", owner: "Owen", description: "A cool project by Owen", link: "https://google.com" }

	];

	let authors: Record<string, {skills: string[]; interests: string[]}> = {
		Kazuya: {skills : ["Go", "Full Stack"], interests: ["Cybersecurity", "Cryptography"]},
		Kohta: {skills : ["AutoCAD", "Fusion 360"], interests: ["Boats", "Cooking"]},
		Owen: {skills : ["Python", "SQL"], interests: ["Databases", "Data Analytics"]}
	}

	let selectedOwner = "";

	function filterProjects(owner:string) {
		selectedOwner = owner;
	}

	
</script>

<MainHeader />

<div>
	<h1>Our Projects</h1>
	<div>
		<button on:click={() => filterProjects("")}>All</button>
		<button on:click={() => filterProjects("Kazuya")}>Kazuya</button>
		<button on:click={() => filterProjects("Kohta")}>Kohta</button>
		<button on:click={() => filterProjects("Owen")}>Owen</button>
	</div>

	<div class="layout">
		{#if selectedOwner}
			<div class="author-selection">
				<AuthorCard
					name={selectedOwner}
					skills={authors[selectedOwner]?.skills|| []}
					interests={authors[selectedOwner]?.interests || []}
					/>
			</div>
			{/if}
			<div
			class="project-list"
			class:selected={selectedOwner === ""}
		>
			{#each projects.filter(p => !selectedOwner || p.owner === selectedOwner) as project}
				<ProjectCard
					title={project.title}
					owner={project.owner}
					description={project.description}
					link={project.link}
				/>
			{/each}
		</div>
	</div>	
</div>

<style>

	.layout {
		display: flex;
		align-items: flex-start;
		justify-content: center;
		/* margin-right: 2%; */
		gap: 1rem;
		height: 100vh;
		overflow: hidden;
	}
	.author-selection { 
		width: 40%;
		min-width: 250px;
		position: sticky;
		top: 0;
		background-color: rgb(53,52,51);
		padding: 1rem;
		/* margin-left: 2%; */
		margin-top: 2%;
		box-shadow: 4px,4px,12px rgba(56, 56, 56, 0.1);
	}
	.project-list {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(400, 2fr));
		background-color: rgb(53,52,51);
		gap: 1rem;
		align-items: center;
		margin-top: 2%;
		/* margin-right: 2%; */
		padding: 1rem;
		overflow-y: auto;
		height: 80%;
		width: 90%;
		scroll-snap-type: y mandatory;
	}
	/* .project-list.selected {
		display: flex;
		overflow-x: auto;
		justify-content: center;
		padding: 1rem 0;
		scroll-snap-type: x mandatory;
		height: 80%;
		width: 60%;
	} */
	button {
		margin-right: 0.5rem;
	}
</style>