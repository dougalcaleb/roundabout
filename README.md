GENERAL SETTINGS: 

Setting | Type | Effect | Default | Example
--------|------|--------|---------|--------
pages | Array | Contains unnamed objects containing elements for each corresponding page. | [] | [{background_image: "../images/numbers/1.png"},{background_image: "../images/numbers/2.png"}]
type | Integer | Integer from 0-2 that defines which carousl type to use: <ul><li>0 defines static (all pages are directly adjacent and can be swiped/dragged)</li><li>1 defines overlap (pages slide in from the sides to overlap the current page and can be swiped/dragged)</li><li>2 defines fade (pages fade in and out over each other)</li></ul> | 0 |
parent | String | Selector of an HTML tag to be the parent of the carousel. | "body" | ".myCarouselWrap"
autoGenHTML | Boolean | Determines whether the required HTML structure will be automatically generated inside the element specified by the "parent" setting, or if it will be created by the user. A reference for custom HTML will be available soon. | true | 
autoGenCSS | Boolean | Determines whether the required CSS styling will be automatically generated and applied to the carousel, or if it will be created by the user. A reference for custom CSS will be available soon. | true |
radioBubbles | Boolean | Determines whether the navigational radio bubbles will be shown or not. | true | 
mobile | Object | Defines a set of values to override when the screen is smaller than the size set by "mobile_breakpoint". | {swipe_threshold: 50} | {keys: false, radioBubbles: false}
mobile_breakpoint | Integer | Maximum size in pixels for the screen to be to apply the values in the "mobile" setting. | 700 |

BEHAVIORAL SETTINGS:

Setting | Type | Effect | Default | Example
--------|------|--------|---------|--------
autoScroll | Boolean | Determines if the autoscroll will be active or not. | false | 
autoScroll_speed | Integer | Time in miliseconds between automatically scrolling between pages. | 5000 | 
autoScroll_timeout | Integer | Time in miliseconds after user interaction to resume autoscroll. | 15000 | 
autoScroll_pauseOnHover | Boolean | Determines whether autoscroll will be paused when user mouses over the carousel or not. | false | 
autoScroll_startAfter | Integer | Time in miliseconds for the first automatic scroll to happen after the page loads. | 5000 |
autoScroll_direction | String | Defines the direction for the autoscroll to scroll. Either "right" or "left". | "right" |
transition | Integer | Time in miliseconds to transition between pages when scrolling. | 300 |
throttle | Boolean | Determines whether user interactions will be throttled or not. | true | 
throttle_timeout | Integer | Time in miliseconds to disallow user interaction for after an interaction. | 300 | 
throttle_matchTransition | Boolean | Determines whether the "throttle_timeout" setting will match the "transition" setting. Overrides "throttle_timeout". | false |
keys | Boolean | Determines whether the arrow keys can be used for navigation or not. | true |
infinite | Boolean | Determines whether the carousel can scroll infinitely or not. | true |
swipe | Boolean | Determines if the carousel can be click-dragged or swiped. | true |
swipe_threshold | Integer | Defines the distance in px that the user must swipe or drag to advance to the next page instead of snapping back to the current one. | 300 | 
swipe_multiplier | Integer | Defines the multiplier for swipe interactions. | 1 |
swipe_resistance | Integer | Defines the resistance when attempting to drag past the end of a non-infinite carousel. Must be between 0 and 1. | 0.95 | 
rtl | Boolean | Determines whether the carousel will be laid out right-to-left or not. | false | 

TYPE-SPECIFIC SETTINGS:

Setting | Type | Effect | Default | Applies To
--------|------|--------|---------|-----------
static_showPages | Integer | Defines the number of pages to show | 1 | type 0 (static)
static_enlargeCenter | Integer | Defines the percentage of the size of a normal slide to set the center slide to | 100 | type 0 (static)
static_sizeFalloff | Integer | Defines the percentage that each successive page will get smaller by | 0 | type 0 (static)
fade_offsetIn | Integer | Defines the movement of a page when it is coming into focus | 20 | type 2 (fade)
fade_offsetOut | Integer | Defines the movement of a page when it is going out of focus | -20 | type 2 (fade)
fade_offsetUnits | String | Defines the units to use for offsetIn and offsetOut | "px" | type 2 (fade)


<ul></ul>
<li></li>


Patch Notes:

v0.2.0:
* Features:
    * Implemented infinite drag scroll - it is no longer limited to the center slide and the two adjacent to it
* Bugfixes:
    * Scrolling quickly with fewer pages caused a pop-in effect
    * Some transitions were not being reset correctly in certain conditions. Switched to a css-class based method instead
    * A single frame of the wrong page could show up when swiping between pages
    * The first page wouldn't accept dragging when not an infinite carousel
    * 4 jitter issues related to edge resistance and non-infinite scrolling
    * Dragging through multiple pages caused transitions to not reset correctly
    * Some global event listeners were not being reset correctly
    * Dragging and then step-scrolling back to the initial page would cause some pages to disappear
    * Dragging and step-scrolling was possible, and could break page order
    * Page order could break when non-infinite and spamming nav buttons

v0.1.0:
* Features:
    * New type: static. All pages are directly next to each other and fill the entire wrapper.
    * Fully implemented swipe/drag scrolling on "static" type
    * Autoscroll
    * Auto-generating HTML and CSS structure
    * User interaction throttling