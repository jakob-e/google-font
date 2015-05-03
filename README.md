Google Font SCSS Mixin
==========


<pre>
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
