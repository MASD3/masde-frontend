<script>
	let { title = "masde.dev" } = $props();
</script>

<a href="https://google.com">
	<h1>
		{title}
	</h1>
</a>

<style>
	h1 {
		color: blue;
		text-align: center;
	}
	:hover {
		cursor: pointer;
	}
	a {
		text-decoration: none;
	}
</style>
