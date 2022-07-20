# CyberTalents - Secure Coding

## Challenge Name

 [*PHPbase*](https://cybertalents.com/challenges/secure-coding/phpbase)

## Challenge Description

Can you fix this vulnerable code?

## Vulnerable code

```html
<!DOCTYPE html>
<html lang="en">

<head>

  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <meta name="description" content="">
  <meta name="author" content="">

  <title>Blog</title>

  <!-- Bootstrap core CSS -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

</head>

<body>

  <!-- Navigation -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark static-top">
    <div class="container">
      <a class="navbar-brand" href="#">Blog</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarResponsive">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <a class="nav-link" href="?file=home">Home
              <span class="sr-only">(current)</span>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="?file=about">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="?file=services">Services</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="?file=contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Page Content -->
<!--   <div class="container"> -->
    <?php
	  include "utils.php";
          $file = function1($_GET["file"]);
          if(preg_match("/^\s*\/|^\s*http:\/\/|^.*?\.\..*?$/", $file)){echo "<center><h3>HOME</h3></center>";}
          if(preg_match("/^\s*\/|^\s*php:\/\/|^.*?\.\..*?$/", $file)){echo "<center><h3>HOME</h3></center>";}
          if(!empty($file)){
            if(!preg_match("/^\s*\/|^\s*file:\/\/|^.*?\.\..*?$/", $file)){
              $page =  file_get_contents($file);
              if($page){
                echo $page;
              }else{
                echo "<center><h3>HOME</h3></center>";
              }

            }
          }else {
            echo file_get_contents("home");
          }
          ?>
<!--           </div> -->

<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>

</body>

</html>
```

## Solution

To fix the vulnerable code we need to perform some code review techniques first, to find out the vulnerability then think about the mitigation process.

First try to find out if there is any user input that is used in file inclusion, os command execution, or database query creation, where you will notice that there is a navigator containing the blog pages' links each send a get request has "*file=PAGE_NAME*" parameter that considers as a shred of evidence tells us that there is a file inclusion logic executes for this page.

![navigator-links](./img/navigator-links.png)


Moving a little bit down, we can find the php code for the file inclusion logic, the function that we will implement to correctly filter the user input, and also you can notice that the developer has already implemented some validation on the user input!

![php-inclusion-code](./img/php-inclusion-code.png)


The developer used *preg_match* to validate that the malicious user will not be able to user wrapper, but he forgot about that this regex expression will only filter the lower case version of "http/php/file" wrappers :)

```php
preg_match("/^\s*\/|^\s*http:\/\/|^.*?\.\..*?$/", $file)
preg_match("/^\s*\/|^\s*php:\/\/|^.*?\.\..*?$/", $file)
!preg_match("/^\s*\/|^\s*file:\/\/|^.*?\.\..*?$/", $file)
```

Now, we know that the code is vulnerable to **LFI/RFI** so let's start implementing a secure filter to mitigate the risks. And as we here know exactly that there are only 4 pages allowed for file inclusion, the best solution is to compare the user input to a list of allowed file names

> Note 1: the allowed pages are: ["home", "about", "services", "contact"] (you can get them from the HTML nav-link tags)

```php
<?php
    function function1($data) {
        $allowed_pages = ['home', 'about', 'services', 'contact'];

        if (in_array($data, $allowed_pages, true)) {
            return $data;
        }
        return 'home';
    }
```

> Note 2: the third argument of *in_array* enables the strict comparison (===), so always stick on enabling this feature to prevent the type juggling risks.

Now, we have a secure user input filter that will fix this vulnerable code :)

### The Flag

 > FLAG{PHP*******************som3times}
