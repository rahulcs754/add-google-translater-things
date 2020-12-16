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


# html code 
```html
    <!-- start google translater -->
	<div id="google_translate_element" style="display:none"></div>
	
	<!-- end google translater -->
	<li class="nav-item dropdown no-arrow mx-1">
	    <a  class="nav-link text-light" href="javascript:void(0)" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"><span ><img src="<?= base_url(); ?>assets/favi/uk.png" id="langflag" width="16" height="16"></span></a>
		<ul class="dropdown-menu user-drop translation-links" id="myflag" style="padding:.5rem 0.7em !important; min-width:0em !important;"> 
			<li style="width:60px;" onclick="flagchange(this)" id="sp" data-lang="Spanish"><a href="?lang=es" rel="es" class="spa notranslate" data-lang="Spanish"><img src="<?= base_url(); ?>assets/favi/spain.png" width="16" height="16"></a></li>
			<li style="width:60px;" onclick="flagchange(this)" id="uk" data-lang="English"><a href="?lang=en" rel="en" class="eng notranslate" data-lang="English"><img src="<?= base_url(); ?>assets/favi/uk.png" width="16" height="16"></a></li>
		</ul> 
	</li>

```


# js code 
```js


 function googleTranslateElementInit() {
    new google.translate.TranslateElement({autoDisplay: true}, 'google_translate_element'); //remove the layout
  }
  
   function triggerHtmlEvent(element, eventName) {
		console.log(element);  
var event;
if(document.createEvent) {
    event = document.createEvent('HTMLEvents');
    event.initEvent(eventName, true, true);
    element.dispatchEvent(event);
} else {
    event = document.createEventObject();
    event.eventType = eventName;
    element.fireEvent('on' + event.eventType, event);
}
}

 <!-- Flag click handler -->
$('.translation-links a').click(function(e) {
  e.preventDefault();
  var lang = $(this).data('lang');
  $('#google_translate_element select option').each(function(){
    if($(this).text().indexOf(lang) > -1) {
        $(this).parent().val($(this).val());
        var container = document.getElementById('google_translate_element');
        var select = container.getElementsByTagName('select')[0];
        triggerHtmlEvent(select, 'change');
    }
});
}); 


 function flagchange(elem){
	var id = $(elem).attr('id');
	let datalang = $(elem).attr('data-lang');
	
	localStorage.setItem("flag",id);
	$spurl = "<?= base_url(); ?>assets/favi/spain.png";
	$ukurl = "<?= base_url(); ?>assets/favi/uk.png";
	
	if(localStorage.getItem("flag") == 'sp'){
		  $('#langflag').attr('src',$spurl);		
    }else{
		 $('#langflag').attr('src',$ukurl);
	}

} 


if(localStorage.getItem("flag")){
$spurl = "<?= base_url(); ?>assets/favi/spain.png";
	$ukurl = "<?= base_url(); ?>assets/favi/uk.png";
	if(localStorage.getItem("flag") == 'sp'){
	
		$('#langflag').attr('src',$spurl);
	}else{
		$('#langflag').attr('src',$ukurl);
	}
	
}	
```

