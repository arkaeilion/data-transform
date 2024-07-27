<script lang="ts">
	import { Handle, Position, type NodeProps } from '@xyflow/svelte';
	import NodeWrapper from './NodeWrapper.svelte';

	type $$Props = NodeProps;

	export let data: $$Props['data'];
	export let isConnectable: $$Props['isConnectable'];

  data = {
    fruit: 'apple',
    vegetable: 'carrot',
    animal: 'tiger',
    color: 'red',
    place: 'home',
  }

  let items: [string, unknown][] = [];

  $: {
    if (data) {
      items = Object.entries(data);
    }
  }

	$$restProps;
</script>

<Handle type="target" position={Position.Left} style="background: #555;" {isConnectable} />

<NodeWrapper nodeName="Expand Node">
  <div class="flex flex-col gap-1">
    {#if data && typeof data === 'object'}
      {#each items as item}
        <div>
          <input type="text" class="input variant-form-material" bind:value={item[0]} />
          <input type="text" class="input variant-form-material" bind:value={item[1]} />
        </div>
      {/each}
    {/if}
  </div>
</NodeWrapper>

<Handle
	type="source"
	position={Position.Right}
	style="background: #555;"
	{isConnectable}
/>
