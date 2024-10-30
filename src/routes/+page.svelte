<script>
	import SelectMenu from "$lib/components/select-menu/select-menu.svelte";
	import { each } from "svelte/internal";
    import ProductsData from "$lib/data/products-data/productsData.json"
	import ProductCard from "$lib/components/product-card/product-card.svelte";

</script>


<div class="grid grid-cols-6 gap-x-3">
    <div class="side-pane h-screen bg-slate-600 col-span-1">
        
    </div>

    <div class="content h-screen bg-[#FFFFFF] col-span-5">
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
                <div>
                    <SelectMenu
                        menuItems={["Rows", "Col-1", "Col-2", "Col-3", "Col-4"]}
                        placeHolder={"view as"}
                    />
                </div>
                <div class="flex gap-4">
                    <div class="flex gap-2">
                        <p class="flex items-center">Items per page</p>
                        <SelectMenu
                            menuItems={[10,15,20,25,30,50]}
                            placeHolder={10}
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
                <div class="grid grid-cols-4 gap-4 gap-y-16">
                    {#each ProductsData as product}
                        <ProductCard
                            productImage_1={product.product_image_1}
                            productImage_2={product.product_image_2}
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