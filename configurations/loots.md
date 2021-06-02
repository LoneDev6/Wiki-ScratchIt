# Loots

{% hint style="warning" %}
### Warning

Loots is not under the scratch\_card YML entry, but it's on its own level, separated from the card info.
{% endhint %}

## Dropping cards from blocks, mobs and fishing

Loots can be used to specify when to drop a card.  
You can decide to create different loot types: 

* blocks
* mobs
* fishing

For example this is the loots category of a .yml file I created.

```yaml
loots:
  blocks:
    nether_quartz_ore:
      type: NETHER_QUARTZ_ORE
      drop_only_first: true
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
        homework:
          item: homework
          min_amount: 1
          max_amount: 2
          chance: 15
    ruby_ore:
      type: itemsadder:ruby_ore
      items:
        clean_it:
          item: clean_it
          min_amount: 1
          max_amount: 2
          chance: 100
```

This example has two loots in **blocks** category.

The first one is a loot from a vanilla **block**. As you imagine it will drop a **defusing\_bomb** card ****or a **homework** card ****when the player breaks a **NETHER\_QUARTZ\_ORE**.  
These **drops** are decided by the plugin ****based on **chance** you set. 

The second one is an [ItemsAdder ](https://www.spigotmc.org/resources/%E2%9C%85must-have%E2%9C%85-itemsadder%E2%9C%A8textures-3d-models-huds-gui-emojis-ores-blocks-wings-tails-hats.73355/)custom block and is called **ruby\_ore** \(you can call them as you prefer\), this will drop a **clean\_it** card when you break a custom **block** of type **itemsadder:ruby\_ore** with a minimum **amount** of **1** and **maximum** amount of **2** with **100% chance**.

{% hint style="info" %}
Special property: **drop\_only\_first**  
This allows you to **stop** the **plugin** from **dropping each** of the **items** that succeed into extracting a **correct** chance to be **dropped**.   
**WARNING**: this would make your items **harder** to be **dropped**.
{% endhint %}

## Ignore fortune enchant

You can make a loot ignore fortune enchant by adding the **ignore\_fortune** property.

```yaml
loots:
  blocks:
    nether_quartz_ore:
      type: NETHER_QUARTZ_ORE
      drop_only_first: true
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
          ignore_fortune: true # <----- here
```

### Other types of loots

As I said before there are other types of loots: mobs and fishing.  
These are some examples:

#### Fishing

```yaml
loots:
  fishing:
    loot_blue_parrotfish:
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
    loot_green_sunfish:
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
    loot_goldfish:
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
```

#### Mobs

```yaml
loots:
  mobs:
    villager:
      type: VILLAGER
      nbt:
        profession:
          path: VillagerData.profession
          value: minecraft:farmer
          type: string
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
    ender_dragon:
      type: ENDER_DRAGON
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
```

{% hint style="info" %}
## Custom mobs loots
{% endhint %}

In order to let ItemsAdder drop an item based on when you kill a custom mob \(created with ItemsAdder\) you have to use the metadata attribute. Example:

```yaml
loots:
  mobs:
    soul:
      type: HUSK
      metadata:
        ItemsAdderMob:
          name: "ItemsAdderMob"
          value: "creaturesplus:soul"
          type: "string"
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
```

As you can see I set **ItemsAdderMob** attribute and specified my custom mob **namespace:id** \(in this example I used the **creaturesplus:soul** mob\)

{% hint style="info" %}
## Villager professions

### \(and any other NBT attribute you want to match\)
{% endhint %}

```yaml
loots:
  mobs:
    villager:
      type: VILLAGER
      nbt:
        profession:
          path: VillagerData.profession
          value: minecraft:farmer
          type: string
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
```

As you can see I set **profession** attribute and specified the **NBT attribute** path, which in this case is **VillagerData.profession**.  
Then I set value to **minecraft:farmer**, this tells ItemsAdder to match only **villagers** with attribute **VillagerData.profession** set to **minecraft:farmer**.

{% hint style="warning" %}
The type attribute of **nbt** and **metadata** are really **important**, don't **forget** them or matches could not occur.
{% endhint %}

{% hint style="info" %}
## Drop based on spawner entity

### \(and any other NBT attribute you want to match\)
{% endhint %}

```yaml
loots:
  blocks:
    change_me:
      enabled: true
      type: SPAWNER
      nbt:
        spawner_type:
          path: SpawnData.id
          value: minecraft:zombie
          type: string
      items:
        defusing_bomb:
          item: defusing_bomb
          min_amount: 1
          max_amount: 2
          chance: 10
```

