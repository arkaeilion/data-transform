<script lang="ts">
	import { Handle, Position, type NodeProps } from '@xyflow/svelte';

	type $$Props = NodeProps;

	export let data: $$Props['data'];
	export let isConnectable: $$Props['isConnectable'];

	$$restProps;
</script>

<Handle type="target" position={Position.Left} style="background: #555;" {isConnectable} />

<div>
	<input type="text" bind:value={data} />
</div>

<Handle
	type="source"
	position={Position.Right}
	style="top: 10px; background: #555;"
	{isConnectable}
/>

<style>
	:global(.svelte-flow__node-expandNode) {
		font-size: 12px;
		background: #eee;
		border: 1px solid #555;
		border-radius: 5px;
		text-align: center;
    padding: 10px;
	}
</style>
