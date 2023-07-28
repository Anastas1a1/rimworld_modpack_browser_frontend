<template>
    <div class="mods">
        <custom-button
            @click="showDialog"
            >Новая коллекция
        </custom-button>
        <dialog-window v-model:show="dialogVisible">

            <mods-form @create="createCard" />
        </dialog-window>
        <mods-list :cards="cards" />

    </div>
</template>

<script>

import ModsList from "@/components/ModsList"
import ModsForm from "@/components/ModsForm"


export default {
    components: {
        ModsForm, ModsList
    },

    data() {
        return {
            cards: [
                { id: 1, title: 'hotel1', link: 'https://..1', logo: "../assets/logo.png" },
                { id: 2, title: 'hotel2', link: 'https://..2', logo: '../assets/logo.png' },
                { id: 3, title: 'hotel3', link: 'https://..3', logo: '../assets/logo.png' },
            ],
            dialogVisible: false,
        }
    },
    methods: {
        createCard(card) {
            this.cards.push(card);
            this.dialogVisible = false;
        },
        showDialog() {
            this.dialogVisible = true;
        }
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