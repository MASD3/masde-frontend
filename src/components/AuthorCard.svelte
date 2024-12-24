<script lang="ts">
	export let name: string;
	export let skills: string[];
	export let interests: string[];
</script>

<div class="author-card">
	<h2>{name}</h2>
	<p><strong>Skills:</strong> {skills.join(", ")}</p>
	<p><strong>Interests:</strong> {interests.join(", ")}</p>
</div>

<style>
	.author-card {
		padding: 1rem;
		border: 1px solid #ccc;
		border-radius: 8px;
		background-color: #46b65b;
		box-shadow: 2px 2px 6px rgba(160, 134, 134, 0.1);
		width: 90%;
    margin-right: 2%;
	}
</style>