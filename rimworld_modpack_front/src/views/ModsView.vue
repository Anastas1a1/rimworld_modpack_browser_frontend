<template>
    <div class="mods">

        <!-- <dialog-window v-model:show="dialogVisible"> -->

        <mods-form @create="createCard" />
        <!-- </dialog-window> -->
        <mods-list :cards="cards" />

    </div>
</template>

<script>

import ModsList from "@/components/ModsList";
import ModsForm from "@/components/ModsForm";
import axios from 'axios';

export default {
    components: {
        ModsForm, ModsList
    },

    data() {
        return {
            cards: [
                // { id: 1, name: 'hotel1', link: 'https://..1', logo: "@/assets/logo.png", views: 50, likes: 33},
                // { id: 2, name: 'hotel2', link: 'https://..2', logo: '../assets/logo.png' },
                // { id: 3, name: 'hotel3', link: 'https://..3', logo: '../assets/logo.png' },
            ],
            dialogVisible: false,
        }
    },
    methods: {
        createCard(card) {
            this.cards.push(card);
            this.dialogVisible = false;
        },
        async fetchCards() {
            try {
                const response = await axios.get('https://mocki.io/v1/e4b2d9ca-890c-4fcf-9b2b-fdafd2c78754');
                this.cards = response.data.items;
                console.log(response);

            } catch (e) {
                alert('Ошибка')
            }

        },
    },
    mounted() {
        this.fetchCards();

    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.mods {
    padding: 50px;
    background-color: #3E5575;
}
</style>