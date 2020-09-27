# Module imagefilter

V1.0.0 19-09-2020

+ Inital release

# License

Free to use. Use at your own risk.

## Class ImageFilter

The ImageFilter module provides simple support for applying various image filters to your gfx.

To use ImageFilter in your game:

+ Import the imagefilter module into your game

Example:
```cerberusx
Strict
Import mojo2
Import imagefilter

#GLFW_WINDOW_WIDTH=1024
#GLFW_WINDOW_HEIGHT=640

Class myClass Extends App
	Field imgf:ImageFilter
	Field img:Image

	Field cnvs:Canvas

	Method OnCreate:Int()
		SetUpdateRate(60)
		cnvs = New Canvas

		img = Image.Load("dales.jpg",0,0)

		imgf = New ImageFilter(img)
		imgf.ApplyFilter(ImageFilter.GREYSCALE)
		Return 0
	End

	Method OnUpdate:Int()
		Return 0
	End

	Method OnRender:Int()
		cnvs.Clear (0,0.5,0)
		cnvs.DrawImage imgf.GetImage(),0,0
		cnvs.Flush

		Return 0
	End
End

Function Main:Int()
	' Create an instance of your class that you have defined above.
	New myClass
	Return 0
End
```

<a name="ImageFilter.New(img"></a>
### Method New(img:Image)

Initialises a new filter and data stack with data from the specified image.

<a name="ImageFilter.SetImage"></a>
### Method SetImage:Void(img:Image)

Resets the data stack with data from the specified image.

<a name="ImageFilter.ApplyFilter"></a>
### Method ApplyFilter:Void(filter:Int)

Apply filter to image stack. These filters are not configurable. **filter** should be one of

| **Filter** | **Description** |
| :-- | :-- |
| ImageFilter.NEGATIVE | Produce a negative image |
| ImageFilter.GREYSCALE | Turns a colour image into greyscale |
| ImageFilter.STRETCH | Stretches the brightness from 0 to 1. |

<a name="ImageFilter.ApplyFilter"></a>
### Method ApplyFilter:Void(filter:Int,v:Float) |

Apply filter to image stack. Use v to configure the filter. **filter** should be one of

| **Filter** | **Description** |
| :-- | :-- |
| ImageFilter.MEAN | Blurs the image using a mean value of a square. **v** is the pixel size of the square. |
| ImageFilter.GUASSIAN | Blurs the image, low radius can be used to remove noise from an image. **v** is the radius of the blur. |
| ImageFilter.SATURATE | Change the saturation of the image. **v** is between -1 and 1. |
| ImageFilter.BRIGHTNESS | Change the brightness of the image. **v** is between -1 and 1. |
| ImageFilter.REDUCE | Reduces the number of colours in the image to **v** colours. |
| ImageFilter.BIT | Reduces the bit level of an image to **v** for a retro look. Bit level is from 1 to 8 |
| ImageFilter.EDGE | Finds the edges of the image. **v** is the thickness of the edge. |
| ImageFilter.TOON | Produces a cartoon like image. **v** is the thickness of the lines |

<a name="ImageFilter.ApplyFilter"></a>
### Method ApplyFilter:Void(filter:Int,v:Float[]) |

Some images filters need more then one value.

Use v[] to configure the filter. **filter** should be one of

| **Filter** | **Description** |
| :-- | :-- |
| ImageFilter.TINT | Tints the image using color RGB in **v[0]** with initensity v[1] , where 0.0 < **v[1]** < 1.0 |

<a name="ImageFilter.GetImage"></a>
### Method GetImage:Image() |

Return the the new image with filters applied.

<a name="ImageFilter.CreateSnapshot"></a>
### Method CreateSnapshot:Void()

Snapshot the current stack, so that you can revert later.

<a name="ImageFilter.RevertSnapshot"></a>
### Method RevertSnapshot:Void()

Revert to the current snapshot.
