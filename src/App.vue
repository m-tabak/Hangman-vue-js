<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="wrapper">
    <header>
      <img alt="logo" src="@/assets/logo.svg" width="125" height="125" />
      <h1>Hangman</h1>
      <nav>
        <RouterLink to="/">Game</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </header>
    <RouterView />
  </div>
</template>

<style>
  .wrapper{
    margin: 0 5px;
  }
  @media (min-width: 1024px){
    .wrapper{ 
      margin: 0 15%;
    }
  }

  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid grey;
  }

  header h1{
    display: inline-block;
  }

  nav a{
    margin: 0.5rem 1rem;
    text-decoration: none;
    color: blueviolet;
  }

  .router-link-exact-active{
    color: rgb(57, 57, 57);
    border-bottom: 1px solid rgb(57, 57, 57);
  }
</style>
