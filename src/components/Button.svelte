<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  export let text: string;
  export let border: "left" | "right";

  const dispatch = createEventDispatcher();

  const onButtonClick = (): void => {
    dispatch("click");
  };
</script>

<style>
</style>

<button
  on:click={onButtonClick}
  class="{border === 'left' ? 'rounded-l' : 'rounded-r'} m-0 bg-blue-600 border-none p-2 w-full text-white text-xl font-semibold"
>
  {text}
</button>
