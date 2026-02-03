<script lang="ts">
  import { fade } from 'svelte/transition';

  const listaUslug = [
    { nr: '01', tytul: 'Leczenie ran', opis: 'Profesjonalna ocena stanu rany, dobór specjalistycznych opatrunków oraz edukacja w zakresie pielęgnacji. Leczenie ran przewlekłych, w tym owrzodzeń odleżynowych i żylnych.' },
    { nr: '02', tytul: 'Cewnikowanie', opis: 'Wymiana lub założenie cewnika Foley\'a u kobiet i mężczyzn w warunkach domowych z zachowaniem pełnej sterylności i dbałości o komfort pacjenta.' },
    { nr: '03', tytul: 'Kroplówki', opis: 'Wlewy dożylne (nawadniające, z lekami) zgodnie ze zleceniem lekarskim.' },
    { nr: '04', tytul: 'Pobieranie krwi', opis: 'Pobranie materiału do badań laboratoryjnych bez konieczności wychodzenia z domu. Wyniki dostępne online lub dostarczane papierowo.' },
    { nr: '05', tytul: 'Usuwanie szwów', opis: 'Fachowe i bezpieczne zdjęcie szwów lub klamer po zabiegach operacyjnych, po wygojeniu rany.' },
    { nr: '06', tytul: 'Iniekcje', opis: 'Wykonywanie zastrzyków domięśniowych, podskórnych oraz dożylnych zgodnie z zaleceniami lekarskimi (antybiotyki, leki przeciwbólowe, witaminy).' },
    { nr: '07', tytul: 'Port naczyniowy', opis: 'Profesjonalna obsługa portów naczyniowych: zakładanie igły Hubera, płukanie, podawanie leków i pobieranie krwi.' },
    { nr: '08', tytul: 'Szkolenie personelu', opis: 'Szkolenie z zakresu opieki paliatywnej i pielęgniarstwa dla personelu medycznego.' }
  ];

  let aktywnyIndex = $state(0); 

  const nastepna = () => aktywnyIndex = (aktywnyIndex + 1) % listaUslug.length;
  const poprzednia = () => aktywnyIndex = (aktywnyIndex - 1 + listaUslug.length) % listaUslug.length;
</script>

<section id="uslugi" class="sekcja sekcjaUslugi">
  <div class="kontener uslugiKontener">
    
    <header class="naglowekUslug animacjaWejscia">
      <span class="nadtytulUslug">Oferta</span>
      <h2 class="podtytul" style="color:#fff">Zakres usług</h2>
      <div class="wskazowka">Wybierz zabieg z listy, aby zobaczyć szczegóły</div>
    </header>

    <div class="ukladUslug animacjaWejscia">
      
      <div class="listaZabiegow">
        {#each listaUslug as usluga, i}
          <button 
            class="kartaZabiegu" 
            class:aktywny={aktywnyIndex === i} 
            onclick={() => aktywnyIndex = i}
          >
            <span class="numerZabiegu">{usluga.nr}</span> 
            <span class="nazwaZabiegu">{usluga.tytul}</span>
          </button>
        {/each}
      </div>

      <div class="nawigacjaMobilna">
          <button onclick={poprzednia} class="strzalkaNav" aria-label="Poprzednia usługa">←</button>
          <div class="aktualnaUslugaInfo">
            <span class="mobileNr">{listaUslug[aktywnyIndex].nr}</span>
            <span class="mobileTytul">{listaUslug[aktywnyIndex].tytul}</span>
          </div>
          <button onclick={nastepna} class="strzalkaNav" aria-label="Następna usługa">→</button>
      </div>

      <div class="opisZabieguKontener">
        {#key aktywnyIndex}
          <div class="zawartoscOpisu" in:fade={{ duration: 300 }}>
             <h3 class="tytulOpisu">{listaUslug[aktywnyIndex].tytul}</h3>
             <p class="tekstOpisu">{listaUslug[aktywnyIndex].opis}</p>
          </div>
        {/key}
      </div>

    </div>
  </div>
</section>

<style>
  .sekcjaUslugi {
    background:
      linear-gradient(180deg, rgba(44, 62, 48, 0.85), rgba(90, 125, 108, 0.65) 60%, rgba(44, 62, 48, 0.9)),
      url("/hero-bg.svg"); 
    background-size: cover;
    background-position: center 30%;
    color: white;
    height: 100vh; 
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0 20px;
  }

  .kontener {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    height: 90vh; 
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .naglowekUslug { margin-bottom: 3vh; text-align: left; }

  .ukladUslug {
    display: grid;
    grid-template-columns: 350px 1fr;
    gap: 40px;
    height: 70vh;
    align-items: stretch;
  }

  .listaZabiegow {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
  }

  .kartaZabiegu {
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    color: rgba(255, 255, 255, 0.7);
    padding: 0 20px; 
    height: 11%;
    border-radius: 12px;
    text-align: left;
    cursor: pointer;
    font-size: 1rem;
    display: flex;
    align-items: center;
    gap: 15px;
    width: 100%;
    transition: all 0.2s;
  }

  .kartaZabiegu:hover { background: rgba(255, 255, 255, 0.1); color: white; }

  .kartaZabiegu.aktywny {
    background: #5A7D6C;
    color: white;
    font-weight: bold;
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    border-color: #5A7D6C;
  }

  .numerZabiegu { font-weight: bold; opacity: 0.5; }

  .opisZabieguKontener {
    background: #FAF9F6;
    color: #333D36;
    padding: 60px;
    border-radius: 24px;
    display: grid !important; 
    align-items: center;
    justify-items: start;
    overflow: hidden;
  }

  .zawartoscOpisu {
    grid-area: 1 / 1;
    width: 100%;
  }

  .tytulOpisu {
    font-size: 2.5rem;
    color: #2C3E30;
    margin-bottom: 30px;
    line-height: 1.1;
  }

  .tekstOpisu {
    font-size: 1.3rem;
    line-height: 1.6;
    color: #5C6660;
  }

  .nawigacjaMobilna { display: none; }

  @media (max-width: 1024px) {
    .ukladUslug { grid-template-columns: 1fr; height: auto; display: block; }
    .listaZabiegow { display: none; }
    
    .kontener { height: auto; display: block; padding-top: 80px; }
    .sekcjaUslugi { height: auto; min-height: 100vh; padding-bottom: 40px; } 

    .nawigacjaMobilna {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      padding: 10px;
      background: rgba(255,255,255,0.1);
      border-radius: 12px;
    }
    
    .strzalkaNav {
      background: #5A7D6C;
      border: none;
      color: white;
      width: 44px; height: 44px;
      border-radius: 50%;
      font-size: 1.2rem;
      cursor: pointer;
    }
    
    .mobileNr { margin-right: 10px; font-weight: bold; opacity: 0.8; }
    .mobileTytul { font-weight: bold; }

    .opisZabieguKontener { 
        height: auto; 
        min-height: 300px; 
        padding: 30px; 
        display: block; 
    }
    
    .tytulOpisu { font-size: 1.8rem; margin-top: 20px; }
    .tekstOpisu { font-size: 1.1rem; }
  }
</style>