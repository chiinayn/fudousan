<template>
    <div class="black-bg" v-if="modalStat == true">
        <div class="white-bg">
            <img :src="rooms[clickNum].image">
            <h4>{{rooms[clickNum].title}}</h4>
            <p>{{rooms[clickNum].content}}</p>
            <!-- <input @input="month = $event.target.value"> -->
            <!-- <input type="range" min="1" max="12"> -->
            <input v-model="month">
            <p>{{month}}ヶ月を選択 : {{rooms[clickNum].price * month}}円</p> 
            <button @click="$emit('setModalStatFalse',false)" >閉じる</button>
        </div>
    </div>
</template>

<script>
export default {
    name : 'ModalComponent',
    data() {
        return {
            month : 1,
        }
    },
    watch : {
        month(a) {
            if (a >= 13) {
                alert('13以上は入力できません。')
                this.month = 1
            }
            
            if (isNaN(a)) {
                alert('数字を入力してください。')
                this.month = 1
            }
        }
    },
    updated() {
        if (this.month == 2) {
            alert('2が入力されました。');
        }
    },
    props : {
        rooms : Array,
        clickNum : Number,
        modalStat : Boolean,
    }
}
</script>

<style>
    .black-bg {
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        position: fixed;
        padding: 20px;
    }
    .white-bg {
        width: 100%;
        background: white;
        border-radius: 8px;
        padding: 20px;
    }
    .fade-enter-from {
    /* opacity: 0; */
    transform: translateY(-1000px);
    }
    .fade-enter-active {
    transition: all 1s;
    }
    .fade-enter-to {
    /* opacity: 1; */
    transform: translateY(0px);
    }
    .fade-leave-from {
    opacity: 1;
    }
    .fade-leave-active {
    transition: all 1s;
    }
    .fade-leave-to {
    opacity: 0;
    }

</style>