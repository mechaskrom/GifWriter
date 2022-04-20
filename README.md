# GifWriter
A simple animated GIF writer written in C#.

# Example Usage
```csharp
//Create a palette.
Color[] palette = new Color[256];
palette[0] = Color.Red; //Index 0 = red.
palette[1] = Color.Green; //Index 1 = green.
palette[2] = Color.Blue; //Index 2 = blue.

//Create a few frames. Frames can also be constructed from 8-bit bitmaps.
GifFrame frame1 = new GifFrame(32, 32); //Width, height.
for (int i = 0; i < frame1.Length; i++)
{
	frame1.Pixels[i] = 0; //Set all pixels to index 0 = red.
}
GifFrame frame2 = new GifFrame(32, 32);
for (int i = 0; i < frame2.Length; i++)
{
	frame2.Pixels[i] = 1; //Set all pixels to index 1 = green.
}
GifFrame frame3 = new GifFrame(32, 32);
for (int i = 0; i < frame3.Length; i++)
{
	frame3.Pixels[i] = 2; //Set all pixels to index 2 = blue.
}

//Create gif writer and add the frames to it.
GifWriter gifWriter = new GifWriter(palette, 0); //Global palette, loop count.
gifWriter.addFrame(frame1, null, 50); //Frame, local palette, display delay between frames.
gifWriter.addFrame(frame2, null, 50);
gifWriter.addFrame(frame3, null, 50);

//Save result as a gif file.
gifWriter.save(Path.Combine(Environment.CurrentDirectory, "result.gif"));
```
