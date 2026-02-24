<script setup lang="ts">
const emit = defineEmits(['back', 'save']);
</script>

<template>
  <div class="relative flex h-screen w-full flex-col overflow-x-hidden bg-deep-dark">
    <div class="flex items-center px-4 py-6 justify-between">
      <button @click="emit('back')" class="text-white flex size-10 shrink-0 items-center justify-center rounded-full hover:bg-white/10">
        <span class="material-symbols-outlined">arrow_back_ios_new</span>
      </button>
      <h2 class="text-lg font-bold leading-tight tracking-tight flex-1 text-center pr-10">Add New Client</h2>
    </div>

    <div class="flex-1 overflow-y-auto px-6 pb-32 scroll-hide">
      <div class="mb-8">
        <h3 class="text-2xl font-bold tracking-tight mb-2">Client Details</h3>
        <p class="text-slate-400 text-sm">Fill in the information below to register a new member to your training roster.</p>
      </div>

      <div class="space-y-6">
        <div class="flex flex-col gap-2">
          <label class="text-sm font-semibold text-white ml-1">Full Name</label>
          <div class="relative">
            <span class="material-symbols-outlined absolute left-4 top-1/2 -translate-y-1/2 text-slate-500">person</span>
            <input class="w-full h-14 pl-12 pr-4 bg-input-dark border border-border-dark rounded-xl focus:ring-2 focus:ring-primary focus:border-primary text-base text-white placeholder-slate-500 transition-all outline-none" placeholder="John Doe" type="text"/>
          </div>
        </div>

        <div class="flex flex-col gap-2">
          <label class="text-sm font-semibold text-white ml-1">Email Address</label>
          <div class="relative">
            <span class="material-symbols-outlined absolute left-4 top-1/2 -translate-y-1/2 text-slate-500">mail</span>
            <input class="w-full h-14 pl-12 pr-4 bg-input-dark border border-border-dark rounded-xl focus:ring-2 focus:ring-primary focus:border-primary text-base text-white placeholder-slate-500 transition-all outline-none" placeholder="john@example.com" type="email"/>
          </div>
        </div>

        <div class="flex flex-col gap-2">
          <label class="text-sm font-semibold text-white ml-1">Phone Number</label>
          <div class="relative">
            <span class="material-symbols-outlined absolute left-4 top-1/2 -translate-y-1/2 text-slate-500">call</span>
            <input class="w-full h-14 pl-12 pr-4 bg-input-dark border border-border-dark rounded-xl focus:ring-2 focus:ring-primary focus:border-primary text-base text-white placeholder-slate-500 transition-all outline-none" placeholder="+1 (555) 000-0000" type="tel"/>
          </div>
        </div>

        <div class="flex flex-col gap-3">
          <label class="text-sm font-semibold text-white ml-1">Training Type</label>
          <div class="flex p-1 bg-input-dark border border-border-dark rounded-xl">
            <button class="flex-1 py-3 px-4 rounded-lg bg-primary shadow-lg text-sm font-bold text-white transition-all">
              Individual
            </button>
            <button class="flex-1 py-3 px-4 rounded-lg text-sm font-medium text-slate-400 hover:text-white transition-all">
              Group
            </button>
          </div>
        </div>

        <div class="flex flex-col gap-3">
          <label class="text-sm font-semibold text-white ml-1">Session Format</label>
          <div class="flex p-1 bg-input-dark border border-border-dark rounded-xl">
            <button class="flex-1 py-3 px-4 rounded-lg text-sm font-medium text-slate-400 hover:text-white transition-all">
              Online
            </button>
            <button class="flex-1 py-3 px-4 rounded-lg bg-primary shadow-lg text-sm font-bold text-white transition-all">
              In-person
            </button>
          </div>
        </div>
      </div>
    </div>

    <div class="absolute bottom-0 left-0 right-0 p-6 bg-gradient-to-t from-deep-dark via-deep-dark/95 to-transparent">
      <button @click="emit('save')" class="w-full h-16 bg-primary text-white rounded-2xl font-bold text-lg shadow-lg shadow-primary/30 flex items-center justify-center gap-2 active:scale-[0.98] transition-transform">
        <span class="material-symbols-outlined">person_add</span>
        Save Client
      </button>
      <div class="mt-6 mx-auto w-32 h-1.5 bg-border-dark rounded-full"></div>
    </div>
  </div>
</template>

<style scoped>
.bg-deep-dark { background-color: #0a0c10; }
.bg-input-dark { background-color: #1a1f26; }
.border-border-dark { border-color: #2d343d; }
</style>
