<script>

	/**
	 * @type {any}
	 */
	 export let segment;
</script>

<style>
	main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
	li{
		text-decoration: none;
		list-style-type: none;
	}
</style>

<ul class="navigation row">
	<li class="m-2 col-2">
		<a class="" href="about">about</a>
	</li>
	<li class="m-2 col-2">
		<a href="contacts">contacts</a>
	</li>
	<li class="m-2 col-2">
		<a href="services">services</a>
	</li>
</ul>

<main>
	<slot></slot>
</main>