---
layout: post
title: "CakePHP, preflight & CORS"
date: 2018-02-15 18:15:00 +0100
---

Today I have faced a problem with CakePHP backend. It was related to preflight `OPTIONS` request made to the app from frontend.

I have received few kinds of errors from my Cake backend depending on how I configured [cakephp-cors](https://github.com/ozee31/cakephp-cors) including `404 not found` (for preflight request).

The first mistake I made was not creating route for the `OPTIONS` method. My whole scope contained one line and looked like `$routes->post('/endpoint', ['controller' => 'MyController', 'action' => 'my_action'])`. Solution was to add another line so the `Router::scope` looks like:

``` PHP
Router::scope('/', function (RouteBuilder $routes) {
    $routes->options('/endpoint', []);
    $routes->post('/endpoint', ['controller' => 'MyController', 'action' => 'my_action']);
});
```

Next thing to do was to sent appropriate headers just for `OPTIONS` requests. In `AppController` I have created `beforeFilter` hook looking like this:

```
public function beforeFilter(Event $event) {
  if($this->request->is('options')) {
    return $this->response
      ->header('Access-Control-Allow-Origin', '*')
      ->header('Access-Control-Allow-Methods', 'GET, POST')
      ->header('Access-Control-Allow-Headers','Content-Type')
      ->withStatus(200);
  }
}
```

I tried using new Cake's [Cors Builder](https://api.cakephp.org/3.2/class-Cake.Network.CorsBuilder.html) unfortunately without success.

Hope you find this useful - I'll surely use this for reference in future. :)

Cheers!
