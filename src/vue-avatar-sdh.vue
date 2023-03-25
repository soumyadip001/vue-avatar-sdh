<script lang="ts">
import { CSSProperties, defineComponent } from 'vue';

interface SampleData {
  abbreviations: string[];
  allowedThemeTypes: string[];
  backgroundColors: string[];
  defaultUserName: string;
  imgError: boolean;
  themeError: boolean;
}

enum ThemeTypes {
  ROBO = 'ROBO',
}

export default defineComponent({
  name: 'Avatar',
  data(): SampleData {
    return {
      abbreviations: [
        'Dr', 'Esq', 'Hon', 'Er', 'Jr', 'Mr', 'Mrs', 'Ms', 'Messrs',
        'Mmes', 'Msgr', 'Prof', 'Rev', 'Rt', 'Sr', 'St',
      ],
      allowedThemeTypes: [ThemeTypes.ROBO],
      backgroundColors: [
        '#F44336', '#FF4081', '#9C27B0', '#673AB7',
        '#3F51B5', '#2196F3', '#03A9F4', '#00BCD4', '#009688',
        '#4CAF50', '#8BC34A', '#CDDC39', /* '#FFEB3B' , */ '#FFC107',
        '#FF9800', '#FF5722', '#795548', '#9E9E9E', '#607D8B'
      ],
      defaultUserName: 'U',
      imgError: false,
      themeError: false,
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
    isImage(): boolean {
      return !this.imgError && Boolean(this.src)
    },
    isTheme(): boolean {
      if (this.theme && this.theme.trim()) {
        return true
      }
      return false
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
    themeSrc(): string {
      return this.getTheme(this.theme?.trim()?.toUpperCase() || '')
    },
    userInitial (): string {
      if (!this.isImage) {
        return this.parseInitial(this.username)
      }
      return this.defaultUserName
    },
  },
  methods: {
    getTheme(theme: string) {
      if (!theme || !this.allowedThemeTypes.includes(theme)) {
        return this.defaultUserName
      }
      const randImg = String(this.randomIntFromInterval(1, 20)).padStart(3, '0')
      const roboImageSrc = require(`./assets/${this.theme?.toLowerCase()}/${randImg}.png`)
      return roboImageSrc
    },
    randomIntFromInterval (min: number = 1, max: number = 10): number {
      return Math.floor(Math.random() * (max - min + 1) + min)
    },
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
       * only added lint fixes
       */
      let usePound = false
      if (hex && hex[0] === '#') {
        hex = hex.slice(1)
        usePound = true
      }
      const num = parseInt(hex, 16)
      let r = (num >> 16) + amt
      if (r > 255) r = 255
      else if (r < 0) r = 0
      let b = ((num >> 8) & 0x00FF) + amt
      if (b > 255) b = 255
      else if (b < 0) b = 0
      let g = (num & 0x0000FF) + amt
      if (g > 255) g = 255
      else if (g < 0) g = 0
      return (usePound ? '#' : '') + (g | (b << 8) | (r << 16)).toString(16)
    },
    onImgError (_evt: any): void {
      this.imgError = true
    },
    onThemeError(_evt: any): void {
      this.themeError = true
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
    theme: {
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
    <img v-if="isTheme" :src="themeSrc" @error="onThemeError" :style="{width: '100%'}" alt="Profile Image" />
    <span v-show="!isImage && !isTheme">{{ userInitial }}</span>
  </div>
</template>
