<script>
  export let data;
</script>

<!--==================== WATERKWALITEIT ====================-->
{#each data.waterkwaliteits as item}
  <section class="climate-container">
    <div class="inner-section">
      <div class="horizontal-flex-row">
        <div class="text-container arrow-list">
          <h2 id="waterkwaliteit">{item.title}</h2>
          <p>{@html item.content.html}</p>
          <a class="green-link" href="/projecten">Bekijk onze projecten</a>
        </div>
        <div class="image-container">
          <img src={item.image.url} alt="" loading="lazy"/>
        </div>
      </div>
    </div>
  </section>
{/each}
