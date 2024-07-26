<script lang="ts">
  // https://svelteflow.dev/examples/nodes/custom-node
  import { writable } from 'svelte/store';
  import {
    SvelteFlow,
    Background,
    Controls,
    MiniMap,
    Position,
    type Node,
    type Edge
  } from '@xyflow/svelte';

  import '@xyflow/svelte/dist/style.css';
	import ImportNode from '$lib/components/ImportNode.svelte';
	import ExpandNode from '$lib/components/ExpandNode.svelte';
  import ExportNode from '$lib/components/ExportNode.svelte';

  const nodeTypes = {
    importNode: ImportNode,
    exportNode: ExportNode,
    expandNode: ExpandNode,
  };

  const initialNodes: Node[] = [
    {
      id: '1',
      type: 'importNode',
      data: { label: 'An input node' },
      position: { x: 0, y: 50 }
    },
    {
      id: '2',
      type: 'expandNode',
      data: { label: 'An expand node' },
      position: { x: 300, y: 50 }
    },
    {
      id: '3',
      type: 'exportNode',
      data: { label: 'Output A' },
      position: { x: 650, y: 25 }
    },
  ];

  const initialEdges: Edge[] = [
    {
      id: 'e1-2',
      source: '1',
      target: '2',
      animated: true,
      style: 'stroke: #ff00ff;'
    },
    {
      id: 'e2-3',
      source: '2',
      target: '3',
      animated: true,
      style: 'stroke: #ff00ff;'
    }
  ];

  const nodes = writable<Node[]>(initialNodes);
  const edges = writable(initialEdges);
</script>

<div style="height:100vh;">
  <SvelteFlow {nodes} {edges} {nodeTypes} fitView>
    <Background />
    <Controls />
    <MiniMap />
  </SvelteFlow>
</div>
