<script>
	import Component1 from "./Component1.svelte";
	import Component2 from "./Component2.svelte";

</script>

<main>
	<section>
	<Component1></Component1>
	<!-- <Component2></Component2>	 -->
	</section>
</main>

<style>
	section {
    width: 100%;
    height: 100%;
	display: flex;
	flex-direction: row;
    /* margin-left: auto;/take component to the left */

	}



	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>