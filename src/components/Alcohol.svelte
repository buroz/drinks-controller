<script lang="ts">
	import Button from './Button.svelte';

	export let key: string;
	export let img: string;

	export let count: number = get();

	function set() {
		window.localStorage.setItem(key, count.toString());
	}

	function get(): number {
		const found = window.localStorage.getItem(key);
		return (found && parseInt(found)) || 0 
	}

  function increase() {
    count++;
		set();
  }

  function decrease() {
		if (count - 1 < 0) {
			return;
		}

    count--;
		set();
  }

  function deleteKey() {
    window.localStorage.removeItem(key);
  }
</script>

<div class="relative">
  <!-- <button on:click={deleteKey} class="absolute right-0 bg-red-600 text-white border-none text-lg p-1">x</button> -->

  <div class="flex flex-col justify-center items-center my-2 space-y-2">
    <img class="h-16" src="assets/{img}" alt="Beer" />
    <span class="text-2xl text-blue-600 font-bold">{key}</span>
  </div>
  
  <div class="flex justify-center items-center w-full rounded border">
    <div class="w-1/4">
      <Button on:click={decrease} text="-" border="left" />
    </div>
    <div class="w-2/4">
      <p class="w-full p-1 font-bold text-center text-blue-600 text-2xl">{count}</p>
    </div>
    <div class="w-1/4">
      <Button on:click={increase} text="+" border="right" />
    </div>
  </div>

  <hr />
</div>