<script lang="ts">
    import * as Accordion from "$lib/components/ui/accordion"
	import AvailabilityContent from "./content/availability-content/availability-content.svelte";
	import BrandContent from "./content/Brand/brand-content.svelte";
    import CategoriesContent from "./content/categories-content/categories-content.svelte";
	import ColorContent from "./content/color-content/color-content.svelte";
	import FeaturedProductsContent from "./content/featuredProducts-content/featuredProducts-content.svelte";
	import MoreFiltersContent from "./content/moreFilters-content/moreFilters-content.svelte";
    import PriceContent from "./content/price-content/price-content.svelte";
	import ProductTypeContent from "./content/productType-content/productType-content.svelte";
	import SizeContent from "./content/size-content/size-content.svelte";

    //Props
    export let accordionTitle: string;

    // Define all possible values that should be open by default
    const defaultOpenItems = ["item-1", "item-2", "item-3", "item-4", "item-5", "item-6", "item-7", "item-8", "item-9"];
</script>

<Accordion.Root class="w-full sm:max-w-[95%]" multiple={true} value={defaultOpenItems}>
    <!-- Categories -->
    {#if accordionTitle === "Categories"}
        <Accordion.Item value="item-1">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <CategoriesContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}

    <!-- Price -->
    {#if accordionTitle === "Price"}
        <Accordion.Item value="item-2">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <PriceContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}
    
    <!-- Brand -->
    {#if accordionTitle === "Brand"}
        <Accordion.Item value="item-3">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <BrandContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}

    <!-- Product Type -->
    {#if accordionTitle === "Product Type"}
        <Accordion.Item value="item-4">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <ProductTypeContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}

    <!-- Availability -->
    {#if accordionTitle === "Availability"}
        <Accordion.Item value="item-5">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <AvailabilityContent/>   
            </Accordion.Content>
        </Accordion.Item>
    {/if}

    <!-- Color -->
    {#if accordionTitle === "Color"}
        <Accordion.Item value="item-6">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <ColorContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}

    <!-- Size -->
    {#if accordionTitle === "Size"}
        <Accordion.Item value="item-7">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <SizeContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}

    <!-- More Filters -->
    {#if accordionTitle === "More Filters"}
        <Accordion.Item value="item-8">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <MoreFiltersContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}

    <!-- Featured Products -->
    {#if accordionTitle === "Featured Products"}
        <Accordion.Item value="item-9">
            <Accordion.Trigger>{accordionTitle}</Accordion.Trigger>
            <Accordion.Content>
                <FeaturedProductsContent />
            </Accordion.Content>
        </Accordion.Item>
    {/if}
</Accordion.Root>