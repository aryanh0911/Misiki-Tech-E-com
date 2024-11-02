<script lang="ts">
    let minPrice = 0;
    let maxPrice = 1000;
    const min = 0;
    const max = 1000;
    
    // Handle min price changes
    function handleMinPriceChange(value: number) {
        minPrice = value > maxPrice ? maxPrice : value;
    }

    // Handle max price changes
    function handleMaxPriceChange(value: number) {
        maxPrice = value < minPrice ? minPrice : value;
    }

    // Calculate slider background gradients for visual feedback
    $: leftPosition = (minPrice / max) * 100;
    $: rightPosition = (maxPrice / max) * 100;
    $: background = `linear-gradient(to right, 
        #e5e7eb 0%, 
        #e5e7eb ${leftPosition}%, 
        #000000 ${leftPosition}%, 
        #000000 ${rightPosition}%, 
        #e5e7eb ${rightPosition}%, 
        #e5e7eb 100%)`;
</script>

<div class="px-3">
    <div class="relative h-14 mb-2">
        <!-- Price labels -->
        <div class="absolute w-full flex justify-between text-xs text-gray-500 -top-6">
            <span>${min}</span>
            <span>${max}</span>
        </div>

        <!-- Slider container -->
        <div class="relative w-full h-2 mt-8">
            <!-- Track background -->
            <div class="absolute w-full h-full rounded-full" style="background: {background}"></div>

            <!-- Sliders container -->
            <div class="relative w-full h-full">
                <!-- Min price slider -->
                <input
                    type="range"
                    value={minPrice}
                    min={min}
                    max={max}
                    class="absolute w-full h-full appearance-none bg-transparent pointer-events-none [&::-webkit-slider-thumb]:pointer-events-auto [&::-webkit-slider-thumb]:w-4 [&::-webkit-slider-thumb]:h-4 [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:bg-white [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-black [&::-webkit-slider-thumb]:ring-1 [&::-webkit-slider-thumb]:ring-black [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:cursor-pointer [&::-moz-range-thumb]:pointer-events-auto [&::-moz-range-thumb]:w-4 [&::-moz-range-thumb]:h-4 [&::-moz-range-thumb]:rounded-full [&::-moz-range-thumb]:bg-white [&::-moz-range-thumb]:border-2 [&::-moz-range-thumb]:border-black [&::-moz-range-thumb]:ring-1 [&::-moz-range-thumb]:ring-black [&::-moz-range-thumb]:appearance-none [&::-moz-range-thumb]:cursor-pointer"
                    on:input={(e) => handleMinPriceChange(parseInt(e.currentTarget.value))}
                />

                <!-- Max price slider -->
                <input
                    type="range"
                    value={maxPrice}
                    min={min}
                    max={max}
                    class="absolute w-full h-full appearance-none bg-transparent pointer-events-none [&::-webkit-slider-thumb]:pointer-events-auto [&::-webkit-slider-thumb]:w-4 [&::-webkit-slider-thumb]:h-4 [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:bg-white [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-black [&::-webkit-slider-thumb]:ring-1 [&::-webkit-slider-thumb]:ring-black [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:cursor-pointer [&::-moz-range-thumb]:pointer-events-auto [&::-moz-range-thumb]:w-4 [&::-moz-range-thumb]:h-4 [&::-moz-range-thumb]:rounded-full [&::-moz-range-thumb]:bg-white [&::-moz-range-thumb]:border-2 [&::-moz-range-thumb]:border-black [&::-moz-range-thumb]:ring-1 [&::-moz-range-thumb]:ring-black [&::-moz-range-thumb]:appearance-none [&::-moz-range-thumb]:cursor-pointer"
                    on:input={(e) => handleMaxPriceChange(parseInt(e.currentTarget.value))}
                />
            </div>
        </div>
    </div>

    <div class="flex gap-2 mb-4">
        <div class="relative flex items-center">
            <span class="absolute ml-1">$</span>
            <input
                type="number"
                value={minPrice}
                class="w-24 px-2 py-1 border rounded pl-4"
                placeholder="Min"
                min={min}
                max={max}
                on:input={(e) => handleMinPriceChange(parseInt(e.currentTarget.value))}
            />
        </div>
        <span class="flex items-center"> to </span>

        <div class="relative flex items-center">
            <span class="absolute ml-1">$</span>
            <input
                type="number"
                value={maxPrice}
                class="w-24 px-2 py-1 border rounded pl-4"
                placeholder="Max"
                min={min}
                max={max}
                on:input={(e) => handleMaxPriceChange(parseInt(e.currentTarget.value))}
            />
        </div>
    </div>
    <div class="flex justify-center">
        <button class="bg-black text-white px-4 py-1 rounded text-sm w-full hover:bg-gray-800">
            Apply
        </button>
    </div>
</div>