<script lang="ts">
  import comp from "../compliments.json";
  import { scale } from "svelte/transition";

  let lang: string = $state("en");
  const compliments: { [key: string]: string[] } = comp;

  let compliment = $state(
    () =>
      compliments[lang][Math.floor(Math.random() * compliments[lang].length)],
  );

  const getCompliment = () => {
    return (compliment = () =>
      compliments[lang][Math.floor(Math.random() * compliments[lang].length)]);
  };
</script>

<div class="h-full flex flex-col justify-center items-center">
  <div class="p-4">
    <div class="m-auto max-w-[600px]">
      {#key compliment}
        <div
          class="text-4xl pb-20 font-quote font-[500] italic leading-[2.35ch] text-center [text-shadow:_2px_4px_6px_#8090a0] text-cyan-300"
          in:scale
        >
          {compliment()}
        </div>
      {/key}
    </div>

    <div class="flex gap-4 justify-center">
      <select
        name="lang"
        class="select py-4 max-w-min text-center"
        id="lang"
        bind:value={lang}
      >
        <option value="en">🇺🇸 English</option>
        <option value="cs">🇨🇿 Czech</option>
        <option value="ro">🇷🇴 Romanian</option>
        <option value="es">🇪🇸 Spanish</option>
      </select>
      <button
        class="btn-md bg-tertiary-400 rounded-lg"
        onclick={() => getCompliment()}>Get compliment</button
      >
    </div>
  </div>
  <div class="max-w-sm text-center mt-4">
    created with 💙 by <a
      href="https://github.com/turtureanu"
      target="_blank"
      class="text-blue-300 hover:underline">@turtureanu</a
    >
    as a friendly alternative to
    <a
      href="https://f-droid.org/packages/com.evilinsult/"
      target="_blank"
      class="text-red-300 hover:underline">Evil Insult Generator</a
    >
  </div>
</div>
