<script lang="ts">
    import * as Accordion from "$lib/components/ui/accordion"

    //Props
    export let item : string
</script>


<Accordion.Root class="w-full sm:max-w-[70%]" multiple={true}>
  <Accordion.Item value="item-1">
    <Accordion.Trigger>{item}</Accordion.Trigger>
    <Accordion.Content>
        
    </Accordion.Content>
  </Accordion.Item>
</Accordion.Root>