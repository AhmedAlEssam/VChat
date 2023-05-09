<script setup>
const props = defineProps(["message", "users", "currentUser"]);
</script>
<template>
    <div v-for="u in users">
        <div v-if="u.id == message.user">
            <div v-if="u.id == currentUser" style="text-align: right;">
                <p style="font-weight: bold;">You</p>
                <div class="flex justify-end bg-[#78e08e] rounded my-2 px-2 py-4 " style="text-align: right;">
                    <p>{{ message.text }}</p>
                </div>
                <p style="color:wheat">{{ message.timestamp }}</p>
            </div>
            <div v-else>
                <p style="font-weight: bold;">{{ u.Name }}</p>
                <div class="flex justify-start bg-[#82ccdc]  rounded my-2 px-2 py-4 " style="text-align: right;">
                    <p>{{ message.text }}</p>
                </div>
                <p style="color:wheat">{{ message.timestamp }}</p>
            </div>
        </div>
    </div>
</template>