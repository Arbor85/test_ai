<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits(['login']);

const handleLogin = () => {
  emit('login');
};
</script>

<template>
  <div class="relative flex h-screen w-full flex-col overflow-x-hidden bg-background-light dark:bg-background-dark">
    <!-- Top App Bar -->
    <div class="flex items-center px-4 py-6 justify-between">
      <div class="text-slate-900 dark:text-slate-100 flex size-10 items-center justify-center rounded-full bg-slate-200 dark:bg-slate-800/50">
        <span class="material-symbols-outlined">chevron_left</span>
      </div>
      <div class="flex-1"></div>
    </div>

    <!-- Hero Branding -->
    <div class="flex flex-col items-center px-6 pt-4 pb-8">
      <div class="w-20 h-20 bg-primary rounded-2xl flex items-center justify-center mb-6 shadow-lg shadow-primary/20">
        <span class="material-symbols-outlined text-white text-5xl">fitness_center</span>
      </div>
      <h1 class="text-3xl font-bold tracking-tight text-slate-900 dark:text-slate-100">Peak Performance</h1>
      <p class="text-slate-500 dark:text-slate-400 mt-2 text-center">Manage your clients and workouts with ease</p>
    </div>

    <!-- Login Form Container -->
    <div class="flex flex-col px-6 gap-6 flex-1">
      <h2 class="text-xl font-semibold">Sign In</h2>
      
      <!-- Email Input -->
      <div class="flex flex-col w-full">
        <p class="text-sm font-medium text-slate-700 dark:text-slate-300 pb-2">Email Address</p>
        <div class="relative">
          <span class="material-symbols-outlined absolute left-4 top-1/2 -translate-y-1/2 text-slate-400">mail</span>
          <input class="block w-full pl-12 pr-4 py-4 rounded-xl border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-900/50 text-slate-900 dark:text-slate-100 focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none" placeholder="name@example.com" type="email"/>
        </div>
      </div>

      <!-- Password Input -->
      <div class="flex flex-col w-full">
        <p class="text-sm font-medium text-slate-700 dark:text-slate-300 pb-2">Password</p>
        <div class="relative flex items-center">
          <span class="material-symbols-outlined absolute left-4 text-slate-400">lock</span>
          <input class="block w-full pl-12 pr-12 py-4 rounded-xl border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-900/50 text-slate-900 dark:text-slate-100 focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none" placeholder="••••••••" type="password"/>
          <button class="absolute right-4 text-slate-400 flex items-center justify-center">
            <span class="material-symbols-outlined">visibility</span>
          </button>
        </div>
      </div>

      <!-- Remember Me & Forgot Password -->
      <div class="flex items-center justify-between">
        <label class="flex items-center gap-2 cursor-pointer group">
          <input class="w-5 h-5 rounded border-slate-300 dark:border-slate-700 text-primary focus:ring-primary bg-transparent" type="checkbox"/>
          <span class="text-sm text-slate-600 dark:text-slate-400 group-hover:text-primary transition-colors">Remember Me</span>
        </label>
        <a class="text-sm font-medium text-primary hover:underline" href="#">Forgot Password?</a>
      </div>

      <!-- Action Buttons -->
      <div class="flex flex-col gap-4 mt-4">
        <button @click="handleLogin" class="w-full bg-primary hover:bg-primary/90 text-white font-bold py-4 rounded-xl shadow-lg shadow-primary/30 transition-all flex items-center justify-center gap-2">
          Sign In
          <span class="material-symbols-outlined text-xl">login</span>
        </button>
        
        <div class="flex items-center gap-4 py-2">
          <div class="h-px bg-slate-200 dark:bg-slate-800 flex-1"></div>
          <span class="text-xs text-slate-400 font-medium uppercase tracking-widest">or</span>
          <div class="h-px bg-slate-200 dark:bg-slate-800 flex-1"></div>
        </div>
        
        <button class="w-full bg-slate-100 dark:bg-slate-800/50 text-slate-900 dark:text-slate-100 font-semibold py-4 rounded-xl border border-slate-200 dark:border-slate-700 flex items-center justify-center gap-3">
          <svg class="w-5 h-5" viewBox="0 0 24 24">
            <path d="M12.48 10.92v3.28h7.84c-.24 1.84-.9 3.22-1.9 4.28-1.2 1.2-3.06 2.48-5.94 2.48-4.6 0-8.22-3.72-8.22-8.32s3.62-8.32 8.22-8.32c2.48 0 4.26.98 5.6 2.26l2.32-2.32C18.46 2.1 15.82 1 12.48 1 6.54 1 1.62 5.84 1.62 11.8s4.92 10.8 10.86 10.8c3.2 0 5.62-1.06 7.48-3.02 1.92-1.92 2.54-4.66 2.54-6.86 0-.66-.06-1.28-.18-1.8H12.48z" fill="#EA4335"></path>
          </svg>
          Continue with Google
        </button>
      </div>
    </div>

    <!-- Footer -->
    <div class="p-8 text-center mt-auto">
      <p class="text-slate-500 dark:text-slate-400 text-sm">
        New to the platform? 
        <a class="text-primary font-bold ml-1 hover:underline" href="#">Start Free Trial</a>
      </p>
    </div>

    <!-- Subtle Background Decorations -->
    <div class="fixed top-0 left-0 w-full h-full -z-10 opacity-30 pointer-events-none">
      <div class="absolute -top-[10%] -left-[10%] w-[50%] h-[40%] bg-primary/20 blur-[120px] rounded-full"></div>
      <div class="absolute bottom-[5%] right-[0%] w-[60%] h-[30%] bg-primary/10 blur-[100px] rounded-full"></div>
    </div>
  </div>
</template>
