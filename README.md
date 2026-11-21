# Radar – QN · dataviz

## La stagione delle stragi (`stragi-mappa/`)

Mappa Leaflet su base OpenStreetMap che segue, passo per passo, le sette autobombe di Cosa nostra tra il 23 maggio 1992 e il 28 luglio 1993.

- Pagina: `https://lorenzobuonarosa.github.io/mafia_stragi/stragi-mappa/`
- Dati: `data/stragi.csv` (separatore `;`, lat/lon con il punto decimale). Per aggiornare la mappa basta cambiare il CSV: totali, frasi del bilancio e striscia temporale sono calcolati da lì.
- Tile: `TILE_URL` e `TILE_ATTRIBUTION` in cima allo script della pagina (tile pubblici di openstreetmap.org, adatti a un traffico moderato; per grandi picchi di lettori valutare un provider di tile).
- Controlli: Avanti / Indietro, pallini, frecce da tastiera, swipe sulla scheda (mai sulla mappa), clic su un marker o su una tacca della striscia.

### Snippet per il CMS

```html
<iframe src="https://lorenzobuonarosa.github.io/mafia_stragi/stragi-mappa/" width="100%" height="1100" frameborder="0" scrolling="no" style="transition:height .3s ease" title="La stagione delle stragi: mappa passo per passo"></iframe>
<script>
(function(){if(window.__radarQNv2)return;window.__radarQNv2=1;var O="https://lorenzobuonarosa.github.io";var MQ=window.matchMedia("(prefers-color-scheme:dark)");function frames(){return Array.prototype.filter.call(document.getElementsByTagName("iframe"),function(f){return(f.getAttribute("src")||"").indexOf(O+"/")===0;});}function theme(){var t=document.documentElement.getAttribute("data-theme");return t==="dark"||t==="light"?t:(MQ.matches?"dark":"light");}function bgOf(el){for(;el&&el.nodeType===1;el=el.parentElement){var c=getComputedStyle(el).backgroundColor;if(c&&c !=="transparent"&&!/rgba\([^)]*,\s*0\)$/.test(c))return c;}return null;}function send(f){try{f.contentWindow.postMessage({sentinel:"radar-qn",type:"theme",theme:theme(),bg:bgOf(f.parentElement)},O);}catch(e){}}function sendAll(){frames().forEach(send);}window.addEventListener("message",function(e){if(e.origin !==O)return;var d=e.data;if(!d||d.sentinel !=="radar-qn"||d.type !=="height")return;frames().forEach(function(f){if(f.contentWindow !==e.source)return;var h=Math.ceil(+d.height);if(h > 0&&20000 > h)f.style.height=h+"px";send(f);});});new MutationObserver(function(){sendAll();setTimeout(sendAll,400);}).observe(document.documentElement,{attributes:true,attributeFilter:["data-theme"]});if(MQ.addEventListener)MQ.addEventListener("change",sendAll);})();
</script>
```

Se in un articolo ci sono più dataviz, lo script può restare in ognuna (il controllo `__radarQNv2` evita il doppio caricamento) oppure si tiene una volta sola.

### Pubblicazione

Su GitHub: *Settings → Pages → Deploy from a branch →* branch e cartella radice. L'indirizzo dello snippet presuppone l'account `lorenzobuonarosa` e la repository `mafia_stragi`: se cambiano, sostituire l'origine nello script (`O="https://…github.io"`) e l'`src` dell'iframe.
