## What
This is a static website using Hugo Blox. Served at https://www.gillangeospatial.com. Domain is managed through Squarespace. 


## Editing Tips

### Superficial Customization

Editing Hugo Blox websites generally occur in yaml config files. It allows you to do minor customization. 

Edit home page `content/_index.md`

Edit other pages like 'about' `content/about`. To display images in pages like 'about', you need to place images in `static/media`. In the markdown file, you should use relative links as `/media/example_image.png`

Edit header menu `config/_default/menus.yaml` and `config/_default/params.yaml`

Edit footer `config/_default/params.yaml`


### Deeper Customization
The real code for the website is in html and css files that are not held in this repo. The html/css is held [Here](https://github.com/HugoBlox/hugo-blox-builder/tree/modules/blox-tailwind/v0.3.1/modules/blox-tailwind). To customize the html/css, you need to copy files from the remote repo into this repo. Then you need to change which template (remote or local) to point to within the yaml files. 

For example, I wanted to customize the header navbar. 

1. Copy the file `https://github.com/HugoBlox/hugo-blox-builder/tree/modules/blox-tailwind/v0.3.1/modules/blox-tailwind/layouts/partials/components/headers/navbar.html` to my local repo at `/layouts/partials/components/headers/my-navbar.html`

2. Within the `params.yaml` file, change `blox:navbar` to `blox:my-navbar`.
   
Some advice on customization is [here](https://docs.hugoblox.com/reference/extend/)

<br>
<br>

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




