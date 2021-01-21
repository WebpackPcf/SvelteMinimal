<script lang="typescript">
  import { createEventDispatcher } from "svelte";
  
  export let val: string;
  export let isDisabled: boolean;
  export let isVisible: boolean;

  const dispatch = createEventDispatcher();

  function onBlur() {
    dispatch("change", {
      val: val,
    });
  }
</script>

<style>
    input {
    height: 35px;
    font-size: 1rem;
    line-height: 2.5rem;
    padding: 0;
    margin: 0;
    border: 0;
    font-weight: bold;
    box-sizing: border-box;
    padding-left: 7px;
    width: 99%;
  }

  input:focus {
    font-weight: normal;
    border: 1px solid black;
  }

  input:focus::placeholder {
    color: transparent;
  }

  input::placeholder {
    color: black;
    font-weight: bold;
  }
</style>

{#if isVisible}
    <input
      disabled={isDisabled}
      type="text"
      bind:value={val}
      on:blur={onBlur}
      placeholder="---" />
{/if}
