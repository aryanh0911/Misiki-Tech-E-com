<script lang="ts">
    import * as Select from "$lib/components/ui/select"

    //Props
    export let placeHolder : (string | number)
    export let menuItems : (string | number)[]
</script>


<Select.Root>
  <Select.Trigger class="w-[150px] rounded-none border-slate-400">
    <Select.Value placeholder={placeHolder} />
  </Select.Trigger>
  <Select.Content class="rounded-none">
    {#each menuItems as item}
        <Select.Item value={item}> {item} </Select.Item>
    {/each}
  </Select.Content>
</Select.Root>