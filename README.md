This is the source for https://darijasart.com and https://darijasart.github.io. It is built using the template engine [Hugo](https://gohugo.io).

## Making and checking changes locally

1. [Install Hugo](https://gohugo.io/getting-started/installing/)
2. git clone https://github.com/darijasart/darijasart.github.io
3. Open a terminal in `darijasart.github.io` directory
4. Run `hugo server`
5. Open a web browser to http://localhost:1313
6. Change the files under `./content`, for example add a new directory with `index.en.md`, `index.no.md` and a picture under `content/gallery/location-norway/` 
7. The web browser will automatically update with the changes
8. When you commit and push the changes to github, GitHub Actions will automatically build and publish the website

## A brief tour

* `/content`: This contains the text and images for the website
    * `/content/events`: Exhibitions where the art has been displayed. Each page must explicitly refer to images
    * `/content/gallery`: Lists all the works in the collections (`location-lithuania`, `location-norway`, `portraits` and `simply-human`) grouped by collection. The `weight` in the `index.no.md` file of a collection will determine which order they are listed. Each work is in a separate directory with `index.en.md` containing the English title, `index.no.md` containing the Norwegian title and the artwork image. Cropped thumbnails are automatically created
    * `/content/projects`: Lists the summary and featured image from each collection. `_index.no.html` contains description of works in the `gallery` in addition to the automatically listed projects
* `/config.toml`: Describes the title of the website, the available languages and which theme is active
* `/themes/darijasart`: The HTML and CSS structure to create the look of the pages
    * `/themes/darijasart/static/style.css` contains the single CSS-files used for all pages
    * `/themes/darijasart/layouts/_default/baseof.html` contains the total layout of the pages. The content of the page is left to be rendered by specific layouts
    * `/themes/darijasart/layouts/_default/list.html` used to render "sections" - that is directories with a `_index.no.md` file
    * `/themes/darijasart/layouts/_default/single.html` used to render "pages" - that is directories with a `index.no.md` file
* `/layouts/events/single.html`: Override of `/themes/darijasart/layouts/_default/single.html` used for `/content/events`
* `/layouts/gallery/single.html`: Override of `/themes/darijasart/layouts/_default/single.html` used for `/content/gallery`. Shows the title and single image of a work in the gallery
* `/layouts/gallery/list.html`: Override of `/themes/darijasart/layouts/_default/list.html` used for `/content/gallery`. Groups collections in the gallery and shows a thumbnail and title for each work
* `/layouts/projects/list.html`: Override of `/themes/darijasart/layouts/_default/list.html` used for `/content/projects`. Shows the featured picture for each project along with the project title and summary

## Status

### What is done

* Converted existing galleries with 32 works of art into the new structure
* Converted three projects
* Converted five events
* Created templates to more or less replicate the layout
* Started on a responsive UI

### What will be done

* Requested adjustments to the stylesheet and corresponding changes to `baseof.html`
* Fix of typos and bugs
* Conversion of pen series into a gallery

### What is possible

* A new theme with custom layout, perhaps responsive title and menus
  * NB: The multi-colored menu is difficult to replicate with Hugo
* Professional pages and portfolio similar to gallery
* It is possible to publish a blog on Hugo, but it may not be worth the effort to convert
