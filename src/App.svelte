<script>
  import { onMount} from 'svelte';
let title = 'New Note';
let note = 'Add a new Note';
let pages =[];
let CurrentPageIndex = 0;
onMount(() =>{
  title = localStorage.getItem('title');
  note = localStorage.getItem('note');
});
function saveNote() {
  console.log(title, note);
  localStorage.setItem('title', title);
  localStorage.setItem('note', note);
}
function addPage(){
  pages.push("New Page");
}

</script>

<aside class="fixed top-0 left-0 z-40 w-60 h-screen">
  <div class="bg-light-gray overflow-y-auto px-3 py-5 h-full border-r border-gray-200">
    <ul class="space-y-2">
      <li>
        <button class="bg-dark-gray py-2 px-3 text-gray-900 rounded-lg">{title || "New Page"}</button>
      </li>
      <li class="text-center"><button on:click={addPage} class="font-medium">+Add Page</button></li>
    </ul>
  </div>
</aside>

<main class="p-4 ml-60 h-auto">
  <div class ="grid grid-cols-2 item-center">
    <h1 class="text-3xl font-bold" contenteditable bind:textContent={title}></h1>
    <button class="bg-gray-800 ml-auto text-white mb-5 px-5 py-2.5 rounded-lg font-medium hover:bg-gray-200 hover:text-black" on:click={saveNote}>Save</button>
  </div>
  <hr/>
<textarea class="mt-3 block w-full bg-gray-50 border border-gray-300 rounded-lg p-2.5" bind:value={note}></textarea>
</main>

<style>
.bg-light-gray {
  background: #fbfbfb;
}

.bg-dark-gray {
  background: #efefef;
}
</style>