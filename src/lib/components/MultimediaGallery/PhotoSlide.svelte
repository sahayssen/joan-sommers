<!--
@component
PhotoSlide.svelte — A full-bleed photo slide with a gradient caption overlay.

Renders an image that fills the viewport with object-fit: cover. A gradient
overlay at the bottom displays the title, caption, and photo credit.

USAGE EXAMPLE:
<PhotoSlide photo={{
  filename: 'subway-platform.jpg',
  title: 'Waiting for the L',
  caption: 'Commuters line the platform at Bedford Avenue during morning rush.',
  credit: 'Photo by Jane Doe'
}} />
-->
<script>
  import { base } from '$app/paths';

  let {
    photo, // Object with filename, title, caption, and credit
  } = $props();
</script>

<div class="slide" data-slide data-photo>
  <img src="{base}/photos/{photo.filename}" alt={photo.title} />
  <div class="caption">
    <div class="caption-inner">
      <h2>{photo.title}</h2>
      <p>{photo.caption}</p>
      <span class="credit">{photo.credit}</span>
    </div>
  </div>
</div>

<style lang="scss">
  .slide {
    height: 100%;
    flex: 0 0 100%;
    position: relative;
    background: #f5ead7;

    @container (min-width: 768px) {
      display: flex;
    }
  }

  .slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;

    @container (min-width: 768px) {
      width: 60%;
      flex-shrink: 0;
    }
  }

  .caption {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 2rem 1.5rem 3.5rem;
    background: linear-gradient(
      to top,
      rgba(245, 234, 215, 0.98) 0%,
      rgba(245, 234, 215, 0.92) 70%,
      rgba(245, 234, 215, 0) 100%
    );
    color: #000;

    @container (min-width: 768px) {
      position: static;
      width: 40%;
      background: #f5ead7;
      display: flex;
      align-items: center;
      padding: 3rem;
    }
  }

  .caption-inner {
    max-width: 600px;
  }

  .caption h2 {
    margin: 0 0 0.5rem;
    font-size: 1.25rem;
    line-height: 1.3;
    color: #000;

    @container (min-width: 768px) {
      font-size: 1.75rem;
      margin-bottom: 1rem;
    }
  }

  .caption p {
    margin: 0 0 0.5rem;
    font-size: 0.9375rem;
    line-height: 1.5;
    opacity: 0.85;

    @container (min-width: 768px) {
      font-size: 1.0625rem;
      line-height: 1.7;
      margin-bottom: 1.5rem;
    }
  }

  .caption .credit {
    font-size: 0.75rem;
    opacity: 0.75;

    @container (min-width: 768px) {
      font-size: 0.8125rem;
    }
  }
</style>
