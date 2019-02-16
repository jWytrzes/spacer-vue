<template>
    <input 
        id="search" 
        name="search" 
        :class="{ dark: dark }"
        :value="value"
        @input="handleChange"
    />
    <!-- {dark: dark} = {dark} [ES6] -->
</template>

<script>
export default {
    name: 'SearchInput',
    props: {
        value: {
            type: String,
            required: true,
        },
        dark: {
            type: Boolean,
            default: false,
        }
    },
    methods: {
        handleChange(e) {
            this.$emit('input', e.target.value);
        },
    },
}
</script>

<style lang='scss' scoped>

input {
    margin-top: 50px;
    display: flex;
    width: 250px;
    height: 30px;
    border: 0;
    border-bottom: 1px solid #fff;
    font-family: Montserrat, sans-serif;
    background: none;
    color: #fff;
    text-align: center;
    font-size: 18px; 
    transition: box-shadow .3s;
    font-weight: 300;

    &:focus {
        outline: none;
        box-shadow: 0 10px 20px -8px rgba(255,255,255,.5);
    }

    @media(min-width: 1024px) {
        font-weight: 400;
    }
}

.dark {
    color: #1e3d4a;
    border-bottom-color: #1e3d4a;

    &:focus {
        box-shadow: 0 10px 20px -8px rgba(#1e3d4a,.2);
    }
}

</style>
