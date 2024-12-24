<script>
	// accept props with default value
	let { title = "masde.dev" } = $props();
</script>

<a href="https://google.com">
	<h1>
		{title}
	</h1>
</a>

<style>
	h1 {
		text-align: center;
		color: green;
	}
	a {
		text-decoration: none;
	}
</style>
