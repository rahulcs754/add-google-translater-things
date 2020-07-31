# add-google-translater-things
some important thing about google translater


#how to disable google translate original text tooltips
```css

.goog-tooltip {
    display: none !important;
}
.goog-tooltip:hover {
    display: none !important;
}
.goog-text-highlight {
    background-color: transparent !important;
    border: none !important; 
    box-shadow: none !important;
}
```

# how top hide google translate top bar
```css
body{
   top:0px !important;
} 
body > .skiptranslate {
    display: none;
}

```

# if you don't want to update any thing by google tranlater then add this class 
```css
class = " notranslate "
```
