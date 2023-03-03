<template>
    <li class=" img-card ">

        <img :src="card.card_images[0].image_url" alt="" class="img-yu-gi">
        <p class="center white-p">{{ card.name }}</p>
        <p class="center">
            {{ card.archetype }}
        </p>

    </li>
</template>
<script>
export default {

    props: {
        card: {
            type: Object,
            required: true
        }


    }
}


</script>

<style lang="scss" scoped>
.img-card {

    flex-basis: 19%;
    background-color: #d48f38;
}

.img-yu-gi {
    width: 225px;
}

.center {
    text-align: center;
}

.white-p {
    color: white;
    padding-top: 5px;
    padding-bottom: 5px;
}
</style>