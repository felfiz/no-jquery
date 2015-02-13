## Ajax

- Post

```javascript
// jQuery
jQuery.ajax({
  type: 'POST',
  url: 'http://www.example.com',
  data: data
});

// Javascript puro
var request = new XMLHttpRequest();
request.open('POST', 'http://www.example.com', true);
request.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
request.send(data);
```

- Request
```javascript
// jQuery
jQuery.ajax({
  type: 'GET',
  url: 'http://www.example.com',
  success: function(data) {
    console.log(data)
  },
  error: function() {

  }
});

// Javascript puro
var request = new XMLHttpRequest();
request.open('GET', 'http://www.example.com');

request.onreadystatechange = function(){
    if (request.status === 200 && request.readyState === 4){
        console.log(request.responseText);
    }
};

request.send();
```

Atualmente, jQuery usa [xhr2](http://caniuse.com/#search=xhr2) com suporte a [FormData](https://developer.mozilla.org/en-US/docs/Web/API/FormData). Tem bastante workaround também relacionado à [compatibilidade](https://developer.mozilla.org/en-US/docs/Web/API/XMLHTTPRequest#Browser_Compatibility).

Exemplo: http://jsfiddle.net/renanmpimentel/us4tfokh/

- JSON
```javascript
// jQuery
jQuery.getJSON('http://www.example.com', function(data) {
    console.log(data);
});

// Javascript puro
var request = new XMLHttpRequest();
request.open('GET', 'http://www.example.com');

request.onreadystatechange = function(){
    if(request.status === 200 && request.readyState === 4){
        console.log(JSON.parse(request.responseText));
    }
};

request.send();
```

Exemplo: http://jsfiddle.net/renanmpimentel/8deopkjj/
