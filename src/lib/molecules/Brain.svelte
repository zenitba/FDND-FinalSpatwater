<script>
  export let data;
</script>

<!--==================== BRAIN ====================-->
{#each data.brains as item}
  <section class="climate-container">
    <div class="inner-section">
      <div class="horizontal-flex-row">
        <div class="text-container arrow-list">
          <h2 id="brain">{item.title}</h2>
          <p>{@html item.content.html}</p>
          <a class="green-link" href="/projecten">Bekijk onze projecten</a>
        </div>
        <div class="image-container">
          <img class="border-radius-img" src={item.image.url} alt="" loading="lazy"/>
        </div>
      </div>
    </div>
  </section>
{/each}