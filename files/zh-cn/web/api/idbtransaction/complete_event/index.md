---
title: 'IDBTransaction: complete event'
slug: Web/API/IDBTransaction/complete_event
---

{{APIRef("IndexedDB")}}

The `complete` handler is executed when a transaction successfully completed.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Bubbles</th>
      <td>No</td>
    </tr>
    <tr>
      <th scope="row">Cancelable</th>
      <td>No</td>
    </tr>
    <tr>
      <th scope="row">Interface</th>
      <td>{{DOMxRef("Event")}}</td>
    </tr>
    <tr>
      <th scope="row">Event handler property</th>
      <td>
        {{DOMxRef("IDBTransaction.oncomplete", "oncomplete")}}
      </td>
    </tr>
  </tbody>
</table>

## Examples

Using {{DOMxRef("EventTarget.addEventListener", "addEventListener()")}}:

```js
// Open the database
const DBOpenRequest = window.indexedDB.open('toDoList', 4);

DBOpenRequest.onupgradeneeded = event => {
  const db = event.target.result;

  db.onerror = () => {
    console.log('Error creating database');
  };

  // Create an objectStore for this database
  var objectStore = db.createObjectStore('toDoList', { keyPath: 'taskTitle' });

  // define what data items the objectStore will contain
  objectStore.createIndex('hours', 'hours', { unique: false });
  objectStore.createIndex('minutes', 'minutes', { unique: false });
  objectStore.createIndex('day', 'day', { unique: false });
  objectStore.createIndex('month', 'month', { unique: false });
  objectStore.createIndex('year', 'year', { unique: false });
};

DBOpenRequest.onsuccess = event => {
  const db = DBOpenRequest.result;

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(['toDoList'], 'readwrite');

  // add a listener for `complete`
  transaction.addEventListener('complete', event => {
    console.log('Transaction was competed');
  });

  const objectStore = transaction.objectStore('toDoList');
  const newItem = { taskTitle: 'my task', hours: 10, minutes: 10, day: 10, month: 'January', year: 2019 };
  const objectStoreRequest = objectStore.add(newItem);
};
```

Using the {{DOMxRef("IDBTransaction.oncomplete", "oncomplete")}} property:

```js
// Open the database
const DBOpenRequest = window.indexedDB.open('toDoList', 4);

DBOpenRequest.onupgradeneeded = event => {
  const db = event.target.result;

  db.onerror = () => {
    console.log('Error creating database');
  };

  // Create an objectStore for this database
  var objectStore = db.createObjectStore('toDoList', { keyPath: 'taskTitle' });

  // define what data items the objectStore will contain
  objectStore.createIndex('hours', 'hours', { unique: false });
  objectStore.createIndex('minutes', 'minutes', { unique: false });
  objectStore.createIndex('day', 'day', { unique: false });
  objectStore.createIndex('month', 'month', { unique: false });
  objectStore.createIndex('year', 'year', { unique: false });
};

DBOpenRequest.onsuccess = event => {
  const db = DBOpenRequest.result;

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(['toDoList'], 'readwrite');

  // add a listener for `complete`
  transaction.oncomplete = event => {
    console.log('Transaction was competed');
  };

  const objectStore = transaction.objectStore('toDoList');
  const newItem = { taskTitle: 'my task', hours: 10, minutes: 10, day: 10, month: 'January', year: 2019 };
  const objectStoreRequest = objectStore.add(newItem);
};
```

## Browser compatibility

{{Compat("api.IDBTransaction.complete_event")}}

## See also

- [Using IndexedDB](/zh-CN/docs/IndexedDB/Using_IndexedDB)
- {{DOMxRef("IDBTransaction.oncomplete", "oncomplete")}} event handler property
