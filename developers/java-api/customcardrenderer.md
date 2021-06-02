# CustomCardRenderer

{% hint style="warning" %}
### This is not for newbie developers.

⚠️Please don't ask for support if you don't know how to use **BufferedImage** and **Color** classes.

Keep in mind that you have to handle all the stuff manually and this is limited compared to Spigot API. The only advantage of using this is that it's not laggy like Spigot API as this is only packet based.

Use this class only if you really need to.
{% endhint %}

## What is a CustomCardRenderer?

It's a class that can be used to create a custom renderer. You can use it to show custom images to the player.  
You will have to obtain pixel colors for example using a [BufferedImage](https://docs.oracle.com/javase/7/docs/api/java/awt/image/BufferedImage.html).

This class is meant to be used to do simple stuff not advanced layering. To do advanced layering, transparency etc you have to handle that on your own.

In the future I may extend this API to fill the gaps.

## Showcase of what you can achieve

![](https://media.giphy.com/media/URRU7u74EZEwyw1gDw/giphy.gif)

## Example code

```java
try
{
    BufferedImage img = ImageIO.read(new File(getDataFolder() + File.separator + "test.png"));

    CustomCardRenderer renderer = new CustomCardRenderer(player, false);
    renderer.start();
    
    for (int x = 0; x < 128; x++)
        for (int y = 0; y < 128; y++)
            renderer.setPixel(x, y, new Color(img.getRGB(x, y)));

    Bukkit.getScheduler().runTaskLater(this, () -> {
        renderer.stop();
    }, 20L * 5);
}
catch (IOException e)
{
    //error
}
```



