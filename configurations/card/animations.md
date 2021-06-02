# Animations

## Introduction

You can create win/lose animations for your cards as you can see in my example cards.

The good thing is that you don't have to draw the background on each frame of the animation but you can separate animation from the background, as you can see in my examples.

## Special notes

### Repeating the same frame multiple times

If you want to repeat the same frame you can avoid copying and pasting the same .png file, instead you can do that:

```yaml
  win_anim:
    frames:
    - 0|x10
    - 1
    - 2
    - 3
    - 4
    - 5
```

As you can see I used this special name `|x10`, this means that the frame named **0.png** will be executed `10 times`.

### Adjusting the animation position

This plugin will center the animation automatically, but if you want to move it you can set this special attribute \(**shift**\):

```yaml
  win_anim:
    shift:
      x: 0
      y: 15
    frames:
      - anim_4|x6
      - anim_5|x2
      - anim_6|x2
      - anim_7|x2
      - anim_8|x2
      - anim_9|x2
```

### Specify win/lose background duration

If your card doesn't have any animation and you want to show the win/lose background for some seconds you can do that:

```yaml
  win_anim:
    static_background_duration: 30
  lose_anim:
    static_background_duration: 30
```

### Automatically create list of frames in the .yml config

You don't need to manually input all the file names, you can use this command to make the plugin write the files list for you: `/scratchit config AutoListAnimationFiles <card_name> <animation_type>`

For example: 

