<script lang="ts">

    //props
    export let productImage_1 : string
    export let productImage_2 : string
    export let productName : string
    export let productPrice : number
    export let priceDiscount : number
    export let productColors : string[]
    export let bundle : boolean

</script>


<div class="">
    <div class="overflow-hidden mb-2">
        <div class="relative">

            <!-- Badges -->
            <div class="badges absolute z-10 left-2 top-2">
                <div class="flex flex-col gap-1">
                    <!-- Discount badge -->
                    {#if priceDiscount != 0}
                        <div class="bg-red-700 px-2 py-[.1rem] w-fit">
                            <p class="text-white text-sm font-bold">-{priceDiscount}%</p>
                        </div>
                    {/if}

                    <!-- Bundle badge -->
                    {#if bundle}
                        <div class="bg-[#69395E] px-2 py-[.1rem]">
                            <p class="text-white text-sm font-bold">Bundle</p>
                        </div>
                    {/if}
                </div>
            </div>

            <!-- Image -->
            <div class="image relative">
                <img src={productImage_1} alt="" class="absolute inset-0 hover:opacity-0 hover:cursor-pointer duration-1000">
                <img src={productImage_2} alt="" class="opacity-0 hover:opacity-100 hover:scale-105 hover:cursor-pointer duration-500">
            </div>
        </div>
    </div>
 
    <!-- Name -->
    <div class="mb-2">
        <p>{productName}</p>
    </div>
    
    <!-- Price -->
    <div class="mb-4">
        {#if priceDiscount === 0}
            <p class="font-bold">${productPrice}</p>
        {:else}
            <div class="flex gap-3">
                <p class="line-through text-gray-400 font-bold">${productPrice}</p>
                <p class="font-bold text-red-700">${productPrice - (priceDiscount/100)*productPrice}</p>
            </div>
        {/if}
    </div>
    
    <!-- Colors -->
    <div>
        <div class="flex gap-2">
            {#each productColors as color}
                <button class={`w-6 h-6 rounded-full ring-1 ring-offset-2 ring-gray-300`} style="background-color: {color};"></button>                
            {/each}
        </div>
    </div>
</div>