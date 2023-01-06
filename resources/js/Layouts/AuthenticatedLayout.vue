<script setup>
import { ref } from 'vue';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import { Link } from '@inertiajs/inertia-vue3';
import Sidebar from "@/Pages/Sidebar.vue";
import Header from "@/Pages/Header.vue";

const showingNavigationDropdown = ref(false);
</script>

<template>
    <!-- Page Content -->
    <main class="min-h-screen bg-gray-100">
        <div class="flex h-screen overflow-hidden">
            <Sidebar/>
            <!-- Content area -->
            <div class="relative flex flex-col flex-1 overflow-y-auto overflow-x-hidden">
                <Header :slot="$slots"/>
                <section>
                    <!-- Page Heading -->
                    <header class="bg-white shadow" v-if="$slots.header">
                        <div class="px-4 sm:px-6 lg:px-4 py-4 w-full max-w-9xl mx-auto">
                            <slot name="header" />
                        </div>
                    </header>
                    <div class="px-4 sm:px-6 lg:px-8 py-8 w-full max-w-9xl mx-auto">
                        <slot/>
                    </div>
                </section>
            </div>
        </div>
    </main>
</template>
