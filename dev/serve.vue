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
  <div id="container">
    <div class="example-container">
      <h5>Basic Usage <code>username</code></h5>
      <p class="description mb-1">How to pass name to generate initials? It very simple actually. Just pass the <code>username</code> attribute to the <code>&lt;Avatar /&gt;</code> component and it's done. You can also control how many initials will the shown in the avatar.</p>
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
      <div class="row code-block">
        <pre>
          <code>&lt;Avatar username="Rickdev" :inline="true" /&gt;</code>
          <code>&lt;Avatar username="Rickdev Hazra" :inline="true" /&gt;</code>
          <code>&lt;Avatar username="Dr. Soumyadip Hazra" :inline="true" /&gt;</code>
          <code>&lt;Avatar username="Rickdev Kumar Hazra" :inline="true" :maxAllowedLength="3" /&gt;</code>
        </pre>
      </div>
    </div>

    <div class="example-container">
      <h5>Name with abbreviations</h5>
      <p class="description mb-1">What if the username can contain abbreviations? No worries we have got you covered. It'll automatically be parsed out and the name will be taken to generate the Avatar. Also notice the different between the two <code>Dr</code> and <code>Dr.</code></p>
      <div class="row">
        <div class="items">
          <Avatar username="Dr Soumyadip Hazra" :inline="true" />
        </div>
        <div class="items">
          <Avatar username="Dr. Soumyadip Hazra" :inline="true" />
        </div>
      </div>
      <div class="row code-block">
        <pre>
          <code>&lt;Avatar username="Dr Soumyadip Hazra" :inline="true" /&gt;</code>
          <code>&lt;Avatar username="Dr. Soumyadip Hazra" :inline="true" /&gt;</code>
        </pre>
      </div>
    </div>

    <div class="example-container">
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
      <div class="row code-block">
        <pre>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#F44336" /&gt;</code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#FF4081" /&gt;</code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true"  backgroundColor="#9C27B0" /&gt;</code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#673AB7" /&gt;</code>
        </pre>
      </div>
    </div>

    <div class="example-container">
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
      <div class="row code-block">
        <pre>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" color="#F44336" backgroundColor="#eadede" /></code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" color="#FF4081" backgroundColor="#eadede" /></code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" color="#9C27B0" backgroundColor="#eadede" /></code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" color="#673AB7" backgroundColor="#eadede" /></code>
        </pre>
      </div>
    </div>

    <div class="example-container">
      <h5>Lighten Color <code>lighten</code></h5>
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
      <div class="row code-block">
        <pre>
        <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :lighten="20" /></code>
        <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :lighten="40" /></code>
        <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :lighten="60" /></code>
        <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :lighten="80" /></code>
        <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :lighten="100" /></code>
        </pre>
      </div>
    </div>
    
    <div class="example-container">
      <h5>Border Radius <code>rounded</code></h5>
      <div class="row">
        <div class="items">
          <Avatar username="Soumyadip Hazra" :inline="true" :rounded="true" />
        </div>
        <div class="items">
          <Avatar username="Soumyadip Hazra" :inline="true" :rounded="false" />
        </div>
      </div>
      <div class="row code-block">
        <pre>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :rounded="true" /></code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :rounded="false" /></code>
        </pre>
      </div>
    </div>

    <div class="example-container">
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
      <div class="row code-block">
        <pre>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :size="40" /></code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :size="60" /></code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :size="70" /></code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :size="80" /></code>
        </pre>
      </div>
    </div>

    <div class="example-container">
      <h5>Custom Style <code>customStyle</code></h5>
      <div class="row">
        <div class="items">
          <Avatar username="Soumyadip Hazra" :customStyle="customstyle1" />
        </div>
        <div class="items">
          <Avatar username="Soumyadip Hazra" :inline="true" :customStyle="customstyle2" />
        </div>
      </div>
      <div class="row code-block">
        <pre>
          <code>&lt;Avatar username="Soumyadip Hazra" :customStyle="customstyle1" /></code>
          <code>customstyle1: {
  borderRadius: '10px',
  color: '#fff',
  backgroundColor: '#ff4081',
  border: '3px solid #d6054c',
},</code>
          <code>&lt;Avatar username="Soumyadip Hazra" :inline="true" :customStyle="customstyle2" /></code>
          <code>customstyle2: {
  borderRadius: '5px',
  padding: '0.6rem',
},</code>
        </pre>
      </div>
    </div>
  </div>
</template>

<style>
.example-container {
  border: 1px solid #999;
  margin-bottom: 1rem;
  padding: 1rem;
}
.row {
  display: flex;
}
h5 {
  width: 100%;
  font-family: 'Courier New', Courier, monospace;
  font-size: 1.2rem;
  line-height: 14px;
}
p {
  font-family: 'Courier New', Courier, monospace;
  font-size: 1rem;
  width: 60%;
}

.mb-1 {
  margin-bottom: 2rem;
}

.description code {
  margin: 0;
  padding: 2px 5px;
  background-color: #2f2f2f;
}

.items {
  margin-right: 1rem;
}
code {
  background: #625f5f;
  padding: 5px 8px;
  color: #d9d9d9;
  border-radius: 5px;
}
.code-block {
  flex-direction: column;
  background-color: #dadada;
  justify-content: center;
  align-items: flex-start;
  padding: 1rem;
  margin-top: 1rem;
  width: fit-content;
}
.code-block pre {
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 0;
}
.code-block pre code {
  display: flex;
  padding: 1rem;
}
.code-block pre code:not(:first-child) {
  margin-top: 1rem;
}
</style>
