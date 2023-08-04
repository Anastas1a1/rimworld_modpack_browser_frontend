<template>
    <div>
      <ModItem :modData="modData" />
    </div>
  </template>
  
  <script>
  import ModItem from "@/components/ModItem.vue";
  
  export default {
    components: {
      ModItem,
    },
    data() {
      return {
        modData: {
          id: 123,
          name: "Classic Pack with Enhancements",
          logo: "link_to_s3",
          short_description:
            "A great modpack with limited progression in the medieval era! Swords and bows only, no laser guns or grenades!",
          description: "Long text description with MD support or a text editor",
          images: [
            "link_to_s3_cloud_storage",
            "link_to_s3_cloud_storage",
            "link_to_s3_cloud_storage",
          ],
          mod_string: "String for copying and pasting into the mod-manager",
          save_file: "path_to_save_file_in_s3_storage",
          views: 55,
          likes: 18,
        },
      };
    },
  };
  </script>
  