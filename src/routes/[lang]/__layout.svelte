<script lang="ts">
  import {page} from '$app/stores'
  import {TolgeeProvider} from "@tolgee/svelte";
  import {TolgeeConfig} from "@tolgee/core";
  import LangSelector from "../../component/LangSelector.svelte";


  const getTolgeeConfig = (lang?: string) => {
    return ({
      preloadFallback: true,
      apiUrl: import.meta.env.VITE_TOLGEE_API_URL, // or provide your API URL directly
      apiKey: import.meta.env.VITE_TOLGEE_API_KEY, // or provide API_KEY directly
      // here we are setting the lang for the SSR
      defaultLanguage: lang || undefined
    } as TolgeeConfig);
  }
</script>

<TolgeeProvider config={getTolgeeConfig($page.params.lang)}>
  <LangSelector/>
  <slot></slot>
</TolgeeProvider>
