<template>
  <Masthead>
    <h1>About Singapore</h1>
    <h3>About the event theme and goals!</h3>
  </Masthead>

  <main>
    <section>
      <h2>
        About Singapore
        
      </h2>

      <p>
        
      </p>
    </section>

   
  </main>
</template>

<style>
.masthead::before {
  color: var(--bg);
  background-image: url("/images/aboutbg2.webp");
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
import { ref, watch, onMounted, onUnmounted } from "vue";
definePageMeta({
  layout: "masthead",
});

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
