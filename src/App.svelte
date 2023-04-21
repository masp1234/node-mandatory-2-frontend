<script>

  import { Router, Link, Route} from 'svelte-navigator';

  import Home from './pages/Home/Home.svelte'
  import Contact from './pages/Contact/Contact.svelte';
  import Login from './pages/LogIn/Login.svelte';
  import SignUp from './pages/SignUp/Signup.svelte';
</script>

<Router>
  <nav>
    <Link class="nav-item" to="/">Home</Link>
    <Link class="nav-item" to="/contact">Contact</Link>
    <Link class="nav-item" to="/sign-up">Sign Up</Link>
    <Link class="nav-item" to="/log-in">Log In</Link>
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
  </div>

</Router>



