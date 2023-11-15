<template>
  <div class="w-full h-full border border-gray-200 overflow-hidden rounded-md">
    <div v-if="editor" class="bg-white sticky top-0 z-10 w-full flex border-b border-gray-200 text-xl text-gray-600">
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleBold().run()">
        <svg width="15" height="15" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path fill="#000000" fill-rule="evenodd" d="M7.609 1A3.609 3.609 0 0 0 4 4.609V19.94A3.06 3.06 0 0 0 7.059 23H14a6 6 0 0 0 2.102-11.621A6 6 0 0 0 12 1H7.609ZM12 11a4 4 0 0 0 0-8H7.609C6.72 3 6 3.72 6 4.609V11h6Zm-6 2v6.941C6 20.526 6.474 21 7.059 21H14a4 4 0 0 0 0-8H6Z" clip-rule="evenodd"/>
        </svg>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleItalic().run()">
        <svg width="15" height="15" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path fill="#000000" fill-rule="evenodd" d="M14.977 1H9a1 1 0 1 0 0 2h4.656l-5.4 18H3a1 1 0 1 0 0 2h12a1 1 0 1 0 0-2h-4.656l5.4-18H21a1 1 0 1 0 0-2h-6.023Z" clip-rule="evenodd"/>
        </svg>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 mr-1 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().underline().toggleItalic().run()">
        <svg width="15" height="15" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path fill="#000000" d="M5 3a1 1 0 0 0-2 0v6a9 9 0 1 0 18 0V3a1 1 0 1 0-2 0v6A7 7 0 1 1 5 9V3ZM4 20a1 1 0 1 0 0 2h16a1 1 0 1 0 0-2H4Z"/>
        </svg>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-l border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().setParagraph().run()">
        P
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleHeading({ level: 1 }).run()">
        H1
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleHeading({ level: 2 }).run()">
        H2
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 mr-1 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleHeading({ level: 3 }).run()">
        H3
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 mr-1 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleHeading({ level: 4 }).run()">
        H4
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 mr-1 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleHeading({ level: 5 }).run()">
        H5
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 mr-1 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleHeading({ level: 6 }).run()">
        H6
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-l border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleBulletList().run()">
        <svg width="24" height="24" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
          <path fill="currentColor" fill-rule="evenodd" d="M5 11.5a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5zm-3 1a1 1 0 1 0 0-2a1 1 0 0 0 0 2zm0 4a1 1 0 1 0 0-2a1 1 0 0 0 0 2zm0 4a1 1 0 1 0 0-2a1 1 0 0 0 0 2z"/>
        </svg>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 mr-1 hover:text-indigo-500 active:bg-gray-50" @click="editor.chain().focus().toggleOrderedList().run()">
        <svg width="24" height="24" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
          <g fill="currentColor">
            <path fill-rule="evenodd" d="M5 11.5a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5z"/>
            <path d="M1.713 11.865v-.474H2c.217 0 .363-.137.363-.317c0-.185-.158-.31-.361-.31c-.223 0-.367.152-.373.31h-.59c.016-.467.373-.787.986-.787c.588-.002.954.291.957.703a.595.595 0 0 1-.492.594v.033a.615.615 0 0 1 .569.631c.003.533-.502.8-1.051.8c-.656 0-1-.37-1.008-.794h.582c.008.178.186.306.422.309c.254 0 .424-.145.422-.35c-.002-.195-.155-.348-.414-.348h-.3zm-.004-4.699h-.604v-.035c0-.408.295-.844.958-.844c.583 0 .96.326.96.756c0 .389-.257.617-.476.848l-.537.572v.03h1.054V9H1.143v-.395l.957-.99c.138-.142.293-.304.293-.508c0-.18-.147-.32-.342-.32a.33.33 0 0 0-.342.338v.041zM2.564 5h-.635V2.924h-.031l-.598.42v-.567l.629-.443h.635V5z"/>
          </g>
        </svg>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-l border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="format('justifyLeft')">
        <svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 6H3m12 6H3m14 6H3"/>
        </svg>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-l border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="format('justifyLeft')">
        <svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <g fill="none">
            <path d="M24 0v24H0V0h24ZM12.593 23.258l-.011.002l-.071.035l-.02.004l-.014-.004l-.071-.035c-.01-.004-.019-.001-.024.005l-.004.01l-.017.428l.005.02l.01.013l.104.074l.015.004l.012-.004l.104-.074l.012-.016l.004-.017l-.017-.427c-.002-.01-.009-.017-.017-.018Zm.265-.113l-.013.002l-.185.093l-.01.01l-.003.011l.018.43l.005.012l.008.007l.201.093c.012.004.023 0 .029-.008l.004-.014l-.034-.614c-.003-.012-.01-.02-.02-.022Zm-.715.002a.023.023 0 0 0-.027.006l-.006.014l-.034.614c0 .012.007.02.017.024l.015-.002l.201-.093l.01-.008l.004-.011l.017-.43l-.003-.012l-.01-.01l-.184-.092Z"/>
            <path fill="currentColor" d="M17 18a1 1 0 0 1 .117 1.993L17 20H7a1 1 0 0 1-.117-1.993L7 18h10Zm3-5a1 1 0 1 1 0 2H4a1 1 0 1 1 0-2h16Zm-3-5a1 1 0 0 1 .117 1.993L17 10H7a1 1 0 0 1-.117-1.993L7 8h10Zm3-5a1 1 0 0 1 .117 1.993L20 5H4a1 1 0 0 1-.117-1.993L4 3h16Z"/>
          </g>
        </svg>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-l border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="format('justifyLeft')">
        <span class="rotate-180">
          <svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 6H3m12 6H3m14 6H3"/>
        </svg>
        </span>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="format('justifyCenter')">
        <i class="mdi mdi-format-align-center"></i>
      </button>
      <button class="flex justify-center items-center outline-none focus:outline-none border-r border-gray-200 w-10 h-10 hover:text-indigo-500 active:bg-gray-50" @click="format('justifyRight')">
        <i class="mdi mdi-format-align-right"></i>
      </button>
    </div>
    <div class="p-5">
      <editor-content class="h-[250px]" :editor="editor" />
    </div>
  </div>
</template>
<script setup lang="ts">
import StarterKit from '@tiptap/starter-kit'
import { Editor, EditorContent } from '@tiptap/vue-3'
import {ref, onMounted, onUnmounted, defineEmits} from "vue";

const emit = defineEmits(['update:modelValue'])

const editor = ref(null)

onMounted(()=> {
  editor.value = new Editor({
    content: '<p>Type your text here... 🎉</p>',
    extensions: [
      StarterKit,
    ],
    onCreate: ()=> {
      const content = editor.value.options.element.innerHTML.replace('contenteditable="true"', 'contenteditable="false"')
      emit('update:modelValue', content)
    },
    onUpdate: ()=>{
      const content = editor.value.options.element.innerHTML.replace('contenteditable="true"', 'contenteditable="false"')
      emit('update:modelValue', content)
    },
    autofocus: "end",
  })
})

onUnmounted(()=> {
  editor.value.destroy()
})
</script>
<style lang="scss">
/* Basic editor styles */
.tiptap {
  height: inherit;
  border: none;
  outline: none;
  z-index: 0;
  > * + * {
    margin-top: 0.75em;
  }

  ul,
  ol {
    padding: 0 1rem;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    line-height: 1.1;
  }

  code {
    background-color: rgba(#616161, 0.1);
    color: #616161;
  }

  pre {
    background: #0D0D0D;
    color: #FFF;
    font-family: 'JetBrainsMono', monospace;
    padding: 0.75rem 1rem;
    border-radius: 0.5rem;

    code {
      color: inherit;
      padding: 0;
      background: none;
      font-size: 0.8rem;
    }
  }

  img {
    max-width: 100%;
    height: auto;
  }

  blockquote {
    padding-left: 1rem;
    border-left: 2px solid rgba(#0D0D0D, 0.1);
  }

  hr {
    border: none;
    border-top: 2px solid rgba(#0D0D0D, 0.1);
    margin: 2rem 0;
  }
}
</style>