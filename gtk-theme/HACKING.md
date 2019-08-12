## Summary

- Do not edit the CSS directly, edit the source SCSS files and run `make gtk3`
- To be able to use the latest/adequate version of Sass, install `sassc`
- To change the SVG assets color, use the recoloring script, and do not edit the
  svg.in files.

## How to tweak the theme

This theme is written and processed in Sass.

You can read about Sass at http://sass-lang.com/documentation/. Once you make
your changes to the SCSS files, run the `./parse-sass.sh` script to rebuild the
CSS files.

Here's a rundown of the stylesheets:

- `_variables.scss`

  variables to allow easier definition of widget sizing/styling.

- `_color-palette.scss`

  Color Palette definitions. This is where the base colors for the theme are
  defined, as well as any special overrides.

- `_colors.scss`

  global color definitions. We keep the number of defined colors to a necessary
  minimum. It covers both the light variant and the dark variant.

- `./gtk-widgets/`
  
  Provides the base theming for different GTK Widgets.

- `./granite-widgets/`
  
  Provides special theming for any supported Granite widgets.

- `./apps/`
  
  Any application-specific styling or style overrides

## How to change the GTK2 assets

The svg.in source files are converted to SVG by the `recolor-assets.sh` script,
and then are rendered out to PNG files when the theme is built from
source. You can manually trigger a rebuild by using the `make assets` command. 
This will cause inkscape to render out all of the PNG files, which will 
overwrite any existing files. 

Before rendering or building, all assets are color matched according to the 
`recolor-assets.sh` script. If you want to change the colors of the assets, that
is the correct place to do it. It's also good for basic stlye changes, like 
changing the border radius. 

If you want to modify the look/style of the assets, you can open them in 
inkscape or another vector graphics editor and modify them there. You may need 
to remove the `.in` extension from the end of the filename first. Be sure that 
you don't modify any `.svg` files or save your modifications as `.svg` without
adding the `.in` extension, as these files will be deleted when you rebuild the 
theme.

## Useful Links

#### GTK3 theme sources

- [GTK+ 4.0](https://github.com/GNOME/gtk/tree/master/gtk/theme/Adwaita)
  - [3.22](https://github.com/GNOME/gtk/tree/gtk-3-22/gtk/theme/Adwaita)
  - [3.20](https://github.com/GNOME/gtk/tree/gtk-3-20/gtk/theme/Adwaita)
  - [3.18](https://github.com/GNOME/gtk/tree/gtk-3-18/gtk/theme/Adwaita)
- [GTK+ 2](https://github.com/GNOME/gnome-themes-standard/tree/master/themes/Adwaita/gtk-2.0)
- [GNOME Shell](https://github.com/GNOME/gnome-shell/tree/master/data/theme)
  - [Sass sources](https://github.com/GNOME/gnome-shell-sass)

#### Tips

- [Unity/Theming](https://wiki.ubuntu.com/Unity/Theming)
- [The GTK+ Inspector](https://blog.gtk.org/2017/04/05/the-gtk-inspector/)
