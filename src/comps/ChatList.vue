<script setup>
import { computed, ref } from "vue";
import Messages from "@/comps/Messages.vue";
const props = defineProps({
    chats: {
        type: [Array],
        required: true,
    },
    currentUser: {
    },
    users: {},
    currentMessage: {},
    addMessage: { type: Function },
})
const selectedConversationIndex = ref();
const currentConversation = computed(() => {
    return props.chats[selectedConversationIndex.value];
});
// const addMessage= () => { console.log(currentMessage)}
</script>
<template>
    <div class="flex gap-6 text-black w-full max-h-full m-4 mx-40">
        <div
            class="flex min-w-[30%] flex-col w-1/5 bg-indigo-100 rounded-3xl  p-0 bg-gradient-to-r from-[#558189] to-[#52708a]">
            <div class="bg-[#38505d] w-[90%] rounded-3xl h-11 m-6">
                <p class="text-gray-400/60 p-2 my-1 mx-3 inline-block">Search...</p>
                <img src="/m.png" class="w-6 inline-block float-right m-2.5 mx-5 " alt="">
            </div>
            <div @click="selectedConversationIndex = index" v-for="(chats, index) in chats"
                class="p-4 rounded px-5 text-white w-full cursor-pointer hover:bg-indigo-200"
                :class="selectedConversationIndex === index ? 'bg-[#395260]' : ''">
                <div class="">
                    <img v-if="chats.type == 'public'" :src=chats.imgUrl alt="" class="inline-block w-24 rounded-full ml-6">
                    <div v-else v-for="M in chats.messages" class="inline-block px-2">
                        <div v-if="M.user != currentUser" v-for="u in users"  >
                            <div v-if="M.user == u.id" class="inline-block ">
                                <img v-if="!u.imgUrl" :src="'https://ui-avatars.com/api/?name=' + u.Name"
                                    class="inline-block w-24 rounded-full">
                                <img v-else :src="u.imgUrl" class="inline- w-24 rounded-full">
                            </div>
                        </div>
                    </div>
                    <div v-if="chats.type == 'public'" class="inline-block px-2">
                        <span class="font-bold  inline-block ">{{ chats.title }}</span>
                    </div>
                    <div v-else class="inline-block my-2   ">
                        <div v-for="M in chats.messages" class="inline-block">
                            <div v-if="M.user != currentUser" v-for="u in users" class="inline-block">
                                <div v-if="M.user == u.id" class="inline-block">
                                    <span class="font-bold  inline-block " >{{ u.Name }}</span>
                                    <p class="text-sm">Offline</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div :a="aaa" class="flex flex-col w-4/5 bg-gradient-to-r from-[#526c8a] to-[#4d5382] rounded-3xl p-4 min-h-full max-h-vh overflow-y-scroll scroll-smooth">
            <div v-if="currentConversation != null" class="flex flex-col w-full px-2">
                <Messages v-for="message in currentConversation.messages" :message="message" :users="users"
                    :currentUser="currentUser"></Messages>
            </div>
            <div v-else class="justify-center items-center h-full w-full">
                <span id="splash">Please select a conversation first.</span>
            </div>
        </div>
    </div></template>
