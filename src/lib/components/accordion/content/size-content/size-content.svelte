<script lang="ts">
    import * as ToggleGroup from "$lib/components/ui/toggle-group"
    

    const sizes = [
        {
            "index": 1,
            "size": "XS"
        },
        {
            "index": 2,
            "size": "S"
        },
        {
            "index": 3,
            "size": "M"
        },
        {
            "index": 4,
            "size": "L"
        },
        {
            "index": 5,
            "size": "XL"
        },

    ]
</script>


<div>
    <div class="flex p-1">
        <ToggleGroup.Root type="single">
            {#each sizes as size}
                <ToggleGroup.Item value={size.size} class="outline-dashed outline-1 rounded-sm focus:ring-1 focus:ring-slate-600">{size.size}</ToggleGroup.Item>
            {/each}
        </ToggleGroup.Root>
    </div>
</div>