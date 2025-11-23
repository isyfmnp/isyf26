<template>
  <Masthead>
    <h1>About Singapore</h1>
    <h3></h3>
  </Masthead>

  <main>
    <section>
      <h2>
        Singapore Locale
      </h2>

      <p>
      </p>

      <PhotoCarousel :images="carouselImages" />
    </section>

  </main>
</template>

<style>
.masthead::before {
  color: var(--bg);
  background-image: url("https://upload.wikimedia.org/wikipedia/commons/5/54/Singapore_Skyline_at_Night_with_Black_Sky_%28banner_esVoy%29.JPG");
  filter: brightness(40%);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 43% 50%;
}
section.goals {
  border: 1px solid black;
  border-radius: 16px;
  padding: 0;
  overflow: hidden;
  margin-inline: -0.75rem;
}
.goals > * {
  padding-inline: 1rem;
}
.goals > * + * {
  border-top: 1px solid black;
}
.goals h2 {
  margin: 0;
  padding-block: 0.5rem;
}
.goal {
  display: grid;
  grid-template-columns: 1rem 1fr;
  padding-left: 0;
}
.goal::before {
  content: "";
  display: inline-block;
  background-color: purple;
  border-right: 1px solid var(--fg);
}
.goal > * {
  padding-left: 1rem;
}

.red::before {
  background-color: var(--red);
}
.green::before {
  background-color: var(--green);
}
.purple::before {
  background-color: var(--purple);
}
</style>

<style scoped>
.collapsible {
  background-color: #eee;
  color: #444;
  cursor: pointer;
  padding: 18px;
  width: 100%;
  border: none;
  text-align: left;
  outline: none;
  font-size: 15px;
}

.active,
.collapsible:hover {
  background-color: #ccc;
}

.content {
  padding: 0 18px;
  display: none;
  overflow: hidden;
  background-color: #f1f1f1;
}
</style>

<script setup>
import PrimaryHighlight from "../components/primaryHighlight.vue";
import PhotoCarousel from "~/components/carousel/PhotoCarousel.vue";
import { ref, watch, onMounted, onUnmounted } from "vue";
definePageMeta({
  layout: "masthead",
});

// Carousel images with transparent overlay text
const carouselImages = [
  {
    src: "/images/singapore-skyline.jpg",
    caption: "Singapore Skyline",
    description: "Experience the stunning cityscape of Singapore, a global hub of innovation and culture. The iconic Marina Bay Sands and Gardens by the Bay showcase the perfect blend of nature and modern architecture.",
    alt: "Singapore skyline"
  },
  {
    src: "/images/marina-bay-sands.jpg",
    caption: "Marina Bay Area",
    description: "Marina Bay is the heart of Singapore's business and entertainment district. This waterfront precinct features world-class convention facilities, museums, and cultural attractions.",
    alt: "Marina Bay waterfront"
  },
  {
    src: "/images/gardens-by-the-bay.jpg",
    caption: "Gardens by the Bay",
    description: "An iconic horticultural attraction spanning 101 hectares. The Supertree Grove and Cloud Forest dome represent Singapore's commitment to sustainability and green innovation.",
    alt: "Gardens by the Bay Supertrees"
  },
  {
    src: "/images/art-science-museum.webp",
    caption: "Singapore Art and Science Museum",
    description: "A space for art, science, and human spirit, with 33 galleries showcasing a multidisciplinary space celebrating cosmology, couture, environmental justice, and other cutting edge innovation.",
    alt: "The ArtScience Museum, Singapore"
  },
];

onMounted(() => {
  var coll = document.getElementsByClassName("collapsible");
  var i;
  for (i = 0; i < coll.length; i++) {
    coll[i].addEventListener("click", function () {
      this.classList.toggle("active");
      var content = this.nextElementSibling;
      if (content.style.display === "block") {
        content.style.display = "none";
      } else {
        content.style.display = "block";
      }
    });
  }
});
</script>
