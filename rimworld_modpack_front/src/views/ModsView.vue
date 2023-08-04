<template>
    <div class="mods">
        <custom-input v-model="searchQuery" placeholder="Поиск..."></custom-input>
        <img :src="require('@/assets/search_icon.png')">
        <mods-form @create="createCard" />
        <mods-list :cards="sortedAndSearchedCards" v-if="!isCardsLoading" />


        <div v-else>Идет загрузка...</div>
        <div v-intersection="loadMoreCards" class="observer"></div>

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
            cards: [],
            dialogVisible: false,
            isCardsLoading: false,
            searchQuery: '',
            totalPages: 0,
            page: 3,
            limit: 5,
        }
    },
    methods: {
        createCard(card) {
            this.cards.push(card);
            this.dialogVisible = false;
        },
        async fetchCards() {
            try {
                this.isCardsLoading = true;
                const response = await axios.get('https://mocki.io/v1/f6eee0f2-c99f-4568-b7cd-cc47cfd56b01', {
                    params: {
                        _page: this.page,
                        _limit: this.limit
                    }
                });
                this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
                this.cards = response.data.items;

            } catch (e) {
                alert('Ошибка')
            } finally {
                this.isCardsLoading = false;
            }
        },
        async loadMoreCards() {
            try {
                this.page += 1;
                const response = await axios.get('https://mocki.io/v1/f6eee0f2-c99f-4568-b7cd-cc47cfd56b01', {
                    params: {
                        _page: this.page,
                        _limit: this.limit
                    }
                });
                this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
                this.posts = [...this.posts, ...response.data];
            } catch (e) {
                alert('Ошибка')
            }
        }

    },
    mounted() {
        this.fetchCards();

    },
    computed: {
        sortedAndSearchedCards() {
            return this.cards.filter(card => card.name.toLowerCase().includes(this.searchQuery.toLowerCase()))
        }
    },
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