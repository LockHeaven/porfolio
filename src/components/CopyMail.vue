<template>
    <div class="relative group/tooltip">
        <button @click="msgCopy = true; copyContent()"
            class="flex bg-emerald-700 hover:bg-opacity-70 py-2.5 px-4 rounded-lg">
            <slot></slot>
        </button>
        <span
            class="absolute pointer-events-none transition-all opacity-0 z-20 bottom-full -translate-y-0 py-1 px-1.5 text-xs left-1/2 -translate-x-1/2 rounded-md whitespace-nowrap text-gray-200 bg-gray-800 before:content-[''] before:absolute before:bg-gray-800 before:rounded-sm before:w-2.5 before:rotate-45 before:h-2.5 before:-bottom-1 before:-z-10 before:left-1/2 before:-translate-x-1/2 group-hover/tooltip:opacity-100 group-hover/tooltip:-translate-y-3">{{
                msgCopy ? 'Copied' : 'Copy email' }}</span>
    </div>
</template>
  
<script setup lang="ts">
import { ref } from 'vue'
var msgCopy = ref(false);

const copyContent = async () => {
    try {
        await navigator.clipboard.writeText('sebas.contreras.ceballos@gmail.com');
    } catch (err) {
        console.error('Failed to copy: ', err);
    }
}
</script>