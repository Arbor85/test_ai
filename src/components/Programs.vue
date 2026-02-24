<script setup lang="ts">
const programs = [
  {
    title: '12-Week Hypertrophy',
    level: 'Advanced',
    description: 'High volume muscle building program focused on heavy compounds and metabolic stress.',
    duration: '12 Weeks',
    sessions: '84 Sessions',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuCZzia1320IYNGoLI5XvP-Lbfua0KBk2unAl52YhlON8kgsp-Q_HO-inInxGT-_9_QNhKxpTC9jvlWZ3_cvBA6Wm3efxmANQh-uAkhvQFakWcWa5g6vwCPsRA4lO_t_bKhBs6jkfnqNYlQ_8j9Z0wl5lK5eEfk8B7L5lKvIf4jy7lClcrs-oMoVQlMHFRhSrhNZroW41unp8o-gYXPCG9Asa1Yj0KIS1X5WYYa-uXM3XDoltfAh8T9E3eMB_Hc5VyxOkYH15Fyz6axx'
  },
  {
    title: 'Engine Builder 1.0',
    level: 'Intermediate',
    description: 'Improve aerobic capacity and lactic threshold through structured intervals.',
    duration: '8 Weeks',
    sessions: '24 Sessions',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBqbeS3DxSgk9OF15vkpP2Nkr_-_GKi42S5uLf-746TggzU6Sw25D7XXdzecvydUNWF1-X8BgMmqzDMhFEBPkw5hO1WPoFXdHpKWjea-6uenvQrsg0EPcZAUZH1YLZjFqiCQCYA62DJIlL6eIlt264Ngqfix40peRDLg5UtKFwehnttF5aBY6CAYXWz69Vag1lXN9A3TWIl3DqmUEmFbZyH29HgWalBLGWzSIBaUcs7fwone-Rbjj_DbE7Je6GU3TfGx1c1BiwXjFM_'
  },
  {
    title: 'Bodyweight Burn',
    level: 'Beginner',
    description: 'Effective full body workouts requiring zero equipment. Perfect for home or travel.',
    duration: '4 Weeks',
    sessions: '20 Sessions',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBzRI1abYUmgg8j5E7lhyCFEVCY6AbNsAl1xxyJ_aqEvjyVqEQTfbkGmQwtl3lQWnKc-mLW_xq0A5BsuZ3tYxJtXcwQcb83RlGUwodi5S9Ktke1YqjSVyg-T3LwPHMGbZ9ERg07wKh5bxAaqFm_MkX5CYt9pHkjLLDjArvOYtrxsxeekE7KWrcneFanmKsX7Vw_KwHXY8njVaaItP9bu534JGQphcqX1f2CIV4j0VQsi0ZisR74_Dd0yqyousPaed-jHL3MGMLwdwyL'
  }
];
</script>

<template>
  <div class="flex flex-col h-full">
    <div class="pt-12 px-4 pb-2 flex items-center justify-between">
      <span class="material-symbols-outlined text-slate-900 dark:text-slate-100 p-2">menu</span>
      <h1 class="text-xl font-bold leading-tight tracking-tight">Programs</h1>
      <div class="flex items-center gap-2">
        <button class="flex items-center justify-center p-2 rounded-full hover:bg-slate-200 dark:hover:bg-slate-800 transition-colors">
          <span class="material-symbols-outlined text-slate-900 dark:text-slate-100">account_circle</span>
        </button>
      </div>
    </div>

    <div class="px-4 py-4">
      <div class="flex items-center gap-3">
        <div class="relative flex-1">
          <span class="material-symbols-outlined absolute left-3 top-1/2 -translate-y-1/2 text-slate-400 text-xl">search</span>
          <input class="w-full bg-slate-100 dark:bg-slate-900 border-none rounded-xl py-3 pl-10 pr-4 text-sm focus:ring-2 focus:ring-primary/50 text-slate-900 dark:text-slate-100 placeholder:text-slate-500 outline-none" placeholder="Search programs..." type="text"/>
        </div>
        <button class="bg-primary text-white p-3 rounded-xl flex items-center justify-center shadow-lg shadow-primary/20">
          <span class="material-symbols-outlined">add</span>
        </button>
      </div>
    </div>

    <div class="px-4 pb-4">
      <div class="flex gap-4 overflow-x-auto scroll-hide border-b border-slate-200 dark:border-slate-800">
        <button class="pb-3 border-b-2 border-primary text-slate-900 dark:text-slate-100 text-sm font-semibold whitespace-nowrap">All Programs</button>
        <button class="pb-3 border-b-2 border-transparent text-slate-500 text-sm font-medium whitespace-nowrap">Strength</button>
        <button class="pb-3 border-b-2 border-transparent text-slate-500 text-sm font-medium whitespace-nowrap">Endurance</button>
        <button class="pb-3 border-b-2 border-transparent text-slate-500 text-sm font-medium whitespace-nowrap">Fat Loss</button>
        <button class="pb-3 border-b-2 border-transparent text-slate-500 text-sm font-medium whitespace-nowrap">Yoga</button>
      </div>
    </div>

    <div class="flex-1 overflow-y-auto px-4 space-y-4 pb-4 scroll-hide">
      <div v-for="(program, index) in programs" :key="index" class="bg-white dark:bg-slate-900/50 rounded-xl overflow-hidden border border-slate-200 dark:border-slate-800 group transition-all hover:border-primary/50">
        <div class="h-40 bg-cover bg-center" :style="{ backgroundImage: `url(${program.image})` }"></div>
        <div class="p-4">
          <div class="flex justify-between items-start mb-1">
            <h3 class="text-lg font-bold">{{ program.title }}</h3>
            <span :class="{
              'bg-primary/10 text-primary': program.level === 'Advanced',
              'bg-emerald-500/10 text-emerald-500': program.level === 'Intermediate',
              'bg-blue-500/10 text-blue-500': program.level === 'Beginner'
            }" class="text-[10px] font-bold px-2 py-0.5 rounded-full uppercase">{{ program.level }}</span>
          </div>
          <p class="text-slate-500 dark:text-slate-400 text-sm mb-4 line-clamp-2">{{ program.description }}</p>
          <div class="flex items-center justify-between">
            <div class="flex gap-4 text-xs text-slate-400 font-medium uppercase tracking-wider">
              <span class="flex items-center gap-1"><span class="material-symbols-outlined text-sm">calendar_today</span> {{ program.duration }}</span>
              <span class="flex items-center gap-1"><span class="material-symbols-outlined text-sm">exercise</span> {{ program.sessions }}</span>
            </div>
            <button class="bg-primary hover:bg-primary/90 text-white px-4 py-2 rounded-lg text-sm font-semibold transition-colors">
              View
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
