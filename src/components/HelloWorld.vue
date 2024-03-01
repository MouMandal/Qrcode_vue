<script setup>
import { ref } from 'vue';
const text = ref('');
const qr = ref(
    {
        src: '',
    }
);
const imgbox = ref(null);
const qrtext = ref(null);
const data = () => {
    if (text.value.length > 0) {
        qr.value.src = `https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=${text.value}`;
        imgbox.value.classList.add("show-img");
    } else {
        qrtext.value.classList.add("show-img");
        setTimeout(() => {
            qrtext.value.classList.remove("show-img");
        }, 1000);
    }
};
</script>
<template>
    <div class="container">
        <div class="wrap">
            <p>Enter your text or URL</p>
            <input type="text" placeholder="Enter your text or URL" v-model="text">
        </div>
        <div :class="imgbox">
            <img :src="qr.src" ref="imgbox">
        </div>
        <button @click="data">Generate Qr Code</button>
    </div>
</template> 
