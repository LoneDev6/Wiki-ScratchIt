# Minecraft versions compatibility

## If your server has ViaVersion

{% hint style="info" %}
### This is important to optimize the plugin if your server accepts only some Minecraft versions.

  
ScratchIt must create different optimized map images because all Minecraft versions have different colors support, you can disable some to speedup the plugin startup process.
{% endhint %}

If you're using ViaVersion to allow multiple clients to connect to your server you have to make sure to check these options in `config.yml`

```yaml
graphics:
  viaversion:
    v1_8: true
    v1_12: true
    v1_16: true
```

* Set `v1_8` to **true** if your server accepts 1.8 to 1.11 clients
* Set `v1_12` to **true** if your server accepts 1.12 to 1.15 clients
* Set `v1_16` to **true** if your server accepts 1.16+ clients



