<script>
  import Carousel from "../common/Carousel.svelte";
  const images = [
    { path: "images/slide1.jpg", id: "slide1" },
    { path: "images/slide2.jpg", id: "slide2" },
    { path: "images/slide3.jpg", id: "slide3" },
    { path: "images/slide4.jpg", id: "slide4" },
  ];
</script>

<main>
  <Carousel {images} />
</main>
