<script setup>
import { ref } from 'vue';

const curCarouselIdx = ref(0);

const changeCorouselIdx = e => {
  curCarouselIdx.value = +e.target.id;
};
</script>

<template>
  <section id="wrapper">
    <article>
      <header id="main-header">
        <nav>
          <ul @click="changeCorouselIdx">
            <li class="hover-green" id="0">Tab 1</li>
            <li class="hover-gray" id="1">Tab 2</li>
            <li class="hover-purple" id="2">Tab 3</li>
          </ul>
        </nav>
      </header>
      <main>
        <section v-if="curCarouselIdx === 0" class="article green" id="article-1">
          <h1>This is article <span class="article-number">#1</span></h1>
          <p>
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Sapiente atque nulla neque fugiat? Veritatis asperiores
            necessitatibus, minus consequuntur commodi error saepe, hic repellat excepturi ut sequi eius illum deleniti pariatur!
          </p>
        </section>
        <section v-if="curCarouselIdx === 1" class="article gray" id="article-2">
          <h1>This is article <span class="article-number">#1</span></h1>
          <p>
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Sapiente atque nulla neque fugiat? Veritatis asperiores
            necessitatibus, minus consequuntur commodi error saepe, hic repellat excepturi ut sequi eius illum deleniti pariatur!
          </p>
        </section>
        <section v-if="curCarouselIdx === 2" class="article purple" id="article-3">
          <h1>This is article <span class="article-number">#1</span></h1>
          <p>
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Sapiente atque nulla neque fugiat? Veritatis asperiores
            necessitatibus, minus consequuntur commodi error saepe, hic repellat excepturi ut sequi eius illum deleniti pariatur!
          </p>
        </section>
      </main>
    </article>
  </section>
</template>

<style scoped>
* {
  --border-color: #cecece;
  --main-color: #eeeeee;
  --header-color: #e8e8e8;
}

h1 {
  font-size: 1.75rem;
}

p {
  font-size: 1.075rem;
}

#wrapper {
  height: 100vh;
  background-color: #e8e8e8;
  display: flex;
  align-items: center;
  justify-content: center;
}

article {
  width: 640px;
  border-radius: 0.5rem;
  overflow: hidden;
  border: 2px solid var(--border-color);
}

#main-header nav ul {
  display: flex;
  flex-direction: row;

  list-style: none;
  border-bottom: 2px solid var(--border-color);
  padding: 0.75rem;
  gap: 0.5rem;

  background-color: var(--header-color);
  color: #444444;
}

#main-header nav li {
  font-size: 1.15rem;
  text-align: center;
  flex-grow: 1;
  max-width: 5rem;
  padding: 0.5rem;

  border-radius: 0.25rem;

  cursor: pointer;

  transition: all 100ms ease-in-out;
}

.hover-green:hover {
  background-color: #04a96d;
  color: #ffffff;
}

.hover-gray:hover {
  background-color: #272a35;
  color: #ffffff;
}

.hover-purple:hover {
  background-color: #9663f6;
  color: #ffffff;
}

.green {
  background-color: #04a96d;
}

.gray {
  background-color: #272a35;
}

.purple {
  background-color: #9663f6;
}

main {
  padding: 2rem;
  background-color: var(--main-color);
}

.article {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  border-radius: 0.5rem;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 13px 27px -5px, rgba(0, 0, 0, 0.3) 0px 8px 16px -8px;
}

.hidden {
  display: none;
}

.article h1 {
  color: white;
}

.article p {
  color: #ffffffdd;
}
</style>
