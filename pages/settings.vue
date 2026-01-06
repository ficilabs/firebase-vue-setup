<script setup>
const settings = {
  systemName: 'Energy Monitoring System',
  timezone: 'Asia/Jakarta',
  currency: 'IDR',
  tariffPerKwh: 1500,

  notification: {
    email: true,
    whatsapp: false,
    thresholdAlert: true,
  },

  appearance: {
    darkMode: false,
    compactLayout: false,
  },
}
</script>

<template>
  <VRow>
    <!-- PAGE HEADER -->
    <VCol cols="12">
      <div class="d-flex align-center justify-space-between">
        <div>
          <h2 class="text-h5 font-weight-bold">Settings</h2>
          <p class="text-body-2 text-medium-emphasis">
            System configuration
          </p>
        </div>

        <VButton color="primary">
          Save Changes
        </VButton>
      </div>
    </VCol>

    <!-- GENERAL SETTINGS -->
    <VCol cols="12" md="6">
      <VCard>
        <VCardItem>
          <VCardTitle>General</VCardTitle>
          <VCardSubtitle>Basic system preferences</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VTextField
            v-model="settings.systemName"
            label="System Name"
            density="comfortable"
          />

          <VSelect
            v-model="settings.timezone"
            label="Timezone"
            :items="['Asia/Jakarta', 'Asia/Makassar', 'Asia/Jayapura']"
            class="mt-4"
          />

          <VSelect
            v-model="settings.currency"
            label="Currency"
            :items="['IDR', 'USD']"
            class="mt-4"
          />
        </VCardText>
      </VCard>
    </VCol>

    <!-- ENERGY SETTINGS -->
    <VCol cols="12" md="6">
      <VCard>
        <VCardItem>
          <VCardTitle>Energy & Tariff</VCardTitle>
          <VCardSubtitle>Electricity cost settings</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VTextField
            v-model="settings.tariffPerKwh"
            label="Tariff per kWh"
            type="number"
            prefix="Rp"
          />

          <VAlert
            type="info"
            variant="tonal"
            class="mt-4"
          >
            Tariff is used to calculate estimated cost.
          </VAlert>
        </VCardText>
      </VCard>
    </VCol>

    <!-- NOTIFICATION SETTINGS -->
    <VCol cols="12" md="6">
      <VCard>
        <VCardItem>
          <VCardTitle>Notifications</VCardTitle>
          <VCardSubtitle>Alert preferences</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VSwitch
            v-model="settings.notification.email"
            label="Email Notification"
          />

          <VSwitch
            v-model="settings.notification.whatsapp"
            label="WhatsApp Notification"
          />

          <VSwitch
            v-model="settings.notification.thresholdAlert"
            label="Threshold Alert"
          />
        </VCardText>
      </VCard>
    </VCol>

    <!-- APPEARANCE -->
    <VCol cols="12" md="6">
      <VCard>
        <VCardItem>
          <VCardTitle>Appearance</VCardTitle>
          <VCardSubtitle>UI preferences</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VSwitch
            v-model="settings.appearance.darkMode"
            label="Dark Mode"
          />

          <VSwitch
            v-model="settings.appearance.compactLayout"
            label="Compact Layout"
          />
        </VCardText>
      </VCard>
    </VCol>

    <!-- FOOTER NOTE -->
    <VCol cols="12">
      <VAlert
        type="warning"
        variant="tonal"
        border="start"
      >
        Changes will take effect after saving.
      </VAlert>
    </VCol>
  </VRow>
</template>
