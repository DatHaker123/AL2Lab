<script>
  import * as Accordion from "$lib/components/ui/accordion" 
  import * as Tooltip from "$lib/components/ui/tooltip"
  import { Slider } from "$lib/components/ui/slider"

  import machines from '$lib/machines.json'
  import { settings } from './stores'
</script>

<Accordion.Root multiple={true} value={['factory']}>
  <Accordion.Item value="factory">
    <Accordion.Trigger>Factory</Accordion.Trigger>
    <Accordion.Content>
      <div class="flex flex-col gap-2 py-2 pr-4">
        {#each Object.entries(machines) as [machine, _]}
        <div class="flex gap-2 items-center">
          <Tooltip.Root>
            <Tooltip.Trigger class="w-8">
              <img src={'/assets/MACHINES_' + machine.toUpperCase() + '_TOP.png'} alt={machine} class="h-5" />
            </Tooltip.Trigger>
            <Tooltip.Content>
              {machine[0].toUpperCase() + machine.replaceAll('_', ' ').slice(1)}
            </Tooltip.Content>
          </Tooltip.Root>
          <span class="w-16">{$settings[machine][0].toFixed(1)}s</span>
          {#if machine.includes('starter')}
          <Slider max={5} min={0.5} step={0.5} bind:value={$settings[machine]} />
          {:else}
          <Slider max={5} min={1} bind:value={$settings[machine]} />
          {/if}
        </div>
        {/each}
      </div>
    </Accordion.Content>
  </Accordion.Item>
  <Accordion.Item value="display">
    <Accordion.Trigger>Display</Accordion.Trigger>
    <Accordion.Content>
      🚧 UNDER CONSTRUCTION 🚧
    </Accordion.Content>
  </Accordion.Item>
  <Accordion.Item value="flow">
    <Accordion.Trigger>Flow</Accordion.Trigger>
    <Accordion.Content>
      🚧 UNDER CONSTRUCTION 🚧
    </Accordion.Content>
  </Accordion.Item>
  <Accordion.Item value="advanced">
    <Accordion.Trigger>Advanced</Accordion.Trigger>
    <Accordion.Content>
      🚧 UNDER CONSTRUCTION 🚧
    </Accordion.Content>
  </Accordion.Item>
</Accordion.Root>