<script lang="ts">
  import type { BeatmapDto } from "../api/gen";
  function getSource(id: number) {
    return `http://assets.ppy.sh/beatmaps/${id}/covers/cover.jpg`;
  }
  let { beatmap }: { beatmap: BeatmapDto } = $props();
  let source = getSource(beatmap.beatmapsetId);
</script>

<div class="beatmap card-size">
  <img
    src={source}
    loading="lazy"
    alt="Background image of beatmap {beatmap.title}"
  />
  <p>{beatmap.title} - {beatmap.artist}</p>
  <p>[{beatmap.difficulty}]</p>
</div>

<style lang="scss">
  @use "sass:color";
  .beatmap {
    overflow: hidden;
    position: relative;
  }
  .card-size {
    min-height: auto;
    max-height: 250px;
    height: 100%;
  }
  p {
    margin: 20px;
  }
  img {
    pointer-events: none;
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
    filter: brightness(40%);
  }
</style>
