# Mindarc DevTest

## Exercise 1

Tools Used: HTML, CSS

### Run Locally

Run Live Server in `exercise-1` directory or open `exercise-1/index.html` file.

## Exercise 2

Tools Used: Vue (Vue CLI), Sass (SCSS)

### Run Locally

Clone the project

```bash
  git clone https://github.com/eefrontend/frontend-assessment.git
```

Go to the `exercise-2` directory

```bash
  cd frontend-assessment/exercise-2
```

Install dependencies

```bash
  yarn install
```

Start the server

```bash
  yarn serve
```

Open <http://localhost:8080/>

## Explain why the result of `('b' + 'a' + + 'a' + 'a').toLowerCase()` is `banana`

Adding `+` infront of a string coerces it into a number if it's in the right format, otherwise it will return `NaN`.

```js
+"1"; // 1
+"a"; // NaN
```

In this example `('b' + 'a' + + 'a' + 'a').toLowerCase()`, `+ 'a'` was evaluated to `NaN` so the string resulted into `"baNaNa"`. After converting to lowercase, `banana`.
