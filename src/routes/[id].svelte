<script context="module">
  export async function preload(page) {
    const { id } = page.params;

    const res = await this.fetch(`https://api.scryfall.com/cards/${id}`);
    const data = await res.json();
    if (res.status === 404) {
      this.error(404, 'Not found');
    }
    return { data };
  }
</script>

<script>
  import Card from '../components/Card.svelte';

  export let data;

  const colors = {
    B: 'Black',
    G: 'Green',
    R: 'Red',
    U: 'Blue',
    W: 'White',
  };
</script>
