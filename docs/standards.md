# Mapping Standards

This document details the standards that all contributions to Parchment mappings must follow.

### Parameter Names

1. Use American English for spellings
    - Example: `color`, not `colour`, `armor`, not `armour`
1. All names should be prefixed with `p`
    - Example: `pLevel`, `pXPos`
1. Names should make sense without the prefix, and should be valid java identifiers NOT reserved keywords as such:
    - Example: `pFloat` is NOT valid, as `float` is a reserved keyword.
    - Example: `pOs` is not a correct use of the prefix, it should be `pPos`
1. Parameter names may be named based on the types, and the context in which they are used. They should be verbose and use complete words - do not omit essential information for brevity's sake.
    - Example: `BlockPos pAdjacentPos, BlockPos pCurrentPos`, not `BlockPos pPos1, BlockPos pPos2`
1. Avoid single letters, or abbreviations.
    - Example: `pNorthWest` over `pNW`, `pMatrixStack` over `pMStack`. 
    - Exception: common abbreviations can be used: `IO` / `NBT`, etc.
    - Exception: common class / parameter names can be shortened: `BlockPos pPos, BlockState pState, WorldGenLevel pLevel`
1. Use Lower Camel Case (`lowerCamelCase`)
1. Do not use `$` or `_` in variable names
1. All parameters should match the regex `p[A-Z][A-Za-z0-9]+`.
    - Example: `pDot`, `pPos`, `pBlockState`
1. Favor using Mojang / Mojmap class names over <1.17 MCP classes to name parameters. In general, the mojmap name is the de-facto standard.
    - Example: Use `level` over `world`, `blockEntity` over `tileEntity`
    - Exception: If a Mojmap name would otherwise break a previous rule (i.e. `setColour(int)`, which would imply a parameter of `pColour`, is not American English)


A note about lambda parameters: They can, and will conflict with both existing variables, other methods, and other lambdas. Care should be taken to review these, until such a time that an automated and/or testable solution is in place to verify that these cannot conflict.  

### Javadocs

Prioritization:

- Prioritize documenting public APIs over private fields and methods.
- Prioritize methods and parameters, important fields, and classes.
- Follow the principle of least effort for best payoff!
- Do not document `package-info.java`.

Content:

1. Fully qualified mojmap class names should be used in javadoc tags such as `@link`.
    - Example: `{@link net.minecraft.math.BlockPos}` instead of `{@link BlockPos}`
2. Javadocs should be informative - there is no explicit restrictions as long as it is useful.
3. Avoid overly simple explanations, or “expected knowledge”:
    - Example: `getWorld() // Gets the world, @return the world`. This not a useful contribution.
    - Example: `BlockPos() {} // This is the constructor for the class BlockPos` This is expected knowledge - javadocs should not be used to document Java itself.
4. You can use the `@return` tag in a javadoc.
5. Do not use `@param` tags directly in method javadocs, use the parameter javadocs instead.
6. Do not use `@author` or `@since` tags in javadocs.
7. Try to avoid overly specific examples or code references as they may go “out of date” in future Minecraft versions.
8. You may add mod loader specific comments: Javadoc lines prefixed with `@<loader>` will indicate information that is only present on one specific mod loader, and should only be visible / be applied when using said mod loader.
