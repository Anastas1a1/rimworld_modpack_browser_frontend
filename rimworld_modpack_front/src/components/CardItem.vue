<template>
    <div class="card" @click.self="handleViews">
        <div class="card__part">
            <div v-if="card.logo">
                <img :src="card.logo || '@/assets/logo.png'" width="100">
            </div>
        </div>

        <div class="card__part">
            <div><strong>Название</strong> {{ card.title || 'Нет названия' }}</div>
            <div><strong>Ссылка</strong> {{ card.link || 'Нет ссылки' }}</div>
            <div><strong>Описание</strong> {{ card.description || '' }}</div>
        </div>

        <div class="card__btns">
            <div><strong>Просмотры  </strong> {{ card.views || 0 }}</div>
            <img :src="isLiked ? require('@/assets/like_pressed.png') : require('@/assets/like.png')" @click="toggleLike"
                :class="{ liked: isLiked }">
            {{ card.likes || 0 }}
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        card: {
            type: Object,
            required: true,
        }
    },
    data() {
        return {
            isLiked: false,
        };
    },
    methods: {
        toggleLike() {
            if (this.isLiked) {
                // Если уже лайкнуто, отменяем лайк
                this.card.likes = Math.max((this.card.likes || 0) - 1, 0);
            } else {
                // Если не лайкнуто, добавляем лайк
                this.card.likes = (this.card.likes || 0) + 1;
            }
            this.isLiked = !this.isLiked; // Переключаем флаг
        },
        handleViews() {
            // Здесь обработчик для просмотра карточки
            // Увеличиваем значение просмотров в объекте card
            this.card.views = (this.card.views || 0) + 1;
        }
    }
}
</script>
  
<style>
.card {
    cursor: pointer;
    text-align: left;
    display: flex;
    align-items: center;
    position: relative;
}

.card:hover {
    background-color: #3E5575;
}

.card__btns {
  position: absolute;
  bottom: 0;
  right: 0;
  margin: 10px;
  display: flex;
  align-items: center;
  font: 0.7em sans-serif;
  margin-top: 10px;
}

.card__part {
    padding: 5px;
    margin-bottom: 30px;
}


img {
    margin-left: 10px;
    margin-right: 5px;
    cursor: pointer;
    border-radius: 10px;
}
</style>
  