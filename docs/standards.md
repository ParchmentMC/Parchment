# Mapping Standards

This document details the standards that all contributions to Parchment mappings must follow.

### Parameter Names

1. Use American English for spellings
    - Example: `color`, not `colour`, `armor`, not `armour`
1. Names should make sense and be valid java identifiers NOT reserved keywords as such:
    - Example: `float` is NOT valid as it is a reserved keyword.
1. Parameter names may be named based on the types, and the context in which they are used. They should be verbose and use complete words - do not omit essential information for brevity's sake.
    - Example: `BlockPos adjacentPos, BlockPos currentPos`, not `BlockPos pos1, BlockPos pos2`
1. Avoid single letters, or abbreviations.
    - Example: `northWest` over `nW`, `matrixStack` over `mStack`. 
    - Exception: common abbreviations can be used: `IO` / `NBT`, etc.
    - Exception: common class / parameter names can be shortened: `BlockPos pos, BlockState state, WorldGenLevel level`
1. Use Lower Camel Case.
    - Example: `lowerCamelCase`
3. Do not use `$` or `_` in variable names
4. All parameters should match the regex `[a-z][A-Za-z0-9]*`.
    - Simply, parameters should contain only alphanumeric characters and start with a lowercase letter.
    - Example: `dot`, `pos`, `blockState`
5. Favor using Mojang / Mojmap class names over <1.17 MCP classes to name parameters. In general, the mojmap name is the de-facto standard.
    - Example: Use `level` over `world`, `blockEntity` over `tileEntity`
    - Exception: If a Mojmap name would otherwise break a previous rule (i.e. `setColour(int)`, which would imply a parameter of `colour`, is not American English)


A note about lambda parameters: They can, and will conflict with both existing variables, other methods, and other lambdas. Care should be taken to review these, until such a time that an automated and/or testable solution is in place to verify that these cannot conflict.  

### Javadocs

Prioritization:

- Prioritize documenting public APIs over private fields and methods.
- Prioritize methods and parameters, important fields, and classes.
- Follow the principle of least effort for best payoff!
- Do not document `package-info.java`.

Content:

1. Fully qualified mojmap class names should be used in javadoc tags that resolve their content, aka `@link` and `@see`.
    - Example: `{@link net.minecraft.math.BlockPos}` instead of `{@link BlockPos}`
2. Javadocs should be informative - there is no explicit restrictions as long as it is useful.
3. Avoid overly simple explanations, or “expected knowledge”:
    - Example: `getWorld() // Gets the world, @return the world`. This not a useful contribution.
    - Example: `BlockPos() {} // This is the constructor for the class BlockPos` This is expected knowledge - javadocs should not be used to document Java itself.
4. You can use the `@return` tag in a javadoc.
5. Do not use `@param` tags directly in method javadocs, use the parameter javadocs instead.
6. Do not use `@author` or `@since` tags in javadocs.
7. Try to avoid overly specific examples or code references as they may go “out of date” in future Minecraft versions.
