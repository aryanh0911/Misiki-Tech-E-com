<script lang="ts">
	import SelectMenu from "$lib/components/select-menu/select-menu.svelte";
    import ProductsData from "$lib/data/products-data/productsData.json"
	import ProductCard from "$lib/components/product-card/product-card.svelte";
	import Accordion from "$lib/components/accordion/accordion.svelte";
    
    const sidePaneElements = [
        {item: "Categories"},
        {item: "Price"},
        {item: "Brand"},
        {item: "Product Type"},
        {item: "Availability"},
        {item: "Color"},
        {item: "Size"},
        {item: "More Filters"},
        {item: "Featured Products"},
    ]

    let viewAs = "Col-4";
    function handleViewAs(value : string | number){
        viewAs = String(value);
    }

</script>


<div class="flex gap-x-3">

    <!-- Side Panel -->
    <div class="side-pane h-screen bg-slate-300 pt-8 min-w-[250px] flex-none">
        <div>
            <div class="pl-3 flex flex-col justify-center items-start">
                {#each sidePaneElements as element}
                    <Accordion
                        item={element.item}
                    />
                {/each}
            </div>
        </div>
    </div>

    <div class="content h-screen bg-[#FFFFFF] flex-grow">
        <section class="banner mb-6">
            <div class="flex justify-center overflow-hidden mb-4">
                <img src="/images/banner.webp" alt="" class="object-cover w-full hover:scale-105 duration-500 hover:cursor-pointer">
            </div>
            <div>
                <h1 class="mb-3 text-2xl font-bold text-gray-700">Cosmopolis</h1>
                <p class="text-gray-700">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Aliquam possimus quidem soluta laboriosam porro! Tenetur ullam aperiam iusto quaerat exercitationem!</p>
            </div>
        </section>

        <hr class="h-[.1rem] bg-gray-200">

        <section class="products mt-8">
            <header class="flex justify-between pr-3 mb-4">
                <div class="view-as">
                    <SelectMenu 
                        menuItems={["Rows", "Col-2", "Col-3", "Col-4"]}
                        placeHolder={"view as"}
                        onValueChange={handleViewAs}
                    />
                </div>
                <div class="flex gap-4">
                    <div class="flex gap-2">
                        <p class="flex items-center">Items per page</p>
                        <SelectMenu
                            menuItems={[10,15,20,25,30,50]}
                            placeHolder={"10"}
                        />
                    </div>
                    <div class="flex gap-2">
                        <p class="flex items-center">Sort By</p>
                        <SelectMenu
                            menuItems={["Featured", "Best Selling", "Alphabetically, A-Z", "Alphabetically, Z-A", "Price, low to high", "Price, high to low", "Date, old to new", "Date, new to old"]}
                            placeHolder={"Featured"}
                        />
                    </div>
                </div>
            </header>
            
            <div class="products-content p-4 mb-24">
                <div class={`grid gap-4 gap-y-16
                    ${
                        viewAs === "Rows"? "grid-cols-1" :
                        viewAs === "Col-2"? "grid-cols-2" :
                        viewAs === "Col-3"? "grid-cols-3" :
                        viewAs === "Col-4"? "grid-cols-4" :
                        "grid-cols-4" //default fallback
                    }
                `}
                >
                    {#each ProductsData as product}
                        <ProductCard
                            productImages={product.product_images}
                            productName={product.product_name}
                            productPrice={product.product_price}
                            priceDiscount={product.price_discount_percent}
                            productColors={product.product_colors}
                            bundle={product.bundle}
                        />
                    {/each}
                </div>
            </div>
        </section>
    </div>
</div>

