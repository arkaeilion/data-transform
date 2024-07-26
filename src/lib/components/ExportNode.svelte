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

<style>
	:global(.svelte-flow__node-exportNode) {
		font-size: 12px;
		background: #eee;
		border: 1px solid #555;
		border-radius: 5px;
		text-align: center;
    padding: 10px;
	}
</style>
