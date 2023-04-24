<script>

  import { Router, Link, Route} from 'svelte-navigator';

  import Home from './pages/home/Home.svelte'
  import Contact from './pages/contact/Contact.svelte';
  import Login from './pages/login/Login.svelte';
  import SignUp from './pages/signup/Signup.svelte';
  import ForgotPassword from './pages/forgot-password/ForgotPassword.svelte'

  import PrivateRoute from './components/private-route/PrivateRoute.svelte';

  import { user } from "./stores/user.js"

  function handleLogout() {
    $user = null
  }
</script>

<Router>
  <nav>
    <Link class="nav-item-container" to="/">
      <h3 class="nav-item">Home</h3>
    </Link>
    <Link class="nav-item-container" to="profile">
      <h3 class="nav-item">Profile</h3>
    </Link>
    
    <Link class="nav-item-container" to="/contact">
      <h3 class="nav-item">Contact</h3>
    </Link>
    {#if !$user}
    <Link class="nav-item-container" to="/sign-up">
      <h3 class="nav-item">Sign up</h3>
    </Link>
    <Link class="nav-item-container" to="/log-in">
      <h3 class="nav-item">Log in</h3>
    </Link>
    {/if}
    {#if $user}
    <button on:click={handleLogout}>Logout</button>
    {/if}
  
  </nav>

  <div id="page-container">
    <Route path="/">
      <Home></Home>
    </Route>
    <Route path="/contact">
      <Contact></Contact>
    </Route>
    <Route path="sign-up">
      <SignUp></SignUp>
    </Route>
    <Route path="/log-in">
      <Login></Login>
    </Route>
    <Route path="/forgot-password">
      <ForgotPassword></ForgotPassword>
    </Route>
  </div>

  <PrivateRoute path="profile" let:location>
    <h3>Welcome {$user.username}</h3>
    <button on:click={handleLogout}>Logout</button>
  </PrivateRoute>

</Router>



