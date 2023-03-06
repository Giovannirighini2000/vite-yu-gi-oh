<template>
    <div class="back-1">
        <div class="container">
            <Filters @onSearch="feathCards" />
        </div>

        <div class=" container back-2">
            <div class="black flex item-aling">
                <p class="white">found {{ store.cards.length }} cards</p>
            </div>
            <ul class="container flex wrap">
                <AppCardMain v-for="card in store.cards" :key="card.id" :card="card" />


            </ul>

        </div>
    </div>
</template>
<script>
import AppCardMain from './AppCardMain.vue'
import store from '../store'
import axios from 'axios'
import Filters from './Filters.vue'

export default {
    components: {
        AppCardMain,
        Filters,

    },
    data() {
        return {
            store
        }


    },
    methods: {
        feathCards() {
            const search = this.store.search
            console.log('cards')
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
                    params: {
                        fname: search,

                    }
                })

                .then((res) => {
                    console.log(res.data.data)
                    this.store.cards = res.data.data
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
    padding-top: 20px;


}

.back-2 {
    background-color: white;
    padding-left: 15px;
    padding-top: 15px;
    padding-bottom: 15px;
}

.black {
    background-color: #212529;
    height: 50px;
    margin-right: 15px;
}

.white {
    color: white;
    padding-left: 10px;
    font-weight: bold;
}


.wrap {
    flex-wrap: wrap;
    gap: 11px;
}
</style>