<script setup lang="ts">
import { ref } from 'vue';
import axios from 'axios';
interface IServer {
  id: number;
  name: string;
  value: string;
}

const serverList = ref<IServer[]>([
  {
    id: 0,
    name: '안톤',
    value: 'anton'
  },
  {
    id: 1,
    name: '바칼',
    value: 'bakal'
  },
  {
    id: 2,
    name: '카인',
    value: 'cain'
  },
  {
    id: 3,
    name: '카시야스',
    value: 'casillas'
  },
  {
    id: 4,
    name: '디레지에',
    value: 'diregie'
  },
  {
    id: 5,
    name: '힐더',
    value: 'hilder'
  },
  {
    id: 6,
    name: '프레이',
    value: 'prey'
  },
  {
    id: 7,
    name: '시로코',
    value: 'siroco'
  }
]);
const dotenv = import.meta.env;
const charServer = ref<string>('default');
const charName = ref<string>('');
const submitEventHandle = async () => {
  if(charServer.value === 'default') {
    alert("서버를 선택해주세요.");
    return;
  }
  if(charName.value === '') {
    alert("캐릭터명을 입력해주세요.");
  }
  const encodeCharName = encodeURIComponent(charName.value);
  const {data} = await axios.get(`${dotenv.VITE_DF_URL}servers/${charServer.value}/characters`, {
    method: 'get',
    headers: {
      "Access-Control-Allow-Origin": "*",
    },
    params: {
      characterName: encodeCharName,
      apikey: dotenv.VITE_DF_API,
    }
  });
  console.log(data);
}
</script>

<template>
  <div class="search">
    <form action="" class="search_form" role="search" @submit.prevent="submitEventHandle">
      <legend class="sr-only">캐릭터 검색</legend>
      <select name="server" id="server" v-model="charServer">
        <option value="default">서버</option>
        <option :value="items.value" v-for="items in serverList" :key="items.id">
          {{ items.name }}
        </option>
      </select>
      <input
        type="text"
        v-model="charName"
        placeholder="캐릭터명을 입력해주세요."
        class="char_name"
      />
      <button type="submit" class="search_button">검색</button>
    </form>
  </div>
</template>

<style scoped lang="scss">
.search {
  padding: 80px 0;
  .search_form {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    column-gap: 16px;
    #server {
      appearance: none; //기본
      -webkit-appearance: none; //크롬
      background: url('../assets/images/arrows.svg') no-repeat 95% 50%;
      background-size: 16px;
      font-size: 16px;
      padding: 4px 8px;
      border: 1px solid #ececec;
      background-color: #ececec;
      color: #20232d;
      border-radius: 4px;
      cursor: pointer;
      transition: 0.3s all;
      &:hover {
        border-color: #20232d;
      }
    }
    .char_name {
      padding: 4px 8px;
      font-size: 16px;
      border: 1px solid #c7c7c7;
      border-radius: 4px;
      transition: 0.3s all;
      cursor: pointer;
      &:focus,
      &:hover {
        border-color: #20232d;
      }
    }
    .search_button {
      padding: 4px 16px;
      font-size: 16px;
      margin: 0;
      border: 1px solid #f9be00;
      border-radius: 4px;
      cursor: pointer;
      background-color: #f9be00;
      color: white;
      transition: 0.3s all;
      &:hover {
        border-color: #20232d;
      }
    }
  }
}
</style>
