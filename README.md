# Tianchang Wang's Personal Website

> Author: Tianchang Wang
>
> Course Link: https://johnguerra.co/classes/webDevelopment_fall_2022/ 
>
> The **design document** is available [here](./docs/design.pdf).

The page is hosted on [https://chang2000.github.io](https://chang2000.github.io) via Github Pages.

Check out this video for a demo of the website: [](https://chang2000.github.io)

Find the presentation slides [here](https://docs.google.com/presentation/d/11oOmDFVqwDcXtJvD0wh2XzJlfMwOaHeyypQoMSOWABE/edit?usp=sharing)

This website **PASSES** W3C validator without errors or warning.

## Project Objective

This personal website is designed as a bridge between me and my potential clients and employers. My skills are listed and are supported by my past experiences. My personal information is also provided for a easier reach out of my potential clients and employers. A secret collection/gallery tab is also provided for inspiration and entertainment.

## Thumbnails

- Hero section with animation: ![hero-animation](./docs/hero-section.gif)

- About section ![about-section](./docs/about-view.png) Click the email icon to email me directly! Your email client will be raised automatically. ![mail-me](./docs/mail-to-me.gif) Important content are being marked with custom marker pen effect: ![marker-pen](./docs/markerpen-effect.gif)
- Resume section ![resume-section](./docs/resume-view.png)
- Contact section ![contact-section](./docs/contact-view.png)
- The Collection Gallery ![galley-section](./docs/gallery-view.png) Hover over gallery images to see comment: ![galley-section-hover](./docs/gallery-hover.gif) Click on the image to enter the gallery. ![galley-section-hover](./docs/gallery.gif)

## Build

This Project is development under node version `18.9.0`. It's recommended to use a **nodejs version manager**.

This project is requires a basic node envrionment. Bootstrap and all other related scripts are provided in the `vendor` folder. To develop with this project, you need install `eslint`,`prettier` and `sass` via `npm` accorading to the following instructions. 

1. Clone the project to your local computer.
2. Use `npm install` to install related development dependencies.
3. Use `npm run sass` while developing to keep css file updated.
4. Use `npm run build` to build the whole project.
4. To host this website, setup the root directory to `.` is alright, where the `index.html` resides.

You may also download a release of this project here: [https://github.com/chang2000/chang2000.github.io/releases](https://github.com/chang2000/chang2000.github.io/releases)

## MISC

This website is based on this template https://bootstrapmade.com/free-html-bootstrap-template-lonely/.
