JavaScript Dynamic Form Validation
==================================

JavaScript Dynamic form validation using backbone.js

[Phone Number](#phone-number)  
[Social Security](#social-security)  


###Phone Number

#####Event

```javascript

//important use on input so it will catch user input before it is displayed!!
events:{
   'input input[name=phone]': 'checkPhoneInput'
}

```

#####Logic

Use this if you want to format the input as the user enters the 10th digit

```javascript
checkPhoneInput: function(evt) {
//Checking at end
   var val = evt.target.value.replace(/\D/g, '');

   if(val.length==11){
      val = val.substr(0, val.length-1);
   }

   val = val.replace(/^(\d{3})(\d{3})(\d{4})$/, "($1) $2-$3", val);

   evt.target.value = val;
}
```
Use this to format as the user enters each number

```javascript
checkPhoneInput: function(evt) {
// Checking as user types
   var val = evt.target.value.replace(/\D/g, '');
   var newVal = '';
   if((val.length > 3) && (val.length <= 6)) {
      newVal += '(' + val.substr(0, 3) + ') ';
      val = val.substr(3);
   }
   if (val.length > 6) {
      newVal +=  '(' + val.substr(0, 3) + ') ';
      newVal += val.substr(3, 3) + '-';
      val = val.substr(6);
      if(val.length > 4){
         val = val.substr(0, val.length - 1);
      }
   }
   newVal += val;
   evt.target.value = newVal;
}
```

###Social Security 

#####Event

```javascript

//important use on input so it will catch user input before it is displayed!!
events:{
   'input input[name=phone]': 'checkSSInput'
}

```

#####Logic

Use this if you want to format the input as the user enters the 10th digit

```javascript
checkSSInput: function(evt) {
   //Checking at end
    var val = evt.target.value.replace(/\D/g, '');
    if(val.length==10){
      val = val.substr(0, val.length-1);
    }
    val = val.replace(/^(\d{3})(\d{2})(\d{4})$/, "$1-$2-$3", val);

    evt.target.value = val;
}
```
Use this to format as the user enters each number

```javascript
checkSSInput: function(evt) {
   //Checking as user types
   var val = evt.target.value.replace(/\D/g, '');
   var newVal = '';
   if((val.length > 3)&&(val.length<6)) {
      newVal += val.substr(0, 3) + '-';
      val = val.substr(3);
   }
   if (val.length > 5) {
   newVal += val.substr(0, 3) + '-';
   newVal += val.substr(3, 2) + '-';
   val = val.substr(5);
      if(val.length > 4){
         val = val.substr(0, val.length - 1);
      }
   }
   newVal += val;
   evt.target.value = newVal;
}
    
```
