<script lang="ts">
	import { page } from "$app/stores";
	import { marked } from "marked";
	import { onMount } from "svelte";

	let markdownContent = "";
	let slug = "";

	// Load the Markdown file
	onMount(async () => {
		slug = $page.params.slug;
		try {
			const response = await fetch(`/markdown/${slug}.md`);
			markdownContent = await response.text();
		} catch (error) {
			markdownContent = "# File not found\nPlease ensure the markdown file exists.";
		}
	});
</script>

<article class="markdown">
	{@html marked(markdownContent)}
</article>
<style>
.markdown {
  font-family: "Georgia", serif; /* A classic font for readability */
  line-height: 1.6;
  color: #333; /* Dark gray for text */
  max-width: 800px; /* Limit width for better readability */
  margin: 2rem auto;
  padding: 1rem;
  background: #fff; /* White background for clarity */
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.markdown :global(h1),
.markdown :global(h2),
.markdown :global(h3),
.markdown :global(h4),
.markdown :global(h5),
.markdown :global(h6) {
  font-weight: bold;
  margin-top: 1.5em;
  color: #2c3e50; /* A rich dark blue */
}

.markdown :global(h1) {
  font-size: 2rem;
  border-bottom: 2px solid #e74c3c; /* Add a line under H1 for emphasis */
  padding-bottom: 0.5rem;
}

.markdown :global(h2) {
  font-size: 1.75rem;
}

.markdown :global(h3) {
  font-size: 1.5rem;
}

.markdown :global(p) {
  margin: 1em 0;
}

.markdown :global(a) {
  color: #3498db; /* Bright blue for links */
  text-decoration: none;
  transition: color 0.3s;
}

.markdown :global(a:hover) {
  color: #2980b9; /* Darker blue on hover */
}

.markdown :global(ul),
.markdown :global(ol) {
  padding-left: 2rem; /* Indent lists */
  margin: 1em 0;
}

.markdown :global(ul) {
  list-style-type: disc; /* Bulleted list */
}

.markdown :global(ol) {
  list-style-type: decimal; /* Numbered list */
}

.markdown :global(li) {
  margin: 0.5em 0;
}

.markdown :global(blockquote) {
  border-left: 4px solid #e67e22; /* Orange bar for blockquotes */
  padding-left: 1rem;
  color: #7f8c8d; /* Light gray for blockquote text */
  font-style: italic;
  margin: 1em 0;
}

.markdown :global(code) {
  font-family: "Courier New", monospace;
  background: #f4f4f4;
  padding: 0.2em 0.4em;
  border-radius: 4px;
}

.markdown :global(pre) {
  background: #2d2d2d; /* Dark background for code blocks */
  color: #f8f8f2; /* Light text for contrast */
  padding: 1rem;
  border-radius: 8px;
  overflow-x: auto; /* Horizontal scroll for long code lines */
}

.markdown :global(img) {
  max-width: 100%;
  height: auto;
  margin: 1rem 0;
  border-radius: 8px;
}

.markdown :global(table) {
  width: 100%;
  border-collapse: collapse;
  margin: 1rem 0;
  background: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.markdown :global(table th),
.markdown :global(table td) {
  border: 1px solid #ddd;
  padding: 0.5rem;
  text-align: left;
}

.markdown :global(table th) {
  background: #f8f9fa; /* Light gray for table headers */
  font-weight: bold;
}

.markdown :global(hr) {
  border: none;
  border-top: 1px solid #ddd;
  margin: 2rem 0;
}
</style>