<!-- Copyright 2023 RADar-AZDelta -->
<!-- SPDX-License-Identifier: gpl3+ -->
<script lang="ts">
  import Search from '../lib/components/Search.svelte'
  import type { ILimitedFilter, ITableFilter } from '../lib/interfaces/Types'

  const limitedFilters: ILimitedFilter[] = [
    {
      name: 'Concept',
      value: 'Standard',
      options: [],
    },
    {
      name: 'Validity',
      value: 'Valid',
      options: [],
    },
    {
      name: 'Vocab',
      options: ['LOINC', 'GGR'],
      exclude: true,
    },
  ]

  let globalFilter: ITableFilter = { column: 'all', filter: 'Andorra' }

  // const limitedFilters = []
  const getVocabularies = async () => ({})
  const getDomains = async () => ({})
  const getConceptClasses = async () => ({})
</script>

<svelte:head>
  <title>Svelte Athena Search</title>
  <meta name="description" content="Svelte Athena Search" />
</svelte:head>

<section class="page-container">
  <h1>Svelte Athena Search</h1>
  <p>
    We have created a component where we can search the Athena database for concepts. The reason for this component is so we can use this in other projects
    where we need to search the Athena database. The layout is based on the design of the webtool from Athena so that the users will have a familiar experience.
    It uses the <a href="https://www.npmjs.com/package/@radar-azdelta/svelte-datatable">svelte-datatable package</a> (also created by us), that is a easy to use
    and fast table component. This example shows a no config search component.
  </p>
  <a href="/custom">Another example with custom actions, custom pages & custom sides</a>
  <div class="container">
    <Search tableOptions={{ rowsPerPageOptions: [10, 20, 100] }} {limitedFilters} bind:globalFilter {getVocabularies} {getDomains} {getConceptClasses} />
  </div>
</section>

<style>
  .container {
    margin: 1rem 1rem 1rem 0;
    height: 80vh;
    border: 1px solid lightgray;
    border-radius: 5px;
    padding: 1rem 0;
  }
</style>
