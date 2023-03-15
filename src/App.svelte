<script>
  // import { chatGPT } from './assets';
  import { Textarea, Toolbar, ToolbarGroup, ToolbarButton, Button, Badge } from 'flowbite-svelte'

  // import { Sidebar, SidebarWrapper, SidebarBrand, SidebarItem, SidebarGroup } from 'flowbite-svelte'
  import { bind } from 'svelte/internal';
  
  import { Drawer, CloseButton, Sidebar, SidebarBrand, SidebarCta, SidebarDropdownItem, SidebarDropdownWrapper, SidebarGroup, SidebarItem, SidebarWrapper } from 'flowbite-svelte';
  import { sineIn } from 'svelte/easing';
  let hidden2 = true;
  // let spanClass = 'flex-1 ml-3 whitespace-nowrap';
  let transitionParams = {
    x: -320,
    duration: 200,
    easing: sineIn
  };

  let newNote = false

  let noteHead = "";
  let text = ``;
  function handleTextChange(e) {
    text = e.target.value;
  }

  function handleSubmit(e) {
    e.preventDefault();
    let newText = text;
    console.log(newText);
    
  }


</script>


<Drawer transitionType="fly" {transitionParams} bind:hidden={hidden2} id='sidebar2'>
<div class='flex items-center'>
  <h5 id="drawer-navigation-label-3" class="text-base font-semibold text-gray-500 uppercase dark:text-gray-400">InkWell Menu</h5>
  <CloseButton on:click={() => (hidden2 = true)} class='mb-4 dark:text-white'/>
</div>
  <Sidebar>
    <SidebarWrapper divClass='overflow-y-auto py-4 px-3 rounded dark:bg-gray-800'>
      <SidebarGroup>
        <SidebarItem label="New Note">
          <svelte:fragment slot="icon">
            <svg width="24px" height="24px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M12.75 11.25V5C12.75 4.80109 12.671 4.61032 12.5303 4.46967C12.3897 4.32902 12.1989 4.25 12 4.25C11.8011 4.25 11.6103 4.32902 11.4697 4.46967C11.329 4.61032 11.25 4.80109 11.25 5V11.25H5C4.80109 11.25 4.61032 11.329 4.46967 11.4697C4.32902 11.6103 4.25 11.8011 4.25 12C4.25 12.1989 4.32902 12.3897 4.46967 12.5303C4.61032 12.671 4.80109 12.75 5 12.75H11.25V19C11.2526 19.1981 11.3324 19.3874 11.4725 19.5275C11.6126 19.6676 11.8019 19.7474 12 19.75C12.1989 19.75 12.3897 19.671 12.5303 19.5303C12.671 19.3897 12.75 19.1989 12.75 19V12.75H19C19.1989 12.75 19.3897 12.671 19.5303 12.5303C19.671 12.3897 19.75 12.1989 19.75 12C19.7474 11.8019 19.6676 11.6126 19.5275 11.4725C19.3874 11.3324 19.1981 11.2526 19 11.25H12.75Z" fill="#000000"/>
              </svg>
          </svelte:fragment>
        </SidebarItem>
      </SidebarGroup>
    </SidebarWrapper>
  </Sidebar>
</Drawer>















{#if !newNote}

<h1 class="mb-5"><span class="underline decoration-sky-500/30">Ink</span>well</h1>

<div class="">
  <label for="" class="">Enter a <span class="underline decoration-pink-500">Heading</span></label>
  <div contenteditable="true" bind:innerHTML={noteHead} class="border-2 rounded mt-2  m-auto"></div>
</div>
<Button gradient color="purpleToPink" on:click={() => newNote = !newNote} class="m-5"><span><svg width="24px" height="24px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M12.75 11.25V5C12.75 4.80109 12.671 4.61032 12.5303 4.46967C12.3897 4.32902 12.1989 4.25 12 4.25C11.8011 4.25 11.6103 4.32902 11.4697 4.46967C11.329 4.61032 11.25 4.80109 11.25 5V11.25H5C4.80109 11.25 4.61032 11.329 4.46967 11.4697C4.32902 11.6103 4.25 11.8011 4.25 12C4.25 12.1989 4.32902 12.3897 4.46967 12.5303C4.61032 12.671 4.80109 12.75 5 12.75H11.25V19C11.2526 19.1981 11.3324 19.3874 11.4725 19.5275C11.6126 19.6676 11.8019 19.7474 12 19.75C12.1989 19.75 12.3897 19.671 12.5303 19.5303C12.671 19.3897 12.75 19.1989 12.75 19V12.75H19C19.1989 12.75 19.3897 12.671 19.5303 12.5303C19.671 12.3897 19.75 12.1989 19.75 12C19.7474 11.8019 19.6676 11.6126 19.5275 11.4725C19.3874 11.3324 19.1981 11.2526 19 11.25H12.75Z" fill="#FFFFFF"/>
  </svg></span> New Note</Button>
{/if}

{#if newNote}
<h1 class="mb-5"><span class="underline decoration-sky-500/30">Ink</span><span class="underline decoration-pink-500">Well</span></h1>

<pre>{noteHead}</pre>
<div class="flex">
  <form class="m-10" >
    <label for="editor" class="sr-only overflow-hidden" >Publish post</label>
    <Textarea id="editor" name="name" rows="14" class="mb-4" placeholder="Write your notes here !! " value={text} on:change={handleTextChange}>
      
      <Toolbar slot="header" embedded>
        <ToolbarGroup>
          <ToolbarButton name="Attach file"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6"><path stroke-linecap="round" stroke-linejoin="round" d="M18.375 12.739l-7.693 7.693a4.5 4.5 0 01-6.364-6.364l10.94-10.94A3 3 0 1119.5 7.372L8.552 18.32m.009-.01l-.01.01m5.699-9.941l-7.81 7.81a1.5 1.5 0 002.112 2.13" /></svg></ToolbarButton>

          <ToolbarButton name="Embed map"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6"><path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" /><path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" /></svg></ToolbarButton>

          <ToolbarButton name="Upload image"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 15.75l5.159-5.159a2.25 2.25 0 013.182 0l5.159 5.159m-1.5-1.5l1.409-1.409a2.25 2.25 0 013.182 0l2.909 2.909m-18 3.75h16.5a1.5 1.5 0 001.5-1.5V6a1.5 1.5 0 00-1.5-1.5H3.75A1.5 1.5 0 002.25 6v12a1.5 1.5 0 001.5 1.5zm10.5-11.25h.008v.008h-.008V8.25zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z" /></svg></ToolbarButton>
        </ToolbarGroup>
        <ToolbarGroup>
          <div>TryGPT
            
          </div>

          <ToolbarButton name="chatGPT"><svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 64 64" width="24px" height="24px" baseProfile="basic"><linearGradient id="9yv_OTO3P9eepfu7Rtqera" x1="32" x2="32" y1="7" y2="58" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#6dc7ff"/><stop offset=".699" stop-color="#e6abff"/></linearGradient><path fill="url(#9yv_OTO3P9eepfu7Rtqera)" d="M53.27,26.96c0.28-1.05,0.42-2.11,0.42-3.17c0-6.86-5.58-12.43-12.43-12.43 c-0.77,0-1.56,0.07-2.35,0.23C36.54,8.67,33.06,7,29.28,7c-5.55,0-10.36,3.62-11.92,8.89C11.43,16.9,7.04,22.05,7.04,28.14 c0,3.45,1.43,6.72,3.93,9.07c-0.44,1.3-0.66,2.64-0.66,4c0,6.86,5.58,12.43,12.43,12.43c0.44,0,0.88-0.02,1.38-0.08 C26.5,56.39,29.93,58,33.63,58c5.88,0,10.96-4.19,12.16-9.88c6.32-0.63,11.17-5.91,11.17-12.35 C56.96,32.46,55.62,29.29,53.27,26.96z M38.25,35.88l-6.63,4l-6.5-4v-7.26l6.63-3.87l6.63,3.75L38.25,35.88z"/><linearGradient id="9yv_OTO3P9eepfu7Rtqerb" x1="32" x2="32" y1=".872" y2="62.679" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#1a6dff"/><stop offset="1" stop-color="#c822ff"/></linearGradient><path fill="url(#9yv_OTO3P9eepfu7Rtqerb)" d="M53.274,26.955 c0.275-1.045,0.415-2.107,0.415-3.166c0-6.855-5.578-12.434-12.434-12.434c-0.766,0-1.553,0.079-2.35,0.235 C36.536,8.665,33.062,7,29.278,7c-5.549,0-10.353,3.622-11.913,8.891c-5.93,1.012-10.32,6.163-10.32,12.254 c0,3.448,1.424,6.715,3.93,9.07c-0.44,1.299-0.664,2.64-0.664,3.996c0,6.855,5.578,12.434,12.434,12.434 c0.433,0,0.874-0.027,1.38-0.087C26.501,56.389,29.934,58,33.633,58c5.875,0,10.96-4.192,12.152-9.878 c6.327-0.629,11.17-5.908,11.17-12.355C56.956,32.463,55.622,29.286,53.274,26.955z M51.689,23.789c0,0.646-0.07,1.293-0.193,1.937 l-12.293-7.185l-13.146,7.991v-4.91l12.814-7.972c0.813-0.191,1.615-0.295,2.383-0.295C47.008,13.355,51.689,18.036,51.689,23.789z M37.397,35.171l-5.563,3.316l-5.776-3.303v-6.311l5.465-3.322l-0.031,0.052l5.905,3.48V35.171z M29.278,9 c2.997,0,5.755,1.251,7.728,3.457l-12.948,8.054V34.04l-4.898-2.801V16.922C20.319,12.254,24.462,9,29.278,9z M9.044,28.145 c0-4.923,3.419-9.109,8.116-10.169v14.424l12.701,7.264l-5.227,3.115l-11.897-6.674C10.392,34.107,9.044,31.211,9.044,28.145z M12.311,41.211c0-0.955,0.138-1.902,0.4-2.828l11.954,6.706l12.732-7.588v6.27l-13.172,7.754c-0.57,0.078-1.043,0.12-1.48,0.12 C16.992,51.645,12.311,46.964,12.311,41.211z M33.633,56c-2.886,0-5.578-1.175-7.546-3.252l13.31-7.835V30.261l4.539,2.675V47.09 C43.192,52.173,38.773,56,33.633,56z M45.936,46.091V31.793l-6.539-3.853v-0.068h-0.115l-5.879-3.465l5.821-3.538l12.309,7.195 c2.174,1.981,3.422,4.782,3.422,7.703C54.956,41.055,51.07,45.406,45.936,46.091z"/></svg>
            <!-- <span class="sr-only">Notifications</span>
            <Badge rounded index color="!pink" class="w-1 h-1"></Badge> -->
          </ToolbarButton>

          <ToolbarButton on:click={() => (hidden2 = false)} class="text-center"><svg fill="#000000" width="24px" height="24px" viewBox="0 0 24 24" id="settings" data-name="Flat Line" xmlns="http://www.w3.org/2000/svg" class="icon flat-line"><path id="secondary" d="M20,10h-.59a1,1,0,0,1-.94-.67v0a1,1,0,0,1,.2-1.14l.41-.41a1,1,0,0,0,0-1.42L17.66,4.93a1,1,0,0,0-1.42,0l-.41.41a1,1,0,0,1-1.14.2h0A1,1,0,0,1,14,4.59V4a1,1,0,0,0-1-1H11a1,1,0,0,0-1,1v.59a1,1,0,0,1-.67.94h0a1,1,0,0,1-1.14-.2l-.41-.41a1,1,0,0,0-1.42,0L4.93,6.34a1,1,0,0,0,0,1.42l.41.41a1,1,0,0,1,.2,1.14v0a1,1,0,0,1-.94.67H4a1,1,0,0,0-1,1v2a1,1,0,0,0,1,1h.59a1,1,0,0,1,.94.67v0a1,1,0,0,1-.2,1.14l-.41.41a1,1,0,0,0,0,1.42l1.41,1.41a1,1,0,0,0,1.42,0l.41-.41a1,1,0,0,1,1.14-.2h0a1,1,0,0,1,.67.94V20a1,1,0,0,0,1,1h2a1,1,0,0,0,1-1v-.59a1,1,0,0,1,.67-.94h0a1,1,0,0,1,1.14.2l.41.41a1,1,0,0,0,1.42,0l1.41-1.41a1,1,0,0,0,0-1.42l-.41-.41a1,1,0,0,1-.2-1.14v0a1,1,0,0,1,.94-.67H20a1,1,0,0,0,1-1V11A1,1,0,0,0,20,10Zm-8,5a3,3,0,1,1,3-3A3,3,0,0,1,12,15Z" style="fill: rgb(44, 169, 188); stroke-width: 2;"></path><path id="primary" d="M15,12a3,3,0,1,1-3-3A3,3,0,0,1,15,12Zm5-2h-.59a1,1,0,0,1-.94-.67v0a1,1,0,0,1,.2-1.14l.41-.41a1,1,0,0,0,0-1.42L17.66,4.93a1,1,0,0,0-1.42,0l-.41.41a1,1,0,0,1-1.14.2h0A1,1,0,0,1,14,4.59V4a1,1,0,0,0-1-1H11a1,1,0,0,0-1,1v.59a1,1,0,0,1-.67.94h0a1,1,0,0,1-1.14-.2l-.41-.41a1,1,0,0,0-1.42,0L4.93,6.34a1,1,0,0,0,0,1.42l.41.41a1,1,0,0,1,.2,1.14v0a1,1,0,0,1-.94.67H4a1,1,0,0,0-1,1v2a1,1,0,0,0,1,1h.59a1,1,0,0,1,.94.67v0a1,1,0,0,1-.2,1.14l-.41.41a1,1,0,0,0,0,1.42l1.41,1.41a1,1,0,0,0,1.42,0l.41-.41a1,1,0,0,1,1.14-.2h0a1,1,0,0,1,.67.94V20a1,1,0,0,0,1,1h2a1,1,0,0,0,1-1v-.59a1,1,0,0,1,.67-.94h0a1,1,0,0,1,1.14.2l.41.41a1,1,0,0,0,1.42,0l1.41-1.41a1,1,0,0,0,0-1.42l-.41-.41a1,1,0,0,1-.2-1.14v0a1,1,0,0,1,.94-.67H20a1,1,0,0,0,1-1V11A1,1,0,0,0,20,10Z" style="fill: none; stroke: rgb(0, 0, 0); stroke-linecap: round; stroke-linejoin: round; stroke-width: 2;"></path></svg></ToolbarButton>
        </ToolbarGroup>


        <!-- <ToolbarButton name="send" slot="end" on:click={handleSubmit} type="submit"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6"><path stroke-linecap="round" stroke-linejoin="round" d="M6 12L3.269 3.126A59.768 59.768 0 0121.485 12 59.77 59.77 0 013.27 20.876L5.999 12zm0 0h7.5" /></svg></ToolbarButton> -->

        
      </Toolbar>


    </Textarea>

    <Button gradient color="blue" on:click={handleSubmit}>Submit</Button>

    <!-- <div class="text-center">
      <Button gradient color="blue" on:click={() => (hidden2 = false)} class="m-5">Show navigation</Button>
    </div> -->
  </form>
</div>

{/if}

