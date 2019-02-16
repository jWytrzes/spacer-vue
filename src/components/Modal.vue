<template>
    <div class="outerWrapper">
        <div class="innerWrapper">
            <div class="photo">
                <img :src="photo">
            </div>
            <div class="description scroll">
                <h2 class="title"> {{ title }} </h2>
                <p class="description">
                    {{ description }}
                </p>
            </div>
            <div class="close" @click="$emit('closeModal')"/>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    props: {
        item: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            photo: null,
            title: null,
            description: null,
        };
    },
    mounted() {
        this.photo = this.item.links[0].href;
        this.title = this.item.data[0].title;
        this.description = this.item.data[0].description;
    },
}
</script>

<style lang="scss" scoped>

.outerWrapper {
    max-width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    background: #f8f8f8;

    @media(min-width: 1024px) {
        max-width: 70%;
        height: 60%;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        margin: auto;
        box-shadow: 0 30px 30px -10px rgba(0,0,0,.3);
    }
}

.innerWrapper {
    display: flex;
    height: 100%;
    padding: 50px;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    @media(min-width: 1024px) {
        flex-direction: row;

        .photo {
            margin-right: 20px;
            max-height: 100%;
            min-width: 40%;
            width: auto;
        }
    }

    .photo {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;

        img {
            max-height: 100%;
            max-width: 100%;
            display: block;
        }
    }

    .description {
        color: #1e3d4a;
        line-height: 1.3;

        &.scroll {
            overflow-y: auto;
            overflow-x: hidden;
            word-break: break-word;
            height: 100%;
        }
    }
}

.close {
    position: absolute;
    right: 0px;
    top: 0px;
    padding: 30px;
    width: 30px;
    height: 30px;
    cursor: pointer;

    &:before, &:after {
        content: '';
        display: block;
        position: absolute;
        top: 30px;
        right: 20px;
        width: 20px;
        height: 2px;
        background: #1e3d4a;
    }

    &:before {
        transform: rotate(45deg);
    }

    &:after {
        transform: rotate(-45deg);
    }
}
</style>
