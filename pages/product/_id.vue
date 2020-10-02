<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">
        Anime
      </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse" />

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">
            Link
          </b-nav-item>
          <b-nav-item href="#" disabled>
            Disabled
          </b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <div class="container">
      <b-card no-body class="overflow-hidden mt-5" style="max-width: 640px;">
        <b-row no-gutters>
          <b-col md="6">
            <b-card-img :src="this.$route.params.id.image_url" alt="Image" class="rounded-0" />
          </b-col>
          <b-col md="6">
            <b-card-body :title="this.$route.params.id.title">
              <b-card-text class="container">
                {{ this.$route.params.id.synopsis }}
              </b-card-text>
            </b-card-body>
          </b-col>
        </b-row>
      </b-card>
    </div>
  </div>
</template>
