# Xoshiro-cpp <a href="https://github.com/Reputeless/Xoshiro-cpp/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-MIT-4aaa4a"></a> <a href="https://github.com/sponsors/Reputeless"><img src="https://img.shields.io/badge/funding-GitHub_Sponsors-ea4aaa"></a>
**Xoshiro-cpp** is a header-only pseudorandom number generator library for modern C++.  
Based on David Blackman and Sebastiano Vigna's [xoshiro generators](http://prng.di.unimi.it/).

## Features
- Meets the `std::uniform_random_bit_generator` concept (C++20)
  - Works with `std::uniform_int_distribution`, `std::shuffle` and the other standard library functions
- Mostly `constexpr` in C++17
- Serialize / deserialize

## Examples

```C++
# include <iostream>
# include "XoshiroCpp.hpp"

int main()
{
    using namespace XoshiroCpp;

    const std::uint64_t seed = 12345;

    Xoshiro256PlusPlus rng(seed);

    for (int i = 0; i < 5; ++i)
    {
        std::cout << rng() << '\n';
    }
}
```
```
10201931350592234856
3780764549115216544
1570246627180645737
3237956550421933520
4899705286669081817
```

----

```C++
# include <iostream>
# include <random>
# include "XoshiroCpp.hpp"

int main()
{
	using namespace XoshiroCpp;

	const std::uint64_t seed = 12345;

	Xoshiro256PlusPlus rng(seed);

	std::uniform_int_distribution<int> dist(1, 6);

	for (int i = 0; i < 5; ++i)
	{
		std::cout << dist(rng) << '\n';
	}
}
```
```
1
5
4
3
6
```

----

```C++
# include <algorithm>
# include <iostream>
# include "XoshiroCpp.hpp"

int main()
{
    using namespace XoshiroCpp;

    const std::uint64_t seed = 12345;

    Xoshiro256PlusPlus rng(seed);

    std::array<int, 10> ar = { 0,1,2,3,4,5,6,7,8,9 };

    std::shuffle(ar.begin(), ar.end(), rng);

    for (const auto& x : ar)
    {
        std::cout << x << '\n';
    }
}
```
```
6
3
7
2
8
5
4
9
1
0
```

----




## Roadmap

- [x] SplitMix64
- [x] xoshiro256+
- [x] xoshiro256++
- [x] xoshiro256** 
- [ ] xoshiro128+
- [ ] xoshiro128++
- [ ] xoshiro128**

## License
Xoshiro-cpp is distributed under the MIT license.