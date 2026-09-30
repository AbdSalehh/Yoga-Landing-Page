<script setup lang="ts">
import { computed } from "vue";
import { cn } from "../lib/utils";

type ButtonVariant = "dark" | "light" | "outline" | "icon";

const properties = withDefaults(
  defineProps<{
    href?: string;
    variant?: ButtonVariant;
    className?: string;
    ariaLabel?: string;
  }>(),
  {
    href: undefined,
    variant: "dark",
    className: undefined,
    ariaLabel: undefined,
  },
);

const buttonClassName = computed(() =>
  cn(
    "inline-flex items-center justify-center gap-2 rounded-full text-sm font-semibold transition duration-300 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-black/40",
    properties.variant === "dark" &&
      "bg-ink px-5 py-3 text-white hover:-translate-y-0.5 hover:bg-black",
    properties.variant === "light" &&
      "bg-white px-5 py-3 text-ink hover:-translate-y-0.5 hover:bg-white/85",
    properties.variant === "outline" &&
      "border border-ink/20 bg-white/70 px-5 py-3 text-ink backdrop-blur hover:border-ink/50",
    properties.variant === "icon" &&
      "size-11 bg-white text-ink hover:rotate-12 hover:bg-lilac",
    properties.className,
  ),
);
</script>

<template>
  <component
    :is="href ? 'a' : 'button'"
    :href="href"
    :type="href ? undefined : 'button'"
    :class="buttonClassName"
    :aria-label="ariaLabel"
  >
    <slot />
  </component>
</template>
