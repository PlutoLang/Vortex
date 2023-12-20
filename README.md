# Vortex

Vortex converts Pluto code to and from a "golfed" representation, which uses Unicode characters in place of certain strings.

## Samples

```AppleScript
∘(π) -- 3.1415926535898
```

#### [Try It Yourself](https://pluto-lang.org/web/#code=local%20WRITE_ONLINE_CODE%20%3D%20%5B%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%5B%0D%0A%E2%88%98(%CF%80)%0D%0A%5D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%5D%0D%0A%0D%0Alocal%20symbols%20%3Cconst%3E%20%3D%20%7B%0D%0A%09--%20Keywords%0D%0A%09%5B%22%E2%88%B5%22%5D%20%3D%20%22for%20%22%2C%0D%0A%09--%20Functions%0D%0A%09%5B%22%E2%88%98%22%5D%20%3D%20%22print%22%2C%0D%0A%09%5B%22%E2%87%A1%22%5D%20%3D%20%22range%22%2C%0D%0A%09%5B%22%E2%8B%95%22%5D%20%3D%20%22tonumber%22%2C%0D%0A%09%5B%22%E2%88%A0%22%5D%20%3D%20%22math.atan%22%2C%0D%0A%09--%20Constants%0D%0A%09%5B%22%CF%80%22%5D%20%3D%20%22math.pi%22%2C%0D%0A%09%5B%22%E2%88%9E%22%5D%20%3D%20%22math.maxinteger%22%2C%0D%0A%09--%20Methods%0D%0A%09%5B%22%E2%8A%82%22%5D%20%3D%20%22%3Aconcat%22%2C%0D%0A%09%5B%22%E2%89%A1%22%5D%20%3D%20%22%3Aforeach%22%2C%0D%0A%09%5B%22%E2%96%BD%22%5D%20%3D%20%22%3Afilter%22%2C%0D%0A%09%5B%22%C2%A4%22%5D%20%3D%20%22%3Amap%22%2C%0D%0A%09%5B%22%E2%8D%89%22%5D%20%3D%20%22%3Areorder()%22%2C%0D%0A%09%5B%22%E2%88%A7%22%5D%20%3D%20%22%3Areduce%22%2C%0D%0A%09%5B%22%E2%86%A7%22%5D%20%3D%20%22%3Areduce(math.min)%22%2C%0D%0A%09%5B%22%E2%86%A5%22%5D%20%3D%20%22%3Areduce(math.max)%22%2C%0D%0A%7D%0D%0A%0D%0A--%20Polyfills%0D%0Arange%20%3F%3F%3D%20function(s%2C%20e%2C%20x%20%3D%201)%0D%0A%09if%20e%20%3D%3D%20nil%20then%0D%0A%09%09assert(s%20~%3D%20nil)%0D%0A%09%09e%20%3D%20s%0D%0A%09%09s%20%3D%201%0D%0A%09end%0D%0A%09local%20t%20%3D%20%7B%7D%0D%0A%09for%20i%20%3D%20s%2C%20e%2C%20x%20do%0D%0A%09%09t%5B%23t%20%2B%201%5D%20%3D%20i%0D%0A%09end%0D%0A%09return%20t%0D%0Aend%0D%0Atable.reduce%20%3F%3F%3D%20function(t%2C%20f%2C%20x%20%3D%201)%0D%0A%09local%20a%20%3D%20x%0D%0A%09for%20t%20as%20v%20do%0D%0A%09%09a%20%3D%20f(a%2C%20v)%0D%0A%09end%0D%0A%09return%20a%0D%0Aend%0D%0A%0D%0Alocal%20function%20golfify(code)%0D%0A%09for%20symbol%2C%20plain%20in%20symbols%20do%0D%0A%09%09code%20%3D%20code%3Agsub(plain%2C%20symbol)%0D%0A%09end%0D%0A%09return%20code%0D%0Aend%0D%0A%0D%0Alocal%20function%20ungolfify(code)%0D%0A%09for%20symbol%2C%20plain%20in%20symbols%20do%0D%0A%09%09code%20%3D%20code%3Agsub(symbol%2C%20plain)%0D%0A%09end%0D%0A%09return%20code%0D%0Aend%0D%0A%0D%0Alocal%20function%20try_run(code)%0D%0A%09code%20%3D%20ungolfify(code)%0D%0A%09local%20chunk%2C%20err%20%3D%20load(code%2C%20arg%5B2%5D)%0D%0A%09if%20chunk%20then%0D%0A%09%09chunk()%0D%0A%09else%0D%0A%09%09print(err)%0D%0A%09end%0D%0Aend%0D%0A%0D%0Aif%20arg%5B-1%5D%20%3D%3D%20%22pluto%22%20and%20arg%5B0%5D%20%3D%3D%20%22script.pluto%22%20then%0D%0A%09try_run(WRITE_ONLINE_CODE)%0D%0Aelseif%20arg%5B1%5D%20%3D%3D%20%22run%22%20and%20arg%5B2%5D%20then%0D%0A%09local%20f%20%3Cclose%3E%20%3D%20io.open(arg%5B2%5D%2C%20%22rb%22)%0D%0A%09if%20not%20f%20then%0D%0A%09%09print(%22Failed%20to%20open%20file%3A%20%22..arg%5B2%5D)%0D%0A%09else%0D%0A%09%09local%20code%20%3D%20f%3Aread(%22*a%22)%0D%0A%09%09try_run(code)%0D%0A%09end%0D%0Aelseif%20arg%5B1%5D%20%3D%3D%20%22golfify%22%20and%20arg%5B2%5D%20then%0D%0A%09local%20f%20%3Cclose%3E%20%3D%20io.open(arg%5B2%5D%2C%20%22rb%22)%0D%0A%09if%20not%20f%20then%0D%0A%09%09print(%22Failed%20to%20open%20file%3A%20%22..arg%5B2%5D)%0D%0A%09else%0D%0A%09%09local%20code%20%3D%20f%3Aread(%22*a%22)%0D%0A%09%09print(golfify(code))%0D%0A%09end%0D%0Aelseif%20arg%5B1%5D%20%3D%3D%20%22ungolfify%22%20and%20arg%5B2%5D%20then%0D%0A%09local%20f%20%3Cclose%3E%20%3D%20io.open(arg%5B2%5D%2C%20%22rb%22)%0D%0A%09if%20not%20f%20then%0D%0A%09%09print(%22Failed%20to%20open%20file%3A%20%22..arg%5B2%5D)%0D%0A%09else%0D%0A%09%09local%20code%20%3D%20f%3Aread(%22*a%22)%0D%0A%09%09print(ungolfify(code))%0D%0A%09end%0D%0Aelse%0D%0A%09print(%22Syntax%3A%20pluto%20vortex.pluto%20%5Brun%7Cgolfify%7Cungolfify%5D%20%3Cscript%3E%22)%0D%0Aend%0D%0A)

```AppleScript
∘(⇡(10)▽(|x|->x%2==0)⍉⊂" ") -- 2 4 6 8 10
```

#### [Try It Yourself](https://pluto-lang.org/web/#code=local%20WRITE_ONLINE_CODE%20%3D%20%5B%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%5B%0D%0A%E2%88%98(%CF%80)%0D%0A%5D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%3D%5D%0D%0A%0D%0Alocal%20symbols%20%3Cconst%3E%20%3D%20%7B%0D%0A%09--%20Keywords%0D%0A%09%5B%22%E2%88%B5%22%5D%20%3D%20%22for%20%22%2C%0D%0A%09--%20Functions%0D%0A%09%5B%22%E2%88%98%22%5D%20%3D%20%22print%22%2C%0D%0A%09%5B%22%E2%87%A1%22%5D%20%3D%20%22range%22%2C%0D%0A%09%5B%22%E2%8B%95%22%5D%20%3D%20%22tonumber%22%2C%0D%0A%09%5B%22%E2%88%A0%22%5D%20%3D%20%22math.atan%22%2C%0D%0A%09--%20Constants%0D%0A%09%5B%22%CF%80%22%5D%20%3D%20%22math.pi%22%2C%0D%0A%09%5B%22%E2%88%9E%22%5D%20%3D%20%22math.maxinteger%22%2C%0D%0A%09--%20Methods%0D%0A%09%5B%22%E2%8A%82%22%5D%20%3D%20%22%3Aconcat%22%2C%0D%0A%09%5B%22%E2%89%A1%22%5D%20%3D%20%22%3Aforeach%22%2C%0D%0A%09%5B%22%E2%96%BD%22%5D%20%3D%20%22%3Afilter%22%2C%0D%0A%09%5B%22%C2%A4%22%5D%20%3D%20%22%3Amap%22%2C%0D%0A%09%5B%22%E2%8D%89%22%5D%20%3D%20%22%3Areorder()%22%2C%0D%0A%09%5B%22%E2%88%A7%22%5D%20%3D%20%22%3Areduce%22%2C%0D%0A%09%5B%22%E2%86%A7%22%5D%20%3D%20%22%3Areduce(math.min)%22%2C%0D%0A%09%5B%22%E2%86%A5%22%5D%20%3D%20%22%3Areduce(math.max)%22%2C%0D%0A%7D%0D%0A%0D%0A--%20Polyfills%0D%0Arange%20%3F%3F%3D%20function(s%2C%20e%2C%20x%20%3D%201)%0D%0A%09if%20e%20%3D%3D%20nil%20then%0D%0A%09%09assert(s%20~%3D%20nil)%0D%0A%09%09e%20%3D%20s%0D%0A%09%09s%20%3D%201%0D%0A%09end%0D%0A%09local%20t%20%3D%20%7B%7D%0D%0A%09for%20i%20%3D%20s%2C%20e%2C%20x%20do%0D%0A%09%09t%5B%23t%20%2B%201%5D%20%3D%20i%0D%0A%09end%0D%0A%09return%20t%0D%0Aend%0D%0Atable.reduce%20%3F%3F%3D%20function(t%2C%20f%2C%20x%20%3D%201)%0D%0A%09local%20a%20%3D%20x%0D%0A%09for%20t%20as%20v%20do%0D%0A%09%09a%20%3D%20f(a%2C%20v)%0D%0A%09end%0D%0A%09return%20a%0D%0Aend%0D%0A%0D%0Alocal%20function%20golfify(code)%0D%0A%09for%20symbol%2C%20plain%20in%20symbols%20do%0D%0A%09%09code%20%3D%20code%3Agsub(plain%2C%20symbol)%0D%0A%09end%0D%0A%09return%20code%0D%0Aend%0D%0A%0D%0Alocal%20function%20ungolfify(code)%0D%0A%09for%20symbol%2C%20plain%20in%20symbols%20do%0D%0A%09%09code%20%3D%20code%3Agsub(symbol%2C%20plain)%0D%0A%09end%0D%0A%09return%20code%0D%0Aend%0D%0A%0D%0Alocal%20function%20try_run(code)%0D%0A%09code%20%3D%20ungolfify(code)%0D%0A%09local%20chunk%2C%20err%20%3D%20load(code%2C%20arg%5B2%5D)%0D%0A%09if%20chunk%20then%0D%0A%09%09chunk()%0D%0A%09else%0D%0A%09%09print(err)%0D%0A%09end%0D%0Aend%0D%0A%0D%0Aif%20arg%5B-1%5D%20%3D%3D%20%22pluto%22%20and%20arg%5B0%5D%20%3D%3D%20%22script.pluto%22%20then%0D%0A%09try_run(WRITE_ONLINE_CODE)%0D%0Aelseif%20arg%5B1%5D%20%3D%3D%20%22run%22%20and%20arg%5B2%5D%20then%0D%0A%09local%20f%20%3Cclose%3E%20%3D%20io.open(arg%5B2%5D%2C%20%22rb%22)%0D%0A%09if%20not%20f%20then%0D%0A%09%09print(%22Failed%20to%20open%20file%3A%20%22..arg%5B2%5D)%0D%0A%09else%0D%0A%09%09local%20code%20%3D%20f%3Aread(%22*a%22)%0D%0A%09%09try_run(code)%0D%0A%09end%0D%0Aelseif%20arg%5B1%5D%20%3D%3D%20%22golfify%22%20and%20arg%5B2%5D%20then%0D%0A%09local%20f%20%3Cclose%3E%20%3D%20io.open(arg%5B2%5D%2C%20%22rb%22)%0D%0A%09if%20not%20f%20then%0D%0A%09%09print(%22Failed%20to%20open%20file%3A%20%22..arg%5B2%5D)%0D%0A%09else%0D%0A%09%09local%20code%20%3D%20f%3Aread(%22*a%22)%0D%0A%09%09print(golfify(code))%0D%0A%09end%0D%0Aelseif%20arg%5B1%5D%20%3D%3D%20%22ungolfify%22%20and%20arg%5B2%5D%20then%0D%0A%09local%20f%20%3Cclose%3E%20%3D%20io.open(arg%5B2%5D%2C%20%22rb%22)%0D%0A%09if%20not%20f%20then%0D%0A%09%09print(%22Failed%20to%20open%20file%3A%20%22..arg%5B2%5D)%0D%0A%09else%0D%0A%09%09local%20code%20%3D%20f%3Aread(%22*a%22)%0D%0A%09%09print(ungolfify(code))%0D%0A%09end%0D%0Aelse%0D%0A%09print(%22Syntax%3A%20pluto%20vortex.pluto%20%5Brun%7Cgolfify%7Cungolfify%5D%20%3Cscript%3E%22)%0D%0Aend%0D%0A)
