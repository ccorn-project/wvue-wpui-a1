import { createApp } from 'vue';
import { Button } from 'vant';

const app = createApp();
app.use(Button);

<van-button type="primary">Primary</van-button>
<van-button type="success">Success</van-button>
<van-button type="default">Default</van-button>
<van-button type="danger">Danger</van-button>
<van-button type="warning">Warning</van-button>



<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
