<script>
</script>

<section id="omnie" class="sekcja sekcjaOmnie">
  <div class="kontener">
    <div class="ukladOmnie">
      
      <div class="animacjaWejscia">
        <div class="kartaOmnie">
          <span class="nadtytul">Poznajmy się</span>
          <h2 class="podtytul">O mnie</h2>
          
          <p class="wstepOmnie">
           Nazywam się Honorata Dawid. Jestem pielęgniarką z ponad 25-letnim stażem, specjalizującą się w opiece paliatywnej.
           Moja praca to połączenie medycznego profesjonalizmu z głębokim szacunkiem do drugiego człowieka. Doświadczenie zdobywane zarówno przy łóżku pacjenta w domu, jak i na oddziałach, nauczyło mnie, jak ważne jest poczucie bezpieczeństwa – nie tylko dla chorych, ale i ich rodzin.
           W codziennej pracy inspiruję się postawą św. Matki Teresy z Kalkuty, realizując misję towarzyszenia w cierpieniu z godnością i miłością.
          </p>

          <h3 class="naglowekMaly">Doświadczenie</h3>
          <ul class="listaKariery">
            <li><strong>Pielęgniarka | Hospicjum domowe</strong> <span>Sprawowanie specjalistycznej opieki pielęgniarskiej nad pacjentami w warunkach domowych.</span></li>
            <li><strong>Pielęgniarka Oddziałowa | Hospicjum stacjonarne</strong> <span>Zarządzanie personelem pielęgniarskim i organizacja pracy oddziału.</span></li>
            <li><strong>Pielęgniarka | Oddział Kardiologiczny</strong> <span>Opieka nad pacjentami z chorobami serca i układu krążenia, a także po zabiegach kardiologicznych.</span></li>
            <li><strong>Wykładowca | Uniwersytet Opolski</strong> <span>Prowadząca zajęcia i wykłady praktyczne.</span></li>
          </ul>

          <div class="cytatMotto">
            <span>♥</span>
            <span>"Dusza musi być złota." — bł. Hanna Chrzanowska</span>
          </div>
        </div>
      </div>

      <div class="ukladOmniePrawa animacjaWejscia">
        <div class="zdjecieProfilowe"></div>
      </div>

    </div>
  </div>
</section>

<style>
    .sekcjaOmnie {
        min-height: 100vh;
        display: flex;
        align-items: center;
        background: #FAF9F6;
        padding: 80px 20px;
        position: relative;
    }

    .kontener {
        max-width: 1100px;
        margin: 0 auto;
        width: 100%;
    }

    .ukladOmnie {
        display: grid;
        grid-template-columns: 1.2fr 1fr;
        gap: 50px;
        align-items: stretch; 
    }

    .ukladOmnie > div {
        display: flex;
        flex-direction: column;
        height: 100%;
    }

    .kartaOmnie {
        background: rgba(255, 255, 255, 0.85);
        backdrop-filter: blur(10px);
        padding: 40px;
        border-radius: 24px;
        border: 1px solid rgba(44, 62, 48, 0.08);
        box-shadow: 0 10px 30px rgba(44, 62, 48, 0.04);
        position: relative;
        z-index: 2;
        height: 100%; 
        display: flex;
        flex-direction: column;
    }

    .nadtytul { color: #5A7D6C; text-transform: uppercase; font-weight: 700; font-size: 0.9rem; letter-spacing: 0.05em; display: block; margin-bottom: 10px; }
    .podtytul { font-size: 2.5rem; color: #2C3E30; margin: 0 0 20px 0; line-height: 1.2; }
    .wstepOmnie { font-size: 1.1rem; line-height: 1.7; color: #333D36; margin-bottom: 30px; text-align: justify; }
    .naglowekMaly { font-size: 1.2rem; color: #2C3E30; font-weight: 700; margin-bottom: 15px; border-bottom: 2px solid #EFEDE6; padding-bottom: 10px; display: inline-block; }

    .listaKariery { list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 15px; }
    .listaKariery li { position: relative; padding-left: 20px; }
    .listaKariery li::before { content: ""; position: absolute; left: 0; top: 8px; width: 8px; height: 8px; border-radius: 50%; background: #5A7D6C; }
    .listaKariery strong { display: block; color: #2C3E30; font-size: 1.05rem; }
    .listaKariery span { color: #5C6660; font-size: 0.95rem; }

    .cytatMotto { margin-top: auto; padding-top: 20px; border-top: 1px solid rgba(44, 62, 48, 0.1); font-style: italic; color: #2C3E30; display: flex; gap: 10px; font-weight: 500; }

    .ukladOmniePrawa {
        position: relative;
        height: 100%; 
        width: 100%;
        border-radius: 24px;
        overflow: hidden;
        box-shadow: 0 20px 40px rgba(0,0,0,0.1);
    }

    .zdjecieProfilowe {
        width: 100%;
        height: 100%;
        background: url("/blacknwhite.jpg") center/cover no-repeat;
        filter: sepia(10%) contrast(0.95);
        transition: transform 0.9s ease;
    }

    .ukladOmniePrawa:hover .zdjecieProfilowe { 
        transform: scale(1.11); 
    }

    @media (max-width: 900px) {
        .ukladOmnie {
            grid-template-columns: 1fr;
            gap: 0;
            align-items: flex-start;
        }
        .ukladOmnie > div {
             height: auto;
        }

        .ukladOmniePrawa {
            display: none;
        }
        
        .sekcjaOmnie {
            background: 
                linear-gradient(rgba(255, 255, 255, 0.4), rgba(255, 255, 255, 0.4)),
                url("/blacknwhite.jpg") center/cover no-repeat;
            background-attachment: fixed;
            padding: 40px 15px;
        }
        
        .kartaOmnie {
            background: rgba(255, 255, 255, 0.92); 
            backdrop-filter: blur(5px);
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            border: 1px solid rgba(255,255,255,0.5);
            padding: 50px 20px;
            height: 100%;
        }
    }
</style>