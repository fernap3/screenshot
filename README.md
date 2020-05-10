# Screenshot API
This proposed API allows developers to programmatically capture an area of the window as an image.  Current solutions for this involve either JavaScript-based renderers (potentially inaccurate and bloat-adding), or server-side rendering using tools like Puppeteer (relatively high development overhead).

## Use cases
* User feedback systems that allow users to snapshot a section of a web app to send back to the developer
* Allowing a user to quickly export a chart or dashboard as an image to print or send to a colleague.


## API design

## Outstanding questions
* How do we control cross-origin scripts’ use of this API?
* How will this feature affect the Permissions API?
* Should the API allow for converting an element to an image, not just a window area?
* Should the coordinates be relative to the page, or relative to the frame? If the page scrolls, should the API be able to capture content that is currently clipped outside of the window bounds?
* Should there be an option to include or exclude the mouse cursor?
* What options should there be for the returned image type and quality?
