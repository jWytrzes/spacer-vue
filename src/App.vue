<template>
    <div :class="[{ flexStart: step === 1 }, 'wrapper']">
        <transition name="slide">
            <img v-if="step === 1" src="./assets/logo.png" class="logo">
        </transition>
        <transition name="fade">
            <HeroImage v-if="step === 0"/>
        </transition>
        <Claim v-if="step === 0"/>
        <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1"/>
        <div class="results" v-if="results && !loading && step === 1">
            <Item v-for="item in results" :item="item" :key="item.data[0].nasa_id"/>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import HeroImage from '@/components/HeroImage.vue';
import Item from '@/components/Item.vue';

const API ='https://images-api.nasa.gov/search';

export default {
    name: "App",
    components: {
        Claim,
        SearchInput,
        HeroImage,
        Item
    },
    data() {
        return {
            loading: false,
            step: 0,
            searchValue: '',
            results: [],
        };
    },
    methods: {
        handleInput: debounce(function() {
            this.loading = true;
            axios.get(`${API}?q=${this.searchValue}&media_type=image`)
                .then((response) => {
                    this.results = response.data.collection.items;
                    this.loading = false;
                    this.step = 1;
                })
                .catch((error) => {
                    console.log(error);
                });
        }, 500),
    },
}

</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800&subset=latin-ext');

* {
    box-sizing: border-box;
}

body {
    font-family: Montserrat, sans-serif;
    padding: 0;
    margin: 0;
}

.wrapper {
    display: flex;
    flex-direction: column;
    align-items: center; 
    justify-content: center;
    position: relative;
    margin: 0;
    padding: 30px;
    width: 100%; 
    min-height: 100vh;

    &.flexStart {
        justify-content: flex-start;
    }
}

.logo {
    position: absolute;
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
    height: 30px;
}

.fade-enter-active, .fade-leave-active {
    transition:  opacity .3s ease;
}

.fade-enter, .fade-leave-to {
    opacity: 0;
}

.slide-enter-active, .slide-leave-active {
    transition: transform .3s ease;
}

.slide-enter, .slide-leave-to {
    transform: translateY(-200%) translateX(-50%);
}

</style>