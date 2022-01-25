<script lang="ts">
import { defineComponent } from 'vue';
import Avatar from '@/vue-avatar-sdh.vue';

export default defineComponent({
  name: 'ServeDev',
  components: {
    Avatar
  },
  data () {
    return {
      customstyle1: {
        borderRadius: '10px',
        color: '#fff',
        backgroundColor: '#ff4081',
        border: '3px solid #d6054c',
      },
      customstyle2: {
        borderRadius: '5px',
        padding: '0.6rem',
      },
    }
  }
});
</script>

<template>
  <div id="app">
    <h5>Basic Usage <code>username</code></h5>
    <div class="row">
      <div class="items">
        <Avatar username="Rickdev" :inline="true" />
      </div>
      <div class="items">
        <Avatar username="Rickdev Hazra" :inline="true" />
      </div>
      <div class="items">
        <Avatar username="Dr. Soumyadip Hazra" :inline="true" />
      </div>
      <div class="items">
        <Avatar username="Rickdev Kumar Hazra" :inline="true" :maxAllowedLength="3" />
      </div>
    </div>

    <h5>Background Color <code>backgroundColor</code></h5>
    <div class="row">
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#F44336" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#FF4081" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#9C27B0" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#673AB7" />
      </div>
    </div>

    <h5>Foreground Color <code>color</code></h5>
    <div class="row">
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" color="#F44336" backgroundColor="#eadede" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" color="#FF4081" backgroundColor="#eadede" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" color="#9C27B0" backgroundColor="#eadede" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" color="#673AB7" backgroundColor="#eadede" />
      </div>
    </div>

    <h5>Lighten Color <code>lighten</code> </h5>
    <div class="row">
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :lighten="20" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :lighten="40" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :lighten="60" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :lighten="80" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :lighten="100" />
      </div>
    </div>

    <h5>Border Radius <code>rounded</code></h5>
    <div class="row">
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :rounded="true" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :rounded="false" />
      </div>
    </div>

    <h5>Sizes <code>size</code></h5>
    <div class="row">
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :size="40" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :size="60" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :size="70" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :size="80" />
      </div>
    </div>

    <h5>Custom Style <code>customStyle</code></h5>
    <div class="row">
      <div class="items">
        <Avatar username="Soumyadip Hazra" :customStyle="customstyle1" />
      </div>
      <div class="items">
        <Avatar username="Soumyadip Hazra" :inline="true" :customStyle="customstyle2" />
      </div>
    </div>
  </div>
</template>

<style>
.row {
  display: flex;
}
h5 {
  width: 100%;
}
.items {
  margin-right: 1rem;
}
code {
  background: #625f5f;
  padding: 5px;
  color: #d9d9d9;
  border-radius: 5px;
}
</style>
