<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits(['add-session']);

const sessions = [
  {
    time: '08:00',
    title: 'Full Body Strength',
    client: 'Marcus Wright',
    duration: '60m',
    location: 'Main Gym',
    avatar: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBqq0RqPRZSCgCmVoqtcWzl8WNau6q6idYUGNo2L9w4PDQCPdW-iYN81jSNLEGHV9R-67Z81rLjMWUTTnUs8Qcnjf_iIqsXSTUP2Nu6Bbg9brReZa0b7Rodt_TM_V2mnT9JYzNPQMq6WkQWFNPIEBM60MWJZMn7ozQNdCb5wshdHJwlEGJm0BOUvmoODHRAwUPlOG2cfYXhHeH0XcT9md9R3AmR6JYPdG_gOMUApmnIvjuIdjGg8QCUgjUTvAJvp7SnxijnK8TH48d4'
  },
  {
    time: '10:30',
    title: 'High Intensity HIIT',
    client: 'Sarah Chen',
    duration: '45m',
    location: 'Virtual',
    isHighlight: true,
    avatar: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBH2mRX9T-Exd3j2LRwJbPeHdiD_NW-G3lIxQzggU3FVZRxHsh5KDASpEjt-ic2AFNSDdviTIEg1lw_0AXUsXZjsFetO3hNxbVkvxxXbEkFUIHOvCEGVQLocdvMzgQiEfjyVZQyqE5O11dWQCKjpZ4sQQYPr8-M3kS4RqUW5ChllT2PMIW-MKFqexpsaoCd0Opqhi_xYD9R4JLjiZ0DzrK55PCnvDWvE_ku--3jZ6f43iXm1CrFrgx-PjgJjMEo8pZPYOQFd_oXeFm1'
  },
  {
    time: '15:00',
    title: 'Post-Injury Mobility',
    client: 'David Miller',
    duration: '30m',
    location: 'Studio A',
    avatar: 'https://lh3.googleusercontent.com/aida-public/AB6AXuDLWD177TjyMiArhiLXulQB7gr0INbwK_68YgAKSLH_-jlVzSjQ9A-idarFjf-oKjRXGAzroOGdPowGDDe6OYu-FsLEqBy7nN9fsTuNx6dy1DbRT07RAYXmdYo0R3Z1sJpcDdGzmlUX83Iwa6YVyYN9LJyfyCmapCkaIqRSaAGxEspHHc6dihsvs7o2VJxvNlRNGmjuQOKmoex5FiLbh0VoBIlRpoeJsBETkFkrulnec-Uwf813EKubwACNLhcOA7fzL7VSPcG2TzMC'
  }
];
</script>

<template>
  <div class="flex flex-col h-full">
    <!-- Header -->
    <header class="flex items-center p-4 pb-2 justify-between sticky top-0 z-20 bg-background-light dark:bg-background-dark">
      <div class="text-primary flex size-10 items-center justify-center rounded-lg hover:bg-primary/10 cursor-pointer">
        <span class="material-symbols-outlined">menu</span>
      </div>
      <h2 class="text-lg font-bold leading-tight tracking-[-0.015em] flex-1 text-center">Scheduler</h2>
      <div class="flex w-10 items-center justify-end">
        <button @click="emit('add-session')" class="flex size-10 cursor-pointer items-center justify-center rounded-lg bg-primary text-white shadow-lg shadow-primary/20">
          <span class="material-symbols-outlined">add</span>
        </button>
      </div>
    </header>

    <!-- View Toggle Tabs -->
    <div class="px-4 pt-2">
      <div class="flex border-b border-slate-200 dark:border-border-dark gap-8">
        <button class="flex flex-col items-center justify-center border-b-[3px] border-b-transparent text-slate-500 dark:text-slate-400 pb-[13px] pt-2">
          <p class="text-sm font-bold leading-normal tracking-[0.015em]">Monthly</p>
        </button>
        <button class="flex flex-col items-center justify-center border-b-[3px] border-b-primary text-primary pb-[13px] pt-2">
          <p class="text-sm font-bold leading-normal tracking-[0.015em]">Weekly</p>
        </button>
      </div>
    </div>

    <!-- Weekly View Calendar -->
    <div class="flex flex-col p-4 gap-2">
      <div class="flex items-center justify-between mb-2">
        <button class="text-slate-600 dark:text-slate-400 p-1">
          <span class="material-symbols-outlined">chevron_left</span>
        </button>
        <p class="text-slate-900 dark:text-slate-100 text-base font-bold">Oct 23 - Oct 29, 2023</p>
        <button class="text-slate-600 dark:text-slate-400 p-1">
          <span class="material-symbols-outlined">chevron_right</span>
        </button>
      </div>
      <div class="grid grid-cols-7 gap-1">
        <div class="flex flex-col items-center p-2 rounded-xl bg-primary/10 border border-primary/20">
          <p class="text-[10px] font-bold text-primary uppercase">Mon</p>
          <p class="text-lg font-bold text-primary">23</p>
        </div>
        <div class="flex flex-col items-center p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-card-dark transition-colors">
          <p class="text-[10px] font-bold text-slate-400 uppercase">Tue</p>
          <p class="text-lg font-bold">24</p>
        </div>
        <div class="flex flex-col items-center p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-card-dark transition-colors">
          <p class="text-[10px] font-bold text-slate-400 uppercase">Wed</p>
          <p class="text-lg font-bold">25</p>
        </div>
        <div class="flex flex-col items-center p-2 rounded-xl bg-primary shadow-lg shadow-primary/30">
          <p class="text-[10px] font-bold text-white uppercase">Thu</p>
          <p class="text-lg font-bold text-white">26</p>
        </div>
        <div class="flex flex-col items-center p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-card-dark transition-colors">
          <p class="text-[10px] font-bold text-slate-400 uppercase">Fri</p>
          <p class="text-lg font-bold">27</p>
        </div>
        <div class="flex flex-col items-center p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-card-dark transition-colors">
          <p class="text-[10px] font-bold text-slate-400 uppercase">Sat</p>
          <p class="text-lg font-bold">28</p>
        </div>
        <div class="flex flex-col items-center p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-card-dark transition-colors">
          <p class="text-[10px] font-bold text-slate-400 uppercase">Sun</p>
          <p class="text-lg font-bold">29</p>
        </div>
      </div>
    </div>

    <!-- Today's Timeline -->
    <div class="flex-1 px-4 pb-4">
      <h3 class="text-slate-900 dark:text-slate-100 text-lg font-bold leading-tight tracking-[-0.015em] mb-4">Today's Sessions</h3>
      <div class="space-y-4">
        <template v-for="(session, index) in sessions" :key="index">
          <div class="flex gap-4">
            <div class="flex flex-col items-center pt-1 min-w-12">
              <span class="text-xs font-bold text-slate-400">{{ session.time }}</span>
              <div class="w-px flex-1 bg-slate-200 dark:bg-border-dark my-2"></div>
            </div>
            <div :class="session.isHighlight ? 'bg-primary/10 dark:bg-primary/20 border-primary/20' : 'bg-white dark:bg-card-dark border-slate-100 dark:border-border-dark'" 
                 class="flex-1 p-4 rounded-xl border shadow-sm relative overflow-hidden">
              <div v-if="session.isHighlight" class="absolute top-0 right-0 p-2 opacity-20">
                <span class="material-symbols-outlined text-4xl text-primary">fitness_center</span>
              </div>
              <div class="flex justify-between items-start mb-2">
                <div>
                  <p class="text-xs font-bold text-primary uppercase mb-0.5">{{ session.title }}</p>
                  <h4 class="font-bold text-slate-900 dark:text-slate-100">{{ session.client }}</h4>
                </div>
                <img class="size-8 rounded-full border border-slate-200 dark:border-border-dark" :src="session.avatar" :alt="session.client"/>
              </div>
              <div class="flex items-center gap-3 text-xs" :class="session.isHighlight ? 'text-primary/80' : 'text-slate-500'">
                <span class="flex items-center gap-1"><span class="material-symbols-outlined text-sm">schedule</span> {{ session.duration }}</span>
                <span class="flex items-center gap-1"><span class="material-symbols-outlined text-sm">{{ session.location === 'Virtual' ? 'videocam' : 'location_on' }}</span> {{ session.location }}</span>
              </div>
            </div>
          </div>
          
          <!-- Add slot after 10:30 session -->
          <div v-if="session.time === '10:30'" class="flex gap-4">
            <div class="flex flex-col items-center pt-1 min-w-12">
              <span class="text-xs font-bold text-slate-400">12:00</span>
              <div class="w-px flex-1 bg-slate-200 dark:bg-border-dark my-2"></div>
            </div>
            <button @click="emit('add-session')" class="flex-1 border-2 border-dashed border-slate-200 dark:border-border-dark p-4 rounded-xl flex items-center justify-center gap-2 text-slate-400 hover:bg-slate-50 dark:hover:bg-card-dark transition-colors">
              <span class="material-symbols-outlined">add_circle</span>
              <span class="text-sm font-medium">Tap to schedule</span>
            </button>
          </div>
        </template>
      </div>
    </div>
  </div>
</template>
