<template>

<nav>
  <ul class ="navbar">
    <li><NuxtLink to="/">HOME</NuxtLink></li>
    <li><NuxtLink to="/workout">WORKOUT</NuxtLink></li>
    <li><NuxtLink to="/ad">AD</NuxtLink></li>
  </ul>
</nav>

</template>

<script>
export default {
  name: 'Navbar',
  // Component logic here
};
</script>

<style>
/* Reset default list styles */

.navbar {
  display: flex;
  flex-direction: row;
  width: border-box;
  height: 50px;
  justify-content: center;
  align-items:center;
  outline-color: black;
  outline-width: 5px;
  outline-style: solid;
  list-style-type: none;
  background-color: #acc1c2;
}
/* Style for navigation items */
.navbar li {
margin-left: 50px;
  margin-right: 50px;
}
.navbar li a {
  text-decoration: none;
  color: #333; /* Text color */
  font-weight: bold;
}

/* Change link color on hover */
.navbar li a:hover {
  color: #ff6600;
}
</style>