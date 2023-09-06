---
title: Migrating from Request library
feed: show
tags: javascript nodejs
date: 06-09-2023
updated: 06-09-2023
type: note
growth: seedlings
---

### Context 

The library for NodeJS `request` is [deprecated since 2019](https://github.com/request/request/issues/3142) but it's still being used by a lot of [my own libraries](https://github.com/Gorzas/spotify-playlist).

There's the needing to migrate from request to the most updated libraries or maybe use the standard library itself with the latest NodeJS versions.

### Solution

Taking this code as an example from [Spotify playlist](https://github.com/Gorzas/spotify-playlist)

```
function getTracks() {
  return new Promise((resolve /*, reject */) => {
    request.post(auth_options, async function (err, resp, body) {
      if (!err && resp.statusCode === 200) {
        ...

        resolve(body.items);
      }
    });
  });
}
```

A proposal to migrate could be:

```
async function getAllTracks() {
  const items = [];

  try {
    const response = await fetch(
      url,
      auth_options
    );

    ...
  } catch (e) {
    console.error('There was an error when connecting with the API\n');
    console.error(e);
  }

  return items;
}
```


### References

### TODO
