<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
   <nav class="navbar navbar-expand-lg navbar-light bg-light"><!--bootstrap navbar-->
        <div class="container-fluid">
            <!-- <a class="navbar-brand" href="#">Individuell inlämningsuppgift Labb 2</a> -->
            <RouterLink class="navbar-brand" to="/">Individuell inlämningsuppgift Labb 2</RouterLink>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <!-- <a class="nav-link active" aria-current="page" href="#">Home</a> -->
                        <RouterLink class="nav-link active" aria-current="page" to="/">Home</RouterLink>
                    </li>
                    <li class="nav-item">
                        <!-- <a class="nav-link" href="#">About</a> -->
                        <RouterLink class="nav-link" to="/API">Cocktails</RouterLink>
                    </li>
                </ul>
            </div>
        </div>
    </nav>


  <RouterView />
</template>

<style scoped>

</style>
