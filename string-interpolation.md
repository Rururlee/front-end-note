#String Interpolation

```css
@mixin photo-content($file) {
  content: url(#{$file}.jpg); 
  object-fit: cover;
}

.photo {
        @include photo-content('titanosaur');
        width: 60%;
        margin: 0px auto;  
 }

 /*css*/
 .photo { 
  content: url(titanosaur.jpg);
  width: 60%;
  margin: 0px auto; 
}
```