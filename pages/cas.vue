<template>
  <main>
    <page-section id="Intro" class="intro">
      <h2 class="intro-text" data-depth="0.2">
        <span class="intro-text-content">
          La <animated-underline id="IntroTextLine">tasa</animated-underline><br>
          <animated-underline id="IntroText2" :delay="0.25">turística</animated-underline><br>
          afecta al<br>
          turismo?
        </span>
      </h2>
      <div class="intro-postcard" data-depth="0.3">
        <img src="~assets/images/cities/benidorm.jpg" alt="Los rasacacielos y la costa de Benidorm">
      </div>
      <animated-plane class="intro-plane" data-depth="0.1" />
    </page-section>
    <page-section id="Map" class="map" no-container>
      <div class="shift">
        <div class="container">
          <h2 class="map-text map-text-first">
            <span class="map-text-content">
              Las ciudades
              <animated-underline id="MapTextLine1">más</animated-underline><br>
              <animated-underline id="MapTextLine2">visitadas</animated-underline>
              de Europa<br>
              tienen tasa turística
            </span>
          </h2>
        </div>
        <tax-map />
        <div class="container shift-md">
          <h2 class="map-text map-text-valencia">
            <span class="map-text-content">
              <animated-underline id="ValenciaText">València</animated-underline>
              es la <animated-circle id="ValenciaCircle" :delay="1">#15</animated-circle>
              ciudad<br>
              más visitada de Europa
            </span>
          </h2>
          <p class="headline-sm mb-5">
            Y aún no tenemos tasa turística.
          </p>
          <p class="headline-sm">
            Otras como Peníscola, Calp, Orpesa o Benidorm también son destinos de referencia
            europeos y covierten el territorio valenciano en<br>
            <animated-underline id="ValenciaMostVisited">uno de los más visitados del mundo.</animated-underline>
          </p>
        </div>
      </div>
    </page-section>
    <page-section id="Lie" class="lie">
      <bob-title />
      <div class="lie-text-animated">
        <animated-underline id="LieOverTitle">Mentira!</animated-underline>
      </div>
      <h2 class="lie-text mt-4">Alguna vez has dejado de visitar una ciudad por la tasa turística?</h2>
      <span class="lie-text-content">De hecho, ciudades con menos turismo ya tienen tasa turística</span>
      <cities-marquee />
      <span class="lie-text-content">
        Y territorios como Catalunya y les Illes Balears la implantaron
        <animated-underline id="GraphTextLine">sin ningún efecto negativo</animated-underline>
      </span>
      <div class="lie-graphs-section mt-6">
        <div class="lie-graphs">
          <img src="@/assets/images/graphs/catalunya-cas.svg" alt="Gráfica de líneas que muestra el crecimiento del turismo en Catalunya, que no decae cuando se aplica la tasa turística en 2012">
          <img src="@/assets/images/graphs/balears-cas.svg" alt="Gráfica de líneas que muestra el crecimiento del turismo en les Illes Balears, que no decae cuando se aplica la tasa turística en 2016">
        </div>
        <div class="mt-3">Fuente: Instituto Nacional de Estadística (INE)</div>
      </div>
    </page-section>
    <page-section id="Funding" class="funding">
      <p class="funding-text">
        La tasa turística no pone en peligro<br>
        el sector turístico, y además <animated-underline id="FundingText1">mejora</animated-underline><br>
        <animated-underline id="FundingText2" :delay=".5">la calidad de vida de las ciudades</animated-underline> y<br>
        <animated-underline id="FundingText3" :delay="1">refuerza el turismo</animated-underline> en el territorio.
      </p>
      <p class="funding-text">
          Esta pequeña aportación crearía un<br>
          <animated-underline id="FundingText4" :delay="1.5">Fondo de sostenibilidad turística</animated-underline> para invertir<br>
          en servicios como...
      </p>

      <ul class="funding-items">
        <funding-item id="Cleaning">
          Limpieza de calles
          <img src="~/assets/images/funding/netejadora.webp" alt="Máquina limpiadora de calle">
        </funding-item>
        <funding-item id="ParksAndRec">
          Mantenimento de Parques
          <img src="~/assets/images/funding/arbre.webp" alt="Árbol de tronco ancho y con la copa poblada de hojas">
        </funding-item>
        <funding-item id="Five-O">
          Seguridad
          <img src="~/assets/images/funding/five-o.webp"  alt="Coche de la Policia local de València">
        </funding-item>
        <funding-item id="Transport">
          Transporte público
          <img src="~/assets/images/funding/bus.webp" alt="Autobús de la EMT de València">
        </funding-item>
        <funding-item id="Heritage">
          Protección del patrimonio
          <img src="~/assets/images/funding/micalet.webp" alt="Torre del Micalet de València">
        </funding-item>
        <funding-item id="Meritxell">
          Revertir el impacto ambiental
          <img src="~/assets/images/funding/avio.webp" alt="Avión comercial de pasajeros">
        </funding-item>
        <funding-item id="Baywatch">
          Mantenimento de playas
          <img src="~/assets/images/funding/socorrista.webp" alt="Silla de socorrista de playa con una socorrista sentada de espaldas.">
        </funding-item>
      </ul>
    </page-section>
    <page-section id="Conclusions" class="conclusions">
      <div class="headline-sm">En resumen...</div>
      <div class="headline-2xl mt-4">Sí.</div>
      <div class="headline-sm mt-4">La tas turística afecta al turismo. Muy positivamente. Es justo que los turistas contribuyan a pagar el mantenimiento de servicios de los que disfrutan.</div>
      <div class="headline-sm mt-4">Además, la tasa turística ayuda a crear un modelo de turismo con proyección de futuro, de calidad, sostenible y que genera más riqueza. </div>
      <div class="conclusions-annex-title">Más información</div>
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
import { title, description, keywords, url } from '@/content/meta'

export default {
  name: 'IndexPage',

  head () {
    return {
      title: title.cas,
      htmlAttrs: {
        lang: 'es',
      },
      meta: [
        { hid: 'description', name: 'description', content: description.cas },
        { hid: 'keywords', name: 'keywords', content: keywords.cas },
        { hid: 'og:locale', property: 'og:locale', content: 'es' },
        { hid: 'og:description', property: 'og:description', content: description.cas },
        { hid: 'og:image', property: 'og:image', content: '/ogimage-cas.png' },
        { hid: 'og:url', property: 'og:url', content: url.cas },
        { hid: 'twitter:title', property: 'twitter:title', content: title.cas },
        { hid: 'twitter:description', property: 'twitter:description', content: description.cas },
        { hid: 'twitter:image', property: 'twitter:image', content: '/ogimage-cas.png' },
        { hid: 'twitter:url', property: 'twitter:url', content: url.cas }
      ],
    }
  }
}
</script>
