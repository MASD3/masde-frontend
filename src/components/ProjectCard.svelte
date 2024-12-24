<script lang="ts">
	export let title: string;
	export let owner: string;
	export let description: string;
	export let link: string;
</script>

<div class="project-card">
	<h2>{title}</h2>
	<p>{description}</p>
	<p><strong>Owner:</strong> {owner}</p>
	<a href={link} target="_blank">View Project</a>
</div>

<style>
	.project-card {
		padding: 1rem;
		border: 1px solid #ccc;
		border-radius: 8px;
		background-color: #46b65b;
	}

	.project-card h2 {
		margin: 0 0 0.5rem;
		font-size: 1.25rem;
	}
</style>