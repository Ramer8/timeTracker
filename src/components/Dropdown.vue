<template>
  <div class="dropdown">
    <button class="dropbtn"><slot></slot></button>
    <div class="dropdown-content">
      <div class="dropdown1">
        Mis Cuentas
        <button class="dropbtn1"></button>
        <div class="dropdown-content1">
          <a href="#"
            >Sesame 1
            <div class="font-bold">
              <slot></slot>
            </div>
          </a>
          <a href="#"
            >Sesame 2
            <div class="font-bold">
              <slot></slot></div
          ></a>
        </div>
      </div>
      <a href="#">Vista empleado</a>
      <a href="#">Mi Perfil</a>
      <a href="#">Cerrar</a>
    </div>
  </div>
</template>
<script></script>

<style>
.dropbtn {
  padding: 16px;
  font-size: 14px;
  border: none;
}
.dropbtn1 {
  padding: 16px;
  font-size: 16px;
  border: none;
}

.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown1 {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  font-size: 14px;
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  font-weight: 300;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
  border-radius: 1vmax;
}
.dropdown-content1 {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  font-weight: 300;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
  border-radius: 1vmax;
}

.dropdown-content a {
  color: black;
  padding: 12px 1px;
  text-decoration: none;
  display: block;
  border-radius: 1vmax;
}
.dropdown-content1 div {
  color: black;
  padding: 12px 1px;
  text-decoration: none;
  display: block;
  border-radius: 1vmax;
}

.dropdown-content a:hover {
  background-color: #ddd;
}
.dropdown-content1 div:hover {
  background-color: #ddd;
}

.dropdown:hover .dropdown-content {
  display: block;
}
.dropdown1:hover .dropdown-content1 {
  display: block;
}

.dropdown:hover .dropbtn {
  color: darkgrey;
}
.dropdown:hover .dropbtn1 {
  color: darkgrey;
}
</style>
