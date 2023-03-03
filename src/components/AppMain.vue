<template>
    <div class="back-1">
        <!-- <select></select> -->
        <div class="back-2">
            <ul class="container">
                <div class="black flex item-aling">
                    <p class="white">found 39 cards</p>
                </div>
                <li v-for="card in cards" :key="card.id">
                    <img :src="card.card_images[0].image_url" alt="">
                    <p>{{ card.name }}</p>
                    <p>
                        {{ card.archetype }}
                    </p>



                </li>

            </ul>

        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data() {
        return {
            cards: []
        }


    },
    methods: {
        feathCards() {
            console.log('cards')
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then((res) => {
                    console.log(res.data.data)
                    this.cards = res.data.data
                })


        }
    },
    created() {
        this.feathCards()
    }

}

</script>
<style lang="scss" scoped>
.back-1 {
    background-color: #d48f38;
    height: 100vh;

}

.back-2 {
    background-color: white;
}

.black {
    background-color: #212529;
    height: 50px;
}

.white {
    color: white;
    padding-left: 10px;
    font-weight: bold;
}
</style>