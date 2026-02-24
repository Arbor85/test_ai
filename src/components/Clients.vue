<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits(['add-client']);

const clients = [
  {
    name: 'Alex Johnson',
    program: 'Summer Shred 2024',
    status: 'Active',
    type: 'Individual',
    format: 'Online',
    next: 'Lower Body A',
    avatar: 'https://lh3.googleusercontent.com/aida-public/AB6AXuD_QPcxq09pNDqf-_Akp4z84Nmq1eb0QCFiFGYpCUOlUKtdsYs6lRQnwBx39-Dl5j_wrx8bEn_ZKXhGbo3rwt2Aqn_RZdc2UppB9qv1BEUavsHhhZh_7Ua_uYR1lItcVHH9fTX6D2TFIqmqYqf7_0Sh82Ifzx22hW_P83iLiF98dUg_Wc3RX7RSy1y31LaehwX7EjkkAsQng7-5WHXX2ZV5kaM_b8v7-bZ-Pg3eUBDUsAe-2_4J3u7l0j99B6X015OFId8SzHFX6POM'
  },
  {
    name: 'Marcus Wright',
    program: 'Strength Foundations',
    status: 'Rest Day',
    type: 'Group',
    format: 'In-person',
    next: 'Active Recovery',
    avatar: 'https://lh3.googleusercontent.com/aida-public/AB6AXuCyePahTiU_Eysdj3CU_0JVz4WsfmfWema6-BskgIBpnQ-Vd7cuXwY1cKHuZO0fyUvsfN3Iqt0pTUK6I6rM71hRDhkEztYxGdjDlPM8riNISkow1iRHA7CfAgIOGQ8Q-JuXhA8RTMjDVyH_04rR9p9mfKrpLpvMxrMke7OjAFz1Ivl6T-3z0zRpQpgVNRx-3k1LV1i05zW3HJ5coQhc4_z6XIiJbxKleUZNiA7DWfheBnSEOLJq7srGc4Us_H8uawp9eQ8pzoN_AN9-'
  },
  {
    name: 'Sarah Chen',
    program: 'Marathon Prep',
    status: 'Active',
    type: 'Individual',
    format: 'In-person',
    next: '10k Tempo Run',
    avatar: 'https://lh3.googleusercontent.com/aida-public/AB6AXuAnWXItrEq01UkAPJpSs7LQpDcN66TkU-sMcF9owYNSZkrEkd9qYs0GuE7RdHf5nZzCpwig-X8zCuFWpuEMD6O1F9cjKgc0aeJg27KzvxwsqJrxB6ATz5A6aphVrT6TLoLwsdlSaNtDCU_hsPipSS2qUq-GyCkBhNuh99mKnwZPMsXdg2tpv8cCmmM5bLiaHjE7pUoJ5-dyNGF4O2QiQRh3Q3ENujj0fUt2f78huq6hzdR2qlkYmaUHMH4DiuWNzpSImLRhQFReYYeK'
  },
  {
    name: 'David Miller',
    program: 'Post-Injury Rehab',
    status: 'Inactive',
    type: 'Individual',
    format: 'Online',
    next: 'Last seen: 2 weeks ago',
    avatar: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBVlElHegKnNEhzYLO3wU8g5wTTtD4m5eSnI8TzyL8PvmL3FUUyZRRvUHOdDqhbfw6_0dkcqJyITIdwem7t8qldqRVeglm-jg1fTLKVQ-Fzw_ycGPrY3HtDVfvB0ZrutdS_0EK1zF9O-IIyJGAVNIhLIYMAUSlP9v7AuX0UFya-ie9oG5CqsecwLygHHhhJuMen8s_GpYp1eOr1qOY-xVsIVGszsOh9yJC8TK489t41IhPDjGohLp9ZpkZXqq1_jnlkPok_mSkQNXiz'
  }
];
</script>

<template>
  <div class="flex flex-col h-full">
    <header class="sticky top-0 z-10 flex items-center justify-between bg-background-light/80 dark:bg-background-dark/80 px-4 py-4 backdrop-blur-md">
      <div class="flex items-center gap-3">
        <span class="material-symbols-outlined text-primary text-3xl">exercise</span>
        <h1 class="text-xl font-bold tracking-tight">Clients</h1>
      </div>
      <div class="flex gap-2">
        <button class="flex h-10 w-10 items-center justify-center rounded-full bg-primary/10 text-primary">
          <span class="material-symbols-outlined">search</span>
        </button>
        <button @click="emit('add-client')" class="flex h-10 w-10 items-center justify-center rounded-full bg-primary text-white shadow-lg shadow-primary/30">
          <span class="material-symbols-outlined">add</span>
        </button>
      </div>
    </header>

    <main class="flex flex-col gap-6 p-4">
      <section class="grid grid-cols-2 gap-4">
        <div class="flex flex-col gap-1 rounded-xl bg-white dark:bg-slate-800 p-4 shadow-sm border border-slate-200 dark:border-slate-700">
          <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-slate-400">Total Clients</span>
          <span class="text-3xl font-bold text-primary">32</span>
        </div>
        <div class="flex flex-col gap-1 rounded-xl bg-white dark:bg-slate-800 p-4 shadow-sm border border-slate-200 dark:border-slate-700">
          <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-slate-400">Active Today</span>
          <span class="text-3xl font-bold text-emerald-500">24</span>
        </div>
      </section>

      <nav class="flex gap-2 overflow-x-auto pb-2 scroll-hide">
        <button class="whitespace-nowrap rounded-full bg-primary px-5 py-2 text-sm font-semibold text-white">All Clients</button>
        <button class="whitespace-nowrap rounded-full bg-white dark:bg-slate-800 px-5 py-2 text-sm font-medium text-slate-600 dark:text-slate-300 border border-slate-200 dark:border-slate-700">Active</button>
        <button class="whitespace-nowrap rounded-full bg-white dark:bg-slate-800 px-5 py-2 text-sm font-medium text-slate-600 dark:text-slate-300 border border-slate-200 dark:border-slate-700">Resting</button>
        <button class="whitespace-nowrap rounded-full bg-white dark:bg-slate-800 px-5 py-2 text-sm font-medium text-slate-600 dark:text-slate-300 border border-slate-200 dark:border-slate-700">Inactive</button>
      </nav>

      <section class="flex flex-col gap-4">
        <div v-for="(client, index) in clients" :key="index" class="flex flex-col gap-4 rounded-xl bg-white dark:bg-slate-800 p-4 shadow-sm border border-slate-200 dark:border-slate-700">
          <div class="flex items-start justify-between">
            <div class="flex items-center gap-3">
              <div class="h-14 w-14 overflow-hidden rounded-full bg-slate-200 dark:bg-slate-700">
                <img class="h-full w-full object-cover" :src="client.avatar" :alt="client.name"/>
              </div>
              <div>
                <h3 class="font-bold text-slate-900 dark:text-slate-100">{{ client.name }}</h3>
                <div class="flex items-center gap-2 mt-0.5">
                  <div class="flex items-center gap-1 text-[10px] font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider bg-slate-100 dark:bg-slate-700 px-1.5 py-0.5 rounded">
                    <span class="material-symbols-outlined text-xs">{{ client.type === 'Individual' ? 'person' : 'groups' }}</span>{{ client.type }}
                  </div>
                  <div class="flex items-center gap-1 text-[10px] font-semibold text-slate-500 dark:text-slate-400 uppercase tracking-wider bg-slate-100 dark:bg-slate-700 px-1.5 py-0.5 rounded">
                    <span class="material-symbols-outlined text-xs">{{ client.format === 'Online' ? 'cloud' : 'location_on' }}</span>{{ client.format }}
                  </div>
                </div>
                <p class="text-xs text-slate-400 dark:text-slate-500 mt-1">{{ client.program }}</p>
              </div>
            </div>
            <span :class="{
              'bg-emerald-100 dark:bg-emerald-900/30 text-emerald-600 dark:text-emerald-400': client.status === 'Active',
              'bg-amber-100 dark:bg-amber-900/30 text-amber-600 dark:text-amber-400': client.status === 'Rest Day',
              'bg-slate-100 dark:bg-slate-700/50 text-slate-500 dark:text-slate-400': client.status === 'Inactive'
            }" class="rounded-full px-3 py-1 text-xs font-bold">{{ client.status }}</span>
          </div>
          <div class="flex items-center justify-between border-t border-slate-100 dark:border-slate-700 pt-3">
            <div class="flex items-center gap-2">
              <span class="material-symbols-outlined text-slate-400 text-lg">calendar_today</span>
              <span class="text-xs font-medium text-slate-600 dark:text-slate-400">{{ client.status === 'Inactive' ? client.next : 'Next: ' + client.next }}</span>
            </div>
            <button class="text-sm font-bold text-primary">View Details</button>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>
