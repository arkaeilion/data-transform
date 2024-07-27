<script lang="ts">
	import IconClose from '$lib/Icons/IconClose.svelte';
  export let nodeName: string = 'Import Node';
</script>

<!-- Container -->
<div class="flex flex-col bg-neutral-200 rounded-md border border-black"> 
  
  <!-- header Container -->
  <div class="flex flex-row gap-1 p-1 items-center bg-neutral-400 rounded-t-md"> 

    <!-- Drag Handle -->
    <div class="flex flex-row gap-1 drag-handle h-8 w-4 items-center justify-center">
      <div class="flex flex-col gap-1">
        <div class="w-1 h-1 rounded-full bg-neutral-500"></div>
        <div class="w-1 h-1 rounded-full bg-neutral-500"></div>
        <div class="w-1 h-1 rounded-full bg-neutral-500"></div>
      </div>
      <div class="flex flex-col gap-1">
        <div class="w-1 h-1 rounded-full bg-neutral-500"></div>
        <div class="w-1 h-1 rounded-full bg-neutral-500"></div>
        <div class="w-1 h-1 rounded-full bg-neutral-500"></div>
      </div>
    </div>

    <!-- Node Type Icon container -->
     <slot name="icon" />

    <!-- Node Name -->
    <input type="text" class="input variant-form-material bg-neutral-300 bg-opacity-30 border-none focus:bg-neutral-50 min-w-24" bind:value={nodeName} />

    <!-- Empty Space -->
    <div class="flex-grow min-w-4"></div>

    <!-- Node Remove Button -->
    <button type="button" class="btn-icon rounded-md variant-filled bg-neutral-300 bg-opacity-30 hover:bg-opacity-100" on:click={() => {console.log('clicked ' + nodeName);}}>
      <IconClose color="black" width=24 height=24 />
    </button>

  </div>

  <!-- Body Container -->
  <div class="p-2">
    <slot />
  </div>

</div>


