<template>
    <div>
        <img :src="room.image" class="room-img">
        <h4 @click="hoge()">{{room.title}} 部屋</h4>
        <p>{{room.price}}円</p>
    </div>
</template>

<script>
export default {
    name : 'CardComponent',
    props : {
        room : Object,
        index : Number,
        reports : Array
    },
    methods: {
        hoge() {
            this.$emit('openModal', this.index)
        }
    },
}
</script>

<style>
    .room-img {
    width: 60%;
    margin-top: 40px;
    }
</style>