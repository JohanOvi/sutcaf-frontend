<script setup>
import { ref } from 'vue';
import Menubar from 'primevue/menubar';
import InputText from 'primevue/inputtext';
import Button from 'primevue/button';

const items = ref([
    {
        label: 'Home',
        icon: 'pi pi-home'
    },
    {
        label: 'Customers',
        icon: 'pi pi-home'
    },
    {
        label: 'Products',
        icon: 'pi pi-home'
    },
    {
        label: 'Invoices',
        icon: 'pi pi-home'
    },
    {
        label: 'Projects',
        icon: 'pi pi-search',
        badge: 3,
        items: [
            {
                label: 'Core',
                icon: 'pi pi-bolt',
                shortcut: '⌘+S'
            },
            {
                label: 'Blocks',
                icon: 'pi pi-server',
                shortcut: '⌘+B'
            },
            {
                separator: true
            },
            {
                label: 'UI Kit',
                icon: 'pi pi-pencil',
                shortcut: '⌘+U'
            }
        ]
    }
]);
</script>

<template>
  <Menubar :model="items"  class="custom-menubar">
    <template #start>
        <svg width="35" height="40" viewBox="0 0 35 40" fill="none" xmlns="http://www.w3.org/2000/svg" class="h-8">
            <path d="..." fill="var(--p-primary-color)" />
            <path d="..." fill="var(--p-text-color)" />
        </svg>
    </template>
    <template #item="{ item, props, hasSubmenu, root }">
        <a v-ripple class="flex items-center" v-bind="props.action">
            <span>{{ item.label }}</span>
            <Badge v-if="item.badge" :class="{ 'ml-auto': !root, 'ml-2': root }" :value="item.badge" />
            <span v-if="item.shortcut" class="ml-auto border border-surface rounded bg-emphasis text-muted-color text-xs p-1">{{ item.shortcut }}</span>
            <i v-if="hasSubmenu" :class="['pi pi-angle-down ml-auto', { 'pi-angle-down': root, 'pi-angle-right': !root }]"></i>
        </a>
    </template>
    <template #end>
        <div class="flex items-center gap-2">
            <InputText placeholder="Search" type="text" class="w-32 sm:w-auto" />
            <Avatar image="/images/avatar/amyelsner.png" shape="circle" />
        </div>
    </template>
  </Menubar>
</template>

<style scoped>
.custom-menubar {
  padding: 0.5rem 1rem !important; /* Reduce el padding vertical */
  border-radius: 0 !important; /* Quita bordes redondeados si los hay */
}

/* Ajusta el tamaño de los items del menú */
:deep(.p-menubar-root-list > .p-menuitem > .p-menuitem-content) {
  padding: 0.5rem 0.75rem !important;
}

/* Ajusta el logo/start */
:deep(.p-menubar-start) {
  padding: 0 !important;
}

/* Ajusta el end */
:deep(.p-menubar-end) {
  padding: 0 !important;
}
</style>