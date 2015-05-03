Google Font SCSS Mixin
==========
Google-font is intended to provide a simple structured way to import google fonts while doing font request optimization under the hood.

**Multi-use syntax**
<pre>
@import '_google-font.scss';
  // '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
  //        
  //  Import syntax:
  //        
  //  $name  :  Font name
  //  $weight:  Font weight 100 - 900 (default: 400)       
  //  $style :  Font style normal/italic/oblique (default: normal)               
  //  $subset:  Font subsets (quoted string or list)       
  //  $text  :  Limit request to these fonts (quoted string)        
  //        
  //  @include google-font($name, [$weight, $style, $subset, $text]);
  //         
  @include google-font(Lato, 300);
  @include google-font(Lato, 400, italic);        
  
  //  CSS output:
  //  @import url(http://fonts.googleapis.com/css?family=Lato:300);
  //  @import url(http://fonts.googleapis.com/css?family=Lato:400italic);        
          
          
          
  // '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
  //        
  //  Combine syntax: 
  //        
  //  @include google-font {
  //      @include google-font($name, [$weight, $style, $subset, $text]);
  //      @include google-font($name, [$weight, $style, $subset, $text]);
  //      ...
  //  } 
  //         
  @include google-font {
      @include google-font(Lato, 300);
      @include google-font(Lato, 400);    
      @include google-font(Open Sans, 300);
      @include google-font(Open Sans, 400);
      @include google-font(Open Sans, 800);        
      @include google-font(Open Sans, 300, italic);
      @include google-font('Marck Script', $text:'F');        
  }
          
  //  CSS output:
  //  Note! Marck Script is limited to specific characters why it is  
  //        excluded from the combined request.          
  //  @import url(http://fonts.googleapis.com/css?family=Marck+Script:400&text=F);
  //  @import url(http://fonts.googleapis.com/css?family=Lato:300,400|Open+Sans:300,400,800,300italic);


</pre>


**Subsets**

Though it is possible to define subsets in the mixin it is recommended to handle this globally using the $google-font-subset map
<pre>
// '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''        
//
//  Subsets (true = enabled)
//  Note! by default google will deliver a Latin font why you only
//  need to enable it if used in combination with another subset.
//    
$google-font-subsets: (
    'arabic'      :false
  , 'cyrillic'    :false
  , 'cyrillic-ext':false
  , 'devanagari'  :false
  , 'freek'       :false
  , 'greek-ext'   :false
  , 'hebrew'      :false
  , 'khmer'       :false
  , 'latin'       :false  
  , 'latin-ext'   :false
  , 'telugu'      :false
  , 'vietnamese'  :false
);    

    
</pre>

**Dependencies**

Google font will work with Ruby Sass 3.3+ (LibSass is on the to-do-list).

Google font does not require other imports – but as the list helper functions are shamelessly ripped from SassyLists by Hugo Giraudel it is recommeded you import the original. By importing [SassyLists](http://SassyLists.com) google-font will automatically switch to the real deal.


