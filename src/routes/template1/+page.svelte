<script context="module" lang="ts">
  export const prerender = true;
</script>

<script lang="ts">
  import { assets, base } from '$app/paths';

  import Card from "$lib/card.svelte";
  import projectsImport from "$lib/../content/projects.json";
  import info from "$lib/../content/general-info.json";
  import experience from "$lib/../content/experience.json";
  import Header from "$lib/header.svelte";

  const projects = projectsImport.slice(0, 3);
</script>

<svelte:head>
  <title>{info.firstName} {info.lastName}</title>
</svelte:head>

<Header entries={{ "Home": "#about", "Projects": "#projects", "Experience": "#awards", "Contact": "#cta" }} />

<section class="w3-container -right"
  id="about"
  style="--imageUrl: url({`${assets}/images/${info.heroImage}`});"
>
  <div class="header-text">
    <h2>{info.firstName} {info.lastName}</h2>
    <h3>{info.tagLine}</h3>
  </div>
</section>

<section id="projects">
  <h2>Projects</h2>

  <div class="flex-row">
    {#each projects as project}
      <Card
        title={project.title}
        description={project.description}
        image_url={project.image_url}
        follow_url={project.follow_url}
      />
    {/each}
  </div>

  <a class="button more-projects-btn" href={`${base}/projects`}> More Projects →</a>
</section>

<section id="work">
  <h2>Current Work</h2>
</section>

<section id="awards">
  <h2>Experience</h2>

  <div class="flex-row">
    {#each experience as experience}
      <Card
        title={experience.title}
        description={experience.description}
        image_url={experience.image_url}
        follow_url={experience.follow_url}
      />
    {/each}
  </div>
</section>

<section id="cta">
  <h1>Contact Me</h1>

  <div class="contacts">
    {#each info.contacts as contact}
      <p>
        {contact.type}: <a href={contact.url}>{contact.displayText}</a>
      </p>
    {/each}
  </div>
</section>
