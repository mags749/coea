<script>
  export let images;
  let count = 0;

  import { ChevronLeft, ChevronRight } from "@bobthered/svelte-heroicons/small";

  function incrementCounter() {
    count++;
    if (count > images.length) {
      count = 0;
    }
  }

  function decrementCounter() {
    count--;
    if (count < 0) {
      count = images.length - 1;
    }
  }
</script>

<div class="carousel relative rounded overflow-hidden shadow-xl">
  <div class="carousel-inner relative overflow-hidden w-full">
    {#each images as { path, id }, i}
      <input
        class="carousel-open hidden"
        type="radio"
        id="carousel-{i + 1}"
        name="carousel"
        aria-hidden="true"
        checked={i === count ? "checked" : ""}
      />
      <div
        class="carousel-item absolute opacity-0 bg-center bg-cover h-auto"
        style="
        height: 600px;
        background-image: url({path});
        "
      />
      <label
        for="carousel-{i === 0 ? images.length : i}"
        class="
        control-{i + 1}
        w-10
        h-10
        ml-2
        md:ml-10
        absolute
        cursor-pointer
        hidden
        font-bold
        text-black
        hover:text-white
        rounded-full
        bg-white
        hover:bg-blue-700
        leading-tight
        text-center
        z-10
        inset-y-0
        left-0
        my-auto
        flex
        justify-center
        content-center
      "
        on:click={decrementCounter}><ChevronLeft /></label
      >
      <label
        for="carousel-{i + 2 > images.length ? 1 : i + 2}"
        class="
        next
        control-{i + 1}
        w-10
        h-10
        mr-2
        md:mr-10
        absolute
        cursor-pointer
        hidden
        font-bold
        text-black
        hover:text-white
        rounded-full
        bg-white
        hover:bg-blue-700
        leading-tight
        text-center
        z-10
        inset-y-0
        right-0
        my-auto
      "
        on:click={incrementCounter}><ChevronRight /></label
      >
    {/each}

    <!-- Add additional indicators for each slide-->
    <ol class="carousel-indicators">
      {#each images as { id }, i}
        <li class="inline-block mr-3">
          <label
            for="carousel-{i + 1}"
            class="
            carousel-bullet
            cursor-pointer
            block
            text-4xl text-white
            hover:text-blue-700
          ">•</label
          >
        </li>
      {/each}
    </ol>
  </div>
</div>

<style>
  .carousel-open:checked + .carousel-item {
    position: static;
    opacity: 100;
  }

  .carousel-item {
    -webkit-transition: opacity 0.6s ease-out;
    transition: opacity 0.6s ease-out;
  }

  #carousel-1:checked ~ .control-1,
  #carousel-2:checked ~ .control-2,
  #carousel-3:checked ~ .control-3,
  #carousel-4:checked ~ .control-4 {
    display: block;
  }

  .carousel-indicators {
    list-style: none;
    margin: 0;
    padding: 0;
    position: absolute;
    bottom: 2%;
    left: 0;
    right: 0;
    text-align: center;
    z-index: 10;
  }

  #carousel-1:checked
    ~ .control-1
    ~ .carousel-indicators
    li:nth-child(1)
    .carousel-bullet,
  #carousel-2:checked
    ~ .control-2
    ~ .carousel-indicators
    li:nth-child(2)
    .carousel-bullet,
  #carousel-3:checked
    ~ .control-3
    ~ .carousel-indicators
    li:nth-child(3)
    .carousel-bullet,
  #carousel-4:checked
    ~ .control-4
    ~ .carousel-indicators
    li:nth-child(4)
    .carousel-bullet {
    color: #2b6cb0;
    /*Set to match the Tailwind colour you want the active one to be */
  }
</style>
