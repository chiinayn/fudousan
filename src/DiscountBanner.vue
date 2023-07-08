<template>
    <div class="discount">
        <h4>今決めると{{percentage}}%割引！</h4>
    </div>
</template>

<script>
export default {
    name: 'DiscountBanner',
    data() {
        return {
            percentage : 20,
            repeat : null
        }
    },
    mounted() {
        // this.repeat = setInterval(() => {
        //     this.percentage -= 1;
        //     if (this.percentage == 0) {
        //         clearInterval(this.repeat);
        //     }
            
        // }, 1000);
    },
}
</script>

<style>

</style>``