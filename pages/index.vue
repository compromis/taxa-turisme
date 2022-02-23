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
        <img src="~assets/images/cities/benidorm.jpg" alt="">
      </div>
      <animated-plane class="intro-plane" data-depth="0.1" />
    </floaty-section>
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
      <cities-marquee />
      <span class="lie-text-content">
        I territoris com Catalunya i les Illes Balears la van implantar
        <animated-underline id="GraphTextLine">sense cap efecte negatiu</animated-underline>
      </span>
      <div class="lie-graphs-section mt-6">
        <div class="lie-graphs">
          <img src="@/assets/images/graphs/catalunya.svg" alt="">
          <img src="@/assets/images/graphs/balears.svg" alt="">
        </div>
        <div class="mt-3">Font: Institut Nacional d'Estadística (INE)</div>
      </div>
    </page-section>
    <page-section id="Funding" class="funding">
      <p class="funding-text">
        La taxa turística no posa en perill<br>
        el sector turístic, i a més <animated-underline id="FundingText1">millora</animated-underline><br>
        <animated-underline id="FundingText2" :delay=".5">la qualitat de vida de les ciutats</animated-underline> i<br>
        <animated-underline id="FundingText3" :delay="1">enforteix el turisme</animated-underline> en el territori.
      </p>
      <p class="funding-text">
          Esta xicoteta aportació crearía un<br>
          <animated-underline id="FundingText4" :delay="1.5">Fons de sostenibilitat turística</animated-underline> per invertir<br>
          en serveis com...
      </p>

      <ul class="funding-items">
        <funding-item id="Cleaning">
          Neteja de carrers
          <img src="~/assets/images/funding/netejadora.webp" alt="">
        </funding-item>
        <funding-item id="ParksAndRec">
          Manteniment de Parcs
          <img src="~/assets/images/funding/arbre.webp" alt="">
        </funding-item>
        <funding-item id="Five-O">
          Seguretat
          <img src="~/assets/images/funding/five-o.webp"  alt="">
        </funding-item>
        <funding-item id="Transport">
          Transport públic
          <img src="~/assets/images/funding/bus.webp" alt="">
        </funding-item>
        <funding-item id="Heritage">
          Protecció del patrimoni
          <img src="~/assets/images/funding/micalet.webp" alt="">
        </funding-item>
        <funding-item id="Meritxell">
          Revertir impacte ambiental
          <img src="~/assets/images/funding/avio.webp" alt="">
        </funding-item>
        <funding-item id="Baywatch">
          Manteniment de platges
          <img src="~/assets/images/funding/socorrista.webp" alt="">
        </funding-item>
      </ul>
    </page-section>
    <page-section id="Conclusions" class="conclusions">
      Conclusions
    </page-section>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>
