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
    <floaty-section id="Map" class="map">
      <h2 class="map-text" data-depth="0.1">
        <span class="map-text-content">
          Les ciutats
          <animated-underline id="MapTextLine1">més</animated-underline><br>
          <animated-underline id="MapTextLine2">visitades</animated-underline>
          d'Europa<br>
          tenen taxa turística
        </span>
      </h2>
      <tax-map />
    </floaty-section>
    <page-section id="Lie" class="lie">
      Lie
    </page-section>
    <page-section id="Funding" class="funding">
      Funding
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
