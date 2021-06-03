# Mapping Standards

This document details the standards that all contributions to Parchment mappings must follow.

### Parameter Names

- Use American English for spellings
  - Example: `color`, not `colour`, `armor`, not `armour`
- All names should be prefixed with `p`
  - Example: `pLevel`, `pXPos`
- Names should make sense without the prefix, and should be valid java identifiers NOT reserved keywords as such:
  - Example: `pFloat` is NOT valid, as `float` is a reserved keyword.
  - Example:`pOs` is not a correct use of the prefix, it should be `pPos`
- Parameter names should be based on current context but otherwise verbose and complete words
  - Avoid single letters, or abbreviations
    - Example: `pNorthWest` over `pNW`, `pMatrixStack` over `pMStack`. 
  - Common abbreviations can be used: `IO` / `NBT`, etc.
  - Use simple parameter names based off of class names, differentiating when there multiple of same type (using more words, not numbers)
- Use Lower Camel Case (`lowerCamelCase`)
- Do not use `$` or `_` in variable names
- All parameters should match the regex `p[A-Z][A-Za-z0-9]+`.
  - Example: `pDot`, `pPos`, `pBlockState`
- Favor using Mojang / Mojmap class names over <1.17 MCP classes. In general, the mojmap name is the de-facto standard (some exceptions may apply).
  - Example: Use `level` over `world`, `blockEntity` over `tileEntity`
- Common parameter names can use abbreviations for brevity:
  - Example: `BlockPos pos, Level level, BlockState state, WorldGenLevel level`


A note about lambda parameters: They can, and will conflict with both existing variables, other methods, and other lambdas. Care should be taken to review these, until such a time that an automated and/or testable solution is in place to verify that these cannot conflict.  

### Javadocs

- Prioritization:
  - Prioritize documenting public APIs over private fields and methods.
  - Prioritize methods and parameters, important fields, and classes.
  - Follow the principle of least effort for best payoff!
- Do not document `package-info.java`.
- Content:
  - Fully qualified mojmap class names should be used in javadoc tags such as `@link`.
    - Example: `{@code net.minecraft.math.BlockPos}` instead of `{@code BlockPos`}
  - Javadocs should be informative - there is no explicit restrictions as long as it is useful.
  - Avoid overly simple explanations, or “expected knowledge”:
    - Example: `getWorld() // Gets the world, @return the world`. This not a useful contribution.
    - Example: `BlockPos() {} // This is the constructor for the class BlockPos` This is expected knowledge - javadocs should not be used to document Java itself.
  - You can use the `@return` tag in a javadoc.
  - Do not use `@param` tags directly in method javadocs, use the parameter javadocs instead.
  - Do not use `@author` or `@since` tags in javadocs.
  - Try to avoid overly specific examples or code references as they may go “out of date” in future Minecraft versions.
  - You may add mod loader specific comments: Javadoc lines prefixed with `@<loader>` will indicate information that is only present on one specific mod loader, and should only be visible / be applied when using said mod loader.