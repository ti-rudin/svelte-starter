<script lang="ts">
  import { Router, Route } from "svelte-routing";
  import "./locale/i18n";
  import TopBanner from "./components/ui/banners/TopBanner.svelte";
  import Landing from "./views/front/Landing.svelte";
  import Pricing from "./views/front/Pricing.svelte";
  import Contact from "./views/front/Contact.svelte";
  import { Theme } from "./application/enums/shared/Theme";
  import { themeState } from "./store/modules/themeStore";
  import PrivacyPolicy from "./views/front/PrivacyPolicy.svelte";
  import TermsAndConditions from "./views/front/TermsAndConditions.svelte";
  import Components from "./views/front/Components.svelte";
  import Login from "./views/front/account/Login.svelte";
  import Register from "./views/front/account/Register.svelte";
  import Verify from "./views/front/account/Verify.svelte";
  import Forgot from "./views/front/account/Forgot.svelte";
  import Reset from "./views/front/account/Reset.svelte";
  import Invitation from "./views/front/account/Invitation.svelte";
  import JoinTenant from "./views/front/account/JoinTenant.svelte";

  export let url = "";

  const htmlClasses = document.querySelector("html")?.classList;
  if ($themeState.value === Theme.DARK) htmlClasses?.add("dark");
  else htmlClasses?.remove("dark");
</script>

<main role="main">
  <Router {url}>
    <TopBanner />
    <Route path="/">
      <Landing />
    </Route>
    <Route path="/pricing" component={Pricing} />
    <Route path="/contact" component={Contact} />
    <Route path="/privacy-policy" component={PrivacyPolicy} />
    <Route path="/terms-and-conditions" component={TermsAndConditions} />
    <Route path="/components" component={Components} />

    <Route path="/login" component={Login} />
    <Route path="/register" component={Register} />
    <Route path="/verify" component={Verify} />
    <Route path="/forgot-password" component={Forgot} />
    <Route path="/reset" component={Reset} />
    <Route path="/invitation" component={Invitation} />
    <Route path="/join/:tenantId" component={JoinTenant} />
  </Router>
</main>
