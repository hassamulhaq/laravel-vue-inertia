<template>
    <header class="sticky top-0 bg-white border-b border-slate-200 z-30">
        <div class="px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16 -mb-px">

                <!-- Header: Left side -->
                <div class="flex">
                    <!-- Hamburger button -->
                    <button class="text-slate-500 hover:text-slate-600 lg:hidden" @click.stop="sidebarOpen = !sidebarOpen" aria-controls="sidebar" :aria-expanded="sidebarOpen" aria-expanded="false">
                        <span class="sr-only">Open sidebar</span>
                        <svg class="w-6 h-6 fill-current" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                            <rect x="4" y="5" width="16" height="2"></rect>
                            <rect x="4" y="11" width="16" height="2"></rect>
                            <rect x="4" y="17" width="16" height="2"></rect>
                        </svg>
                    </button>
                </div>

                <!-- Header: Right side -->
                <nav class="bg-white border-b border-gray-100">
                    <div class="flex items-center space-x-3">
                        <!-- Profile dropdown -->
                        <div class="hidden sm:flex sm:items-center sm:ml-6">
                            <!-- Settings Dropdown -->
                            <div class="ml-3 relative">
                                <Dropdown align="right" width="48">
                                    <template #trigger>
                                    <span class="inline-flex rounded-md">
                                        <button
                                            type="button"
                                            class="inline-flex items-center px-3 py-2 border border-transparent text-sm leading-4 font-medium rounded-md text-gray-500 bg-white hover:text-gray-700 focus:outline-none transition ease-in-out duration-150"
                                        >
                                            {{ $page.props.auth.user.name }}

                                            <svg
                                                class="ml-2 -mr-0.5 h-4 w-4"
                                                xmlns="http://www.w3.org/2000/svg"
                                                viewBox="0 0 20 20"
                                                fill="currentColor"
                                            >
                                                <path
                                                    fill-rule="evenodd"
                                                    d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                                    clip-rule="evenodd"
                                                />
                                            </svg>
                                        </button>
                                    </span>
                                    </template>

                                    <template #content>
                                        <DropdownLink :href="route('profile.edit')"> Profile </DropdownLink>
                                        <DropdownLink :href="route('logout')" method="post" as="button">
                                            Log Out
                                        </DropdownLink>
                                    </template>
                                </Dropdown>
                            </div>
                        </div>
                        <!-- /_Profile dropdown -->

                        <!-- Hamburger -->
                        <div class="-mr-2 flex items-center sm:hidden">
                            <button
                                @click="showingNavigationDropdown = !showingNavigationDropdown"
                                class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 focus:text-gray-500 transition duration-150 ease-in-out"
                            >
                                <svg class="h-6 w-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                                    <path
                                        :class="{
                                        hidden: showingNavigationDropdown,
                                        'inline-flex': !showingNavigationDropdown,
                                    }"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                        stroke-width="2"
                                        d="M4 6h16M4 12h16M4 18h16"
                                    />
                                    <path
                                        :class="{
                                        hidden: !showingNavigationDropdown,
                                        'inline-flex': showingNavigationDropdown,
                                    }"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                        stroke-width="2"
                                        d="M6 18L18 6M6 6l12 12"
                                    />
                                </svg>
                            </button>
                        </div>
                        <!-- Responsive Navigation Menu -->
                        <div
                            :class="{ block: showingNavigationDropdown, hidden: !showingNavigationDropdown }"
                            class="sm:hidden"
                        >
                            <div class="pt-2 pb-3 space-y-1">
                                <ResponsiveNavLink :href="route('dashboard')" :active="route().current('dashboard')">
                                    Dashboard
                                </ResponsiveNavLink>
                            </div>

                            <!-- Responsive Settings Options -->
                            <div class="pt-4 pb-1 border-t border-gray-200">
                                <div class="px-4">
                                    <div class="font-medium text-base text-gray-800">
                                        {{ $page.props.auth.user.name }}
                                    </div>
                                    <div class="font-medium text-sm text-gray-500">{{ $page.props.auth.user.email }}</div>
                                </div>

                                <div class="mt-3 space-y-1">
                                    <ResponsiveNavLink :href="route('profile.edit')"> Profile </ResponsiveNavLink>
                                    <ResponsiveNavLink :href="route('logout')" method="post" as="button">
                                        Log Out
                                    </ResponsiveNavLink>
                                </div>
                            </div>
                        </div>
                    </div>
                </nav>
                <!-- /_Header: Right side -->
            </div>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue';
import Header from "@/Pages/Header.vue";
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';

const showingNavigationDropdown = ref(false);
</script>

<style scoped>

</style>
