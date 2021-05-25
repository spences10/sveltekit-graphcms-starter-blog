<script>
  import Nav from '$lib/nav.svelte'
  import '../app.css'
</script>

<Nav />

<div class="container max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
  <slot />
</div>
