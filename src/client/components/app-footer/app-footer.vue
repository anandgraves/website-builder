<template>
  <ul class="app-footer">
    <li
      v-for="(item, index) in socialmedia"
      :key="index"
      class="app-footer__item"
    >
      <a
        class="app-footer__link"
        :href="platformUrl(item.platform, item.username)"
        target="_blank"
        rel="noopener noreferrer"
      >
        <icon-base
          width="36"
          height="36"
          viewbox="0 0 24 24"
          :icon-name="item.platform"
          ><component :is="`icon-${item.platform}`"></component></icon-base
      ></a>
    </li>
  </ul>
</template>

<script>
import iconBase from '../icon-base/icon-base.vue'
import iconInstagram from '../icons/icon-instagram.vue'
import iconTwitter from '../icons/icon-twitter.vue'
import iconFacebook from '../icons/icon-facebook.vue'
import iconYoutube from '../icons/icon-youtube.vue'
import iconPinterest from '../icons/icon-pinterest.vue'
import iconLinkedin from '../icons/icon-linkedin.vue'

export default {
  components: {
    iconBase,
    iconFacebook,
    iconInstagram,
    iconLinkedin,
    iconPinterest,
    iconTwitter,
    iconYoutube
  },
  props: {
    socialmedia: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      urls: {
        twitter: 'https://twitter.com',
        instagram: 'https://instagram.com',
        facebook: 'https://facebook.com',
        pinterest: 'https://pinterest.com',
        youtube: 'https://youtube.com',
        linkedin: 'https://linkedin.com'
      }
    }
  },
  methods: {
    platformUrl(platform, username) {
      return `${this.urls[platform]}/${username}`
    }
  }
}
</script>

<style>
.app-footer {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
}

.app-footer__item {
  flex: 0 0 60px;
}

.app-footer__item:not(:first-child) {
  margin-left: 24px;
}

.app-footer__link {
  display: block;
  text-align: center;
  transform-origin: bottom;
  transition: transform 0.1s ease;
}

.app-footer__link:hover {
  transform: scale(1.1);
}
</style>
