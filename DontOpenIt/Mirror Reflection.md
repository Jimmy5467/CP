## 858. Mirror Reflection

There is a special square room with mirrors on each of the four walls. Except for the southwest corner, there are receptors on each of the remaining corners, numbered 0, 1, and 2.

The square room has walls of length p and a laser ray from the southwest corner first meets the east wall at a distance q from the 0th receptor.

Given the two integers p and q, return the number of the receptor that the ray meets first.

The test cases are guaranteed so that the ray will meet a receptor eventually.

```
class Solution {
public:
    int mirrorReflection(int p, int q) {
        while (p % 2 == 0 && q % 2 == 0){ 
            p/=2;
            q/=2;
        }
        return 1 - p % 2 + q % 2;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
