<script setup>
import { computed, ref } from "vue";
import ChatList from "@/comps/ChatList.vue";
const chats = ref([]);
const users = ref([]);
const currentUser = ref();
const currentMessage = ref("");
currentUser.value = 100;
const selectedConversationIndex = ref();
users.value.push({
  id: 100,
  Name: "Ahmed AL-Essam",
  imgUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoJc19tQ_AopxBuHsUkpKujzTkScWv5SfRLI9Zl1sC73551njfMD1mPhovwKFbWW6p9mk&usqp=CAU",
  lastseen: "",
});
users.value.push({
  id: 101,
  Name: "Hassan",
  imgUrl: "",
  lastseen: "",
});
users.value.push({
  id: 102,
  Name: "Ali",
  imgUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoJc19tQ_AopxBuHsUkpKujzTkScWv5SfRLI9Zl1sC73551njfMD1mPhovwKFbWW6p9mk&usqp=CAU",
  lastseen: "",
});
users.value.push({
  id: 103,
  Name: "Abd Azezz",
  imgUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoJc19tQ_AopxBuHsUkpKujzTkScWv5SfRLI9Zl1sC73551njfMD1mPhovwKFbWW6p9mk&usqp=CAU",
  lastseen: "",
});
chats.value.push({
  title: "AI Dojo",
  type: "privet",
  imgUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoJc19tQ_AopxBuHsUkpKujzTkScWv5SfRLI9Zl1sC73551njfMD1mPhovwKFbWW6p9mk&usqp=CAU",
  messages: [
    {
      user: "100",
      text: "Hello, World!",
      username: "hdrm147",
      dilverdTo: [],
      seenuser: [],
      timestamp: "",
    },
    {
      user: "101",
      text: "Hello, Haidar!",
      username: "azeez",
      dilverdTo: [],
      seenuser: [],
      timestamp: "",
    },
  ]
})
chats.value.push({
  title: "AI Dojo",
  type: "privet",
  imgUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoJc19tQ_AopxBuHsUkpKujzTkScWv5SfRLI9Zl1sC73551njfMD1mPhovwKFbWW6p9mk&usqp=CAU",
  messages: [
    {
      user: "100",
      text: "Hello, World!",
      username: "hdrm147",
      dilverdTo: [],
      seenuser: [],
      timestamp: "11:11",
    },
    {
      user: "103",
      text: "Hello, Haidar!",
      username: "azeez",
      dilverdTo: [],
      seenuser: [],
      timestamp: "11:15",
    },
  ]
})
chats.value.push({
  title: "AI Dojo",
  type: "public",
  imgUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoJc19tQ_AopxBuHsUkpKujzTkScWv5SfRLI9Zl1sC73551njfMD1mPhovwKFbWW6p9mk&usqp=CAU",
  messages: [
    {
      user: "100",
      text: "Hello, World!",
      username: "hdrm147",
      dilverdTo: [],
      seenuser: [],
      timestamp: "",
    },
    {
      user: "101",
      text: "Hello, Haidar!",
      username: "azeez",
      dilverdTo: [],
      seenuser: [],
      timestamp: "",
    },
    {
      user: "102",
      text: "Hello, Haidar!",
      username: "azeez",
      dilverdTo: [],
      seenuser: [],
      timestamp: "",
    },
  ]
})
const currentConversation = computed(() => {
  return chats[selectedConversationIndex.value];
});
const addMessage = () => {
  console.log(chats.value[currentConversation])
  var today = new Date();
  var date = today.getFullYear() + '-' + (today.getMonth() + 1) + '-' + today.getDate();
  var time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
  var dateTime = date + ' ' + time;
  chats.value[0].messages.push({
    user: currentUser.value,
    text: currentMessage.value,
    username: currentUser.value,
    dilverdTo: [currentUser.value],
    seenuser: [currentUser.value],
    timestamp: dateTime,
  });
  currentMessage.value = "";
}
</script>
<template>
  <h1 class=" text-6xl text-black text-center p-9">Vue Chat System</h1>
  <div class=" flex justify-center w-full h-[80%] ">
    <chat-list :chats="chats" :currentUser="currentUser" :users="users" :currentMessage="currentMessage"></chat-list>
  </div>
  <input @keyup.enter="addMessage()" v-model="currentMessage" type="text"
    class="  w-[50%] rounded px-4 py-2 m-4  mx-[36%]  text-black" placeholder="Type Here and press Enter .....">
</template>
<!-- v-if="currentConversation != null" -->
