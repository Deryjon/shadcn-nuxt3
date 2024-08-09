<script setup>
const open = ref(true)
</script>
<template>
    <div class="bg-[#fafafa]">
        <div class="flex lg:hidden z-50 items-center justify-between w-full h-full p-4 ">
            <Logo />
            <Icon class="z-50 cursor-pointer left-2 top-2" size="30" name="iconamoon:menu-burger-horizontal"
                @click="open = true" />
            <div v-if="open" class="fixed  top-0 left-0 z-[999] w-full h-full  bg-white">
                <Icon class="absolute right-4 z-50 cursor-pointer top-[34px]" size="30" name="material-symbols:close"
                    @click="open = false" />

                <SidebarMenu />
            </div>
        </div>
        <div class="hidden lg:flex w-[250px] h-screen flex-col justify-between border-r">
            <SidebarMenu />
            <div class="">
                UserItem
            </div>
        </div>
    </div>
</template>