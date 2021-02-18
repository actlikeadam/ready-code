# Ready-code


## JS/TS normalize height container

Use case: Flexbox with inner flexbox column direction<br>
Caveat: It does not work for hidden element

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
