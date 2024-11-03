<script lang="ts">
    import ProductsData from "$lib/data/products-data/productsData.json"

    const colors = ["red", "gray", "brown", "white", "black"]
</script>


<!-- Colors -->
<div>
    <div class="flex gap-3 flex-wrap p-2">
        {#each colors as color}
            <button class={`w-6 h-6 rounded-full ring-1 ring-offset-2`} style="background-color: {color};">
            </button>                
        {/each}
    </div>
</div>