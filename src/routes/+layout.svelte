<script lang="ts">
  import '../app.css';
  import { onMount } from 'svelte';
  import favicon from '$lib/assets/favicon.svg';

  let { children } = $props();
  let aktywnaSekcja = $state('');

  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) aktywnaSekcja = entry.target.id;
      });
    }, { rootMargin: '-40% 0px -40% 0px' });

    document.querySelectorAll('section[id]').forEach((s) => observer.observe(s));
    return () => observer.disconnect();
  });
</script>

<nav class="nawigacja">
  <div class="nawigacjaSrodek">
    <a class="logo" href="/#top" onclick={() => aktywnaSekcja = ''}>
      <img src={favicon} alt="" class="logoIkona" />
      <span>Honorata Dawid</span>
    </a>
    
    <div class="menuLista">
      <a class="menuLink" class:aktywny={aktywnaSekcja === 'omnie'} href="/#omnie">O mnie</a>
      <a class="menuLink" class:aktywny={aktywnaSekcja === 'uslugi'} href="/#uslugi">Usługi</a>
      <a class="menuLink" class:aktywny={aktywnaSekcja === 'kontakt'} href="/#kontakt">Kontakt</a>
    </div>
  </div>
</nav>

<main id="top">
  {@render children()}
</main>