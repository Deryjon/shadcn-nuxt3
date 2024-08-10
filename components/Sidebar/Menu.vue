<script setup>
import Logo from '../Logo.vue'
const items = ref([
    {
        title: 'Overview',
        path: '/overview',
        icon: 'ri:dashboard-line',
        path: '/',
    },
    {
        title: 'Transactions',
        path: '/transactions',
        icon: 'oi:transfer',
        path: '/transactions',

    },
    {
        title: 'Account',
        path: '/account',
        icon: 'ri:account-circle-line',
path: '/account',
    },
    {
        title: 'Contacts',
        path: '/contacts',
        icon: 'mingcute:contacts-4-fill',
        path: '/contacts',
    },
    {
        title: 'Settings',
        path: '/settings',
        icon: 'ri:settings-3-line',
        path: '/settings',
    },
])
</script>
<template>
    <div>
        <header class="flex items-center gap-2 p-4 hover:scale-[101%] transition cursor-pointer">
            <Logo />
            <p class="font-bold text-black">Nuxt-Finance</p>
        </header>
        <div class="px-4 grow">
            <div class="grid gap-4">
                <NuxtLink :href="item.path" v-for="(item, index) in items" :key="index"
                    class="flex items-center gap-2 px-2 py-1 transition rounded cursor-pointer hover:bg-neutral-100 text-lg">
                    <Icon size="20" :name="item.icon" color="black" />
                    <span class="">{{ item.title }}</span>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>