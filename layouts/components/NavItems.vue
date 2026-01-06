<script setup>
import VerticalNavLink from "@layouts/components/VerticalNavLink.vue"
</script>

<template>
  <VerticalNavLink
    :item="{
      title: 'Dashboard',
      icon: 'bx-home',
      to: '/dashboard',
    }"
  />

  <VerticalNavLink
    :item="{
      title: 'Realtime',
      icon: 'bx-pulse',
      to: '/realtime',
    }"
  />

  <VerticalNavLink
    :item="{
      title: 'History',
      icon: 'bx-bar-chart-alt-2',
      to: '/history',
    }"
  />

  <VerticalNavLink
    :item="{
      title: 'Prediction',
      icon: 'bx-line-chart',
      to: '/prediction',
    }"
  />

  <VerticalNavLink
    :item="{
      title: 'Devices',
      icon: 'bx-bulb',
      to: '/devices',
    }"
  />

  <VerticalNavLink
    :item="{
      title: 'Settings',
      icon: 'bx-cog',
      to: '/settings',
    }"
  />
</template>
