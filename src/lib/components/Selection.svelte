<!-- Copyright 2023 RADar-AZDelta -->
<!-- SPDX-License-Identifier: gpl3+ -->
<script lang="ts">
  import type { ISelectionProps, IView } from '../interfaces/Types'

  let { views, changeView }: ISelectionProps = $props()

  const expandedViews: IView[] = [{ name: 'Athena concepts', value: 'athena', viewSlot: 0 }, ...views]
  let selection: number = $state(0)

  $effect(() => {
    changeView(selection)
  })
</script>

<div class="concept-choice">
  {#each expandedViews as view}
    <button class="concept-choice-button" class:selected={selection === view.viewSlot}>
      <input type="radio" bind:group={selection} id={view.value} value={view.viewSlot} />
      <label class="concept-choice-label" for={view.value}>{view.name}</label>
    </button>
  {/each}
</div>

<style>
  .concept-choice {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 2rem 1rem 2rem;
  }

  .concept-choice-button {
    width: 45%;
    border: 1px solid #d8d8d8;
    border-radius: 5px;
    background-color: inherit;
    cursor: pointer;
    display: flex;
    padding: 0;
  }

  .concept-choice-button:has(input[type='radio'].checked) {
    background-color: #cecece;
  }

  .concept-choice-button:hover {
    background-color: #d8d8d8;
  }

  .concept-choice-button:active {
    outline: none;
    box-shadow: 0 0 0 2px #c5c5c5;
  }

  input {
    display: none;
  }

  .concept-choice-label {
    text-align: center;
    width: 100%;
    height: 100%;
    padding: 0.5rem 0;
    cursor: pointer;
  }

  .selected {
    background-color: lightgray;
  }
</style>
