# Hermes

Client-side messaging channel for sending data from one browser tab to another with the same origin. Think of it as a PubSub module that can send messages across multiple browser tabs.

To see a demo of Hermes in action, open [this page](https://hermes.arnelle.me/) in multiple browser tabs.

## Usage

Get a copy of `hermes.js` or `dist/hermes.min.js` and include it in your code:

```html
<script src="/path/to/hermes.js"></script>
```

Hermes also supports AMD, so it can also be included this way:

```js
require(["path/to/hermes"], function (hermes) {});
```

Hermes exposes an object named `hermes` which contains the API methods.

## API

-   **`send(topic, data, [type='all' | 'justme' | 'justOthers'])`**: Send data to other browser tabs subscribed to a specified topic.

    -   `topic`: The name of the topic in which the data will be sent to.
    -   `data`: The data to be sent. This needs to be a JSON-serializable object.
    -   `type` (optional, default='all'): A enum indicating whether the data should also be sent to the current tab.

    ```js
    hermes.send("some-topic", "hello world");
    hermes.send("some-topic", { title: "awesome" });
    hermes.send("some-topic", { title: "awesome" }, true);
    ```

-   **`on(topic, callback)`**: Add a callback function for a specified topic.

    -   `topic`: The name of the topic to subscribe to.
    -   `callback`: The callback function, which accepts a single argument representing the data that was sent originally.

    ```js
    hermes.on("some-topic", function (data) {});
    ```

-   **`off(topic, [callback])`**: Remove a callback function for a specified topic.

    -   `topic`: The name of the topic to unsubscribe from.
    -   `callback` (optional): The callback function to remove, or don't provide in order to remove all callback functions for the `topic` topic.

    ```js
    hermes.off("some-topic", callbackFunction);
    hermes.off("some-topic");
    ```

## License

MIT License
