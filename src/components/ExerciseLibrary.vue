<script setup lang="ts">
const emit = defineEmits(['back']);

const exercises = [
  {
    name: 'Bench Press',
    muscle: 'Chest',
    equipment: 'Barbell',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuCkp0oqXZV2COgCJqoAxHmj-rotC2ZYfC7omH_uG-i-MnJPySg7IRy_sNIHyUGo2BkPqlw9IIUanETfcyicESHXNfhkvfLd7V5gbwColZhIm24fVfoPfzu3DLzqQXDb1kd4ADymXnBr12ZNXUWr5tC3gCyPL7g-WQ5i664h5R91Lmef1mUj_FTZXdM4duhFm0RRehKAu0TE6N6i2_vdV1WnZM2-7zXJmYa7N78Lc66_3ZBpFkW9GmE3GcLQZbQm8pYecm34GCMkcZpQ'
  },
  {
    name: 'Lat Pulldown',
    muscle: 'Back',
    equipment: 'Machine',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBbBEJoz_JzilRrOaLyQuktpnP_AQoABG-QgKfm82y7wbPNidgPYqZY4mPP3O0rARYdnK5RdC3HbVmNsfIK1UrSOAhPfLju4YSxU6aAew4o8GY4PIijI6xue031g_NDzpABEZFkbOenHCeYv_2QottA7uXhT8yZfAMjTnjMmu5-dBJc8yaHiaT_NmqKbg_hHmoyPyUo48RSmW87OV5ij-IVlfdfwoQHXfSAcoqFCwTPDvBGsgJAd8umwY56wCghsOWIVrfOOXknUB8L'
  },
  {
    name: 'Dumbbell Flyes',
    muscle: 'Chest',
    equipment: 'Dumbbell',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuCwdLswK0ggVyxJ1hloOwSEhf99CHxi44eA7Tq8zWPpthVgbwcGYfRpTmuw4_p_o3uCSfF_37lghxYLpvGlzhwUSHIHAllOVcCqDHKotdLxPzcy_mOKTzRZe_aBzM0zpdpwtHYCp9bSps5IMQVRaXDgJ6KOvwZ03UPlvePCUWERiSr0_Jkp7BS86ybT6j4wglK6A-7oo-If2qgF02a2-XHJPKplhSXpiIEHr5LZIq7fP9cmTY-Ann2ALp90VjfKxAVJSCM3F06hTy5Q'
  },
  {
    name: 'Back Squat',
    muscle: 'Legs',
    equipment: 'Barbell',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBdWNuIK2nFRgrr4Zkg2RwGGLhq0lftBTOzSdOtj0KvToG_6gXezEogvbALftFOhuLltivcUS3eU4IWohBRZEK7QJt38flcVQeCPiidNSRpOKA1OmIVCwcYn8JmM7cN-OH1kALl0S1cXqI4KIfUeQTJGrsa6GDRGTQSnEzzirCcX82lIi2SnxkEgGW5QHLWVei7zIqMjud4NdmtGO7q4H0a-IbS4JY782bClOvygh8Oj5jRnSgqEcre_nWVhcYcfGYyldO6jrC79NDl'
  },
  {
    name: 'Seated Row',
    muscle: 'Back',
    equipment: 'Cable',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuB99qVWyMrF7TI6Pj6lXX6ZfDFz1OScUJfZMG_EmpzQQb9mzXnATfDJQXE4h5H6n4X-x-RqFkku9JNGB4zEcPeP2Q9NUT80kdviX1HaIiZXFHG0CtiwQC1UHESAEOdoAWf3VstlYYg37VN-fj-5KFrwxsbSaMXAt8z9VD4Coaf9S4pXIt0_eNAoAKPfndJ-YFstVzSSc1HanziFnbTbuNV3fw-TFuhLRHhrC_SnidNsQ31soIj1NqvAOM702n2lxGxCF6iwGu6foXis'
  },
  {
    name: 'Walking Lunges',
    muscle: 'Legs',
    equipment: 'Bodyweight',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuCr1Uplgg0E5fP0JFluNbyIKVtX9nHRgOVpiByDPeP2JrnFde0S2oo-lpQ7Yaxk7A18FeS8PqwTWPsZylVYax-kn-owR-DPblNnPvleEGLhDdCLIqjaVp2npqbhxZ9R_gVTuAT1xgutA3ffo1mgMhAkhazGUez3npHGMX9r1w5ys7wPoBSUv28g0K-ph_eIH1Ej5aMebUt0jDyr8IMZYEG2-yNoA-1tZJpWN-wYZj2KujA3F2kY1buyZKvYF8Ri9JEeRf4m73jTsN4z'
  }
];
</script>

<template>
  <div class="flex flex-col h-full">
    <div class="sticky top-0 z-10 bg-background-light/80 dark:bg-background-dark/80 backdrop-blur-md border-b border-slate-200 dark:border-slate-800">
      <div class="flex items-center px-4 py-4 justify-between">
        <button @click="emit('back')" class="flex items-center gap-2">
          <span class="material-symbols-outlined text-slate-600 dark:text-slate-400">arrow_back_ios</span>
          <h2 class="text-xl font-bold tracking-tight">Exercise Library</h2>
        </button>
        <div class="flex gap-3">
          <button class="flex items-center justify-center size-10 rounded-full bg-slate-200/50 dark:bg-slate-800/50 text-slate-700 dark:text-slate-300">
            <span class="material-symbols-outlined">filter_list</span>
          </button>
          <button class="flex items-center justify-center size-10 rounded-full bg-primary text-white shadow-lg shadow-primary/20">
            <span class="material-symbols-outlined">add</span>
          </button>
        </div>
      </div>
      
      <div class="px-4 pb-4">
        <label class="relative flex items-center w-full">
          <span class="material-symbols-outlined absolute left-4 text-slate-400">search</span>
          <input class="w-full h-12 pl-12 pr-4 rounded-xl border-none bg-slate-200/50 dark:bg-slate-800/50 focus:ring-2 focus:ring-primary/50 text-base placeholder:text-slate-400 outline-none" placeholder="Search exercises..." type="text"/>
        </label>
      </div>

      <div class="flex gap-2 px-4 pb-4 overflow-x-auto scroll-hide">
        <button class="flex h-9 shrink-0 items-center justify-center gap-2 rounded-full bg-primary text-white px-5 text-sm font-medium">
          <span>All</span>
        </button>
        <button class="flex h-9 shrink-0 items-center justify-center gap-2 rounded-full bg-slate-200/50 dark:bg-slate-800/50 text-slate-700 dark:text-slate-300 px-5 text-sm font-medium">
          <span>Chest</span>
          <span class="material-symbols-outlined text-[18px]">expand_more</span>
        </button>
        <button class="flex h-9 shrink-0 items-center justify-center gap-2 rounded-full bg-slate-200/50 dark:bg-slate-800/50 text-slate-700 dark:text-slate-300 px-5 text-sm font-medium">
          <span>Back</span>
          <span class="material-symbols-outlined text-[18px]">expand_more</span>
        </button>
        <button class="flex h-9 shrink-0 items-center justify-center gap-2 rounded-full bg-slate-200/50 dark:bg-slate-800/50 text-slate-700 dark:text-slate-300 px-5 text-sm font-medium">
          <span>Legs</span>
          <span class="material-symbols-outlined text-[18px]">expand_more</span>
        </button>
      </div>
    </div>

    <div class="flex flex-col px-4 pt-4 gap-4 pb-4">
      <div v-for="(exercise, index) in exercises" :key="index" class="flex items-center gap-4 bg-white dark:bg-slate-900 p-3 rounded-xl shadow-sm border border-slate-100 dark:border-slate-800">
        <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-lg size-16 bg-slate-200 dark:bg-slate-800" :style="{ backgroundImage: `url(${exercise.image})` }"></div>
        <div class="flex flex-col flex-1 justify-center">
          <p class="text-slate-900 dark:text-slate-100 text-base font-semibold leading-tight">{{ exercise.name }}</p>
          <p class="text-slate-500 dark:text-slate-400 text-xs font-medium mt-1 uppercase tracking-wider">{{ exercise.muscle }} • {{ exercise.equipment }}</p>
        </div>
        <button class="flex size-10 shrink-0 items-center justify-center rounded-full bg-primary/10 dark:bg-primary/20 text-primary">
          <span class="material-symbols-outlined font-bold">add</span>
        </button>
      </div>
    </div>
  </div>
</template>
