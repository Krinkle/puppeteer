---
sidebar_label: Browser
---

# Browser class

A Browser is created when Puppeteer connects to a browser instance, either through [PuppeteerNode.launch()](./puppeteer.puppeteernode.launch.md) or [Puppeteer.connect()](./puppeteer.puppeteer.connect.md).

#### Signature:

```typescript
export declare class Browser extends EventEmitter<BrowserEvents>
```

**Extends:** [EventEmitter](./puppeteer.eventemitter.md)&lt;[BrowserEvents](./puppeteer.browserevents.md)&gt;

## Remarks

The Browser class extends from Puppeteer's [EventEmitter](./puppeteer.eventemitter.md) class and will emit various events which are documented in the [BrowserEvent](./puppeteer.browserevent.md) enum.

The constructor for this class is marked as internal. Third-party code should not call the constructor directly or create subclasses that extend the `Browser` class.

## Example 1

An example of using a [Browser](./puppeteer.browser.md) to create a [Page](./puppeteer.page.md):

```ts
import puppeteer from 'puppeteer';

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto('https://example.com');
  await browser.close();
})();
```

## Example 2

An example of disconnecting from and reconnecting to a [Browser](./puppeteer.browser.md):

```ts
import puppeteer from 'puppeteer';

(async () => {
  const browser = await puppeteer.launch();
  // Store the endpoint to be able to reconnect to the browser.
  const browserWSEndpoint = browser.wsEndpoint();
  // Disconnect puppeteer from the browser.
  browser.disconnect();

  // Use the endpoint to reestablish a connection
  const browser2 = await puppeteer.connect({browserWSEndpoint});
  // Close the browser.
  await browser2.close();
})();
```

## Methods

| Method                                                                                         | Modifiers | Description                                                                                                                                                                                                            |
| ---------------------------------------------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [browserContexts()](./puppeteer.browser.browsercontexts.md)                                    |           | Returns an array of all open browser contexts. In a newly created browser, this will return a single instance of [BrowserContext](./puppeteer.browsercontext.md).                                                      |
| [close()](./puppeteer.browser.close.md)                                                        |           | Closes the browser and all of its pages (if any were opened). The [Browser](./puppeteer.browser.md) object itself is considered to be disposed and cannot be used anymore.                                             |
| [createIncognitoBrowserContext(options)](./puppeteer.browser.createincognitobrowsercontext.md) |           | Creates a new incognito browser context. This won't share cookies/cache with other browser contexts.                                                                                                                   |
| [defaultBrowserContext()](./puppeteer.browser.defaultbrowsercontext.md)                        |           | Returns the default browser context. The default browser context cannot be closed.                                                                                                                                     |
| [disconnect()](./puppeteer.browser.disconnect.md)                                              |           | Disconnects Puppeteer from the browser, but leaves the browser process running. After calling <code>disconnect</code>, the [Browser](./puppeteer.browser.md) object is considered disposed and cannot be used anymore. |
| [isConnected()](./puppeteer.browser.isconnected.md)                                            |           | Indicates that the browser is connected.                                                                                                                                                                               |
| [newPage()](./puppeteer.browser.newpage.md)                                                    |           | Promise which resolves to a new [Page](./puppeteer.page.md) object. The Page is created in a default browser context.                                                                                                  |
| [pages()](./puppeteer.browser.pages.md)                                                        |           | An array of all open pages inside the Browser.                                                                                                                                                                         |
| [process()](./puppeteer.browser.process.md)                                                    |           | The spawned browser process. Returns <code>null</code> if the browser instance was created with [Puppeteer.connect()](./puppeteer.puppeteer.connect.md).                                                               |
| [target()](./puppeteer.browser.target.md)                                                      |           | The target associated with the browser.                                                                                                                                                                                |
| [targets()](./puppeteer.browser.targets.md)                                                    |           | All active targets inside the Browser. In case of multiple browser contexts, returns an array with all the targets in all browser contexts.                                                                            |
| [userAgent()](./puppeteer.browser.useragent.md)                                                |           | The browser's original user agent. Pages can override the browser user agent with [Page.setUserAgent()](./puppeteer.page.setuseragent.md).                                                                             |
| [version()](./puppeteer.browser.version.md)                                                    |           | A string representing the browser name and version.                                                                                                                                                                    |
| [waitForTarget(predicate, options)](./puppeteer.browser.waitfortarget.md)                      |           | Searches for a target in all browser contexts.                                                                                                                                                                         |
| [wsEndpoint()](./puppeteer.browser.wsendpoint.md)                                              |           | The browser websocket endpoint which can be used as an argument to [Puppeteer.connect()](./puppeteer.puppeteer.connect.md).                                                                                            |
