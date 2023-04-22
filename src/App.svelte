<script>

  import { Router, Link, Route} from 'svelte-navigator';

  import Home from './pages/home/Home.svelte'
  import Contact from './pages/contact/Contact.svelte';
  import Login from './pages/login/Login.svelte';
  import SignUp from './pages/signup/Signup.svelte';
  import ForgotPassword from './pages/forgot-password/ForgotPassword.svelte';
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
    <Route path="/forgot-password">
      <ForgotPassword></ForgotPassword>
    </Route>
  </div>

</Router>



