# Jeito ótimo de estruturar os arquivos num projeto React

Fonte: https://medium.com/@Charles_Stover/optimal-file-structure-for-react-applications-f3e35ad0a145

## Public

Guarde arquivos estáticos, que nunca serão importados por um documento javascript, e nunca terão seus nomes modificados no pc do usuário. Estes arquivos irão para o cache do usuário.

## src

```
src
├── assets
│ └──images
│ └── logo.svg
├── components
│ └── app
│ ├── app.css
│ ├── app.js
│ └── app.test.js
├── index.css
├── index.js
└── service-worker.js
```

## src/assets

Arquivos compartilhados pela aplicação. São imagens, SASS, etc. É geralmente o diretório onde há o contato com outros profissionais não-programadores, como os designers.

## src/utils

Funções JS prontas, usadas globalmente no projeto. Também chamado de src/helpers ou src/packages em alguns projetos.

## src/components

App tb é component. Pasta única. Todos os Components estão nela.

## src/components/ComponentName

Árvore hierárquica da pasta de cada Component (capitalize it!):

```
my-app
└── src
└── components
└── ComponentName
├── ComponentName.css
├── ComponentName.scss
├── ComponentName-container.js
├── ComponentName-redux.js
├── ComponentName-styles.js
├── ComponentName-view.js
└── index.js
```

### src/components/ComponentName/index.js

A única função do index.js é exportar o maior arquivo hierárquico.
`export { default } from './Foobar';`

### src/components/ComponentName/ComponentName-view.js

São os stateless components. São funções puras. A maioria dos casos.

### src/components/ComponentName/ComponentName-styles.js

Aqui ficam JSS. JSS é o css dentro do javascript `const StyledButton = injectSheet(styles)(Button)`.
Comum em algumas libs, como MaterialUI.

### src/components/ComponentName/ComponentName-redux.js

São os mapStateToProps, mapDispatchToProps e connect do Redux.

### src/components/ComponentName/ComponentName-container.js

São os stateful components. As classes.

## src/components/ComponentName/SubComponent

Os sub-componentes possuirão os files com o nome do component e do subcomponent.
Ex:

```
github-repo
├── icon
│ ├── github-repo-icon.scss
│ ├── github-repo-icon-view.js
│ └── index.js
├── title
│ ├── github-repo-title.scss
│ ├── github-repo-title-view.js
│ └── index.js
├── github-repo.scss
├── github-repo-view.js
└── index.js
```

Acima, github-repo é um component, e icon é um subcomponent.

## src/routes

Aonde ficam as rotas do react router.

## Tests

Testes unitários dos arquivos ficam juntos com os arquivos.
Ex:

```
my-app
└── src
└── components
└── component-name
├── component-name-container.js
├── component-name-container.test.js
├── component-name-redux.js
├── component-name-redux.test.js
├── component-name-view.js
└── component-name-view.test.js
```
