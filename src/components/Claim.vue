<template>
    <div class="claimWrapper">
        <h1 class="claim"> SPACER </h1>
        <p class="subclaim"> 
            Begin your journey through our amazing galaxy and discover places you never heard of. 
        </p>
        <p class="subclaim"> 
            Type anything space-related to start. 
        </p>
    </div>
</template>

<script>
export default {
    name: 'Claim'
}
</script>
<style lang="scss" scoped>
    .claimWrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center; 
        text-align: center;
        color: #fff;
    }

    .claim {
        font-size: 60px;
        margin: 0;

        @media(min-width: 768px) {
            font-size: 80px;
        }

        @media(min-width: 1024px) {
            font-size: 100px;
        }
    }

    .subclaim {
        margin: 20px 0 0 ;
        font-size: 13px;
        font-weight: 400;
        max-width: 500px;

        @media(min-width: 768px) {
            font-size: 17px;
            letter-spacing: 1px;
            line-height: 1.3;
        }
    }
</style>

