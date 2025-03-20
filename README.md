## What
This is a static website using Hugo Blox. Served at https://www.gillangeospatial.com


## Editing Tips

Editing Hugo Blox websites generally occur in yaml config files. It allows you to do minor customization. The real code for the website is in html and css files that are not held in this repo. The html/css is held [Here](https://github.com/HugoBlox/hugo-blox-builder/tree/modules/blox-tailwind/v0.3.1/modules/blox-tailwind). To customize the html/css, you need to copy files from the remote repo into this repo. Then you need to change which template (remote or local) to point to within the yaml files. For example, I wanted to customize the header navbar. The limited customization options are in local yamls `config/_default/menus.yaml` and `config/_default/params.yaml`. For more customization, I needed to copy the file `https://github.com/HugoBlox/hugo-blox-builder/tree/modules/blox-tailwind/v0.3.1/modules/blox-tailwind/layouts/partials/components/headers/navbar.html` to my local repo at `/layouts/partials/components/headers/my-navbar.html`

Edit home page `content/_index.md`

Edit header menu `config/_default/menus.yaml` and `config/_default/params.yaml`

Edit footer `config/_default/params.yaml`





## Make Changes Locally
You get edit this website by cloning it to your local machine
`git clone git@github.com:jeffgillan/gillan_geospatial_website.git`

## Install hugo
For macOS
`brew install hugo`

## Install Go
For macOS
`brew install go`

`git submodule update --init --recursive`

`hugo server -D`

The website is served at `localhost:1313`




