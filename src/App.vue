<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="page-wrapper">

<!-- Header -->
  <section id="header">

    <!-- Logo -->
      <h1><a href="index.html">SF BOOKS</a></h1>

    <!-- Nav -->
      <nav id="nav">
        <ul>
          <li class="current"><a href="index.html">Home</a></li>
          <!-- <li><a href="left-sidebar.html">Pokémons</a></li> -->
          <li><router-link to="/books">Admin</router-link></li>
        </ul>
      </nav>

    <!-- Banner -->
    <RouterView />

    <!-- Intro -->


  </section>

<!-- Footer -->
  <section id="footer">
    <div class="container">
      <div class="row">						
        <div class="col-12">

          <!-- Copyright -->
            <div id="copyright">
              <ul class="links">
                <li>&copy;Yamayo . All rights reserved.</li><li>Design: <a href="http://html5up.net">HTML5 UP</a></li>
              </ul>
            </div>

        </div>
      </div>
    </div>
  </section>

</div>
</template>

<style scoped>
</style>
