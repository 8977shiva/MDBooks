# SASS

- It is an extension to CSS that can help us write more flexible styles.

- Use variables,functions,conditional statements and more..

- Split our SASS files up into modules, making it easier to keep on top of CSS for large Projects.

- When we write in SASS, browsers will not understand our code.

- It needs to be translated into  CSS

- SASS is written in Ruby

  ## Download 

   https://prepros.io/downloads  link for the  sass complier  application.

  ## Variables

  ```scss
  $variablesName
  $deepBlue :#032f3e   // saving color
  
  //we can save fontsize
      section h1{
          font-size:24px;
          color:$deepBlue
  }
  ```

  ## Nesting styles

  ```
  $deepBlue :#032f3e;
  
  #main-nav {
      background: $deepBlue;
  
      ul {
          width: 100%;
      }
  
      li {
          float: left;
          width: 14%
      }
  
      a {
          color: #f8f9fb;
          text-decoration: none;
          padding: 16px;
          display: block;
          text-align: center
      }
  
  }
  
  //clear fix
  #main-nav ul:after {
      content: "";
      display: block;
      clear: both;
  }
  ```

  ## Mixins 

```scss
$bannerHeading:46px;

@mixin banner {
    width: 100%;
    position: relative;
    color: white;

    .banner-content {
        position: absolute;
        top: 50px;
        width: 100%;
    }

    img {
        width: 100%
    }

    span {
        font-size: $bannerHeading;
        display: block;
        text-transform: uppercase;
        font-weight: bold;
    }

    span.title {
        font-weight: normal;
        margin-bottom: 30px
    }
}

.lead-banner {
    @include banner;
    text-align: right;

}

.lessons-banner {
    @include banner;

    li {
        text-transform: uppercase;
        font-size: 20px;
        max-width: 500px;
        margin:60px 0;
    }
}
```





## importing

```
@import "reset";
@import "variables"

```





## Pseudo Classes

in normal CSS we  would use 

```scss
#main-nav a:hover{
  background:#333;
}
&:hover{
background:#333;
}
// move  the  clearfix to    ul &
```





## Math ope

 in use  +,- ,/,

```scss
li{
 width:(100/6)
}


#services{
 margin-bootm:60px;
 li{
	float:left;
	box-align:border-box;
	text-align:center;
	width:(100%/3);
}
img{
	width:60%;
    margin:20px 20px;
}
    a{
	   text-decoration:none;
        color:$deepBlue;
        font-weight:bold;
        &:hover{
            color:red;
        }
}
    ul{
        
    }
}
```

   

grid using math

in mixins

```
@mixins grid($cols,$mgn){
	float:left
	margin-right:$mgn;
	margin-bottom:$mgn;
	width:((100%-(($cols-1)*$mgn))/$cols);
	&:nth-child({$cols}n){
		margin-right:0;
}
	
}
```

