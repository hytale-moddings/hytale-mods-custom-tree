# Hytale Mod: Enchanted Tree (Custom Trees and Saplings)

A companion mod for the [Hytale Modding Manual](https://hytale-moddings.github.io/hytale-modding-docs/) tutorial on **Custom Trees and Saplings**.

## What This Mod Does

Creates an **Enchanted Tree** that grows by absorbing blue-green light from Crystal Glow blocks.

### Features

- **Enchanted Sapling** — plantable sapling with 4 growth stages
- **Crystal Growth Modifier** — tree grows very slowly naturally, but instantly near Crystal Glow blocks (`#88ccff` light)
- **Custom Trunk** — Ash-based bark with crystal-blue heartwood
- **Crystal Leaves** — bright ice-blue foliage
- **Light Shards** — glowing fruit drops
- **Crystal Moss** — wall moss and rug moss with crystal tint
- **Crystal Glow blocks** spawn at the base of the fully grown tree
- **Multilingual** — EN-US, ES, PT-BR translations

### Growth Mechanic

The `CrystalGlow` modifier uses `LightLevel` type with strict RGB filtering:
- **Red 0-5** — filters out torches (high red component)
- **Green 1-127, Blue 1-127** — accepts Crystal Glow light (`#88ccff`)
- **Sunlight 0-5** — tree only grows in darkness/shade
- **RequireBoth: true** — both artificial light AND sunlight conditions must be met
- **Modifier: 2500** — massive growth speed boost near crystal

## Installation

1. Copy the mod folder to `%APPDATA%/Hytale/UserData/Mods/CreateACustomTree/`
2. The folder name **must** be `CreateACustomTree`
3. Requires the [Crystal Glow Block mod](https://github.com/hytale-moddings/hytale-mods-custom-block) for the growth mechanic
4. Start a Hytale server with the mod enabled

## Testing In-Game

```
/spawnitem Plant_Sapling_Enchanted
/spawnitem Ore_Crystal_Glow
```

1. Place the sapling on soil
2. Place Crystal Glow blocks nearby
3. Wait in darkness (night or underground) — the tree grows through 4 stages

## File Structure

```
CreateACustomTree/
├── manifest.json
├── Common/
│   ├── BlockTextures/          # Trunk textures (side + top)
│   ├── Blocks/Foliage/         # Leaf, sapling models + textures
│   └── Resources/Ingredients/  # Fruit model + texture
└── Server/
    ├── Farming/Modifiers/      # CrystalGlow.json (growth modifier)
    ├── Item/Items/
    │   ├── Plant/              # Sapling, leaves, fruit, moss definitions
    │   └── Wood/Enchanted/     # Trunk definition
    ├── Languages/              # en-US, es, pt-BR translations
    ├── PrefabList/             # Tree prefab registry
    └── Prefabs/Trees/Enchanted/ # 4 growth stage prefabs
```

## Block Reference

| Block | Parent | Description |
|-------|--------|-------------|
| `Wood_Enchanted_Trunk` | `Wood_Ash_Trunk` | Dark bark trunk with crystal textures |
| `Plant_Leaves_Enchanted` | `Plant_Leaves_Azure` | Ice-blue crystal leaves |
| `Plant_Fruit_Enchanted` | `Template_Fruit` | Glowing Light Shard fruit |
| `Plant_Sapling_Enchanted` | `Plant_Sapling_Oak` | Plantable sapling with farming stages |
| `Plant_Moss_Wall_Crystal` | `Plant_Moss_Wall_Blue` | Crystal-tinted wall moss |
| `Plant_Moss_Rug_Crystal` | `Plant_Moss_Rug_Blue` | Crystal-tinted rug moss |

## Related

- [Tutorial: Custom Trees and Saplings](https://hytale-moddings.github.io/hytale-modding-docs/tutorials/intermediate/custom-trees-and-saplings/)
- [Hytale Modding Manual](https://hytale-moddings.github.io/hytale-modding-docs/)
- [Crystal Glow Block Mod](https://github.com/hytale-moddings/hytale-mods-custom-block)

## License

MIT
