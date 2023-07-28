<template>
    <div class="cards__list">
        <div v-if="cards.length > 0">
            <h2>Коллекции</h2>
            <card-item class="card" v-for="card in cards" :card="card" />
        </div>
        
        <h4 v-else>
            Коллекции не найдены
        </h4>
    </div>
</template>


<script>
import CardItem from "@/components/CardItem";
export default {
    components: { CardItem },
    props: {
        cards: {
            type: Array,
            required: true
        }
    }
}
</script>


<style scoped>
.cards__list {
    margin: 0;
    margin-top: 50px;
    padding: 0;
    border: 20px solid #232C40;
    background-color: #232C40;
    color: aliceblue;
    border-radius: 25px;
}

.card {
    padding: 15px;
    border: 3px solid #8589AC;
    margin-top: 15px;
    border-radius: 25px;
}
</style>