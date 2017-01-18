eslint-plugin-dom
=====================
[![Build Status](https://travis-ci.org/amilajack/eslint-plugin-dom.svg?branch=master)](https://travis-ci.org/amilajack/eslint-plugin-dom)
[![Build status](https://ci.appveyor.com/api/projects/status/0suu7sewpme8mp6t/branch/master?svg=true)](https://ci.appveyor.com/project/amilajack/eslint-plugin-dom/branch/master)
[![NPM version](https://badge.fury.io/js/eslint-plugin-dom.svg)](http://badge.fury.io/js/eslint-plugin-dom)
[![Dependency Status](https://img.shields.io/david/amilajack/eslint-plugin-dom.svg)](https://david-dm.org/amilajack/eslint-plugin-dom)
[![npm](https://img.shields.io/npm/dm/eslint-plugin-dom.svg)](https://npm-stat.com/charts.html?package=eslint-plugin-dom)

**⚠️ WORK IN PROGRESS ⚠️**

## Goals
 - Use static analysis to detect forced reflow. Suggest requestAnimationFrame
 - Warn when using forcing sync layout calculation (ex. offsetLeft)
 - Warn against general perf issues, ex. `document.write()`

## Idea
```
 22:  const elem = document.querySelector('.some')
 23:  elem.offsetLeft
           ^^^^^^^^^^   `offsetLeft` will trigger synchronous style and layout calculation
```

```
 34:  const h1 = element1.clientHeight;
 35:  element1.style.height = `${h1 * 2}px`;
 36:  const h2 = element2.clientHeight;
                 ^^^^^^^^^^^^^^^^^^^^^^  Forced reflow will occur. Layout invalidated at line 35.
                                         Use requestAnimationFrame() to prevent this
```
