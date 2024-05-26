#### what are Packages in GO? 
> Packages are golang’s way of managing code/ organising code. Packages can be imported.

> Packages should be implemented in a way such that it focuses on one task and performs a single thing (Questionable).

```go
import (
    "name"
    "namespace/packagename"
)

import (
    .
    "package" // Dot before the package get all from the package
   _ package "namespace/packagename" //alias, using underscore tels go that the package is to be ignored
)
```