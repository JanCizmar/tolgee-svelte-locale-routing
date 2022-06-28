<script lang="ts">
  import {getLanguageStore} from "@tolgee/svelte";
  import {goto} from '$app/navigation';
  import {page} from '$app/stores'

  const languageStore = getLanguageStore();

  let currentLang: string

  page.subscribe((page) => {
    if (currentLang !== page.params.lang) {
      currentLang = page.params.lang
      languageStore.set(page.params.lang)
    }
  })

  languageStore.subscribe((lang) => {
    if (currentLang !== lang) {
      currentLang = lang
      goto(`/${lang}`)
    }
  })
</script>

<select bind:value={$languageStore} class="lang-selector">
  <option value="en">🇬🇧 English</option>
  <option value="cs">🇨🇿 česky</option>
</select>
