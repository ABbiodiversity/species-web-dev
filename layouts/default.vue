<template>
<div>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://abmi.ca">
        <img src="~/static/abmi-logo-grey.png" alt="ABMI">
      </a>
      <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbar" class="navbar-menu">
      <div class="navbar-start">
        <a class="navbar-item">
          <nuxt-link to="/">Species Website</nuxt-link>
        </a>

        <div class="navbar-item has-dropdown is-hoverable">
          <a class="navbar-link">
            Species
          </a>
          <div class="navbar-dropdown">
            <a class="navbar-item">
              <a href="/mammals-camera/">Mammals (Camera)</a>
            </a>
            <a class="navbar-item">
              <a href="/birds/">Birds</a>
            </a>
            <a class="navbar-item">
              <a href="/mites/">Mites</a>
            </a>
            <a class="navbar-item">
              <a href="/vplants/">Vascular Plants</a>
            </a>
            <a class="navbar-item">
              <a href="/mosses/">Mosses</a>
            </a>
            <a class="navbar-item">
              <a href="/lichens/">Lichens</a>
            </a>
          </div>
        </div>
        
      </div>
    </div>

  </nav>

  <section>
    <div class="container">
      <div class="columns">
        <div class="column is-10 is-offset-1">        
          <nuxt />
        </div>
      </div>
    </div>
  </section>

  <footer class="footer">
    <div class="container">
      <div class="content has-text-centered">
        <p id="footer">
          &copy; <a href="http://www.abmi.ca/" target=_blank>Alberta Biodiversity Monitoring Institute</a> 
          (2014&ndash;2019) under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/" target=_blank>CC BY-SA 4.0</a> license.          
        </p>
      </div>
    </div>
  </footer>
</div>
</template>
