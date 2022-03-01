<template>
  <main>
    <floaty-section id="Intro" class="intro">
      <h2 class="intro-text" data-depth="0.2">
        <span class="intro-text-content">
          La <animated-underline id="IntroTextLine">taxa</animated-underline><br>
          <animated-underline id="IntroText2" :delay="0.25">turística</animated-underline><br>
          afecta el<br>
          turisme?
        </span>
      </h2>
      <div class="intro-postcard" data-depth="0.3">
        <img src="~assets/images/cities/benidorm.jpg" alt="Els gratacels i la costa de Benidorm">
      </div>
    </floaty-section>
    <div class="intro-plane-scene">
      <animated-plane class="intro-plane" />
    </div>
    <page-section id="Map" class="map" no-container>
      <div class="shift">
        <div class="container">
          <h2 class="map-text map-text-first">
            <span class="map-text-content">
              Les ciutats
              <animated-underline id="MapTextLine1">més</animated-underline><br>
              <animated-underline id="MapTextLine2">visitades</animated-underline>
              d'Europa<br>
              tenen taxa turística
            </span>
          </h2>
        </div>
        <tax-map />
        <div class="container shift-md">
          <h2 class="map-text map-text-valencia">
            <span class="map-text-content">
              <animated-underline id="ValenciaText">València</animated-underline>
              és la <animated-circle id="ValenciaCircle" :delay="1">#15</animated-circle>
              ciutat<br>
              més visitada d'Europa
            </span>
          </h2>
          <p class="headline-sm mb-5">
            I encara no tenim taxa turística.
          </p>
          <p class="headline-sm">
            Altres com Peníscola, Calp, Orpesa o Benidorm també són destins de referencia
            europeus i converteixen el territori valencià en<br>
            <animated-underline id="ValenciaMostVisited">un dels més visitats del món.</animated-underline>
          </p>
        </div>
      </div>
    </page-section>
    <page-section id="Lie" class="lie">
      <bob-title />
      <div class="lie-text-animated">
        <animated-underline id="LieOverTitle">Mentida!</animated-underline>
      </div>
      <h2 class="lie-text mt-4">Alguna vegada has deixat de visitar una ciutat per la taxa turística?</h2>
      <span class="lie-text-content">De fet, ciutats amb menys turisme ja tenen taxa turística</span>
      <cities-marquee lang="cas"/>
      <span class="lie-text-content">
        I territoris com Catalunya i les Illes Balears la van implantar
        <animated-underline id="GraphTextLine">sense cap efecte negatiu</animated-underline>
      </span>
      <div class="lie-graphs-section mt-6">
        <div class="lie-graphs">
          <img src="@/assets/images/graphs/catalunya.svg" alt="Gràfica de línies que mostra el creixement del turisme en Catalunya, que no decau quan s'aplica la taxa turística en 2012">
          <img src="@/assets/images/graphs/balears.svg" alt="Gràfica de línies que mostra el creixement del turisme en Les Illes Balears, que no decau quan s'aplica la taxa turística en 2016">
        </div>
        <div class="mt-3">Font: Institut Nacional d'Estadística (INE)</div>
      </div>
    </page-section>
    <page-section id="Funding" class="funding">
      <p class="funding-text">
        La taxa turística no posa en perill<br>
        el sector turístic, i a més <animated-underline id="FundingText1">millora</animated-underline><br class="d-none d-md-block">
        <animated-underline id="FundingText2" :delay=".5">la qualitat de vida</animated-underline> de les ciutats i<br>
        <animated-underline id="FundingText3" :delay="1">enforteix el turisme</animated-underline> en el territori.
      </p>
      <p class="funding-text">
          Esta xicoteta aportació crearía un<br>
          <animated-underline id="FundingText4" :delay="1.5">Fons de sostenibilitat turística</animated-underline> per invertir<br class="d-none d-md-block">
          en serveis com...
      </p>

      <ul class="funding-items">
        <funding-item id="Cleaning">
          Neteja de carrers
          <img src="~/assets/images/funding/netejadora.webp" alt="Máquina netejadora de carrer">
        </funding-item>
        <funding-item id="ParksAndRec">
          Manteniment de Parcs
          <img src="~/assets/images/funding/arbre.webp" alt="Arbre de tronc ample i amb copa poblada de fulles">
        </funding-item>
        <funding-item id="Five-O">
          Seguretat
          <img src="~/assets/images/funding/five-o.webp"  alt="Cotxe de la Policia local de València">
        </funding-item>
        <funding-item id="Transport">
          Transport públic
          <img src="~/assets/images/funding/bus.webp" alt="Autobús de la EMT de València">
        </funding-item>
        <funding-item id="Heritage">
          Protecció del patrimoni
          <img src="~/assets/images/funding/micalet.webp" alt="Torre del Micalet de València">
        </funding-item>
        <funding-item id="Meritxell">
          Revertir impacte ambiental
          <img src="~/assets/images/funding/avio.webp" alt="Avió comercial de passatgers">
        </funding-item>
        <funding-item id="Baywatch">
          Manteniment de platges
          <img src="~/assets/images/funding/socorrista.webp" alt="Cadira de socorrista de platja amb una socorrista asseguda d'esquenes.">
        </funding-item>
      </ul>
    </page-section>
    <page-section id="Conclusions" class="conclusions">
      <div class="headline-sm">En resum...</div>
      <div class="headline-2xl mt-4">Sí.</div>
      <div class="headline-sm mt-4">La taxa turística afecta el turisme. Molt positivament. És just que els turistes contribuisquen a pagar el manteniment dels serveis dels que disfruten.</div>
      <div class="headline-sm mt-4">A més, la taxa turística ajuda a crear un model de turisme amb projecció de futur, de qualitat, sostenible i que genera més riquesa. </div>
      <div class="conclusions-annex-title">Més informació</div>
      <div class="conclusions-annex-grid mt-4">
        <a class="conclusions-annex-card row-span-2 focus-dark" href="https://valenciaplaza.com/tasa-turistica-cataluna-baleares-197-millones-ingresos-mas-viajeros" target="_blank" rel="noopener noreferer">
          <h2>La tasa turística en Cataluña y Baleares: 197 millones en ingresos y más viajeros hasta la covid</h2>
          <div class="mt-auto">Valencia Plaza</div>
        </a>
        <a class="conclusions-annex-card conclusions-annex-document focus-dark" href="https://www.researchgate.net/publication/347919126_Tourist_Tax_to_Improve_Sustainability_and_the_Experience_in_Mass_Tourism_Destinations_The_Case_of_Andalusia_Spain" target="_blank" rel="noopener noreferer">
          <span class="document-tag">PDF</span> Tourist Tax to Improve Sustainability and the Experience in Mass Tourism Destinations: The Case of Andalusia (Spain)
        </a>
        <a class="conclusions-annex-card row-span-3 focus-dark" href="https://valenciaplaza.com/la-tasa-turistica-por-que-solo-debemos-pagar-los-valencianos" target="_blank" rel="noopener noreferer">
          <h2>La tasa turística: ¿por qué solo debemos pagar los valencianos?</h2>
          <div class="mt-auto">Valencia Plaza</div>
        </a>
        <a class="conclusions-annex-card conclusions-annex-document focus-dark" href="https://www.liligo.es/magazine-viajes/tasas-turisticas-espana-europa" target="_blank" rel="noopener noreferer">
          <span class="document-tag">WEB</span> Las tasas turísticas en España y Europa en 2019
        </a>
        <a class="conclusions-annex-card row-span-2 focus-dark" href="https://valenciaplaza.com/la-tasa-turistica-por-que-solo-debemos-pagar-los-valencianos" target="_blank" rel="noopener noreferer">
          <h2>A favor de la tasa turística</h2>
          <div class="mt-auto">Málaga Hoy</div>
        </a>
        <a class="conclusions-annex-card conclusions-annex-document focus-dark" href="https://www.e-unwto.org/doi/pdf/10.18111/9789284421992" target="_blank" rel="noopener noreferer">
          <span class="document-tag">PDF</span> Las emisiones de CO2 del sector turístico
        </a>
      </div>
    </page-section>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>
