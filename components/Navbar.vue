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
.navbar {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style-type: none;
  background-color: #2a2929; /* Hot pink background color */
  padding: 0;
  margin: 0;
  height: 50px;
  border-bottom: 2px solid #2a2929; /* Lighter pink border */
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
}

.navbar li {
  margin: 0 20px;
}

.navbar li a {
  text-decoration: none;
  color: #fff; /* White text color */
  font-weight: bold;
  transition: color 0.3s;
}

.navbar li a:hover {
  color: rgba(175, 208, 210, 0.89); /* Vibrant yellow on hover */
}
</style>