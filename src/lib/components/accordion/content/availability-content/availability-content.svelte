<script lang="ts">
    import { Checkbox } from "$lib/components/ui/checkbox/index.js";
</script>



<div class="flex flex-col justify-center gap-3">
    <div class="flex items-center gap-2">
        <Checkbox id="terms" />
        <span>In Stock</span>
    </div>
        
    <div class="flex items-center gap-2 text-gray-500">
        <Checkbox id="terms" disabled />
        <span>Out of Stock</span>
    </div>
</div>