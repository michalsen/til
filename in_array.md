There is a list of zipcodes:
```
13503
13504
13505
13599
01119
01120
01121
01122
01123
01124
01125
...
```

As you can see, some have leading zeros.

I have some jQuery watching a form:
If the zip code entered is in the list, a class is added.
If the zip code is then changed to one that is not on the list, the class is removed.

```javascript
$(document).ready(function($){
    $('#field-zip-value').on('blur', function() {
    var input = $(this);
    var zip = input.val();
    $.ajax({
          url: '../ajax/check_zip.php',
          type: 'post',
          data: {service_type: "zip", keys: zip},
           success: function(output) {
              var checkreturn = $(output);
              console.log(checkreturn.selector);
             if(checkreturn.selector == 'Yep'){
                  $('#field-zip-value').closest('.form-item')
                                                  .addClass("remote_charges");
                }
                 else {
                   $('#field-zip-value').closest('.form-item')
                                                   .removeClass("remote_charges");
                }
      }
    }); // end ajax call
  });
});
```

The checkzip.php
```php
if(isset($_REQUEST['keys'])) {
  $search = $_REQUEST['keys'];
  $matches = array();

  $string = file_get_contents($_SERVER['DOCUMENT_ROOT'] . "../zipcode.list");
  $string = explode("\n", $string);
  if(in_array($search, $string, true)) {
    echo "Yep";
      }
        else {
    echo "Nope";
  }
}
```
**It is the true in the in_array() that fixed the leading zero issue, as the zip codes
were being treated as integers instead of strings.**
