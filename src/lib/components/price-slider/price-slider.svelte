<script lang="ts">
    import { Slider } from "$lib/components/ui/slider"
    
    //Props
    export let priceValue : number[]

</script>


<Slider value={priceValue} max={100} step={1} />