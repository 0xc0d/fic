# Usage

```go
package main

import (
	"image"
	"image/jpeg"
	"os"

	"github.com/0xc0d/ficblur"
)

func main() {
	imageFile, err := os.Open("img.jpeg")
	panicNotNil(err)
	original, _, err := image.Decode(imageFile)
	panicNotNil(err)

	blurred := ficblur.Gaussian(original, 15, 2)

	blurredFile, _ := os.Create("blurred.jpeg")
	err = jpeg.Encode(blurredFile, blurred, nil)
	panicNotNil(err)
}

func panicNotNil(err error) {
	if err != nil {
		panic(err)
	}
}
```