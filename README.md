# Screenshot API
This proposed API allows developers to programmatically capture an area of the window as an image.  Current solutions for this involve either JavaScript-based renderers (potentially inaccurate and bloat-adding), or server-side rendering using tools like Puppeteer (relatively high development overhead).

## Use cases
* User feedback systems that allow users to snapshot a section of a web app to send back to the developer
* Allowing a user to quickly export a chart, dashboard, or other data visualization as an image to print or send to a colleague


## API design

```ts
Window.screenshot(bounds?: { x, y, width, height }, type: "png" | "jpeg" | "raw" = "png"): Promise<Blob>
```

If `bounds` is null or undefined, the entire window is captured.

### Examples
```ts
if (!("screenshot" in window))
  throw "The screenshot API isn't available!";
  
const fullscreenImg = await window.screenshot();
console.log(fullscreenImg); // Blob {size: 12345, type: "image/png"}

const rectImg = await window.screenshot({ 10, 10, 50, 50 });
console.log(rectImg); // Blob {size: 12345, type: "image/png"}

const rectJpeg = await window.screenshot({ 10, 10, 50, 50 }, "jpeg");
console.log(rectJpeg); // Blob {size: 12345, type: "image/jpeg"}

const fullscreenJpeg = await window.screenshot(null, "jpeg");
console.log(rectJpeg); // Blob {size: 12345, type: "image/jpeg"}

```

## Permissions
TODO: Figure out interoperability with the Permissions API


## Security and Privacy
TODO

## Outstanding questions
* Do we need to control cross-origin scripts’ use of this API?
* How will this interact with iframes
* How will this feature affect the Permissions API?
* Should the API allow for converting an element to an image, not just a window area?
* Should the coordinates be relative to the page, or relative to the frame? If the page scrolls, should the API be able to capture content that is currently clipped outside of the window bounds?
* Should there be an option to include or exclude the mouse cursor?
* What options should there be for the returned image type and quality?
* We should consider the use case where the developer wants access to the pixel data for the web page.
