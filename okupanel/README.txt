=== OkuPanel ===
Contributors: moon155
Tags: kiosk, calendar, events, ics, squat
Requires at least: 4.0
Tested up to: 4.9.4
Stable tag: trunk
Requires PHP: 5.2.4
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

A panel that displays live events from one or several calendar files (.ics). A cDb project.


== Features ==

- Display events from one from one or several online calendars (.ics or Google Calendar)
- Event changes are automatically updated on the client via periodic ajax calls.
- Autodetect specific events and show them in the sidebar.
- Display a popup for every event, with full address and description.
- Fully responsive frontend.
- Auto-scrolling events in fullscreen mode (for days ahead).
- Auto-scrolling bottom bar that can be updated without reloading the page.
- Events can be included in any normal wordpress page, via the [okupanel] shortcode.
- Events subscription/synchronization via ICS output.
- Graphical timeline of all events via the [okupanel_timeline] shortcode.
- Automatic management of cafeteria turns via an etherpad.
- Virtual nodes to show different centers in one common URL/screen.
- Federation capabilities to show events from many okupanels at once via a switch button.
- Feature special set of events via autodetected custom hashtags.
- Available in English and Spanish. Can be translated to any language through .po files.
- Can be set as the root page of the wordpress.
- Coming soon: integrate events with OpenStreetMaps

See [a live OkuPanel](https://ingobernable.net/okupanel/)!
Or [this other one](http://evarganzuela.org/eva/okupanel).

== Installation ==

**Requirements for a physical screen:**

- A [Raspberry Pi3 Model B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/), an Orange Pi or any computer you can dedicate to the task, plug to your screen and connect to the internet. 
- A [good charger](https://www.raspberrypi.org/products/raspberry-pi-universal-power-supply/) if you opted for a Raspberry or similar.
- A 8GB+ MicroSD card (better class 10, though it might work with a class 4), if you opted for a Raspberry or similar.
- A nice screen with an HDMI input + an HDMI cable (if you opted for a Raspberry or similar, otherwise just make sure you can connect the screen with the computer)

- Optional: a fan for the Pi.
- Extra: you'll probably love 3D-printing your own custom bio-degradable, ecological, cheap Pi case! If so, follow the dedicated part of [our previous kiosk tutorial](https://wiki.ingobernable.net/doku.php?id=pantalla_entrada#imprimir_en_3d_una_cajita_si_la_que_tenemos_esta_un_poco_rota) (Spanish only).

**Plugin installation:**

- Copy the `okupanel` folder to your server's `wp-content/plugins` folder.
- Enable the OkuPanel plugin via the `Plugins` tab.
- Go to `Settings > OkuPanel` and follow the instructions.

**Kiosk configuration:**

- Write down the fullscreen URL given in the previous step (it ends up in `?fullscreen=1&moving=1`).

- [Download FullpageOS](https://github.com/guysoft/FullPageOS) and extract it somewhere on your machine (with `unzip -u thefile` for example).

- Plug your MicroSD card to your computer and find its master path (for example with `sudo gparted`). Please make sure you use the right path, and not your HDD path! Otherwise you could wipe out all your local disk.

- Burn the extracted .img on the MicroSD card (for example with `dd if=/path/to/the/image.img of=/dev/microsd_id`).

- Once done, eject and re-insert the MicroSD card in order to mount it to your computer.

* On the "boot" partition of the MicroSD card, edit `fullpageos-network.txt` and put your network settings.
* Edit `fullpageos.txt` and leave only your OkuPanel's fullscreen URL.
* Edit `fullpagedashboard.txt` and leave only your OkuPanel's fullscreen URL there again.

* Eject the MicroSD card, insert it into your Pi, plug the Pi to a screen, and boot it.

* In a couple of minutes you should see the Pi automatically start Chromium in fullscreen mode and display your OkuPanel page ;)

* Additionally, you may log into your Pi via SSH (it may be located at fullpageos.local, default username is "pi", default password is "raspberry") and change the password using the passwd command. 

OkuPanel, by cDb.


== Frequently Asked Questions ==

**My panel is not reflecting the changes I make to the events, what should I do?**
- OkuPanel retrieves the events every 5 minutes, so it is normal if you don't see your changes immediately, just wait 5 minutes in fullscreen mode, or 15 in client mode (without ?fullscreen=1..). If you need to force the panel to reflect the changes you just made (due to a mistake, or just because you're testing), you can ever add ?update=1 to your OkuPanel URL while logged in, this will force the events to be retrieved again.

**Do you plan to add other languages?**
- No, but if you send us translation files (.po), we can add them to the plugin's available languages.

**Do you offer installation support?**
- Not really.. but you're very welcome to ask us anything at okupanel@riseup.net

**Do you offer software support?**
- Not really either.. but if you found a nice bug, we'll be pleased to fix it! Please use [our Github repository](https://github.com/OkuTeam/OkuPanel/issues) for all support tickets and suggestions.

**Do you have a donate link?**
- No, but if you really think we deserve your donation, you can always visit us (see address below) or contact us at luna155 at riseup dot net.

**Can you give us sample values for the config fields?**
- Sure. Here is an example of configuration:

Panel title: 
~~~~
Centro So<i class="fa fa-copyright fa-rotate-180"></i>ial de Comunes Urbanos <span>La Ingobernable <span class="okupanel-heart"><img src=".../rayo.png" class="okupanel-ray" /><i class="fa fa-heart"></i></span></span>
~~~~

Sidebar HTML:
~~~~
[okupanel_line label="Web" url="https://ingobernable.net" link_label="ingobernable.net"]
[okupanel_line label="Wiki" url="https://wiki.ingobernable.net" link_label="wiki.ingobernable.net"]
[okupanel_line label="Info / Actividades" url="mailto:example@example.com" link_label="example@example.com"]
[okupanel_line label="Twitter" url="https://twitter.com/CSIngobernable" link_label="@CSIngobernable"]

[okupanel_separator]

[okupanel_line label="Esta página" url="https://ingobernable.net/okupanel" link_label="ingobernable.net/okupanel"]

<div class="okupanel-qr">
<div class="okupanel-qr-intro"><i class="fa fa-mobile"></i><i class="fa fa-long-arrow-down"></i></div>
<img src="../QR.png" />
</div>
[okupanel_separator last="1"]
[okupanel_most_important]
<div class="okupanel-most-important"><i class="fa fa-thumb-tack"></i><div class="okupanel-most-important-right"><strong>Hackmeeting 2017</strong> <br>12/10 <i class='fa fa-arrow-right'></i> 15/10<span class="okupanel-most-important-location">(<a href="https://es.hackmeeting.org/" target="_blank">es.hackmeeting.org</a>)</span></div></div>
[/okupanel_most_important]
~~~~

Bottom bar content:
~~~~
Bienvenid<span class="okupanel-clean-font">@</span> a La Ingobernable, un espacio libre de racismo, sexismo, lgtbi-phobia, autoritarismo, especismo, y cualquier otra forma de violencia. Make <i class="fa fa-heart okupanel-icon-no-space"></i>, not <i class="fa fa-bomb okupanel-icon-no-space"></i>

¿Puedes enseñar algo nuevo e interesante? ¡Crear tu colectivo es fácil y legitimiza este espacio! Más información en ingobernable.net y bienvenida<span class="okupanel-clean-font">@</span>ingobernable.net ;)`
~~~~

Menu link label:
~~~~
Enlaces Ingobernables
~~~~

Extra CSS:
~~~~
html.okupanel, html.okupanel body {
    background: #000 !important;
}

.okupanel-header i.fa-copyright {
font-size: 51%;
margin: 0 2px 0 1px;
position: relative;
top: -2px;
}
.okupanel-clean-font {
font-weight: bold;
color: white;
    font-family: roboto;
}
.okupanel-header i.fa-heart {
    font-size: 30px;
    position: absolute;
    margin-left: 3px;
    left: 0;
    z-index: 1;
    top: 0;
}
.okupanel-header {
    background: #052100;
}

.okupanel-header span {
font-weight: bold;
white-space: nowrap;
}
.okupanel-header img.okupanel-ray {

    z-index: 7;
    height: 38px;
    width: 38px;
    position: relative;
    top: 4px;
}
.okupanel-header span.okupanel-heart {
   white-space: nowrap;
    position: relative;
    z-index: 5;
top: 3px;
}
.okupanel-header {
padding-bottom: 0px;
}

.shareaholic-canvas {
display: none !important;
}

body.okupanel-fullscreen .okupanel-panel {
    font-size: 20px;
}

.okupanel-table a {
    font-weight: normal;
}

.okupanel-table tr.okupanel-started td, 
.okupanel-table tr.okupanel-started td a {
    font-weight: bold;
}

.okupanel-qr {
display: none;
position: fixed;
right: 0;
bottom: 34px;
}
.okupanel-qr img {
margin: 0;
width: 200px;
height: auto;
}

.okupanel-fullscreen .okupanel-qr {
display: block;
}

html.okupanel .okupanel-fullscreen .okupanel-footer {
font-size: 13px;
right: 200px;
    bottom: 34px;
}
.okupanel-qr-intro {
text-align: center;
margin-bottom: 13px;
}
.okupanel-qr-intro i.fa-mobile {
font-size: 32px;
position: relative;
top: 3px;
}
.okupanel-qr-intro i {
margin: 0 5px;
}

.okupanel-most-importants {
display: block;
text-align: left;
}
~~~~

Extra Javascript:
~~~~
jQuery(document).ready(function(){

  // rotate copyright once every 2 min 300 ms
  setInterval(function(){
    jQuery('.okupanel-header i.fa-copyright').addClass('okupanel_rotatebox');
    setTimeout(function(){
      jQuery('.okupanel-header i.fa-copyright').removeClass('okupanel_rotatebox');
    }, 2000);
  }, 120300);
			
  // pulse heart once every 20 s
  setInterval(function(){
    jQuery('.okupanel-header i.fa-heart').addClass('okupanel-pulse');
    setTimeout(function(){
      jQuery('.okupanel-header i.fa-heart').removeClass('okupanel-pulse');
    }, 800);
  }, 20000);

});
~~~~

Autodetected events:
~~~~
'#as[ea]mblea\s*general#ius Asamblea General
'#s[áa]bado\s*rojo#ius Sábado Rojo
~~~~

See [a live OkuPanel](https://ingobernable.net/okupanel/)!

OkuPanel, a project inited at the Ingoberlab, now maintained by the OkuTeam @ cDb.


== Screenshots ==
Desktop version of an OkuPanel
An event popup from the web version
A photo from a real OkuPanel entrance screen
Mobile version of an OkuPanel
