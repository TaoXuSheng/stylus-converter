<div  align="center">
  <img src="../banner.png"></img>
</div>

<p align="center">
  <a href="http://img.shields.io/travis/txs1992/stylus-converter.svg">
    <img src="http://img.shields.io/travis/txs1992/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/dt/stylus-converter.svg">
    <img src="https://img.shields.io/npm/dt/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/dm/stylus-converter.svg">
    <img src="https://img.shields.io/npm/dm/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/v/stylus-converter.svg">
    <img src="https://img.shields.io/npm/v/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/l/stylus-converter.svg">
    <img src="https://img.shields.io/npm/l/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/node/v/passport.svg">
    <img src="https://img.shields.io/node/v/passport.svg" />
  </a>
</p>

<div align="center">
  <h3>
    <a href="https://github.com/txs1992/stylus-converter">
      中文
    </a>
    <span> | </span>
    <a href="https://github.com/txs1992/stylus-converter/blob/master/doc/en-us.md#readme">
      English
    </a>
  </h3>
</div>

## Why do this tool

> Since early projects used stylus, stylus is very cool to develop，but the stylus-based indentation code is not very convenient at the time of the modification, plus the team development and use of SCSS, in order to facilitate maintenance and unification, ready to replace the project stylus to SCSS. However, I am very lazy, manual conversion of stylus is a waste of time, and the error rate is large，So this project was born. **Please use your little fortunate hand and give me a `star`. Be grateful.^_^**

## stylus-converter config

### converter options

| Attribute | Description | Type | Accepted Values | Default |
| ---- | ---- | ---- | ---- | ---- |
| `quote` | The quote type to use when converting strings | string | `'` / `"` | `'` |
| `conver` | Conversion type, such as conversion to scss syntax | string | scss | scss |
| `autoprefixer ` | Whether or not to automatically add a prefix, stylus will automatically add prefixes when converting stylus grammars. `@keyframes` | boolean | true / false | true |

### cli options

| Attribute | Shorthand | Description | Accepted Values | Default |
| ---- | ---- | ---- | ---- | ---- |
| `--quote` | `-q` | The quote type to use when converting strings | single / dobule | single |
| `--input` | `-i` | Enter a name, which can be a path to a file or a folder | - | - |
| `--output` | `-o` | Output name, can be a path to a file or a folder | - | - |
| `--conver ` | `-c` | Conversion type, such as conversion to scss syntax | scss | scss |
| `--directory` | `-d` | Whether the input and output paths are directories | yes / no | no |
| `--autoprefixer ` | `-p` | Whether to add a prefix | yes / no | yes |

## Use examples

```javascript
// download stylus-converter
npm install -g stylus-converter

// Run the cli conversion file
stylus-conver -i test.styl -o test.scss
```

## Conversion file comparison

### Stylus source code before conversion

```stylus
handleParams(args...)
  args

@media screen and (max-width: 500px) and (min-width: 100px), (max-width: 500px) and (min-height: 200px)
  .foo
    color: #100

.foo
  for i in 1..4
    @media (min-width: 2 * (i + 7) px)
```

### Converted sass source code

```scss
@function handleParams($args...) {
  @return $args;
}

@media screen and (max-width: 500px) and (min-width: 100px), (max-width: 500px) and (min-height: 200px) {
  .foo {
    color: #100;
  }
}

.foo {
  @for $i from 1 through 4 {
    @media (min-width: 2 * ($i + 7) px) {
      width: 100px * $i;
    }
  }
}
```

> If you do not want to add the default prefix for your converted @keyframes, please set `options.autoprefixer = false`

### The `.vue` file before conversion

```html
<template>
  <div class="page-home">
    <el-button>click me</el-button>
  </div>
</template>

<style lang="stylus">
.page-home
  .el-button
    margin: 10px auto
</style>
```

### Converted `.vue`  file

```html
<template>
  <div class="page-home">
    <el-button>click me</el-button>
  </div>
</template>

<style lang="scss">
.page-home {
  .el-button {
    margin: 10px auto;
  }
}
</style>
```

## Build a development environment

```text
1. First fork project and then clone project to local
git clone git@github.com:<your github>/stylus-converter.git

2. Enter the project directory
cd stylus-converter

3. Installation project depends
npm install

4. Package compilation source file
npm run build

5. Local debugging cli
npm link
```