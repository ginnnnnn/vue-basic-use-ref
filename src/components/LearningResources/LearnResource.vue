<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat" @click="deleteStoredResourse(id)"
          >Delete</base-button
        >
      </header>
      <p>{{ description }}</p>
      <nav>
        <a :href="link">View Resourse</a>
      </nav>
    </base-card>
  </li>
  <h2></h2>
</template>

<script>
export default {
  props: ['title', 'description', 'link', 'id'],
  inject: ['deleteStoredResourse']
};
</script>
<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>
