## Description

This is a partial port of the [MEC Free](https://assetstore.unity.com/packages/tools/animation/more-effective-coroutines-free-54975 "MEC Free") asset for [Godot 4.x](https://godotengine.org/ "Godot") .NET published with permission under the MIT license.

Original source by Teal Rogers at [Trinary Software](http://trinary.tech/ "Trinary Software").

## Installation
1. Download Latest commit or the stable Release version.
2. Place the `addons` folder into your project root.
3. Build the project solution under `MSBuild > Build > Build Project`

## Usage
Documentation for the original Unity asset may be found [here](http://trinary.tech/category/mec/free/ "here"). Usage is largely unchanged, aside from changes to the naming conventions.

### Example Coroutine
```cs
    public override void _Ready()
    {
        Timing.RunCoroutine(DestroyAfter(2));
    }

    IEnumerator<double> DestroyAfter(double seconds)
    {
        yield return Timing.WaitForSeconds(seconds);
        GD.Print("Goodbye!");
        QueueFree();
    }
```

## Notable Differences

### Doubles
Godot uses `double` for its scalars, so coroutines return `IEnumerator<double>`.

### Naming
Names have been changed to match Godot terminology, most notably:

- `Update` -> `Process`
- `GameObject` -> `Node`

### Execution order
To avoid ambiguous execution order at runtime depending on the tree layout, all `Timing` instances start with a `ProcessPriority` and `ProcessPhysicsPriority` of -1. This means coroutines will update before regular nodes by default. 

## Contribution
 If you spot a bug while using this, please create an [Issue](https://github.com/WeaverDev/GDMEC/issues).


## License

[MIT License](LICENSE)

Copyright (c) 2023-present, Teal Rogers, Isar Arason (WeaverDev)