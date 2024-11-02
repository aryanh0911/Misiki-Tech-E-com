<script lang="ts">
    import * as Select from "$lib/components/ui/select"

    //Props
    export let placeHolder : string
    export let menuItems : (string | number)[]
    export let onValueChange : ((value : string | number) => void) | undefined = undefined

</script>


<Select.Root onSelectedChange={(selected) => {
    //Type guard
    if(selected !== undefined){
      const value = selected.value
      if(typeof value === 'string' || typeof value === 'number'){
        onValueChange?.(value)
      }
    }
}}>
  <Select.Trigger class="w-[150px] rounded-none border-slate-400">
    <Select.Value placeholder={String(placeHolder)} />
  </Select.Trigger>
  <Select.Content class="rounded-none">
    {#each menuItems as item}
        <Select.Item value = {item}> {item} </Select.Item>
    {/each}
  </Select.Content>
</Select.Root>