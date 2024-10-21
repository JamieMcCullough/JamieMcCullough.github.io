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
  image: research_widget.png
  text: 'Weak gravitational lensing makes use of millions of galaxies to probe the largest structures in our universe. With spectroscopic and imaging surveys we can gain a high resolution picture of galaxies in the cosmic web.'
widget2:
  title: "Visualizations"
  url: '/visualization/figures/'
  text: 'I have created a number of tools and figures to explain astrophysical phenomena that instructors, scientists, and students alike are welcome to use in any format.'
  image: hubble_deep_stronglens.gif
widget3:
  title: "Play with the data"
  url: '/data/'
  image: data_widget.jpg
  text: 'Are you a researcher? Find some of the <strong>publicly available data</strong> related to my papers here and engage with it <strong>interactively</strong>.'
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
  url: '/contact/'
  text: Contact me about science or outreach ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---
