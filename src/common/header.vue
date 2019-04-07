<template>
<header>
    <nav class="navbar navbar-expand-lg navbar-light">
        <img src="@/assets/img/ddlogo.png" class="navbar-brand logo" href="#">
        <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item menuitem" v-for="item in menuItems" :key="item">
                    <a class="nav-link" href="#">{{item}}</a>
                </li>
            </ul>
        </div>
    </nav>
</header>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      menuItems: []
    }
  },
  mounted () {

  },
  created () {
    axios.get('http://localhost:4000/items')
      .then(response => {
        // JSON responses are automatically parsed.
        this.menuItems = response.data
      })
      .catch(e => {
        this.errors.push(e)
      })
  }
}
</script>
