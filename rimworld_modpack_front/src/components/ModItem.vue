<template>
    <div class="mod-item">
      <div class="mod-logo">
        <img :src="modData.logo" alt="Mod Logo" width="100" />
      </div>
      <div class="mod-info">
        <h2>{{ modData.name }}</h2>
        <p>{{ modData.short_description }}</p>
        <div v-if="modData.images.length > 0">
          <scroll-pic :images="modData.images" />
        </div>
        <p>{{ modData.description }}</p>
        <p><strong>Mod String:</strong> {{ modData.mod_string }}</p>
        <p><strong>Save File Path:</strong> {{ modData.save_file }}</p>
        <div class="mod-likes-views">
          <div><strong>Views:</strong> {{ modData.views }}</div>
          <div><strong>Likes:</strong> {{ modData.likes }}</div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  
  export default {
    props: {
      modData: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style>
  /* Add your custom styles for ModItem component here */
  .mod-item {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .mod-logo {
    margin-right: 20px;
  }
  
  .mod-info {
    flex: 1;
  }
  
  .mod-likes-views {
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
  }
  
  /* You can add more styles as per your requirements */
  </style>
  