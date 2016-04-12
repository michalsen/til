**Form Submission**

This really is a 4 mile trip for a 1/2 mile journey, but I wanted to play
with several ideas, such as populating a form with previous entered data,
and posting that data cleanly by base64_encoding() it.

There are multiple libraries out there that handle this, and there provides
very little in terms of integration.

I have also been up since 430am w/o coffee...so I may just delete this by
this afternoon.

Form Submission Check / Server Side Validation
```php
      $error = 0;
      foreach($_POST as $key => $value) {
          if ($key == 'website' && strlen($value) > 0) {
            die();
          }
          $data .= $key . '=' . $value . '::';
          if ($key == 'name' && strlen($value) < 1) {
            $error++;
            }
          if ($key == 'email' && strlen($value) < 1) {
            $error++;
            }
          if ($key == 'phone' && strlen($value) < 1) {
            $error++;
            }
        }
```

Just a simple validation to ensure there is content in the form
If not let us send it back to the form
```php
  if ($error > 0) {
    $formData = base64_encode($data);
    $path  = $_SERVER['HTTP_REFERER'] . '?formdata=';
    $path .= $formData;
    header('location: ' . $path);
  }
```

This is where the fun begins:
The first thing we do is grab that $formdata and clean it.
If not, and the user submits several times, the variable will just build on
itself.
```php
   foreach ($_REQUEST as $key => $value) {
     if ($key == 'formdata') {
       $fd = explode('formdata=', $value);
       $lastEl = array_pop((array_slice($fd, -1)));
     }
   }
```

```php
  $page = explode('/', $_SERVER['SCRIPT_NAME']);
  $formData = base64_decode($lastEl);
  $data = explode('::', $formData);

  foreach ($data as $key => $value) {
    $row = explode('=', $value);
    if ($row[0] == 'name') $name = $row[1];
    if ($row[0] == 'email') $email = $row[1];
    if ($row[0] == 'phone') $phone = $row[1];
    if ($row[0] == 'message') $message = $row[1];
  }
```
