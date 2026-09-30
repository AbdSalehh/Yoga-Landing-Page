<script setup lang="ts">
import { ref } from "vue";
import { AppButtonVue } from "@/shared/ui";
import { cn } from "@/shared/lib";

interface NavigationLink {
  label: string;
  href: string;
}

defineProps<{
  navigationLinks: NavigationLink[];
}>();

const isMenuOpen = ref(false);

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}

function closeMenu() {
  isMenuOpen.value = false;
}
</script>

<template>
  <div class="md:hidden">
    <AppButtonVue
      variant="icon"
      aria-label="Buka menu navigasi"
      class-name="size-10 bg-white/65"
      @click="toggleMenu"
    >
      <svg viewBox="0 0 24 24" class="size-5" fill="none" aria-hidden="true">
        <path
          d="M5 8h14M5 16h14"
          stroke="currentColor"
          stroke-width="1.8"
          stroke-linecap="round"
        />
      </svg>
    </AppButtonVue>

    <nav
      :class="
        cn(
          'absolute inset-x-0 top-18.5 flex origin-top flex-col rounded-3xl border border-white/70 bg-white/60 p-3 shadow-2xl backdrop-blur-[32px] backdrop-saturate-150 transition duration-300',
          isMenuOpen
            ? 'translate-y-0 scale-100 opacity-100'
            : 'pointer-events-none -translate-y-3 scale-95 opacity-0',
        )
      "
      aria-label="Navigasi mobile"
    >
      <a
        v-for="navigationLink in navigationLinks"
        :key="navigationLink.href"
        :href="navigationLink.href"
        class="rounded-2xl px-4 py-3 text-sm font-medium hover:bg-white"
        @click="closeMenu"
      >
        {{ navigationLink.label }}
      </a>
    </nav>
  </div>
</template>
