<script lang="ts">

    //props
    export let productImages : string[]
    export let productName : string
    export let productPrice : number
    export let priceDiscount : number
    export let productColors : string[]
    export let bundle : boolean

    //States to track currently selected color and image
    let selectedColor = productColors[0];
    let currentImageIndex = 0;
    let randomImageIndex = 0;

    //Function to generate randomImageIndex different from currentImageIndex
    function getRandomImageIndex(currentIndex : number) : number {
        //if there's only one image, return the same index
        if(productImages.length <= 1) return currentIndex;

        //Get random image index that's different from current
        let newIndex
        do{
            newIndex = Math.floor(Math.random() * productImages.length);
        } while(newIndex === currentIndex)

        return newIndex;
    }

    //Set initial randomImageIndex
    $: randomImageIndex = getRandomImageIndex(currentImageIndex);

    //Function to handle color selection
    function handleColorSelection(color : string, index : number){
        selectedColor = color;
        currentImageIndex = index;

        //Get new random image whenever color changes
        randomImageIndex = getRandomImageIndex(index);
    }


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
                <img src={productImages[currentImageIndex]} alt="" class="absolute inset-0 hover:opacity-0 hover:cursor-pointer duration-1000">
                <img src={productImages[randomImageIndex]} alt="" class="opacity-0 hover:opacity-100 hover:scale-105 hover:cursor-pointer duration-500">
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
            {#each productColors as color, index}
                <button class={`w-6 h-6 rounded-full ring-1 ring-offset-2 ${(selectedColor == color)? "ring-gray-800" : "ring-gray-300"}`} style="background-color: {color};"
                    on:click={()=> handleColorSelection(color, index)}
                >
                </button>                
            {/each}
        </div>
    </div>
</div>