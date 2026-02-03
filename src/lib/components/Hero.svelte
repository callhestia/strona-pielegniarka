<script lang="ts">
</script>

<header id="start" class="sekcja sekcjaPowitalna">
  <div class="tloSekcji"></div>

  <div class="kontener">
    <span class="nadtytul hero">Usługi pielęgniarskie • Kluczbork</span>
    
    <h1 class="tytulGlowny animacjaWejscia">
      Opieka z sercem w Twoim domu
    </h1>
    
    <p class="tekstWstepny animacjaWejscia">
      Zapewniam profesjonalne zabiegi pielęgniarskie w domu pacjenta.
      <br>
      Moim celem jest nie tylko leczenie, ale także wsparcie emocjonalne pacjenta i jego rodziny.
    </p>

    <div class="akcje animacjaWejscia">
      <a class="przycisk przyciskGlowny" href="#kontakt">Kontakt</a>
      <a class="przycisk przyciskPusty" href="#uslugi">Usługi</a>
    </div>
  </div>
  
  <div class="przewinWDol">
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <path d="M7 13l5 5 5-5M7 6l5 5 5-5"/>
    </svg>
  </div>
</header>

<style>
  .sekcjaPowitalna {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 20px;
    background-color: #2C3E30; 
    color: #fff;
    overflow: hidden;
  }

  .tloSekcji {
    position: absolute;
    inset: 0;
    z-index: 0;
    background:
      linear-gradient(180deg, rgba(44, 62, 48, 0.85), rgba(90, 125, 108, 0.65) 60%, rgba(44, 62, 48, 0.9)),
      url("/hero-bg.svg"); 
    background-size: cover;
    background-position: center 30%;
  }

  .kontener {
    position: relative;
    z-index: 1;
    max-width: 1100px;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }

  .nadtytul.hero {
    color: #D1E0D6;
    display: block;
    margin-bottom: 16px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    font-size: 0.9rem;
  }

  .tytulGlowny {
    font-size: clamp(2.5rem, 5vw, 4.5rem);
    line-height: 1.1;
    margin: 0 0 24px 0;
    font-weight: 800;
  }

  .tekstWstepny {
    font-size: 1.25rem;
    line-height: 1.6;
    max-width: 650px;
    margin: 0 0 40px 0;
    color: #F0F5F2;
  }
  
  /* UKŁAD PRZYCISKÓW DESKTOP */
  .akcje {
    display: flex;
    flex-direction: row;
    /* Kluczowa zmiana: flex-start zamiast center eliminuje przesunięcia pionowe */
    align-items: flex-start; 
    gap: 20px;
    margin-top: 20px;
  }

  .przycisk {
    display: flex;
    justify-content: center;
    align-items: center;
    
    width: 200px;
    height: 56px; 
    padding: 0; 
    margin: 0; /* Reset marginesów */
    
    border-radius: 14px;
    font-weight: 600;
    text-decoration: none;
    cursor: pointer;
    transition: transform .2s ease, background .2s ease;
    font-size: 1.1rem;
    box-sizing: border-box; 
  }

  .przycisk:hover { transform: translateY(-3px); }

  .przyciskGlowny {
    background: #fff;
    color: #2C3E30;
    border: 2px solid #fff; 
  }

  .przyciskGlowny:hover {
    background: #f0f0f0;
    border-color: #f0f0f0;
  }

  .przyciskPusty {
    background: transparent;
    border: 2px solid rgba(255,255,255,0.4);
    color: #fff;
  }

  .przyciskPusty:hover {
    background: rgba(255,255,255,0.1);
    border-color: #fff;
  }

  .przewinWDol {
    position: absolute;
    bottom: 30px;
    left: 50%;
    transform: translateX(-50%);
    color: rgba(255,255,255,0.7);
    animation: bounce 2s infinite;
    z-index: 2;
  }

  @keyframes bounce {
    0%, 100% { transform: translate(-50%, 0); }
    50% { transform: translate(-50%, -10px); }
  }

  /* UKŁAD PRZYCISKÓW MOBILE */
  @media (max-width: 768px) {
    .kontener {
      align-items: center;
      text-align: center;
    }
    
    .akcje {
      width: 100%;
      flex-direction: column;
      /* Na mobile centrujemy elementy w pionie (jeden pod drugim) */
      align-items: center; 
      gap: 16px;
    }

    .przycisk {
      width: 100%;
      max-width: 300px;
      height: 56px; 
    }
    
    .tytulGlowny {
        font-size: 2.5rem;
    }
  }
</style>