<script>
  export let categories = [];
  export let onFilter;

  const handleChange = (event) => {
    const target = event.target;
    if (target instanceof HTMLSelectElement) {
      onFilter(target.value);
    }
  };
</script>

<div>
  <select on:change={handleChange}>
    <option value="">All Categories</option>
    {#each categories as category}
      <option>{category}</option>
    {/each}
  </select>
</div>
