<script lang="ts">
	import { Handle, Position, type NodeProps } from '@xyflow/svelte';
  import {writable} from 'svelte/store';
	import IconValid from '$lib/Icons/IconValid.svelte';
	import IconError from '$lib/Icons/IconError.svelte';
	import IconDownload from '$lib/Icons/IconDownload.svelte';
	import NodeWrapper from './NodeWrapper.svelte';

	type $$Props = NodeProps;
	export let isConnectable: $$Props['isConnectable'];

	export let dataWorking = writable('{}');
  export let dataValid = writable(true);
	export let dataOutput = writable({});

  $: {
    try {
      let data = JSON.parse($dataWorking);
      $dataOutput = data;
      $dataValid = true;
    } catch (e) {
      $dataOutput = {};
      $dataValid = false;
    }
  }

	$$restProps;
</script>

<NodeWrapper nodeName="Import Node">
  <svelte:fragment slot="icon">
    <IconDownload color="black" />
  </svelte:fragment>

  <div class="relative">
    <textarea class="textarea variant-form-material resize min-h-32 min-w-full" rows="4" cols="10" bind:value={$dataWorking} />
    <div class="absolute top-2 right-2">
      {#if $dataValid}
        <IconValid />
      {:else}
        <IconError />
      {/if}
    </div>
  </div>
</NodeWrapper>

<Handle
  type="source"
  position={Position.Right}
  style="background: #555;"
  {isConnectable}
/>