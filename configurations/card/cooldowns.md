# Cooldowns

## Per-card usage cooldown

You can set an usage cooldown separated for each card using the `usage_cooldown_ticks` attribute.

### Example:

```yaml
scratch_card:
    id: example
  permissions:
    show_in_list_gui: new_card.example
    use: new_card.example
  name: "example"
  usage_cooldown_ticks: 60
```

## Global cards cooldown

You can edit this in **config.yml** 

```yaml
cards:
  usage_cooldown_ticks: 20
```

