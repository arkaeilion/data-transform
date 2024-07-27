<script lang="ts">
	export let color = 'red';
  export let width: string | number | null | undefined = 24;
  export let height: string | number | null | undefined = 24;

  // let _width = width;

  // $: {
  //   let w = width.toString();
  //   if (!w.endsWith('px')) {
  //     w += 'px';
  //   }


  //   let h = height.toString();
  //   if (!h.endsWith('px')) {
  //     h += 'px';
  //   }
  // }
</script>

<svg
	xmlns="http://www.w3.org/2000/svg"
	height={height}
	viewBox="0 -960 960 960"
	width={width}
	fill={color}
	><path
		d="m256-200-56-56 224-224-224-224 56-56 224 224 224-224 56 56-224 224 224 224-56 56-224-224-224 224Z"
	/></svg
>
