<script lang="ts">
  import { onMount } from 'svelte';
  
  import Hero from '$lib/components/Hero.svelte';
  import About from '$lib/components/About.svelte';
  import Services from '$lib/components/services.svelte';
  import Contact from '$lib/components/Contact.svelte';

  onMount(() => {
    const pasekObserver = new IntersectionObserver((entries) => {
      const entry = entries[0];
      const pasekElement = document.getElementById('mobileBar');

      if (pasekElement) {
        if (entry.isIntersecting) {
          pasekElement.classList.add('schowany');
        } else {
          pasekElement.classList.remove('schowany');
        }
      }
    }, {
      threshold: 0, 
      rootMargin: "0px 0px -10px 0px"
    });

    const animObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) entry.target.classList.add('widoczny');
        else entry.target.classList.remove('widoczny');
      });
    }, { threshold: 0.1 });

    setTimeout(() => {
      const kontaktSekcja = document.getElementById('kontakt');
      if (kontaktSekcja) pasekObserver.observe(kontaktSekcja);
      
      document.querySelectorAll('.animacjaWejscia').forEach(el => animObserver.observe(el));
    }, 500);
  });
</script>

<Hero />
<About />
<Services />
<Contact />

<div id="mobileBar" class="pasekMobilny">
  <a href="#kontakt" class="akcjaMobilna">Napisz wiadomość</a>
</div>