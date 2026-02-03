<script lang="ts">
  const rok = new Date().getFullYear();
  
  const daneFirmy = {
    nazwa: "Indywidualna działalność gospodarcza: Honorata Dawid",
    nip: "7511474211",
    adres: "ul. Byczyńska 10/1, 46-200 Kluczbork"
  };
</script>

<section class="sekcja sekcjaPolityka">
  <div class="kontener politykaKontener">
    
    <header class="politykaNaglowek">
      <a href="/" class="linkPowrotu">← Powrót do strony głównej</a>
      <h1>Polityka prywatności</h1>
      <p class="wstep">
        Jako podmiot wykonujący działalność leczniczą, przykładam szczególną wagę do ochrony Twoich danych. 
        Niniejsza dokumentacja spełnia wymogi RODO oraz Ustawy o prawach pacjenta i Rzeczniku Praw Pacjenta.
      </p>
    </header>

    <div class="politykaTresc">
      <article>
        <h2>1. Administrator danych</h2>
        <p>
          Administratorem Twoich danych osobowych jest:<br>
          <strong>{daneFirmy.nazwa}</strong><br>
          NIP: {daneFirmy.nip}<br>
          Adres: {daneFirmy.adres}<br>
          Kontakt: <a href="mailto:honoratadawid@gmail.com">honoratadawid@gmail.com</a>
        </p>
      </article>

      <article>
        <h2>2. Dokumentacja medyczna i dane wrażliwe</h2>
        <p>
          W ramach świadczonych usług pielęgniarskich przetwarzam dane dotyczące stanu zdrowia. 
          Podstawą prawną ich przetwarzania jest <strong>Art. 9 ust. 2 lit. h RODO</strong> w związku z ustawą o prawach pacjenta.
        </p>
        <div class="notatka-wazne">
          <strong>Ważne:</strong> Serwis służy głównie do kontaktu organizacyjnego. Prosimy o nieprzesyłanie szczegółowych wyników badań 
          poprzez formularz kontaktowy. Dokumentację medyczną wymieniamy podczas wizyty lub dedykowanymi kanałami bezpiecznymi.
        </div>
      </article>

      <article>
        <h2>3. Szczegółowy wykaz przetwarzania</h2>
        <div class="tabelaWrapper">
          <table class="tabelaRODO">
            <thead>
              <tr>
                <th>Cel przetwarzania</th>
                <th>Podstawa prawna</th>
                <th>Okres przechowywania</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><strong>Kontakt i obsługa zapytania</strong></td>
                <td>Art. 6 ust. 1 lit. f RODO (prawnie uzasadniony interes)</td>
                <td>Do czasu zakończenia korespondencji.</td>
              </tr>
              <tr>
                <td><strong>Realizacja świadczeń zdrowotnych</strong> (Dokumentacja medyczna)</td>
                <td>Art. 9 ust. 2 lit. h RODO w zw. z ustawą o prawach pacjenta</td>
                <td><strong>Zasadniczo 20 lat</strong> od końca roku, w którym dokonano ostatniego wpisu.</td>
              </tr>
              <tr>
                <td><strong>Rozliczenia i księgowość</strong></td>
                <td>Art. 6 ust. 1 lit. c RODO (obowiązek prawny)</td>
                <td>5 lat od końca roku podatkowego.</td>
              </tr>
            </tbody>
          </table>
        </div>
      </article>

      <article>
        <h2>4. Odbiorcy danych</h2>
        <p>Twoje dane mogą być przekazywane wyłącznie zaufanym podmiotom:</p>
        <ul class="listaStandard">
          <li>Biuro rachunkowe (obsługa księgowa faktur/rachunków).</li>
          <li>Dostawca hostingu i poczty e-mail (przechowywanie korespondencji).</li>
          <li>Podmioty uprawnione na podstawie przepisów prawa (np. NFZ, Sanepid, organy nadzorcze).</li>
        </ul>
      </article>

      <article>
        <h2>5. Twoje prawa</h2>
        <ul class="listaPraw">
          <li>Prawo dostępu do danych oraz otrzymania ich kopii (w tym dokumentacji medycznej).</li>
          <li>Prawo do sprostowania danych.</li>
          <li>Prawo do usunięcia danych (nie dotyczy danych w dokumentacji medycznej, które muszę przechowywać przez okresy ustawowe).</li>
          <li><strong>Prawo do cofnięcia zgody</strong> w dowolnym momencie (jeśli przetwarzanie odbywa się na podstawie zgody).</li>
          <li>Prawo wniesienia skargi do Prezesa UODO (ul. Stawki 2, 00-193 Warszawa).</li>
        </ul>
      </article>

      <article>
        <h2>6. Cookies</h2>
        <p>Strona używa wyłącznie niezbędnych ciasteczek technicznych do poprawnego wyświetlania treści.</p>
      </article>

      <footer>
        <p>Ostatnia aktualizacja: 2025-12-27 </p> <p>© {rok} Honorata Dawid</p>
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
  </div>
</section>

<style>
  .sekcjaPolityka {
    padding-top: 140px;
    background: #FAF9F6;
    min-height: 100vh;
  }

  .politykaKontener {
    max-width: 850px;
    margin: 0 auto;
    padding: 0 20px 80px;
  }

  .politykaNaglowek { margin-bottom: 50px; }
  .linkPowrotu { color: #5A7D6C; text-decoration: none; font-weight: 600; display: block; margin-bottom: 20px; font-size: 0.9rem; }
  
  h1 { font-size: 2.5rem; color: #2C3E30; margin-bottom: 20px; font-family: 'Merriweather', serif; }
  h2 { font-size: 1.5rem; color: #2C3E30; margin: 40px 0 20px; border-left: 4px solid #5A7D6C; padding-left: 15px; font-family: 'Merriweather', serif; }

  .politykaTresc p { line-height: 1.7; color: #333D36; margin-bottom: 15px; }

  a[href] { color: #5A7D6C; text-decoration: underline; }

  .notatka-wazne {
    background: #fff5f5;
    border: 1px solid #feb2b2;
    padding: 20px;
    border-radius: 12px;
    margin: 20px 0;
    font-size: 0.95rem;
    color: #c53030;
  }

  .tabelaWrapper { overflow-x: auto; margin: 30px 0; border-radius: 12px; }
  .tabelaRODO {
    width: 100%;
    border-collapse: collapse;
    background: #fff;
  }
  .tabelaRODO th, .tabelaRODO td {
    padding: 18px;
    text-align: left;
    border-bottom: 1px solid #f0f0f0;
    font-size: 0.9rem;
  }
  .tabelaRODO th { background: #5A7D6C; color: #fff; font-weight: 600; }

  .listaStandard, .listaPraw { padding-left: 20px; color: #333D36; }
  .listaStandard li, .listaPraw li { margin-bottom: 12px; line-height: 1.5; }

  footer { margin-top: 60px; padding-top: 30px; border-top: 1px solid #e0e0e0; font-size: 0.85rem; color: #5C6660; text-align: center; }

  @media (max-width: 600px) {
    .sekcjaPolityka { padding-top: 110px; }
    h1 { font-size: 1.8rem; }
    .tabelaRODO th, .tabelaRODO td { padding: 12px; }
  }
</style>