<template>
    <select class="form-select" v-model="clocale">
        <option
            v-for="(lang, i) in availableLocales"
            :key="`Lang${i}`"
            :value="lang"
        >
            {{ t("language.name", {}, { locale: lang }) }}
        </option>
    </select>
</template>

<script setup lang="ts">
import { setLocale } from "@/i18n";
import { computed } from "vue";
import { useI18n } from "vue-i18n";

const { t, locale, availableLocales } = useI18n();

const clocale = computed({
    get: () => locale.value,
    set: (value) => setLocale(value),
});
</script>
