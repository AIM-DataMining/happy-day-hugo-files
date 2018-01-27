+++
title = "Web API Reference"
weight = 20
+++

### GET `/`
Gibt den String `Hello World!\n` zurück.

### GET `/images/`
lists all images in dir.

### GET `/images/<sentiment>`
lists all images in dir `<sentiment>` only "sad" and "smile" are available

### GET `/self-test/<sentiment>`
tests models with predefined image. `<sentiment>` can be one of:
- sad
- smile
- neutral

### POST `/test/`
receives a file and moves it to webdav destination, and later for testing

### POST `/self-test/<sentiment>`
performs a test prediction with a image from the given sentiment (`sad`, `smile`, `neutral`)

### POST `/train/<sentiment>`
receives a file and moves it to webdav destination, and later for training
One of: (`sad`, `smile`, `sleep`, `kiss`, `neutral`, `angry`, `surprised`)
Then it gets uploaded to the specified remote webdav. In our case https://schrolm.de

### POST `/retrain/<sentiment>`
NOT YET IMPLEMENTED, empty endpoint. Returns always `{"ok": true}`
retrains a file for given sentiment (sad or smile)
