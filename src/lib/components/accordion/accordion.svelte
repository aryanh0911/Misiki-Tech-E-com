<script lang="ts">
    import * as Accordion from "$lib/components/ui/accordion"
	import CategoriesContent from "./content/categories-content/categories-content.svelte";
	import PriceContent from "./content/price-content/price-content.svelte";

    //Props
    export let accordionTitle : string
</script>


<Accordion.Root class="w-full sm:max-w-[95%]" multiple={true}>
  <Accordion.Item value="item-1">
    <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
    <Accordion.Content>
        <!-- Categories -->
         {#if accordionTitle === "Categories"}
            <CategoriesContent />
         {/if}

        <!-- Price -->
         {#if accordionTitle === "Price"}
            <PriceContent />
         {/if}
         
        <!-- Brand -->
         {#if accordionTitle === "Brand"}
            <p>Brand</p>
         {/if}

        <!-- Product Type -->
         {#if accordionTitle === "Product Type"}
            <p>Product Type</p>
         {/if}

        <!-- Availability -->
         {#if accordionTitle === "Availability"}
            <p>Availability</p>
         {/if}

        <!-- Color -->
         {#if accordionTitle === "Color"}
            <p>Color</p>
         {/if}

        <!-- Size -->
         {#if accordionTitle === "Size"}
            <p>Size</p>
         {/if}

        <!-- More Filters -->
         {#if accordionTitle === "More Filters"}
            <p>More Filters</p>
         {/if}

        <!-- Featured Products -->
        {#if accordionTitle === "Featured Products"}
            <p>Featured Products</p>
        {/if}
    </Accordion.Content>
  </Accordion.Item>
</Accordion.Root>