<script setup lang="ts">
import { ref, computed } from 'vue';
import Scheduler from './components/Scheduler.vue';
import Clients from './components/Clients.vue';
import Programs from './components/Programs.vue';
import Login from './components/Login.vue';
import ExerciseLibrary from './components/ExerciseLibrary.vue';
import ActiveWorkout from './components/ActiveWorkout.vue';
import AddClient from './components/AddClient.vue';

const currentScreen = ref('login');
const isDarkMode = ref(true);

const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value;
  document.documentElement.classList.toggle('dark', isDarkMode.value);
};

// Initialize dark mode
document.documentElement.classList.add('dark');

const navigate = (screen: string) => {
  currentScreen.value = screen;
};
</script>

<template>
  <div :class="{ 'dark': isDarkMode }" class="min-h-screen bg-background-light dark:bg-background-dark text-slate-900 dark:text-slate-100 font-display transition-colors duration-300">
    <Login v-if="currentScreen === 'login'" @login="navigate('scheduler')" />
    
    <div v-else class="max-w-[430px] mx-auto min-h-screen relative shadow-2xl border-x border-slate-200 dark:border-slate-800 flex flex-col overflow-hidden">
      <!-- Main Content Area -->
      <div class="flex-1 overflow-y-auto pb-24">
        <Scheduler v-if="currentScreen === 'scheduler'" @add-session="navigate('exercise-library')" />
        <Clients v-if="currentScreen === 'clients'" @add-client="navigate('add-client')" />
        <Programs v-if="currentScreen === 'programs'" />
        <ExerciseLibrary v-if="currentScreen === 'exercise-library'" @back="navigate('scheduler')" />
        <ActiveWorkout v-if="currentScreen === 'active-workout'" @finish="navigate('scheduler')" />
        <AddClient v-if="currentScreen === 'add-client'" @back="navigate('clients')" @save="navigate('clients')" />
      </div>

      <!-- Bottom Navigation -->
      <nav v-if="!['login', 'active-workout', 'add-client'].includes(currentScreen)" 
           class="absolute bottom-0 left-0 right-0 border-t border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-900 px-4 pb-6 pt-2 flex justify-around items-center z-30">
        <button @click="navigate('scheduler')" :class="currentScreen === 'scheduler' ? 'text-primary' : 'text-slate-400'" class="flex flex-col items-center gap-1">
          <span class="material-symbols-outlined" :class="{ 'fill-1': currentScreen === 'scheduler' }">calendar_today</span>
          <span class="text-[10px] font-bold">Schedule</span>
        </button>
        <button @click="navigate('clients')" :class="currentScreen === 'clients' ? 'text-primary' : 'text-slate-400'" class="flex flex-col items-center gap-1">
          <span class="material-symbols-outlined" :class="{ 'fill-1': currentScreen === 'clients' }">group</span>
          <span class="text-[10px] font-bold">Clients</span>
        </button>
        <button @click="navigate('programs')" :class="currentScreen === 'programs' ? 'text-primary' : 'text-slate-400'" class="flex flex-col items-center gap-1">
          <span class="material-symbols-outlined" :class="{ 'fill-1': currentScreen === 'programs' }">exercise</span>
          <span class="text-[10px] font-bold">Programs</span>
        </button>
        <button @click="navigate('active-workout')" class="flex flex-col items-center gap-1 text-slate-400">
          <span class="material-symbols-outlined">monitoring</span>
          <span class="text-[10px] font-bold">Stats</span>
        </button>
        <button @click="toggleDarkMode" class="flex flex-col items-center gap-1 text-slate-400">
          <span class="material-symbols-outlined">{{ isDarkMode ? 'light_mode' : 'dark_mode' }}</span>
          <span class="text-[10px] font-bold">Theme</span>
        </button>
      </nav>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;500;600;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200');

:root {
  --primary: #135bec;
  --background-light: #f6f6f8;
  --background-dark: #101622;
  --card-dark: #192233;
  --border-dark: #232f48;
}

body {
  font-family: 'Lexend', sans-serif;
  -webkit-tap-highlight-color: transparent;
}

.material-symbols-outlined {
  font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 24;
}

.fill-1 {
  font-variation-settings: 'FILL' 1;
}

.scroll-hide::-webkit-scrollbar {
  display: none;
}

.dark {
  color-scheme: dark;
}
</style>
