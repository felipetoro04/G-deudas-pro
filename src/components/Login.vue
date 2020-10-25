<template>


  <div id="login">
  <form method="post">
    <div class="imgcontainer">
      <img src="../assets/images/logo.png" alt="login" class="avatar">
    </div>

    <div class="container">
      <label for="uname"><b>Usuario</b></label>
      <input type="text" placeholder="Ingresa Usuario" name="uname" required>

      <label for="psw"><b>Contrasena</b></label>
      <input type="password" placeholder="Ingresa Contrasena" name="psw" required>
      <router-link to="/home"><button type="submit">Login</button></router-link>

      <label>
        <input type="checkbox" checked="checked" name="remember"> Recordar
      </label>
    </div>

    <div class="container" style="background-color:#f1f1f1">
      <router-link to="/registro"><button type="button" class="registro">Registrar</button></router-link>

      <span class="psw"><a href="#">Olvidaste tu contrasena?</a></span>
    </div>
  </form>
  </div>

</template>

<script>

export default {
  name: 'Login',

}
</script>
<style>
/* Bordered form */
#login form {
  border: 3px solid #f1f1f1;
}

/* Full-width inputs */
#login input[type=text], input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

/* Set a style for all buttons */
#login button {
  background-color: mediumslateblue;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

/* Add a hover effect for buttons */
#login button:hover {
  opacity: 0.8;
}


/* Center the avatar image inside this container */
#login .imgcontainer {
  text-align: center;
  margin: 24px 0 12px 0;
}

/* Avatar image */
#login img.avatar {
  width: 200px;
  border-radius: 50%;
  text-align: center;
}

/* Add padding to containers */
#login .container {
  padding: 16px;
  text-align: center;
}

/* The "Forgot password" text */
#login span.psw {
  float: right;
  padding-top: 16px;
}

/* Change styles for span and cancel button on extra small screens */
#login @media screen and (max-width: 300px) {
  span.psw {
    display: block;
    float: none;
  }
  .registro {
    width: 100%;
  }
}
</style>