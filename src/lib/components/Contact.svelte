<script lang="ts">
  let imie = $state('');
  let email = $state('');
  let wiadomosc = $state('');
  
  let bledy = $state({ imie: false, email: false, wiadomosc: false });
  let status = $state({ wiadomosc: '', typ: '' }); 
  let wysylanie = $state(false);

  async function wyslijWiadomosc(e: Event) {
    e.preventDefault();
    
    bledy = { imie: false, email: false, wiadomosc: false };
    status = { wiadomosc: '', typ: '' };

    let czyBlad = false;

    if (imie.trim().length < 3) {
      bledy.imie = true;
      czyBlad = true;
    }
    if (!email.includes('@') || !email.includes('.')) {
      bledy.email = true;
      czyBlad = true;
    }
    if (wiadomosc.trim().length < 5) {
      bledy.wiadomosc = true;
      czyBlad = true;
    }

    if (czyBlad) {
      status = { wiadomosc: 'Popraw zaznaczone pola.', typ: 'blad' };
      return;
    }

    wysylanie = true;
    status = { wiadomosc: 'Wysyłanie...', typ: '' };

    try {
      const response = await fetch("https://formspree.io/f/xaqyyvyn", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ imie, email, wiadomosc })
      });

      if (response.ok) {
        status = { wiadomosc: 'Wysłano pomyślnie! Dziękuję.', typ: 'sukces' };
        imie = ''; email = ''; wiadomosc = '';
      } else {
        status = { wiadomosc: 'Błąd wysyłania. Spróbuj później.', typ: 'blad' };
      }
    } catch (error) {
      status = { wiadomosc: 'Błąd połączenia.', typ: 'blad' };
    } finally {
      wysylanie = false;
    }
  }

  const rok = new Date().getFullYear();
</script>

<section id="kontakt" class="sekcja sekcjaKontakt">
  <div class="kontener kontaktKontener">
    
    <div class="kontaktNaglowek">
      <span class="nadtytul animacjaWejscia">Ustalmy szczegóły</span>
      <h2 class="podtytul animacjaWejscia">Kontakt</h2>
    </div>

    <div class="ukladKontaktowy animacjaWejscia">
      
      <form onsubmit={wyslijWiadomosc} class="formularz">
        <h3 class="formularzTytul">Napisz wiadomość</h3>
        
        <div class="wierszFormularza">
          <label class="poleFormularza">
            <span>Imię i nazwisko</span>
            <input 
              type="text" 
              bind:value={imie} 
              class:blad={bledy.imie}
              placeholder="Jan Kowalski"
            >
            {#if bledy.imie}<small class="tekstBledu">Wpisz poprawne imię</small>{/if}
          </label>
          
          <label class="poleFormularza">
            <span>E-mail</span>
            <input 
              type="email" 
              bind:value={email} 
              class:blad={bledy.email}
              placeholder="twoja@poczta.com"
            >
            {#if bledy.email}<small class="tekstBledu">Wpisz poprawny e-mail</small>{/if}
          </label>
        </div>

        <label class="poleFormularza">
          <span>Treść wiadomości</span>
          <textarea 
            rows="6" 
            bind:value={wiadomosc} 
            class:blad={bledy.wiadomosc}
            placeholder="Krótko opisz w czym mogę pomóc."
          ></textarea>
          {#if bledy.wiadomosc}<small class="tekstBledu">Wiadomość jest za krótka</small>{/if}
        </label>

        <button type="submit" class="przycisk przyciskGlowny" disabled={wysylanie}>
          {wysylanie ? 'Wysyłanie...' : 'Wyślij'}
        </button>
        
        <p class="zgodaPolityka"> 
          Wysyłając wiadomość, akceptujesz <a href="/polityka">politykę prywatności</a>.
        </p>

        {#if status.wiadomosc}
          <p class="statusWysylki {status.typ}">{status.wiadomosc}</p>
        {/if}
      </form>

      <div class="kontaktDane">
        <div class="kartaKontaktowa">
           <h3>E-mail</h3>
           <p>Preferowana forma kontaktu.</p>
           <a href="mailto:honoratadawid@gmail.com" class="linkKontaktowy">honoratadawid@gmail.com</a>
        </div>
        
        <div class="kartaKontaktowa">
           <h3>Telefon</h3>
           <p>W pilnych sprawach.</p>
           <a href="tel:+48608650919" class="linkKontaktowy maly">+48 608 650 919</a>
        </div>
      </div>

    </div>

    <footer class="stopkaKontaktu">
      <div class="stopkaKlient">
        <p>© <span>{rok}</span> Honorata Dawid • <a href="/polityka">Polityka prywatności</a></p>
      </div>
      
      <div class="stopkaAutor">
        <p>
          Realizacja strony: 
          <a href="https://www.linkedin.com/in/franciszek-dawid/" target="_blank" rel="noopener noreferrer">
            Franciszek Dawid
          </a>
        </p>
      </div>
    </footer>
  </div>
</section>

<style>
  .sekcjaKontakt {
    min-height: 100vh;
    display: flex;
    align-items: center;
    background: #FAF9F6;
    padding: 80px 20px 40px 20px;
  }

  .kontener {
    width: 100%;
    max-width: 1100px;
    margin: 0 auto;
  }

  .kontaktNaglowek { text-align: center; margin-bottom: 40px; }
  
  .nadtytul { color: #5A7D6C; text-transform: uppercase; font-weight: 700; font-size: 0.9rem; letter-spacing: 0.05em; display: block; margin-bottom: 10px; }
  .podtytul { font-size: 2.5rem; color: #2C3E30; margin: 0; }

  .ukladKontaktowy {
    display: grid;
    grid-template-columns: 2fr 1fr; 
    gap: 40px;
    align-items: start;
  }
  .formularz {
    background: #fff;
    padding: 40px; 
    border-radius: 20px;
    border: 1px solid rgba(44, 62, 48, 0.08);
    box-shadow: 0 10px 40px rgba(44, 62, 48, 0.05);
  }
  
  .formularzTytul { margin: 0 0 24px; color: #2C3E30; }

  .wierszFormularza {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  
  .poleFormularza { display: flex; flex-direction: column; gap: 8px; margin-bottom: 20px; }
  .poleFormularza span { font-weight: 600; font-size: 0.95rem; color: #333D36; }

  input, textarea {
    width: 100%;
    padding: 14px; 
    border: 1px solid #ddd;
    border-radius: 8px;
    background: #f9f9f9;
    font-family: inherit;
    font-size: 1rem;
    transition: 0.2s;
  }
  
  input:focus, textarea:focus {
    outline: none;
    border-color: #5A7D6C;
    background: #fff;
  }

  input.blad, textarea.blad { border-color: #e74c3c; background: #fff5f5; }
  .tekstBledu { color: #e74c3c; font-size: 0.85rem; }

  .przyciskGlowny {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    background: #5A7D6C; 
    color: #fff;
    padding: 16px;
    border: none;
    border-radius: 12px;
    font-weight: 600;
    font-size: 1.1rem;
    cursor: pointer;
    transition: all 0.2s;
    margin-top: 10px;
  }

  .przyciskGlowny:hover { 
    background: #2C3E30; 
    transform: translateY(-2px);
  }
  
  .przyciskGlowny:disabled { 
    opacity: 0.7; 
    cursor: not-allowed; 
    transform: none;
  }

  .zgodaPolityka { font-size: 0.8rem; color: #5C6660; margin-top: 12px; text-align: center; }
  .zgodaPolityka a { color: #5A7D6C; }

  .statusWysylki { margin-top: 15px; text-align: center; font-weight: 600; }
  .statusWysylki.sukces { color: #5A7D6C; }
  .statusWysylki.blad { color: #e74c3c; }

  .kontaktDane { display: flex; flex-direction: column; gap: 20px; }

  .kartaKontaktowa {
    background: #fff;
    padding: 24px;
    border-radius: 16px;
    border: 1px solid rgba(44, 62, 48, 0.08);
  }
  .kartaKontaktowa h3 { margin: 0 0 5px; color: #2C3E30; font-size: 1.1rem; }
  .kartaKontaktowa p { margin: 0 0 10px; color: #5C6660; font-size: 0.9rem; }
  
  .linkKontaktowy { color: #5A7D6C; font-weight: 700; text-decoration: none; font-size: 1.05rem; display: block; word-break: break-all; }
  .linkKontaktowy:hover { text-decoration: underline; }

  .stopkaKontaktu {
    margin-top: 40px; 
    padding-top: 20px;
    border-top: 1px solid rgba(0,0,0,0.1);
    text-align: center;
    font-size: 0.85rem;
    color: #5C6660;
  }
  .stopkaKontaktu a { color: #5A7D6C; text-decoration: none; }

  @media (max-width: 900px) {
    .ukladKontaktowy { grid-template-columns: 1fr; gap: 40px; }
    .wierszFormularza { grid-template-columns: 1fr; gap: 0; }
    .formularz { padding: 24px; }
  }
</style>