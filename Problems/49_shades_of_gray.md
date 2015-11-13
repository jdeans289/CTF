#49 Shades of Gray (125 Points)

We only have 49 shades of gray D:

\#000000 to #F5F5F5... there's one shade missing! Find the hex value of the missing shade. Pound sign optional.

## Hint:
How can we tell which color is which?

![Shades]({{site.baseurl}}/Problems/shades.png)![shades.png]

## Solution:
My first instinct in this problem was to find an online tool that would list all colors in an image, however, I could not find one that gave a complete list, so I programmed my own (probably overcomplicated) tool in Java.

```java
import java.io.*;
import javax.imageio.ImageIO;
import java.awt.image.BufferedImage;
import java.util.*;

public class GetColorList
{
    public static void main(String args[]) throws IOException{
        File file= new File("shades.png");
        BufferedImage image = ImageIO.read(file);
        ArrayList<String> colors = new ArrayList<>();
        int rows = image.getHeight();
        int cols = image.getWidth();
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                String col = getPixelColor(i,j,image);
                if (!colors.contains(col))
                {
                    colors.add(col);
                }
            }
        }
        Collections.sort(colors);
        for (int i = 0; i < 49; i++)
        {
            System.out.print(colors.get(i) + " ");
        }
  }
  
  static String getPixelColor (int x, int y, BufferedImage image)
  {
        int clr =  image.getRGB(x,y);
        String hexValue = Integer.toHexString(clr);
        hexValue = hexValue.substring(2);
        return hexValue;
  }
}
```
The output was a complete, sorted list of all colors in the image. The range of colors given by the problem (#000000 to #F5F5F5) is far greater than 50 shades, but from the list of colors one can see that they are at an interval of five. Upon examining the list for a break in the pattern, the shade #505050 is missing. Figures.

## Flag: #505050







