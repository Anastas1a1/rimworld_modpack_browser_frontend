<template>
    <div class="input__form">

        <form @submit.prevent>
            <h2>Новая сборка</h2>
            <input v-model="card.title"
                class="input" type="text"
                placeholder="Название">
            <input v-model="card.link" 
                class="input" type="text" 
                placeholder="Ссылка">
            <input v-model="card.description" 
                class="input" type="text" 
                placeholder="Описание">
            <input class="input" type="file" 
                @change="handleImageUpload" 
                accept="image/*">

            <img v-if="card.logo" 
                :src="card.logo" 
                width="100">
            <img v-else src="../assets/logo.png" 
                width="100">

            <button class="btn" 
                @click="createCard">Создать
            </button>
        </form>

    </div>
</template>




<script>
export default {
  data() {
    return {
      card: {
        title: '',
        link: '',
        description: '',
        logo: null 
      }
    };
  },
  methods: {

    createCard() {
            this.card.id = Date.now(),
            this.$emit('create', this.card);
            this.card = {
                title: '',
                link: '',
                description: '',
                logo: null,               
            }
        },


    handleImageUpload(event) {
      const file = event.target.files[0];
      if (file && file.type.startsWith('image/')) {
        const reader = new FileReader();

        reader.onload = () => {
          this.card.logo = reader.result;
        };

        reader.readAsDataURL(file);
      } else {
        this.card.logo = null;
      }
    }
  }
};
</script>




<style scoped>

form {
  display: flex;
  flex-direction: column;
  color:aliceblue;
}


.input__form {
    margin: 0;
    padding: 0;
    border: 20px solid #8589AC;
    background: #8589AC;
    color: aliceblue;
    border-radius: 25px;  
}

::placeholder {
    color: aliceblue
}

.input {
  width: 100%;
  border: 2px solid aliceblue;
  padding: 10px 15px;
  margin-top: 15px;
  border-radius: 10px;
  background-color: #8589AC;

}


.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: aliceblue;
  color: #35656F;
  border: 2px solid aliceblue;
  border-radius: 10px;
}

.btn:hover {
    background-color: #6C80EF;
    color: aliceblue;

}
</style>