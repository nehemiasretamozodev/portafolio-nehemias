<script lang="ts">
  import { onMount } from 'svelte';
  import Icon from '$lib/Icon.svelte';
  const perfil = {
    nombre: 'Josue Nehemias Retamozo Ataucusi',
    titular: 'Desarrollador Web & Software · Diseño y creación de soluciones digitales',
    ubicacion: 'Junín, Perú',
    correo: 'nehemiasretamozo@icloud.com',
    telefono: '+51910064458',
    linkedin: 'https://www.linkedin.com/in/josue-nehemias-retamozo-ataucusi-48a23b277/',
    github: 'https://github.com/nehemiasretamozodev',
    acerca: 'Me dedico a crear páginas web, aplicaciones y sistemas que ayudan a organizar procesos y convertir ideas en soluciones digitales. Me interesa el desarrollo de software, el diseño de interfaces claras y la experiencia de las personas que usan cada producto.'
  };
  // Experiencias organizadas por áreas de proyecto. Confirma las fechas reales antes de publicar.
  const experiencia = [
    {
      lugar: 'Desarrollo de sistemas empresariales',
      cargo: 'Desarrollador de aplicaciones web · Proyectos de software',
      periodo: '2022 – Actualidad',
      detalle: 'Desarrollo de sistemas web para organizar información y facilitar procesos administrativos. Implementación de módulos, formularios, reportes e interfaces para una gestión más sencilla.'
    },
    {
      lugar: 'Diseño y desarrollo de páginas web',
      cargo: 'Desarrollo frontend · Proyectos web',
      periodo: '2022 – Actualidad',
      detalle: 'Creación de páginas web y portafolios adaptables a celulares y computadoras. Diseño de interfaces claras, navegación intuitiva y mejoras en la presentación de contenidos.'
    },
    {
      lugar: 'Herramientas y plataformas digitales',
      cargo: 'Desarrollo de funcionalidades y paneles de gestión',
      periodo: '2022 – Actualidad',
      detalle: 'Construcción de herramientas para publicar contenido, administrar datos y simplificar tareas mediante tecnologías web. Trabajo enfocado en funcionalidad, organización y facilidad de uso.'
    }
  ];
  const proyectos = [
    { nombre: 'OML Europe', detalle: 'Sistema de gestión empresarial con módulos administrativos y procesos operativos.', tags: ['Laravel', 'PHP', 'MySQL'], href: '' },
    { nombre: 'Portafolio creativo', detalle: 'Experiencia personal interactiva, adaptable a distintas pantallas.', tags: ['SvelteKit', 'Responsive'], href: '' },
    { nombre: 'Generador de publicaciones', detalle: 'Herramienta para organizar y publicar contenidos digitales.', tags: ['Laravel', 'Web'], href: '' },
    { nombre: 'Diseño de interfaces', detalle: 'Propuestas visuales para páginas web y paneles administrativos.', tags: ['UI', 'Frontend'], href: '' },
    { nombre: 'GitHub', detalle: 'Consulta mi perfil de GitHub y mis repositorios públicos.', tags: ['Código', 'Repositorios'], href: perfil.github },
    { nombre: 'Contacto profesional', detalle: '¿Tienes una idea o proyecto? Puedes escribirme directamente.', tags: ['Correo', 'Colaboración'], href: `mailto:${perfil.correo}` }
  ];
  const habilidades = [{nombre:'HTML',icono:'html'},{nombre:'CSS',icono:'css'},{nombre:'JavaScript',icono:'javascript'},{nombre:'TypeScript',icono:'typescript'},{nombre:'SvelteKit',icono:'code'},{nombre:'Laravel',icono:'code'},{nombre:'PHP',icono:'code'},{nombre:'MySQL',icono:'database'},{nombre:'Git',icono:'git'},{nombre:'GitHub',icono:'github'},{nombre:'Responsive Design',icono:'monitor'}];
  type Accion = { nombre: string; grupo: string; tecla: string; simbolo: string; accion: () => void };
  let abierto = false;
  let busqueda = '';
  let seleccionado = 0;
  const abrirUrl = (url: string) => { if (typeof window !== 'undefined') window.open(url, '_blank', 'noopener,noreferrer'); };
  const acciones: Accion[] = [
    { nombre: 'Imprimir', grupo: 'Acciones', tecla: 'Ctrl P', simbolo: 'printer', accion: () => window.print() },
    { nombre: 'Enviar correo', grupo: 'Contacto', tecla: 'Ctrl E', simbolo: 'mail', accion: () => { window.location.href = `mailto:${perfil.correo}`; } },
    { nombre: 'Llamar por teléfono', grupo: 'Contacto', tecla: 'Ctrl T', simbolo: 'phone', accion: () => { window.location.href = `tel:${perfil.telefono}`; } },
    { nombre: 'Visitar LinkedIn', grupo: 'Social', tecla: 'Ctrl L', simbolo: 'linkedin', accion: () => abrirUrl(perfil.linkedin) },
    { nombre: 'Visitar GitHub', grupo: 'Social', tecla: 'Ctrl G', simbolo: 'github', accion: () => abrirUrl(perfil.github) },
    { nombre: 'Ir a proyectos', grupo: 'Navegación', tecla: '', simbolo: 'briefcase', accion: () => { document.getElementById('proyectos')?.scrollIntoView({behavior:'smooth'}); } }
  ];
  $: filtradas = acciones.filter(a => a.nombre.toLowerCase().includes(busqueda.toLowerCase()));
  function ejecutar(a: Accion) { abierto = false; busqueda = ''; a.accion(); }
  function teclas(event: KeyboardEvent) {
    const mod = event.ctrlKey || event.metaKey;
    if (mod && event.key.toLowerCase() === 'k') { event.preventDefault(); abierto = !abierto; seleccionado = 0; }
    if (mod && abierto && ['l','g','e','t'].includes(event.key.toLowerCase())) { event.preventDefault(); const a = acciones.find(x => x.tecla.toLowerCase().endsWith(event.key.toLowerCase())); if(a) ejecutar(a); }
    if (abierto && event.key === 'Escape') abierto = false;
    if (abierto && event.key === 'ArrowDown') { event.preventDefault(); seleccionado = Math.min(seleccionado+1, filtradas.length-1); }
    if (abierto && event.key === 'ArrowUp') { event.preventDefault(); seleccionado = Math.max(seleccionado-1, 0); }
    if (abierto && event.key === 'Enter' && filtradas[seleccionado]) { event.preventDefault(); ejecutar(filtradas[seleccionado]); }
  }
  onMount(() => { const f = (e: KeyboardEvent) => teclas(e); window.addEventListener('keydown', f); return () => window.removeEventListener('keydown', f); });
</script>

<svelte:head>
  <title>{perfil.nombre} | Desarrollador Web y Software</title>
  <meta name="description" content="Portafolio de Josue Nehemias Retamozo Ataucusi. Desarrollo web, software, Laravel, SvelteKit y proyectos digitales en Perú." />
  <meta name="robots" content="index, follow" />
  <meta name="theme-color" content="#ffffff" />
  <meta property="og:title" content={`${perfil.nombre} | Desarrollador Web y Software`} />
  <meta property="og:description" content="Proyectos, experiencia, habilidades y contacto de Nehemias Retamozo." />
  <meta property="og:type" content="profile" />
  {@html `<script type="application/ld+json">${JSON.stringify({'@context':'https://schema.org','@type':'Person', name:perfil.nombre, jobTitle:'Desarrollador web', email:perfil.correo, sameAs:[perfil.linkedin, perfil.github]})}</script>`}
</svelte:head>

<div class="page">
  <main>
    <header class="hero">
      <div class="hero-copy">
        <h1>{perfil.nombre}</h1>
        <p class="position">{perfil.titular}</p>
        <p class="location"><Icon name="globe" size={13} /> {perfil.ubicacion}</p>
        <nav class="social" aria-label="Contacto y redes sociales">
          <a href={`mailto:${perfil.correo}`} title="Correo" aria-label="Enviar correo"><Icon name="mail" size={16} /></a>
          <a href={`tel:${perfil.telefono}`} title="Teléfono" aria-label="Llamar"><Icon name="phone" size={16} /></a>
          <a href={perfil.linkedin} target="_blank" rel="noopener noreferrer" title="LinkedIn" aria-label="LinkedIn"><Icon name="linkedin" size={16} /></a>
          <a href={perfil.github} target="_blank" rel="noopener noreferrer" title="GitHub" aria-label="GitHub"><Icon name="github" size={16} /></a>
        </nav>
      </div>
      <div class="portrait" aria-label="Monograma NR de Nehemias Retamozo">NR</div>
    </header>

    <section id="sobre-mi" class="section about"><h2>Sobre mí</h2><p class="body-copy">{perfil.acerca}</p></section>

    <section id="experiencia" class="section"><h2>Experiencia laboral</h2>
      {#each experiencia as item}
        <article class="job"><div class="job-line"><h3>{item.lugar}</h3><span class="date">{item.periodo}</span></div><p class="role">{item.cargo}</p><p class="body-copy">{item.detalle}</p></article>
      {/each}
    </section>

    <section id="educacion" class="section"><h2>Educación</h2>
      <article class="job education"><div class="job-line"><h3>Universidad Peruana Los Andes (UPLA)</h3><span class="date">2022 – 2026</span></div><p class="role">Estudios universitarios</p></article>
    </section>

    <section id="proyectos" class="section projects-section"><h2>Proyectos</h2>
      <div class="projects">
        {#each proyectos as p}
          <article class="project"><div><h3>{#if p.href}<a href={p.href} target={p.href.startsWith('mailto:') ? undefined : '_blank'} rel="noopener noreferrer">{p.nombre} <span class="dot">●</span></a>{:else}{p.nombre} <span class="dot">●</span>{/if}</h3><p class="body-copy">{p.detalle}</p></div><div class="tags">{#each p.tags as tag}<span>{tag}</span>{/each}</div></article>
        {/each}
      </div>
    </section>

    <section id="habilidades" class="section skills-section"><h2>Habilidades</h2><div class="skills">{#each habilidades as skill}<span><Icon name={skill.icono} size={14}/>{skill.nombre}</span>{/each}</div></section>
    <footer><a href={`mailto:${perfil.correo}`}>{perfil.correo}</a><span>© {new Date().getFullYear()} {perfil.nombre}</span></footer>
  </main>
  <button class="command-hint" onclick={() => { abierto = true; busqueda=''; seleccionado=0; }} aria-label="Abrir paleta de comandos">Pulsa <kbd>Ctrl</kbd> + <kbd>K</kbd> para abrir la paleta de comandos.</button>
</div>
{#if abierto}
  <div class="overlay" role="presentation" onclick={() => abierto = false}></div>
  <div class="palette" role="dialog" aria-modal="true" aria-label="Paleta de comandos">
    <input aria-label="Buscar comando" autofocus placeholder="Buscar comando" bind:value={busqueda} oninput={() => seleccionado = 0} />
    <div class="palette-scroll">
      {#if filtradas.length===0}<p class="empty">No se encontraron comandos.</p>{/if}
      {#each filtradas as item, index}
        {#if index===0 || filtradas[index-1].grupo !== item.grupo}<p class="group">{item.grupo}</p>{/if}
        <button class:active={seleccionado===index} onclick={() => ejecutar(item)} onmouseenter={() => seleccionado = index}><span class="cmdicon"><Icon name={item.simbolo} size={17}/></span><span>{item.nombre}</span>{#if item.tecla}<span class="shortcut">{#each item.tecla.split(' ') as part}<kbd>{part}</kbd>{/each}</span>{/if}</button>
      {/each}
    </div><div class="palette-footer"><span><kbd>↵</kbd> seleccionar</span><span><kbd>↑</kbd><kbd>↓</kbd> navegar</span><span><kbd>Esc</kbd> cerrar</span></div>
  </div>
{/if}

<style>
  :global(*){box-sizing:border-box}
  :global(body){margin:0;background:#fff;color:#080808;font-family:Arial,Helvetica,sans-serif;-webkit-font-smoothing:antialiased}
  :global(html){scroll-behavior:smooth}
  :global(a){color:inherit;text-decoration:none}
  .page{min-height:100vh}.page main{width:min(700px,calc(100% - 40px));margin:auto;padding:63px 0 110px}
  .hero{display:flex;justify-content:space-between;gap:24px;align-items:center;margin-bottom:46px}.hero-copy{max-width:480px}
  h1{font-size:28px;font-weight:400;letter-spacing:-.85px;line-height:1.15;margin:0 0 10px}.position{font-size:15px;line-height:1.4;font-weight:500;margin:0 0 4px}.location{display:flex;align-items:center;gap:4px;font:12px/1.4 ui-monospace,SFMono-Regular,Consolas,monospace;color:#575757;margin:0 0 12px}
  .portrait{width:84px;height:84px;flex-shrink:0;background:linear-gradient(150deg,#0776ce,#003d8c);color:#fff;border-radius:13px;display:grid;place-items:center;font-weight:700;letter-spacing:-2px;font-size:29px}
  .social{display:flex;gap:5px}.social a{height:26px;min-width:26px;border:1px solid #e8e8e8;border-radius:5px;color:#656565;display:grid;place-items:center;font-size:17px}.social a strong{font-size:13px}.social a:hover{background:#f2f2f2;color:#111}
  .section{margin:0 0 53px}h2{font-size:20px;font-weight:700;letter-spacing:-.45px;margin:0 0 10px;line-height:1.2}.body-copy{font:13px/1.46 ui-monospace,SFMono-Regular,Consolas,'Liberation Mono',monospace;color:#545454;margin:0}
  .job{margin:0 0 27px}.job-line{display:flex;justify-content:space-between;align-items:baseline;gap:18px}.job h3,.project h3{font-size:14px;font-weight:600;line-height:1.4;margin:0}.date{color:#5b5b5b;font:12px/1.5 ui-monospace,Consolas,monospace;white-space:nowrap}.role{font-size:13px;font-weight:400;margin:1px 0 4px}.hint{font:11px/1.5 ui-monospace,Consolas,monospace;color:#999;margin:12px 0 0}
  .projects-section{margin-bottom:47px}.projects{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:14px;width:100%}.project{border:1px solid #ebebeb;border-radius:8px;padding:14px 14px 13px;min-height:166px;display:flex;flex-direction:column;justify-content:space-between;gap:16px}.project .body-copy{font-size:12.5px;line-height:1.52;margin-top:4px}.project a:hover{text-decoration:underline}.dot{font-size:9px;color:#20ad63;vertical-align:middle}.tags,.skills{display:flex;flex-wrap:wrap;gap:6px}.tags span,.skills span{background:#eee;border-radius:5px;font:10.2px/1.45 ui-monospace,SFMono-Regular,Consolas,monospace;padding:2px 6px}.skills span{display:inline-flex;align-items:center;gap:5px;font-size:11.4px;font-weight:600;padding:3px 7px}.skills-section{margin-bottom:63px}
  footer{border-top:1px solid #eee;padding-top:14px;font-size:11px;color:#747474;display:flex;justify-content:space-between;gap:15px;flex-wrap:wrap}footer a:hover{text-decoration:underline}
  .command-hint{position:fixed;bottom:0;left:0;width:100%;background:#fff;border:0;border-top:1px solid #eee;height:30px;color:#292929;cursor:pointer;font:11px ui-monospace,SFMono-Regular,Consolas,monospace}.command-hint:hover{background:#fafafa}kbd{border:1px solid #d5d8de;background:#f8f9fa;border-radius:4px;padding:2px 5px;font:11px ui-monospace,Consolas,monospace}
  .overlay{position:fixed;inset:0;background:#0003;z-index:20}.palette{position:fixed;z-index:21;left:50%;top:35%;transform:translate(-50%,-20%);width:min(550px,calc(100vw - 30px));border:1px solid #d6dce5;border-radius:8px;background:white;box-shadow:0 20px 45px #0003;overflow:hidden}.palette>input{width:100%;height:53px;border:0;border-bottom:1px solid #e3e5ea;padding:0 17px;font:16px ui-monospace,Consolas,monospace;outline:none}.palette-scroll{max-height:345px;overflow:auto;padding:5px 0}.group{font:11px Arial,sans-serif;color:#7e8592;margin:9px 15px 4px}.palette-scroll button{width:100%;padding:10px 15px;border:0;background:#fff;display:flex;align-items:center;text-align:left;gap:14px;cursor:pointer;font:12px ui-monospace,Consolas,monospace}.palette-scroll button.active,.palette-scroll button:hover{background:#f1f2f5}.cmdicon{width:19px;display:grid;place-items:center;color:#536173}.shortcut{display:flex;gap:4px;margin-left:auto}.palette-footer{border-top:1px solid #e2e3e5;display:flex;justify-content:space-between;gap:7px;padding:11px 15px;color:#66707f;font:11px ui-monospace,Consolas,monospace}.palette-footer span{display:flex;align-items:center;gap:3px}.empty{font-size:12px;padding:20px;color:#888}
  .project h3{font-weight:600}.social a:focus-visible,.project a:focus-visible{outline:2px solid #2563eb;outline-offset:2px}
  @media(min-width:601px) and (max-width:760px){.page main{width:calc(100% - 40px)}}
  @media(max-width:600px){.page main{padding-top:36px;width:calc(100% - 32px)}.hero{align-items:flex-start;gap:15px;margin-bottom:43px}h1{font-size:clamp(24px,5.6vw,28px)}.position{font-size:14px}.body-copy{font-size:13px}.job-line{flex-wrap:wrap;gap:2px 12px}.portrait{width:64px;height:64px;border-radius:10px;font-size:22px}.projects{grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}.section{margin-bottom:41px}.palette{top:22%;transform:translate(-50%,0)}}
  @media(max-width:420px){.hero-copy{min-width:0}.portrait{width:58px;height:58px;font-size:21px}.projects{grid-template-columns:1fr}.project{min-height:130px}.project .body-copy{font-size:13px}}
  @media(max-width:380px){.projects{grid-template-columns:1fr}.portrait{width:52px;height:52px}.palette-footer{flex-wrap:wrap}}
  /* Responsive refinado: mantiene el diseño de escritorio y mejora la lectura móvil. */
  .hero-copy{min-width:0}
  .hero{display:grid;grid-template-columns:minmax(0,1fr) 84px;column-gap:24px}
  .hero h1{overflow-wrap:break-word}
  .project{min-width:0}
  .project h3,.project .body-copy,.tags span{overflow-wrap:anywhere}
  .social a:focus-visible,.command-hint:focus-visible,.palette button:focus-visible,.palette input:focus-visible{outline:2px solid #086ac1;outline-offset:2px}
  @media(max-width:760px){
    .page main{width:calc(100% - 36px)}
    .projects{grid-template-columns:repeat(2,minmax(0,1fr))}
  }
  @media(max-width:600px){
    .page main{padding-top:32px;padding-bottom:100px}
    .hero{grid-template-columns:minmax(0,1fr) 64px;column-gap:16px;align-items:start}
    .hero-copy{max-width:none}
    .social a{height:36px;min-width:36px;border-radius:7px}
    .social a :global(svg){width:18px;height:18px}
    .position{line-height:1.45}
    .section{margin-bottom:39px}
    .job{margin-bottom:25px}
    .job-line{align-items:flex-start}
    .date{white-space:normal;text-align:right}
    .command-hint{height:39px;font-size:10px;padding:0 10px}
    .palette{top:14vh;transform:translateX(-50%)}
    .palette-scroll{max-height:48vh}
  }
  @media(max-width:520px){
    .projects{grid-template-columns:1fr}
    .project{min-height:122px;padding:13px}
    .project .body-copy{font-size:13px}
    footer{flex-direction:column;gap:7px}
    .palette-footer{flex-wrap:wrap}
  }
  @media(max-width:420px){
    .hero{grid-template-columns:minmax(0,1fr) 55px;column-gap:11px}
    h1{font-size:clamp(21px,5.6vw,24px);letter-spacing:-.5px}
    .portrait{width:55px;height:55px;font-size:20px;border-radius:10px}
  }
  @media(prefers-reduced-motion:reduce){:global(html){scroll-behavior:auto}}
  @media print{.command-hint,.overlay,.palette{display:none}.page main{padding:10px 0}.section{break-inside:avoid}}
</style>
