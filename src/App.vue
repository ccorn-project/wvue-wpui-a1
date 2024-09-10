<script setup lang="ts">

import { createApp } from 'vue';
import { ref } from 'vue';
import { showImagePreview } from 'vant';
import enUS from 'vant/es/locale/lang/en-US';
import { Cell, CellGroup } from 'vant';

const showCalendar = ref(false)
const showPopup = ref(false)
const showCascader = ref(false)
const showFloatingPanel = ref(false)
const showKeyboard = ref(false)
const input = ref('')
const date = ref('')
const cascaderValue = ref('')
const activeNames = ref(['1'])
const options = [
  {
    text: 'cica',
    value: '330000',
    children: [{ text: 'acic', value: '330100' }]
  },
  {
    text: 'kutya',
    value: '320000',
    children: [{ text: 'kutyuj', value: '320100' }]
  }
]

const openPopup = () => {
  showPopup.value = true
}
const openFloatingPanel = () => {
  showFloatingPanel.value = true
}
const formatDate = (date: Date) => `${date.getMonth() + 1}/${date.getDate()}`
const onConfirm = (value: Date) => {
  showCalendar.value = false
  date.value = formatDate(value)
}

</script>

<template>
  <section>
    <van-sticky>
      <van-notice-bar
        left-icon="volume-o"
        text="tavel vunet tosza hosszu szoveg"
      />
    </van-sticky>
    <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
      <van-swipe-item>1</van-swipe-item>
      <van-swipe-item>2</van-swipe-item>
      <van-swipe-item>3</van-swipe-item>
      <van-swipe-item>4</van-swipe-item>
    </van-swipe>
    <van-tabs>
      <van-tab title="a 1">
        内容 1
      </van-tab>
      <van-tab title="b 2">
        内容 2
      </van-tab>
      <van-tab title="c 3">
        内容 3
      </van-tab>
      <van-tab title="d 4">
        内容 4
      </van-tab>
    </van-tabs>
<br>
    <van-row>
      <van-col span="20">
        <LazyVanButton type="success" @click="openPopup">
          lazy button
        </LazyVanButton>
        <LazyVanButton type="success" @click="openFloatingPanel">
          Open Floating Panel
        </LazyVanButton>
      </van-col>
      <van-col span="4">
        <van-icon name="chat-o" />
        <van-tag type="primary">
          Tag
        </van-tag>
        <van-loading />
      </van-col>
    </van-row>
    <br>
    <van-skeleton title avatar :row="3" />
    <van-steps active-icon="success" active-color="#07c160">
      <van-step>szia</van-step>
      <van-step>mija</van-step>
      <van-step>paja</van-step>
      <van-step>jaja</van-step>
    </van-steps>
    <br>
    <van-cell-group inset>
      <van-cell title="Cell title" value="Content" />
      <van-cell title="Cell title" value="Content" label="Description" />
    </van-cell-group>
    <br>

    <van-cell-group>
  <van-cell title="Cell title" value="Content" size="large" />
  <van-cell
    title="Cell title"
    value="Content"
    size="large"
    label="Description"
  />
</van-cell-group>

    <van-cell-group>
      <van-cell
        title="fejelo"
        :value="date"
        @click="showCalendar = true"
      />
      <van-cell
        title="focista"
        :value="cascaderValue"
        @click="showCascader = true"
      />
      <van-cell @touchstart.stop="showKeyboard = true">
        弹出默认键盘
      </van-cell>
    </van-cell-group>
    <van-pagination :total-items="24" :items-per-page="5" />

    <van-collapse v-model="activeNames">
      <van-collapse-item title="asd" name="1">
        asdasdasd
      </van-collapse-item>
      <van-collapse-item title="qwe" name="2">
        qweqweqwe
      </van-collapse-item>
      <van-collapse-item title="yxc" name="3">
        yxcyxcyxc
      </van-collapse-item>
    </van-collapse>

    <van-divider>tekeno</van-divider>

   >

    <van-calendar v-model:show="showCalendar" @confirm="onConfirm" />
    <van-number-keyboard :show="showKeyboard" @blur="showKeyboard = false" />
    <van-popup
      v-model:show="showPopup"
      :style="{ height: '40%' }"
      position="bottom"
    ><br>
      <van-field v-model="input" label="talan" placeholder="szoveg" />
      <van-password-input />
      <van-radio>dsa</van-radio>
      <van-checkbox>ewq</van-checkbox>
      <van-rate />
      <van-switch />
      <van-stepper />
      <van-progress :percentage="50" />
      <van-uploader />
    </van-popup>
    <van-popup v-model:show="showCascader" round position="bottom">
      <van-cascader
        v-model="cascaderValue"
        title="boci"
        :options="options"
        @close="showCascader = false"
      />
    </van-popup>
    <!-- <van-floating-panel
      v-model:show="showFloatingPanel"
      :content-draggable="false"
      :lock-scroll="true"
      :anchors="[240, 480, 680]"
    >
      <van-cell-group>
        <van-cell v-for=" (n, i) in 150" :key="i" :title="n" :value="n" />
      </van-cell-group>
    </van-floating-panel> -->

    <van-back-top bottom="70" />
    <van-sticky position="bottom">
      <van-tabbar>
        <van-tabbar-item icon="home-o">
          a1
        </van-tabbar-item>
        <van-tabbar-item icon="search">
          b2
        </van-tabbar-item>
        <van-tabbar-item icon="friends-o">
          c3
        </van-tabbar-item>
        <van-tabbar-item icon="setting-o">
          d4
        </van-tabbar-item>
      </van-tabbar>
    </van-sticky>
  </section>
</template>

<style>
.my-swipe .van-swipe-item {
  color: #fff;
  font-size: 20px;
  line-height: 150px;
  text-align: center;
  background-color: #39a9ed;
}
</style>