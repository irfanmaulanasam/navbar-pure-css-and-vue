<template>
    <div id="app">
        <header>
        <a href="#main-menu"
            id="main-menu-toggle"
            class="menu-toggle"
            aria-label="Open main menu">
            <span class="sr-only">Open main menu</span>
            <span class="fa fa-bars" aria-hidden="true"></span>
        </a>
        
        <h1 class="logo">hamburgers</h1>
        
        <nav id="main-menu" class="main-menu" aria-label="Main menu">
            <a href="#main-menu-toggle"
            id="main-menu-close"
            class="menu-close"
            aria-label="Close main menu">
            <span class="sr-only">Close main menu</span>
            <span class="fa fa-close" aria-hidden="true"></span>
            </a>
            <sidebar/>
        </nav>
        <a href="#main-menu-toggle"
            class="backdrop"
            tabindex="-1"
            aria-hidden="true" hidden></a>
        </header>

        <!--
        Demo purposes only.
        Lots of text = scroll testing!
        -->
        <article>
        <h2>Hamburgers are delicious</h2>
        <p>Even better is bacon...ipsum dolor amet kielbasa sirloin pancetta andouille biltong jowl brisket corned beef turducken flank. Andouille corned beef shank tongue leberkas turducken cow pork chop salami bresaola frankfurter shankle. Pork belly porchetta prosciutto, pancetta meatloaf cow frankfurter pork chuck biltong boudin ball tip ham. Corned beef pig beef ribs burgdoggen.</p>

        <p>Flank jerky tri-tip strip steak tail biltong. Tongue chicken burgdoggen, leberkas ham hock landjaeger sausage cupim shankle strip steak ribeye tenderloin jowl. Pork drumstick flank pork loin, tenderloin chuck pastrami kielbasa brisket kevin cow swine strip steak. Picanha shoulder t-bone burgdoggen, alcatra tongue tail ham hock bacon meatloaf rump shankle. Boudin ham leberkas burgdoggen ground round short ribs chicken pancetta meatloaf picanha t-bone. Short loin rump strip steak, short ribs cupim tongue pancetta flank ball tip tail.</p>

        <p>Alcatra jowl biltong kevin, shankle ham hock sausage turducken andouille. Ribeye prosciutto turkey flank, picanha kielbasa ball tip. Shoulder tenderloin bresaola, corned beef boudin capicola burgdoggen t-bone bacon short loin hamburger drumstick. Beef pork belly biltong sausage jerky picanha frankfurter boudin beef ribs cupim capicola salami. Biltong alcatra sirloin, kevin frankfurter short loin doner beef ribs landjaeger sausage venison. Shoulder t-bone ham hock pig.</p>

        <p>Brisket beef spare ribs, pastrami pancetta bresaola pig short loin flank t-bone. Porchetta biltong filet mignon pork loin picanha shank kielbasa boudin sausage alcatra. Ball tip bresaola salami tail meatloaf shoulder short ribs pancetta pork loin venison, picanha tongue pig turkey. Rump filet mignon sausage ribeye biltong. Short ribs pork chop corned beef, venison kevin pork loin tail strip steak ham hock porchetta.</p>

        <p>Cow beef ribs ham hock ball tip bacon pork belly. Shank beef tenderloin landjaeger. Pork loin shank drumstick ball tip, turkey pig ground round kevin t-bone chicken. Ham hock chicken ribeye jowl pork belly bresaola. Sausage leberkas landjaeger ham pork belly bresaola short ribs burgdoggen shank jowl capicola kielbasa swine. Pork belly leberkas boudin tail. Pork chop cow leberkas tenderloin corned beef, shankle ham hock cupim tail chuck jerky rump.</p>
        </article>
    </div>
</template>
<script>
import sidebar from './sidebar'
export default {
    name:'app',
    components:{
        sidebar
    }
}
</script>

<style>
/* Screen reader only */
.sr-only {
  position: absolute;
  width: 10px;
  height: 10px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0,0,0,0);
  border: 0;
}

/* Button styling */
.menu-toggle {
  display: inline-block;
  padding: .75em 15px;
  line-height: 1em;
  font-size: 1em;
  color: #333;
}

.menu-toggle:hover,
.menu-toggle:focus {
  color: #c00;
}

/*
 Default styles + Mobile first
 Offscreen menu style
*/
.main-menu {
  position: absolute;
  display: none;
  left: -200px;
  top: 0;
  height: 100%;
	overflow-y: scroll;
	overflow-x: visible;
	transition: left 0.3s ease,
				      box-shadow 0.3s ease;
	z-index: 999;
}

.main-menu ul {
  list-style: none;
  margin: 0;
  padding: 2.5em 0 0;
  /* Hide shadow w/ -8px while 'closed' */
  -webkit-box-shadow: -8px 0 8px rgba(0,0,0,.5);
     -moz-box-shadow: -8px 0 8px rgba(0,0,0,.5);
          box-shadow: -8px 0 8px rgba(0,0,0,.5);
  min-height: 100%;
  width: 200px;
  background: #1a1a1a;
}

.main-menu a {
  display: block;
  padding: .75em 15px;
  line-height: 1em;
  font-size: 1em;
  color: #fff;
  text-decoration: none;
  border-bottom: 1px solid #383838;
}

.main-menu li:first-child a {
  border-top: 1px solid #383838;
}

.main-menu a:hover,
.main-menu a:focus {
  background: #333;
  text-decoration: underline;
}

.main-menu .menu-close {
  position: absolute;
  right: 0;
  top: 0;
}

/*
 On small devices, allow it to toggle...
*/
/*
 :target for non-JavaScript
 [aria-expanded] will be used if/when JavaScript is added to improve interaction, though it's completely optional.
*/
.main-menu:target,
.main-menu[aria-expanded="true"] {
  display: block;
  left: 0;
  outline: none;
  -moz-box-shadow: 3px 0 12px rgba(0,0,0,.25);
  -webkit-box-shadow: 3px 0 12px rgba(0,0,0,.25);
  box-shadow: 3px 0 12px rgba(0,0,0,.25);
}

.main-menu:target .menu-close,
.main-menu[aria-expanded="true"] .menu-close {
  z-index: 1001;
}

.main-menu:target ul,
.main-menu[aria-expanded="true"] ul {
  position: relative;
  z-index: 1000;
}

/* 
 We could us `.main-menu:target:after`, but
 it wouldn't be clickable.
*/
.main-menu:target + .backdrop,
.main-menu[aria-expanded="true"] + .backdrop{
  position: absolute;
  display: block;  
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 998;
  background: #000;
  background: rgba(0,0,0,.85);
  cursor: default;
}

@supports (position: fixed) {
  .main-menu,
  .main-menu:target + .backdrop,
  .main-menu[aria-expanded="true"] + .backdrop{
    position: fixed;
  }
}

/*
 Larger screen styling
 Horizontal menu
*/
@media (min-width: 768px) {
  .menu-toggle,
  .main-menu .menu-close {
    display: none;
  }
  
  /* Undo positioning of off-canvas menu */
  .main-menu {
    position: relative;
		left: auto;
		top: auto;
		height: auto;
    display: block;
  }
  
  .main-menu ul {
    display: flex;
    
    /* Undo off-canvas styling */
    padding: 0;
    -webkit-box-shadow: none;
       -moz-box-shadow: none;
            box-shadow: none;
    height: auto;
    width: auto;
    background: none;
  }
  
  .main-menu a {
    color: #06c;
    border: 0 !important; /* Remove borders from off-canvas styling */
  }
  
  .main-menu a:hover,
  .main-menu a:focus {
    background: none; /* Remove background from off-canvas styling */
    color: #c00;
  }
}

/*
 Demo purposes only
*/
*,
*:before,
*:after {
  box-sizing: border-box;
}

header {
  padding: 20px;
  display: flex;
  align-items: baseline;
}

article {
  padding: 30px;
  max-width: 55em;
  font-size: 16px;
  line-height: 1.5em;
}

article h2 {
  font-weight: 500;
  font-size: 28px;
}

.logo {
  margin: 0 30px 0 10px;
  font-size: 1.5em;
}
</style>
