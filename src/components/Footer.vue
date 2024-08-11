<template>
  <footer class="footer">
    <div class="footer__main">
      <div class="container">
        <div class="footer__company-info">
          <RouterLink to="/" class="logo">VeganMarket</RouterLink>
          <p class="text">
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Odit, corporis.
          </p>
          <div class="socials">
            <a class="social__icon" href="#">
              <img src="../assets/images/icons/linkedin.svg" alt="linkedin" />
            </a>
            <a class="social__icon" href="#">
              <img src="../assets/images/icons/facebook.svg" alt="facebook" />
            </a>
            <a class="social__icon" href="#">
              <img src="../assets/images/icons/instagram.svg" alt="instagram" />
            </a>
            <a class="social__icon" href="#">
              <img src="../assets/images/icons/twitter_x.svg" alt="twitter_x" />
            </a>
          </div>
        </div>
        <nav class="footer__nav">
          <div class="footer__nav-title">Menu</div>
          <ul class="footer__nav-list">
            <li class="footer__nav-item"><a href="#">About us</a></li>
            <li class="footer__nav-item"><a href="#">News</a></li>
            <li class="footer__nav-item"><a href="#">Partners</a></li>
            <li class="footer__nav-item"><a href="#">Team</a></li>
            <li class="footer__nav-item"><a href="#">Contacts</a></li>
          </ul>
        </nav>
        <nav class="footer__nav">
          <div class="footer__nav-title">Help</div>
          <ul class="footer__nav-list">
            <li class="footer__nav-item"><a href="#">Privacy Policy</a></li>
            <li class="footer__nav-item"><a href="#">Support Policy</a></li>
            <li class="footer__nav-item"><a href="#">Term &amp; Conditions</a></li>
            <li class="footer__nav-item"><a href="#">FAQ</a></li>
            <li class="footer__nav-item"><a href="#">Sitemap</a></li>
          </ul>
        </nav>
        <div class="footer__contacts">
          <div class="contact-item">
            <img
              src="../assets/images/icons/location.svg"
              alt="location"
              class="contact-item__icon"
            />
            <address class="contact-item__text">
              Vegan Market Ltd, 533 Central Boulevard, Suite 400, Kyiv, 01001, Ukraine
            </address>
          </div>
          <div class="contact-item">
            <img src="../assets/images/icons/phone.svg" alt="phone" class="contact-item__icon" />
            <a class="contact-item__text" href="tel:+38(099)999-99-99">+38(099)999-99-99</a>
          </div>
          <div class="contact-item">
            <img src="../assets/images/icons/phone.svg" alt="phone" class="contact-item__icon" />
            <a class="contact-item__text" href="tel:+38(099)999-99-99">+38(099)999-99-99</a>
          </div>
          <div class="contact-item">
            <img src="../assets/images/icons/phone.svg" alt="phone" class="contact-item__icon" />
            <a class="contact-item__text" href="tel:+38(099)999-99-99">+38(099)999-99-99</a>
          </div>
          <div class="contact-item">
            <img
              src="../assets/images/icons/envelope.svg"
              alt="envelope"
              class="contact-item__icon"
            />
            <a class="contact-item__text" href="mailto:veganm@mail.com">veganm@mail.com</a>
          </div>
        </div>
      </div>
    </div>
    <div class="footer__underline">
      <div class="container">Copyright &copy; 2024. All Rights Reserved.</div>
    </div>
  </footer>
</template>

<script>
import { RouterLink } from 'vue-router'

export default {
  components: {
    RouterLink
  }
}
</script>
