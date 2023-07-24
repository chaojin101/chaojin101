---
title: Web service worker
tags: ["web"]
---

This is a note for [MDN web service worker](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API). I will clarity some concepts and add some examples.

## Clarify `skipWaiting()` and `clients.claim()`

### `skipWaiting()`

`skipWaiting()` is used in the `install` event of service worker. It will force the service worker to be activated immediately, instead of waiting for all the pages controlled by the old version of the service worker to be closed.

MDN link: [`skipWaiting()`](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers#basic_architecture)

In Basic architecture section of the link above, at point 4, it says:

> 4 Once all pages controlled by the old version of the service worker have closed, it's safe to retire the old version, and the newly installed service worker receives an activate event. The primary use of activate is to clean up resources used in previous versions of the service worker. The new service worker can call `skipWaiting()` to ask to be activated immediately without waiting for open pages to be closed. The new service worker will then receive activate immediately, and will take over any open pages.

### `clients.claim()`

`clients.claim()` is used in the `activate` event of service worker. It will force the service worker to take control of all the pages under its scope, instead of waiting for the pages to be reloaded.

MDN link: [`clients.claim()`](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers#basic_architecture)

In Basic architecture section of the link above, at point 5, it says:

> 5 After activation, the service worker will now control pages, but only those that were opened after the register() is successful. In other words, documents will have to be reloaded to actually be controlled, because a document starts life with or without a service worker and maintains that for its lifetime. To override this default behavior and adopt open pages, a service worker can call clients.claim().

## Simple example

### `index.html`'s inline script

```js
const registerServiceWorker = async () => {
  if ("serviceWorker" in navigator) {
    try {
      const registration = await navigator.serviceWorker.register("sw.js");
    } catch (error) {
      console.warn(`Registration failed with ${error}`);
    }
  }
};

registerServiceWorker();
```

### sw.js

```js
const CACHE_NAME = "v1";
const addResourcesToCache = async (resources) => {
  const cache = await caches.open(CACHE_NAME);
  await cache.addAll(resources);
};

const putInCache = async (request, response) => {
  const cache = await caches.open(CACHE_NAME);
  await cache.put(request, response);
};

const cacheFirst = async (request) => {
  const responseFromCache = await caches.match(request);
  if (responseFromCache) {
    return responseFromCache;
  }

  // Next try to get the resource from the network
  try {
    const responseFromNetwork = await fetch(request.clone());
    putInCache(request, responseFromNetwork.clone());
    return responseFromNetwork;
  } catch (error) {
    // const fallbackResponse = await caches.match(fallbackUrl);
    // if (fallbackResponse) {
    //   return fallbackResponse;
    // }
    console.warn(error);
    return new Response("Network error happened", {
      status: 408,
      headers: { "Content-Type": "text/plain" },
    });
  }
};

const networkFirst = async (request) => {
  try {
    const response = await fetch(request.clone());
    putInCache(request, response.clone());
    return response;
  } catch (error) {
    const responseFromCache = await caches.match(request);
    if (responseFromCache) {
      return responseFromCache;
    }
    console.warn(error);
    return new Response("Network error happened", {
      status: 408,
      headers: { "Content-Type": "text/plain" },
    });
  }
};

self.addEventListener("install", (event) => {
  event.waitUntil(
    // TODO: add fallback resources
    addResourcesToCache(["./index.html"])
  );
  event.waitUntil(self.skipWaiting());
});

self.addEventListener("activate", (event) => {
  event.waitUntil(self.clients.claim());
});

self.addEventListener("fetch", (event) => {
  // request.destination is a string that indicates the type of content being requested.
  // below is the list of possible values
  // https://developer.mozilla.org/en-US/docs/Web/API/Request/destination
  const cacheFirstDestinations = ["document", "style", "script", "image"];
  const NetworkFirstDestinations = [];
  if (cacheFirstDestinations.includes(event.request.destination)) {
    event.respondWith(cacheFirst(event.request));
  } else if (NetworkFirstDestinations.includes(event.request.destination)) {
    event.respondWith(networkFirst(event.request));
  } else {
    // console.log(
    //   "Not sure how to handle this request:" + event.request.destination
    // );
    event.respondWith(fetch(event.request));
  }
});
```
