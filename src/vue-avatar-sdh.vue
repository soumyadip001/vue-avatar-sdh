<script lang="ts">
import { CSSProperties, defineComponent } from 'vue';

interface SampleData {
  abbreviations: string[];
  backgroundColors: string[];
  defaultUserName: string;
  imgError: boolean;
}

export default defineComponent({
  name: 'Avatar',
  data(): SampleData {
    return {
      abbreviations: [
        'Dr', 'Esq', 'Hon', 'Er', 'Jr', 'Mr', 'Mrs', 'Ms', 'Messrs',
        'Mmes', 'Msgr', 'Prof', 'Rev', 'Rt', 'Sr', 'St',
      ],
      backgroundColors: [
        '#F44336', '#FF4081', '#9C27B0', '#673AB7',
        '#3F51B5', '#2196F3', '#03A9F4', '#00BCD4', '#009688',
        '#4CAF50', '#8BC34A', '#CDDC39', /* '#FFEB3B' , */ '#FFC107',
        '#FF9800', '#FF5722', '#795548', '#9E9E9E', '#607D8B'
      ],
      defaultUserName: 'SH',
      imgError: false,
    };
  },
  computed: {
    background (): string {
      if (!this.isImage) {
        return this.backgroundColor || this.randomBackgroundColor(this.username.length, this.backgroundColors)
      }
      return ''
    },
    customStyleComputed () {
      return this.customStyle ? this.customStyle : {}
    },
    fontColor (): string {
      if (!this.isImage) {
        return this.color || this.lightenColor(this.background, this.lighten)
      }
      return ''
    },
    isImage (): boolean {
      return !this.imgError && Boolean(this.src)
    },
    style (): CSSProperties {
      const style = {
        display: this.inline ? 'inline-flex' : 'flex',
        width: `${this.size}px`,
        height: `${this.size}px`,
        borderRadius: this.rounded ? '50%' : '0',
        lineHeight: `${(this.size + Math.floor(this.size / 20))}px`,
        fontWeight: 'bold' as "bold",
        alignItems: 'center',
        justifyContent: 'center',
        textAlign: 'center' as "center",
        userSelect: 'none' as "none"
      }
      const imgBackgroundAndFontStyle = {
        background: `transparent url('${this.src}') no-repeat scroll 0% 0% / ${this.size}px ${this.size}px content-box border-box`
      }
      const initialBackgroundAndFontStyle = {
        backgroundColor: this.background,
        font: `${Math.floor(this.size / 2.5)}px/${this.size}px Helvetica, Arial, sans-serif`,
        color: this.fontColor
      }
      const backgroundAndFontStyle = (this.isImage)
        ? imgBackgroundAndFontStyle
        : initialBackgroundAndFontStyle
      Object.assign(style, backgroundAndFontStyle)
      return style
    },
    userInitial (): string {
      if (!this.isImage) {
        return this.parseInitial(this.username)
      }
      return this.defaultUserName
    },
  },
  methods: {
    isAbbr (p: string): boolean {

      /******
       * Remove .,! etc from the string
       * ex: Dr. Mrs. Mr, Jr!
       */
      if (p.endsWith('.') || p.endsWith(',') || p.endsWith('!')) {
        p = p.slice(0, -1)
      }

      if (this.abbreviations.some(v => v.toLowerCase() === p.toLowerCase())) {
        return true
      }
      return false
    },
    lightenColor (hex: string, amt: number) {
      /**** 
       * From https://css-tricks.com/snippets/javascript/lighten-darken-color/
       */
      var usePound = false
      if (hex && hex[0] === '#') {
        hex = hex.slice(1)
        usePound = true
      }
      var num = parseInt(hex, 16)
      var r = (num >> 16) + amt
      if (r > 255) r = 255
      else if (r < 0) r = 0
      var b = ((num >> 8) & 0x00FF) + amt
      if (b > 255) b = 255
      else if (b < 0) b = 0
      var g = (num & 0x0000FF) + amt
      if (g > 255) g = 255
      else if (g < 0) g = 0
      return (usePound ? '#' : '') + (g | (b << 8) | (r << 16)).toString(16)
    },
    onImgError (_evt: any): void {
      this.imgError = true
    },
    parseInitial (username: string): string {
      if (!username) return this.defaultUserName

      let parts = username.split(/[ -]/)
      let initials = ''
      parts.forEach(p => {
        if (p.trim() !== '' && !this.isAbbr(p)) {
          initials += p.charAt(0).toUpperCase()
        }
      })

      if (initials.length > this.maxAllowedLength) {
        switch (this.maxAllowedLength) {
          case 2:
            return `${initials.charAt(0)}${initials.charAt(initials.length - 1)}`
          
          case 3:
            return `${initials.substring(0, 2)}${initials.charAt(initials.length - 1)}`
          
          default:
            return initials.substring(0, this.maxAllowedLength)
        }
      }
      return initials
    },
    randomBackgroundColor (seed: number, colors: string[]): string {
      return colors[seed % (colors.length)]
    },
  },
  props: {
    backgroundColor: {
      type: String,
    },
    color: {
      type: String,
    },
    customStyle: {
      type: Object,
    },
    maxAllowedLength: {
      type: Number,
      default: 2,
    },
    initials: {
      type: String,
    },
    inline: {
      type: Boolean,
    },
    lighten: {
      type: Number,
      default: 80,
    },
    rounded: {
      type: Boolean,
      default: true,
    },
    size: {
      type: Number,
      default: 50,
    },
    src: {
      type: String,
    },
    username: {
      type: String,
      required: true,
    },
  },
});
</script>

<template>
  <div class="vue-avatar--wrapper" aria-hidden="true" :style="[style, customStyleComputed]">
    <img v-if="isImage" style="display: none" :src="src" @error="onImgError" alt="Profile Image" />
    <span v-show="!isImage">{{ userInitial }}</span>
  </div>
</template>
