<template>
    <div class="container">
        <div>
            <input @keyup.enter="$emit('onSearch')" type="text" v-model="store.search"
                placeholder="Cerca la carta con il suo nome">
        </div>

    </div>
</template>
  
<script>
import store from '../store'
export default {
    data() {
        return {
            store,
        }
    },

}
</script>
  
<style lang="scss" scoped></style>