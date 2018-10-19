# Асинхронно програмиране

Програмите които пишем се изпълняват от процесора на компютъра. Но те много често взаимодействат и с други устройства (твърдия диск, мрежата) и тези взаимодействия отнемат време а процесора в този момент е неизползван.

## Асинхронност

В синхронното програмиране инструкциите се изпълняват последователно във времето и няма инструкции, които да се изпълняват паралелно една на друга.
```js
var res1 = Call(1)
var res2 = Call(2, res1)
var res3 = Call(3, res2)
var res4 = Call(4, res3)
var res5 = Call(5, res4)
// прави нещо с резултатите
```

В асинхронното програмиране много инструкции могат да се изпълняват паралелно (комуникация със сървъра, четене от твърдия диск), като програмата е уведомена когато действието завърши и може да получи резултатът от него.

![Callback hell](https://cdn-images-1.medium.com/max/1000/1*tR_X2VN31nM7GX_SEJynew.png)

В синхронното програмиране също има начин за изпълнение на паралелни процеси - това става чрез създаване на нови процесорни нишки (threads), ползвайки някое от свободните процесорни ядра.

![](http://eloquentjavascript.net/img/control-io.svg)

## Обещания (Promises)

Обещанието е асинхронен процес, който може да завърши в бъдещето и да върне някаква стойност, като при това ще оповести всички заинтересувани.
```js
let fifteen = Promise.resolve(15);
fifteen.then(value => console.log(`Got ${value}`));
// → Got 15
```

```js
let q = new Promise((resolve, reject) => {
  call(1, res => {
  	resolve(res)
  }, err => {
  	reject(err)
  })
}, q1=...,

q.then((res) => {...}, (err) => {...})
.catch((err) => {...})

Promise.all([q,q1,q2...])
.then(result => {...})
```

## Async/Await

```js
async function f() {

  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("done!"), 1000)
  });

  let result = await promise; // wait till the promise resolves (*)

  alert(result); // "done!"
}

f();
```

```js
async function showAvatar() {

  // read our JSON
  let response = await fetch('/article/promise-chaining/user.json');
  let user = await response.json();

  // read github user
  let githubResponse = await fetch(`https://api.github.com/users/${user.name}`);
  let githubUser = await githubResponse.json();

  // show the avatar
  let img = document.createElement('img');
  img.src = githubUser.avatar_url;
  img.className = "promise-avatar-example";
  document.body.append(img);

  // wait 3 seconds
  await new Promise((resolve, reject) => setTimeout(resolve, 3000));

  img.remove();

  return githubUser;
}

showAvatar();
```

### Errors
```js
async function f() {

  try {
    let response = await fetch('/no-user-here');
    let user = await response.json();
  } catch(err) {
    // catches errors both in fetch and response.json
    alert(err);
  }
}

f();

async function f() {
  let response = await fetch('http://no-such-url');
}

// f() becomes a rejected promise
f().catch(alert); // TypeError: failed to fetch // (*)
```

## Библиотеки за Ajax заявки

### Fetch
```js 
fetch('https://www.example.com', {
        method: 'get'
    })
    .then(response => response.json())
    .then(jsonData => console.log(jsonData))
    .catch(err => {
            //error block
        }
```

### Axios
Най-пълната библиотека. Поддържа глобални настройки, прихващане на заявките и повторно изпълнение. Базирана е на XMLHttpRequests.

```js
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```js
// Add a request interceptor
axios.interceptors.request.use(function (config) {
    // Do something before request is sent
    return config;
  }, function (error) {
    // Do something with request error
    return Promise.reject(error);
  });

// Add a response interceptor
axios.interceptors.response.use(function (response) {
    // Do something with response data
    return response;
  }, function (error) {
    // Do something with response error
    return Promise.reject(error);
  });
```

### jQuery

```js
$.ajax({
  url: '/users',
  type: "GET",
  dataType: "json",
  success: function (data) {
      console.log(data);
  }
  fail: function () {
      console.log("Encountered an error")
  }
});
```

## Научи повече
- [Asynchronous Programming](http://eloquentjavascript.net/11_async.html)
- [Asynchronous JavaScript: From Callback Hell to Async and Await](https://blog.hellojs.org/asynchronous-javascript-from-callback-hell-to-async-and-await-9b9ceb63c8e8)
- [Async/await](https://javascript.info/async-await)
- [Top JavaScript Libraries for Making AJAX Calls](https://dzone.com/articles/top-javascript-libraries-for-making-ajax-calls)
- [axios](https://github.com/axios/axios)
- [JavaScript ES 2017: Learn Async/Await by Example](https://codeburst.io/javascript-es-2017-learn-async-await-by-example-48acc58bad65)