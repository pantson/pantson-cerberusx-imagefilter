# Module imagefilter

V1.0.0 19-09-2020

+ Inital release

## Class imagefilter.ImageFilter

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
End</pre>

# Const GAUSSIAN
# Const REDUCE
# Const SATURATE
# Const GREYSCALE
# Const NEGATIVE

# Method New(img:Image)

Initialises a new filter and data stack with data from the specified image.

# Method SetImage:Void(img:Image)

Resets the data stack with data from the specified image.

# Method ApplyFilter:Void(filter:Int)

# Method ApplyFilter:Void(filter:Int,v:Float)

# Method ApplyFilter:Void(filter:Int,v:Float,buffer:Int)

# Method GetImage:Image()
