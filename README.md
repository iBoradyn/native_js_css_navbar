# Native Sidebar
Responsive sidebar created with native js and css.

It contains 3 sections:
- Top section - small section with some basic info (e.g. user info)
- Middle section - main section containing scrollable nav list
- Bottom section - small section for e.g. logout button

## How to use
Create base html for your page with structure like in `side_navbar.html`.
If your sidebar will be without any sublist you can ignore `js/subNavList.js`

> NOTE: The example includes font awesome free icons that can be removed or replaced with other icons.

### Important components in nav list
#### Basic nav item
```html
<li class="nav-item">
   <a class="nav-link" href="#">
      <i class="fa-solid fa-home"></i>
      Link 1
   </a>
</li>
```

#### Nav item with sublist
```html
<li class="nav-item">
  <div class="dropdown">
    <a class="nav-link" href="#">
      <i class="fa-solid fa-file-circle-plus"></i>
      Link 3 with dropdown
    </a>
    <div class="sub-items-collapse-icon">
      <i class="fa-solid fa-arrow-down"></i>
      <!-- OR SIMPLE -->
      <div>&darr;</div>
    </div>
  </div>
  <ul id="id_sl_name_1" class="sub-nav-list">
    ...
  </ul>
</li>
```

#### Sublist item
```html
<li class="sub-item">
  <i class="fa-solid fa-leaf"></i>
  <a class="sub-link" href="#">
    Sub link 1
  </a>
</li>
```

### Activate link
To activate link use:
```html
<div id="active_nav_link_number" class="d-none">{{ nav_index }}</div>
```
Replace `{{ nav_index }}` with number of link counting from top and starting with 1.

### Activate sub link
To activate sub link use:

```html
<div id="active_sub_nav_link_selector" class="d-none">{{ sublist_id }},{{ sub_nav_index }}</div>
```
Replace `{{ sub_nav_index }}` with number of sub link counting from top and starting with 1.

Replace `{{ sublist_id }}` with id of sublist e.g.:
```html
<ul class="nav-list">
   ...
   <ul id="id_sl_name_1" class="sub-nav-list">
    ...
   </ul>
  ...
</ul>
<div id="active_sub_nav_link_selector" class="d-none">id_sl_name_1,1</div>
```

## SASS File Watcher config (PyCharm)
SCSS files located in scss directory are compiled into CSS files with the same filename in css directory.
> NOTE: The files are created directly in the `css` directory even if the source files are in a subdirectory.

1. File > Settings > Tools > File Watchers > Add('+') > SCSS
2. Scope: '...' > Add scope('+') > Local
   - Select scss directory and click 'Include Recursively'
   - Click 'Apply' and 'OK'
3. Program: Path to sass
4. Arguments: ```--no-cache --update $FileName$:$ProjectFileDir$/css/$FileNameWithoutExtension$.min.css --style compressed```
5. Output paths to refresh: ```../css/$FileNameWithoutExtension$.min.css:../css/$FileNameWithoutExtension$.min.css.map```
6. OK > Apply > OK


## Project structure
```
native_js_css_sidebar
│ README.md
│ side_navbar.html
├───css
│   └───sidebar.min.css
├───js
│   ├───sidebar.js
│   └───subNavList.js
└───scss
    └───sidebar.scss
```