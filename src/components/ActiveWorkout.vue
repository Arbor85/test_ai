<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits(['finish']);

const sets = ref([
  { id: 1, lbs: 225, reps: 5, completed: true },
  { id: 2, lbs: 225, reps: 5, completed: false },
  { id: 3, lbs: 225, reps: 5, completed: false, upcoming: true }
]);

const toggleSet = (index: number) => {
  sets.value[index].completed = !sets.value[index].completed;
};
</script>

<template>
  <div class="flex flex-col h-full bg-background-light dark:bg-background-dark">
    <!-- Top App Bar -->
    <header class="flex items-center p-4 pb-2 justify-between sticky top-0 z-10 border-b border-slate-200 dark:border-slate-800 bg-background-light dark:bg-background-dark">
      <div class="text-primary flex size-12 shrink-0 items-center justify-center">
        <span class="material-symbols-outlined text-3xl">fitness_center</span>
      </div>
      <h2 class="text-slate-900 dark:text-slate-100 text-lg font-bold leading-tight tracking-[-0.015em] flex-1 px-2">Lower Body Power</h2>
      <div class="flex w-12 items-center justify-end">
        <button class="flex items-center justify-center rounded-lg h-12 w-12 bg-transparent text-slate-900 dark:text-slate-100">
          <span class="material-symbols-outlined">info</span>
        </button>
      </div>
    </header>

    <!-- Progress Section -->
    <div class="flex flex-col gap-3 p-4">
      <div class="flex gap-6 justify-between items-center">
        <p class="text-slate-900 dark:text-slate-100 text-base font-medium leading-normal">Workout Progress</p>
        <p class="text-slate-500 dark:text-slate-400 text-sm font-normal leading-normal">4 of 10 exercises</p>
      </div>
      <div class="rounded-full bg-slate-200 dark:bg-slate-800 h-2 overflow-hidden">
        <div class="h-full rounded-full bg-primary" style="width: 40%;"></div>
      </div>
    </div>

    <!-- Exercise Details -->
    <main class="flex-1 overflow-y-auto pb-32 scroll-hide">
      <div class="px-4 pt-5 pb-3">
        <h2 class="text-slate-900 dark:text-slate-100 tracking-tight text-[28px] font-bold leading-tight">Barbell Back Squat</h2>
      </div>

      <!-- Visual Guide -->
      <div class="p-4">
        <div class="flex flex-col items-stretch justify-start rounded-xl shadow-lg bg-slate-50 dark:bg-slate-900/50 border border-slate-200 dark:border-slate-800">
          <div class="w-full bg-center bg-no-repeat aspect-video bg-cover rounded-t-xl" style='background-image: url("https://lh3.googleusercontent.com/aida-public/AB6AXuCxd4sY5c_flcno4FjGJlTmExE8dWk42i3AGSKW_7GZVqNAitOaHDBdfBrji4nLMh6QvRqUnsyb3fCIIVe2buaFski-Kpcgd7J_tIWDQAQ7_70NldWzSwwKoR5mVIKIyDhor1uj-g9JKz80_u6kLbvOQco2SJtOMEoxLxTYbIQBBXXiR6ZPEiiW2LXCKaW2GLeDScGQo7LAcKjidX7W0Fy1hIKxHWXQHMz7kgDwYB5vdtTJ8DnhLXvXTp7C74gmTtCwf4I_3L4HnT5h");'>
          </div>
          <div class="flex w-full min-w-72 grow flex-col items-stretch justify-center gap-1 py-4 px-4">
            <p class="text-slate-900 dark:text-slate-100 text-lg font-bold leading-tight tracking-[-0.015em]">Proper Form Guide</p>
            <p class="text-slate-500 dark:text-slate-400 text-sm font-normal leading-normal">Keep your chest up, core engaged, and drive through your heels. Ensure thighs are parallel to floor.</p>
          </div>
        </div>
      </div>

      <!-- Set Details Section -->
      <div class="px-4 pb-2 pt-4 flex justify-between items-center">
        <h3 class="text-slate-900 dark:text-slate-100 text-lg font-bold leading-tight tracking-[-0.015em]">Set Details</h3>
        <span class="text-xs font-semibold text-primary uppercase tracking-wider">Rest: 90s</span>
      </div>

      <!-- Sets List -->
      <div class="flex flex-col gap-2 px-4 pb-4">
        <div v-for="(set, index) in sets" :key="set.id" 
             :class="[
               set.completed ? 'bg-primary/10 border-primary/20' : (set.upcoming ? 'bg-slate-50 dark:bg-slate-900 border-slate-200 dark:border-slate-800 opacity-60' : 'bg-slate-50 dark:bg-slate-900 border-2 border-primary')
             ]"
             class="flex items-center gap-4 p-4 rounded-xl border">
          <div :class="set.completed ? 'bg-primary text-white' : 'bg-slate-200 dark:bg-slate-800 text-slate-900 dark:text-slate-100'" class="flex flex-col items-center justify-center w-8 h-8 rounded-full text-sm font-bold">{{ set.id }}</div>
          <div class="flex-1 grid grid-cols-2 gap-4">
            <div class="flex flex-col">
              <span class="text-[10px] uppercase font-bold" :class="set.completed ? 'text-slate-500 dark:text-slate-400' : 'text-primary'">LBS</span>
              <input v-if="!set.completed && !set.upcoming" class="bg-transparent border-none p-0 text-xl font-bold focus:ring-0 text-slate-900 dark:text-slate-100 w-full outline-none" type="number" v-model="set.lbs"/>
              <span v-else class="text-xl font-bold">{{ set.lbs }}</span>
            </div>
            <div class="flex flex-col">
              <span class="text-[10px] uppercase font-bold" :class="set.completed ? 'text-slate-500 dark:text-slate-400' : 'text-primary'">REPS</span>
              <input v-if="!set.completed && !set.upcoming" class="bg-transparent border-none p-0 text-xl font-bold focus:ring-0 text-slate-900 dark:text-slate-100 w-full outline-none" type="number" v-model="set.reps"/>
              <span v-else class="text-xl font-bold">{{ set.reps }}</span>
            </div>
          </div>
          <button @click="toggleSet(index)" class="w-12 h-12 rounded-lg flex items-center justify-center" :class="set.completed ? 'bg-primary text-white' : 'bg-slate-200 dark:bg-slate-800 text-slate-400'">
            <span class="material-symbols-outlined">{{ set.completed ? 'check_circle' : 'circle' }}</span>
          </button>
        </div>
      </div>

      <!-- Timer Action -->
      <div class="px-4 mt-4">
        <button class="w-full py-4 rounded-xl bg-slate-200 dark:bg-slate-800 flex items-center justify-center gap-3 font-bold">
          <span class="material-symbols-outlined">timer</span>
          <span>Start Rest Timer (01:30)</span>
        </button>
      </div>
    </main>

    <!-- Bottom Actions Bar -->
    <footer class="fixed bottom-0 left-0 right-0 p-4 bg-background-light/80 dark:bg-background-dark/80 backdrop-blur-md border-t border-slate-200 dark:border-slate-800 z-20">
      <div class="flex gap-4">
        <button class="flex-1 py-4 bg-slate-200 dark:bg-slate-800 text-slate-900 dark:text-slate-100 rounded-xl font-bold text-lg flex items-center justify-center gap-2">
          <span class="material-symbols-outlined">skip_next</span>
          Skip
        </button>
        <button @click="emit('finish')" class="flex-[2] py-4 bg-primary text-white rounded-xl font-bold text-lg flex items-center justify-center gap-2 shadow-lg shadow-primary/20">
          <span class="material-symbols-outlined">check</span>
          Finish Workout
        </button>
      </div>
    </footer>
  </div>
</template>
