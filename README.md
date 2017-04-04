# api documentation for  [mockery (v2.0.0)](https://github.com/mfncooper/mockery)  [![npm package](https://img.shields.io/npm/v/npmdoc-mockery.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-mockery) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-mockery.svg)](https://travis-ci.org/npmdoc/node-npmdoc-mockery)
#### Simplifying the use of mocks with Node.js

[![NPM](https://nodei.co/npm/mockery.png?downloads=true)](https://www.npmjs.com/package/mockery)

[![apidoc](https://npmdoc.github.io/node-npmdoc-mockery/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-mockery_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-mockery/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-mockery/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-mockery/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Martin Cooper",
        "email": "mfncooper@gmail.com"
    },
    "bugs": {
        "url": "http://github.com/mfncooper/mockery/issues"
    },
    "contributors": [
        {
            "name": "Bryan Donovan",
            "email": "bdondo@gmail.com"
        },
        {
            "name": "Dav Glass",
            "email": "davglass@gmail.com"
        }
    ],
    "dependencies": {},
    "description": "Simplifying the use of mocks with Node.js",
    "devDependencies": {
        "istanbul": "~0.3.5",
        "jshint": "~2.6.0",
        "sinon": "1.2.x",
        "unix-dgram": "^0.2.3",
        "vows": "~0.8.1"
    },
    "directories": {},
    "dist": {
        "shasum": "0569a11a1848461fdc347cf8cca2df2f3129bc03",
        "tarball": "https://registry.npmjs.org/mockery/-/mockery-2.0.0.tgz"
    },
    "gitHead": "ad2d72710c6ac433bb9ee24680acbfaf7ef03f63",
    "homepage": "https://github.com/mfncooper/mockery",
    "jshintConfig": {
        "node": true
    },
    "keywords": [
        "mock",
        "stub",
        "require",
        "module",
        "cache",
        "unit",
        "test",
        "unittest",
        "testing",
        "tdd"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "http://github.com/mfncooper/mockery/raw/master/LICENSE"
        }
    ],
    "main": "mockery.js",
    "maintainers": [
        {
            "name": "bengl",
            "email": "bryan@bryanenglish.com"
        },
        {
            "name": "davglass",
            "email": "davglass@gmail.com"
        },
        {
            "name": "gotwarlost",
            "email": "kananthmail-github@yahoo.com"
        },
        {
            "name": "mfncooper",
            "email": "mfncooper@gmail.com"
        }
    ],
    "name": "mockery",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/mfncooper/mockery.git"
    },
    "scripts": {
        "pretest": "jshint mockery.js ./test/*.js",
        "test": "istanbul cover --print both -- vows --spec ./test/*.js"
    },
    "version": "2.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module mockery](#apidoc.module.mockery)
1.  [function <span class="apidocSignatureSpan">mockery.</span>deregisterAll ()](#apidoc.element.mockery.deregisterAll)
1.  [function <span class="apidocSignatureSpan">mockery.</span>deregisterAllowable (mod)](#apidoc.element.mockery.deregisterAllowable)
1.  [function <span class="apidocSignatureSpan">mockery.</span>deregisterAllowables (mods)](#apidoc.element.mockery.deregisterAllowables)
1.  [function <span class="apidocSignatureSpan">mockery.</span>deregisterMock (mod)](#apidoc.element.mockery.deregisterMock)
1.  [function <span class="apidocSignatureSpan">mockery.</span>deregisterSubstitute (mod)](#apidoc.element.mockery.deregisterSubstitute)
1.  [function <span class="apidocSignatureSpan">mockery.</span>disable ()](#apidoc.element.mockery.disable)
1.  [function <span class="apidocSignatureSpan">mockery.</span>enable (opts)](#apidoc.element.mockery.enable)
1.  [function <span class="apidocSignatureSpan">mockery.</span>registerAllowable (mod, unhook)](#apidoc.element.mockery.registerAllowable)
1.  [function <span class="apidocSignatureSpan">mockery.</span>registerAllowables (mods, unhook)](#apidoc.element.mockery.registerAllowables)
1.  [function <span class="apidocSignatureSpan">mockery.</span>registerMock (mod, mock)](#apidoc.element.mockery.registerMock)
1.  [function <span class="apidocSignatureSpan">mockery.</span>registerSubstitute (mod, subst)](#apidoc.element.mockery.registerSubstitute)
1.  [function <span class="apidocSignatureSpan">mockery.</span>resetCache ()](#apidoc.element.mockery.resetCache)
1.  [function <span class="apidocSignatureSpan">mockery.</span>warnOnReplace (enable)](#apidoc.element.mockery.warnOnReplace)
1.  [function <span class="apidocSignatureSpan">mockery.</span>warnOnUnregistered (enable)](#apidoc.element.mockery.warnOnUnregistered)



# <a name="apidoc.module.mockery"></a>[module mockery](#apidoc.module.mockery)

#### <a name="apidoc.element.mockery.deregisterAll"></a>[function <span class="apidocSignatureSpan">mockery.</span>deregisterAll ()](#apidoc.element.mockery.deregisterAll)
- description and source-code
```javascript
function deregisterAll() {
    Object.keys(registeredAllowables).forEach(function (mod) {
        var allow = registeredAllowables[mod];
        if (allow.unhook) {
            allow.paths.forEach(function (p) {
                delete m._cache[p];
            });
        }
    });

    registeredMocks = {};
    registeredSubstitutes = {};
    registeredAllowables = {};
}
```
- example usage
```shell
...

## Deregistering everything

Since it's such a common use case, especially when you're using a unit test
framework and its setup and teardown functions, Mockery provides a convenience
function to deregister everything:

    mockery.deregisterAll();

This will deregister all mocks, substitutes, and allowable modules, as well as
unhooking any hooked modules.

## Controlling the module cache

One of the common problems that people encounter when trying to use mocks in
...
```

#### <a name="apidoc.element.mockery.deregisterAllowable"></a>[function <span class="apidocSignatureSpan">mockery.</span>deregisterAllowable (mod)](#apidoc.element.mockery.deregisterAllowable)
- description and source-code
```javascript
function deregisterAllowable(mod) {
    if (registeredAllowables.hasOwnProperty(mod)) {
        var allow = registeredAllowables[mod];
        if (allow.unhook) {
            allow.paths.forEach(function (p) {
                delete m._cache[p];
            });
        }
        delete registeredAllowables[mod];
    }
}
```
- example usage
```shell
...

    mockery.registerAllowable('./my-source-under-test');

As with 'registerMock' and 'registerSubstitute', the first argument, _module_,
is the name or path of the module as it would be provided to 'require'. Once
again, you can deregister it if you need to:

    mockery.deregisterAllowable('./my-source-under-test');

Sometimes you'll find that you need to register several modules at once. A
convenience function lets you do this with a single call:

    mockery.registerAllowables(['async', 'path', 'util']);

and similarly to deregister several modules at once, as you would expect:
...
```

#### <a name="apidoc.element.mockery.deregisterAllowables"></a>[function <span class="apidocSignatureSpan">mockery.</span>deregisterAllowables (mods)](#apidoc.element.mockery.deregisterAllowables)
- description and source-code
```javascript
function deregisterAllowables(mods) {
    mods.forEach(function (mod) {
        deregisterAllowable(mod);
    });
}
```
- example usage
```shell
...
Sometimes you'll find that you need to register several modules at once. A
convenience function lets you do this with a single call:

    mockery.registerAllowables(['async', 'path', 'util']);

and similarly to deregister several modules at once, as you would expect:

    mockery.deregisterAllowables(['async', 'path', 'util']);

### Unhooking

By default, the Node module loader will load a given module only once, caching
the loaded module for the lifetime of the process. When you're using Mockery,
this is almost always what you want. _Almost_. In relatively rare situations,
you may find that you need to use different mocks for different test cases
...
```

#### <a name="apidoc.element.mockery.deregisterMock"></a>[function <span class="apidocSignatureSpan">mockery.</span>deregisterMock (mod)](#apidoc.element.mockery.deregisterMock)
- description and source-code
```javascript
function deregisterMock(mod) {
    if (registeredMocks.hasOwnProperty(mod)) {
        delete registeredMocks[mod];
    }
}
```
- example usage
```shell
...
"clever" matching.
* _mock_, the mock to be provided. Whatever is provided here is what will
become the result of subsequent 'require' calls; that is, the 'exports' of the
module.

If you no longer want your mock to be used, you can deregister it:

    mockery.deregisterMock('fs');

Now the original module will be provided for any subsequent 'require' calls.

## Registering substitutes

Sometimes you want to implement your mock itself as a module, especially if it's
more complicated and you'll be reusing it more widely. In that case, you can
...
```

#### <a name="apidoc.element.mockery.deregisterSubstitute"></a>[function <span class="apidocSignatureSpan">mockery.</span>deregisterSubstitute (mod)](#apidoc.element.mockery.deregisterSubstitute)
- description and source-code
```javascript
function deregisterSubstitute(mod) {
    if (registeredSubstitutes.hasOwnProperty(mod)) {
        delete registeredSubstitutes[mod];
    }
}
```
- example usage
```shell
...
* _module_, the name or path of the module for which a substitute is being
registered. This must exactly match the argument to 'require'; there is no
"clever" matching.
* _substitute_, the name or path of the module to substitute for _module_.

If you no longer want your substitute to be used, you can deregister it:

    mockery.deregisterSubstitute('fs');

Now the original module will be provided for any subsequent 'require' calls.

## Registering allowable modules

If you enable Mockery and _don't_ mock or substitute a module that is later
loaded via 'require', Mockery will print a warning to the console to tell you
...
```

#### <a name="apidoc.element.mockery.disable"></a>[function <span class="apidocSignatureSpan">mockery.</span>disable ()](#apidoc.element.mockery.disable)
- description and source-code
```javascript
function disable() {
    if (!originalLoader) {
        // Not hooked
        return;
    }

    if (options.useCleanCache) {
        // Previously this just set m._cache to originalCache. This would make
        // node re-require native addons that were required while mockery was
        // enabled, which breaks it in node@>=0.12. Instead populate
        // originalCache with any native addons that were first required since
        // mockery was enabled.
        Object.keys(m._cache).forEach(function(k){
            if (k.indexOf('\.node') > -1 && !originalCache[k]) {
                originalCache[k] = m._cache[k];
            }
        });
        removeParentReferences();
        m._cache = originalCache;
        originalCache = null;
    }

    m._load = originalLoader;
    originalLoader = null;
}
```
- example usage
```shell
...
Mockery in the test setup and teardown functions for your test cases. Something
like this:

    setUp: function() {
        mockery.enable();
    },
    tearDown: function() {
        mockery.disable();
    }

### Options

You can set up some initial configuration by passing an options object to
'enable'. Omitting the options object, or any of the defined keys, causes the
standard defaults to be used.
...
```

#### <a name="apidoc.element.mockery.enable"></a>[function <span class="apidocSignatureSpan">mockery.</span>enable (opts)](#apidoc.element.mockery.enable)
- description and source-code
```javascript
function enable(opts) {
    if (originalLoader) {
        // Already hooked
        return;
    }

    options = getEffectiveOptions(opts);

    if (options.useCleanCache) {
        originalCache = m._cache;
        m._cache = {};
        repopulateNative();
    }

    originalLoader = m._load;
    m._load = hookedLoader;
}
```
- example usage
```shell
...
your usage as narrowly as possible.

If you're using a typical unit testing framework, you might enable and disable
Mockery in the test setup and teardown functions for your test cases. Something
like this:

    setUp: function() {
        mockery.enable();
    },
    tearDown: function() {
        mockery.disable();
    }

### Options
...
```

#### <a name="apidoc.element.mockery.registerAllowable"></a>[function <span class="apidocSignatureSpan">mockery.</span>registerAllowable (mod, unhook)](#apidoc.element.mockery.registerAllowable)
- description and source-code
```javascript
function registerAllowable(mod, unhook) {
    registeredAllowables[mod] = {
        unhook: !!unhook,
        paths: []
    };
}
```
- example usage
```shell
...
that. This is so that you don't inadvertently use downstream modules without
being aware of them. By registering a module as "allowable", you tell Mockery
that you know about its use, and then Mockery won't print the warning.

The most common use case for this is your source-under-test, which obviously
you'll want to load without warnings. For example:

mockery.registerAllowable('./my-source-under-test');

As with 'registerMock' and 'registerSubstitute', the first argument, _module_,
is the name or path of the module as it would be provided to 'require'. Once
again, you can deregister it if you need to:

mockery.deregisterAllowable('./my-source-under-test');
...
```

#### <a name="apidoc.element.mockery.registerAllowables"></a>[function <span class="apidocSignatureSpan">mockery.</span>registerAllowables (mods, unhook)](#apidoc.element.mockery.registerAllowables)
- description and source-code
```javascript
function registerAllowables(mods, unhook) {
    mods.forEach(function (mod) {
        registerAllowable(mod, unhook);
    });
}
```
- example usage
```shell
...
again, you can deregister it if you need to:

    mockery.deregisterAllowable('./my-source-under-test');

Sometimes you'll find that you need to register several modules at once. A
convenience function lets you do this with a single call:

    mockery.registerAllowables(['async', 'path', 'util']);

and similarly to deregister several modules at once, as you would expect:

    mockery.deregisterAllowables(['async', 'path', 'util']);

### Unhooking
...
```

#### <a name="apidoc.element.mockery.registerMock"></a>[function <span class="apidocSignatureSpan">mockery.</span>registerMock (mod, mock)](#apidoc.element.mockery.registerMock)
- description and source-code
```javascript
function registerMock(mod, mock) {
    if (options.warnOnReplace && registeredMocks.hasOwnProperty(mod)) {
        console.warn("WARNING: Replacing existing mock for module: " + mod);
    }
    registeredMocks[mod] = mock;
}
```
- example usage
```shell
...

You register your mocks with Mockery to tell it which mocks to provide for which
'require' calls. For example:

    var fsMock = {
        stat: function (path, cb) { /* your mock code */ }
    };
    mockery.registerMock('fs', fsMock);

The arguments to 'registerMock' are as follows:

* _module_, the name or path of the module for which a mock is being
registered. This must exactly match the argument to 'require'; there is no
"clever" matching.
* _mock_, the mock to be provided. Whatever is provided here is what will
...
```

#### <a name="apidoc.element.mockery.registerSubstitute"></a>[function <span class="apidocSignatureSpan">mockery.</span>registerSubstitute (mod, subst)](#apidoc.element.mockery.registerSubstitute)
- description and source-code
```javascript
function registerSubstitute(mod, subst) {
    if (options.warnOnReplace && registeredSubstitutes.hasOwnProperty(mod)) {
        console.warn("WARNING: Replacing existing substitute for module: " + mod);
    }
    registeredSubstitutes[mod] = {
        name: subst
    };
}
```
- example usage
```shell
...

## Registering substitutes

Sometimes you want to implement your mock itself as a module, especially if it's
more complicated and you'll be reusing it more widely. In that case, you can
tell Mockery to substitute that module for the original one. For example:

    mockery.registerSubstitute('fs', 'fs-mock');

Now any 'require' invocation for 'fs' will be satisfied by loading the 'fs-mock'
module instead.

The arguments to 'registerSubstitute' are as follows:

* _module_, the name or path of the module for which a substitute is being
...
```

#### <a name="apidoc.element.mockery.resetCache"></a>[function <span class="apidocSignatureSpan">mockery.</span>resetCache ()](#apidoc.element.mockery.resetCache)
- description and source-code
```javascript
function resetCache() {
    if (options.useCleanCache && originalCache) {
        removeParentReferences();
        m._cache = {};
        repopulateNative();
    }
}
```
- example usage
```shell
...
disabled. The original cache is reinstated at that point, so you are back to
where you were before enabling the clean cache option.

While you are working with a temporary cache, it may occasionally be useful to
reset it to a clean state again, without disabling and re-enabling Mockery. You
can do this with:

    mockery.resetCache();

This function has no effect if the clean cache option is not already in use.

## Disabling warnings

As mentioned above, if you enable Mockery and _don't_ mock, substitute, or
allow a module that is later loaded, Mockery will print a warning to the
...
```

#### <a name="apidoc.element.mockery.warnOnReplace"></a>[function <span class="apidocSignatureSpan">mockery.</span>warnOnReplace (enable)](#apidoc.element.mockery.warnOnReplace)
- description and source-code
```javascript
function warnOnReplace(enable) {
    options.warnOnReplace = enable;
}
```
- example usage
```shell
...

Mockery will also print a warning to the console whenever you register a mock
or substitute for a module for which one is already registered. This is almost
always what you want, since you should be deregistering mocks and substitutes
that you no longer need. Occasionally, though, you may want to suppress these
warnings, which you can do like this:

    mockery.warnOnReplace(false);

In either of these cases, if you later need to re-enable the warnings, then
passing 'true' to the same functions will do that, as you might imagine.

## The name

Mockery is to mocks as rookery is to rooks.
...
```

#### <a name="apidoc.element.mockery.warnOnUnregistered"></a>[function <span class="apidocSignatureSpan">mockery.</span>warnOnUnregistered (enable)](#apidoc.element.mockery.warnOnUnregistered)
- description and source-code
```javascript
function warnOnUnregistered(enable) {
    options.warnOnUnregistered = enable;
}
```
- example usage
```shell
...
so that you don't end up using modules you weren't aware of.

In certain circumstances, such as when writing functional or integration tests,
you may find it irritating to have to allow each module or to have all the
warnings appear on the console. If you need to, you can tell Mockery to turn
off those warnings:

    mockery.warnOnUnregistered(false);

Mockery will also print a warning to the console whenever you register a mock
or substitute for a module for which one is already registered. This is almost
always what you want, since you should be deregistering mocks and substitutes
that you no longer need. Occasionally, though, you may want to suppress these
warnings, which you can do like this:
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
