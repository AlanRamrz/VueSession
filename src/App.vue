<template>
  <div id="app">
    <h1 v-if="$session.exists()">Common</h1>
    <router-view/>
  </div>
</template>
