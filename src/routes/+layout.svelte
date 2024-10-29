<script lang="ts">
	import Navbar from '$lib/components/navbar/navbar.svelte';
	import 'remixicon/fonts/remixicon.css'
import '../app.css';
</script>



<div class="max-w-[1850px] mx-auto">
	<Navbar />
</div>

<main class="max-w-[1850px] mx-auto">
	<slot />
</main>