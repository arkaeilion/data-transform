<script lang="ts">
	import { Handle, Position, type NodeProps } from '@xyflow/svelte';
	import NodeWrapper from './NodeWrapper.svelte';

	type $$Props = NodeProps;

	export let data: $$Props['data'];
	export let isConnectable: $$Props['isConnectable'];

  let dataString: string;

  $: {
    if (data) {
      dataString = JSON.stringify(data, null, 2);
    }
  }

	$$restProps;
</script>

<Handle type="target" position={Position.Left} style="background: #555;" {isConnectable} />

<NodeWrapper nodeName="Export Node">
  <textarea class="textarea variant-form-material resize min-h-32 min-w-full" rows="4" cols="10" />
</NodeWrapper>
