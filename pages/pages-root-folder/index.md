---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: rubin.jpeg
  #caption: Image credit: Rubin Observatory/NSF/AURA/B. Quint

widget1:
  title: "Research"
  url: '/research/'
  image: widget-1-302x182.jpg
  text: 'Weak gravitational lensing makes use of millions of galaxies to probe the largest structures in our universe. With spectroscopic and imaging surveys we can gain a high resolution picture of galaxies in the cosmic web.'
widget2:
  title: "Visualizations"
  url: '/visualization/figures/'
  text: 'I have created a number of didactic figures to explain astrophysical phenomena that scientists and students alike are welcome to use in any context.'
  video: '<a href="#" data-reveal-id="videoModal"><img src="http://phlow.github.io/feeling-responsive/images/start-video-feeling-responsive-302x182.jpg" width="302" height="182" alt=""/></a>'
widget3:
  title: "Play with the data"
  url: '/data/'
  image: widget-github-303x182.jpg
  text: 'Are you a researcher? Find some of the publicly available data related to my papers.'
#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
callforaction:
  url: https://tinyletter.com/feeling-responsive
  text: Inform me about new updates and features ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---
