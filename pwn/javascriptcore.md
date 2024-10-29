## debugging
### with vscode
https://browser.training.ret2.systems/content/module_1/2_building/exercises/building_jsc#building-jsc
- set up debugging with vscode
### bytecode tracing
https://zon8.re/posts/jsc-internals-part1-tracing-js-source-to-bytecode/
- tracing how js source gets compiled to bytecode
### CVE 2017-2446
https://doar-e.github.io/blog/2018/07/14/cve-2017-2446-or-jscjsglobalobjectishavingabadtime/
- exploits internal appendMemcpy function
## dollarVm
- enable set `JSC_useDollarVM=true` in env or pass `--useDollarVM=1` on the cmdline
### functions
https://github.com/WebKit/WebKit/blob/8471a1156fd686d067c8ac4b6ce60b919738db76/Source/JavaScriptCore/builtins/BuiltinNames.h
### builtin functions
https://github.com/WebKit/WebKit/blob/7b4e2500f1524427c59dddd6d5362ee5008dba8a/Source/JavaScriptCore/bytecode/BytecodeIntrinsicRegistry.h#L94
### exploitation
#### createBuiltin
```js
var appendMemcpy = $vm.createBuiltin("(function (){ return @appendMemcpy; })")();
// > appendMemcpy
// [Function: appendMemcpy]
// reference to internal appendMemcpy that does not do any typechecking
// see CVE 2017-2446
```