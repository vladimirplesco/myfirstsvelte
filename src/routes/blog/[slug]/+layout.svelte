<script >
    export let data;
</script>
<!-- <h1>Hello {data}!</h1> -->
<div class="layout">
    <main>
	<slot />
    </main>
</div>

<style>
    @media (min-width: 640px) {
	.layout {
	    display: grid;
	    gap: 2em;
	    grid-template-columns: 1fr 16em;
	}
    }
</style>