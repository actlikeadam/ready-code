# Ready-code
This is a collection of coding snippet useful to solve different common problems, mainly Front End world.

If it's a good piece of code, add it here!

## JS/TS normalize height container

Use case: Flexbox with inner flexbox column direction<br>
Caveat: It does NOT work for hidden element<br>
Demo: fiddle/codepen whatever

```
public mounted () {
    if (process.client) {
      window.addEventListener('resize', this.onResize)
    }
  }

  private onResize () {
    if (process.client) {
      let maxHeight = 0
      const el = document.querySelectorAll('.edShed__reviews-box')

      el.forEach((element, _i) => {
        const box = element.getBoundingClientRect()
        if (box.height > maxHeight) {
          if (box.height !== 0) { maxHeight = box.height }
        }
        element.setAttribute('style', `height: ${maxHeight}px`)
      })
    }
  }
```


## JS/TS Add accordion to list on mobile

Use case: List too long<br>
Caveat: It is NOT advisable for conditional lists, e.g. 10 elements showed partially in relation with Geolocation<br>
Demo: fiddle/codepen whatever

```
<ul>
    <li>a</b>
    <li>b</b>
    <li>c</b>
    <details class="full-list" open>
        <summary hidden>See more</summary>
        <li>d</b>
        <li>e</b>
        <li>f</b>
        <li>h</b>
        <li>g</b>
    </details
</ul>

public mounted () {
    const details = document.querySelectorAll('details')
    const summary = document.querySelectorAll('summary')

    if (window.screen.width <= 600) {
      details.forEach((target) => {
        target.removeAttribute('open')
      })

      summary.forEach((target) => {
        target.removeAttribute('hidden')
      })
    }
}
```


## CSS parent selector

Use case: Impossibility to add class to the interested selector with dynamic elements involved
Caveat: none
Demo: https://jsfiddle.net/actlikeadam/fw5dsej2/4/

```
HTML:
<div class="container">
  <div>
    <p class="css-child">
      CSS child
    </p>
  </div>
</div>

JS:
const cssChild = document.querySelectorAll('.css-child')

cssChild.forEach((c) => {
  c.parentElement.classList.add('css-parent')
})
```
