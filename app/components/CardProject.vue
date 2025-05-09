<script setup lang="ts">
  import type { DropdownMenuItem } from '@nuxt/ui';
  import { ref } from 'vue';
  import { useRouter } from 'vue-router'

  const router = useRouter();
  const isFavorite = ref(false);
  const defaultImage = new URL('@/assets/images/default-cover.png', import.meta.url).href; 
  const itemsDropDownMenu = ref<DropdownMenuItem[]>([
    {
      label: 'Editar',
      icon: 'i-material-symbols:open-in-new-down-rounded',
      color: 'primary',
      onSelect: () => {
      const projetoParaEditar = {
        projectId: props.projectId,
        projectName: props.title,
        client: props.subTitle,
        beginDate: props.beginDate,
        endDate: props.endDate,
        capaPreview: props.cover
      } 
      console.log(projetoParaEditar)
      localStorage.setItem('editarProjeto', JSON.stringify(projetoParaEditar))
      router.push(`/projects/id?${props.projectId}`)
      }        
    },
    {
      label: 'Remover',
      icon: 'i-lucide-trash',
      color: 'primary'
    },
  ]);
  const props = defineProps({
    projectId: {type: String, default: ''},
    title: { type: String, default: 'Default title' },
    subTitle: { type: String, default: 'Default client' },
    beginDate: { type: String, default: '00/00/0000' },
    endDate: { type: String, default: '11/11/1111' },
    cover: { type: String, default: '' }
  });
  
  const toggleFavorite = () => {
    isFavorite.value = !isFavorite.value;
  }
</script>

<template>
  <div class="card-container">
    <div class="image-container">
      <img class="logo" :src="cover !== null ? cover : defaultImage" alt="Imagem do projeto">

      <div class="buttons-overlay">
        <button class="cursor-pointer w-6 h-6" @click="toggleFavorite" >
          <UIcon       
          :name="isFavorite ? 'i-mdi-star' : 'i-mdi-star-outline'"
          class="transition-all duration-200 icon-favorite"
          :class="isFavorite ? 'text-yellow-400' : 'text-white'"/>
        </button>

          <UDropdownMenu
            :items="itemsDropDownMenu"
            :content="{
              align: 'start',
              side: 'bottom',
              sideOffset: 8
            }"
            :ui="{content: 'w-48, bg-white'}">
            <button @click="onDelete">
              <UIcon name="i-mdi:dots-horizontal-circle" class="icon-more" />
            </button>
          </UDropdownMenu>
      </div>
    </div>

    <div class="information-container">
      <div>
        <h1 class="title">{{ title }}</h1>
        <h2 class="sub-title">Cliente:<span class="sub-title-content">{{ subTitle }}</span></h2>
      </div>
      <div class="line" />
      <p class="begin-date"><UIcon name="i-mdi:calendar-today-outline" class="icon" />{{ beginDate }}</p>
      <p class="end-date"><UIcon name="i-mdi-calendar-check-outline" class="icon" />{{ endDate }}</p>
    </div>
  </div>
</template>

<style >
  .card-container {
    width: 100%;
    max-width: 346px; 
    height: auto; 
  }
  .logo {
    width: 100%; 
    height: 232px; 
    max-height: 232px;
    object-fit: cover;
    border-top-right-radius: 16px;
    border-top-left-radius: 16px;
  }
  .title {
    color: #1F1283;
    font-family: Encode Sans Semi Expanded;
    font-weight: 700;
    font-size: 20px;
    line-height: 100%;
    letter-spacing: 0%;
    margin-bottom: 15px;
  }
  .information-container {
    padding: 25px;
    background-color: #fff;
    border-bottom-right-radius: 16px;
    border-bottom-left-radius: 16px;
    
  }
  .sub-title{
    color: #717171;
    font-family: Encode Sans Semi Expanded;
    font-weight: 700;
    font-size: 16px;
    line-height: 100%;
    letter-spacing: 0%;
    margin-bottom: 10px;
  }
  .sub-title-content {
    color: #717171;
    font-family: Encode Sans Semi Expanded;
    font-weight: 300;
    font-size: 16px;
    line-height: 100%;
    letter-spacing: 0%;
    margin-bottom: 10px;
    margin-left: 10px;

  }
  .line{
    height: 1px;
    background-color: #ECECEC;
    margin-bottom: 10px;
  }
  .begin-date {
    color: #717171;
    font-family: Encode Sans Semi Expanded;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    letter-spacing: 0%;
    margin-bottom: 10px;
  }
  .end-date {
    color: #717171;
    font-family: Encode Sans Semi Expanded;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    letter-spacing: 0%;
  }
  .icon {
    vertical-align: text-bottom;
    margin-right: 10px;
    width: calc(var(--spacing) * 6);
    height: calc(var(--spacing) * 6); 
  }
  .image-container {
    position: relative;
  }
  .buttons-overlay {
    position: absolute;
    bottom: 10px;
    right: 10px;
    display: flex;
    gap: 8px;
    z-index: 10;
  }
  .btn {
    background-color: rgba(255, 255, 255, 0.9);
    border: none;
    padding: 6px 10px;
    border-radius: 6px;
    font-size: 14px;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  .icon-more {
    margin-right: 10px;
    width: calc(var(--spacing) * 7);
    height: calc(var(--spacing) * 7); 
    color: #FFFFFF;
    cursor: pointer;
  }
  .icon-favorite {
    margin-right: 10px;
    width: calc(var(--spacing) * 7);
    height: calc(var(--spacing) * 7); 
  }
</style>