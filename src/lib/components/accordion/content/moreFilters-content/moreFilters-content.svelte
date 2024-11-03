<script lang="ts">
    import { ScrollArea } from "$lib/components/ui/scroll-area/index.js";
    import { Checkbox } from "$lib/components/ui/checkbox"
    

    const moreFilters = [
        {
            index: 1,
            filter: "18'",
            isDisabled: true,
        },
        {
            index: 2,
            filter: "19'",
            isDisabled: true,
        },
        {
            index: 3,
            filter: "20'",
            isDisabled: true,
        },
        {
            index: 4,
            filter: "21'",
            isDisabled: true,
        },
        {
            index: 5,
            filter: "22'",
            isDisabled: true,
        },
        {
            index: 6,
            filter: "Beauty-All",
            isDisabled: false,
        },
        {
            index: 7,
            filter: "Beauty-New",
            isDisabled: false,
        },
        {
            index: 8,
            filter: "Black",
            isDisabled: false,
        },
        {
            index: 9,
            filter: "Brown",
            isDisabled: false,
        },
        {
            index: 10,
            filter: "Daventry Meers",
            isDisabled: false,
        },
        {
            index: 11,
            filter: "LifeSavers",
            isDisabled: false,
        },
    ]
</script>
    
<div class="flex items-center justify-center">
    <ScrollArea class="h-[200px] w-[250px] rounded-md border p-2">
        <div class="flex flex-col gap-2">
            {#each moreFilters as filter}
                <div class="flex gap-2 items-center pl-1">
                    <Checkbox id="terms" aria-labelledby="terms-label" disabled={filter.isDisabled} />
                    <span class = {`${filter.isDisabled? "text-slate-600" : ""}`}>{filter.filter}</span>
                </div>
            {/each}
        </div>
    </ScrollArea>
</div>

