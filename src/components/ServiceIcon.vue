<script setup lang="ts">
import {
  Clock3,
  Headset,
  MonitorSmartphone,
  SearchCheck,
  Target,
  Share2,
  CarFront,
  ClipboardCheck,
  Workflow,
  Lightbulb,
  type LucideIcon,
} from '@lucide/vue'

export type ServiceIconName =
  | 'dispatch'
  | 'support'
  | 'website'
  | 'seo'
  | 'ppc'
  | 'social'
  | 'fleet'
  | 'admin'
  | 'process'
  | 'consulting'

const props = defineProps<{
  name: ServiceIconName
}>()

const icons: Record<ServiceIconName, LucideIcon> = {
  dispatch: Clock3,
  support: Headset,
  website: MonitorSmartphone,
  seo: SearchCheck,
  ppc: Target,
  social: Share2,
  fleet: CarFront,
  admin: ClipboardCheck,
  process: Workflow,
  consulting: Lightbulb,
}
</script>

<template>
  <component
    :is="icons[props.name]"
    class="icon"
    :stroke-width="1.75"
    aria-hidden="true"
  />
</template>

<style scoped>
.icon {
  width: 100%;
  height: 100%;
  display: block;
}
</style>
