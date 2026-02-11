# Tailblocks
### Ready-to-use Tailwind CSS blocks
##### Features

* 60+ Blocks
* Responsive
* Dark Mode Support
* Color Variations

## How to use this project

[![tailblocks](https://github.com/mertjf/tailblocks/blob/master/public/preview.gif)](https://tailblocks.cc)

This project provides multiple blocks built using [Tailwind
CSS](https://tailwindcss.com/) that you can use in your own projects. This
project is not a dependency that you add to your project, but instead provides
you with HTML that you can easily copy and paste into your own project.

To use the project:

1. Go to the [Tailblocks](https://tailblocks.cc)
1. Select a block that you would like to use.
1. Choose a color from the color palette for the block you selected.
1. Select whether you would like to use light or dark mode with the dark/light toggle button.
1. Click the "View Code" button.
1. Copy/paste into your project.
1. 🎉


## Development

### Prerequisites

- [Node.js](https://nodejs.org/) (v12+)
- [Yarn](https://yarnpkg.com/)

### Setup

```bash
git clone https://github.com/affonso/tailblocks-ltu.git
cd tailblocks-ltu
yarn install
```

### Commands

| Command | Description |
|---------|-------------|
| `yarn start` | Start development server |
| `yarn build` | Create production build |
| `yarn test` | Run tests |
| `yarn deploy` | Build and deploy to GitHub Pages |

### Project Structure

```
src/
├── App.js              # Main application component
├── index.css           # Global styles and theme variables
├── blocks/             # Tailwind CSS block components
│   ├── index.js        # Block registry
│   └── <category>/
│       ├── light/      # Light mode variants
│       └── dark/       # Dark mode variants
└── icons/              # SVG thumbnail icons for the sidebar
    ├── index.js        # Icon registry
    └── <category>/
```

### Adding a New Block

1. Create the block component in `src/blocks/<category>/light/<letter>.js` and `src/blocks/<category>/dark/<letter>.js`. Each component receives a `theme` prop used in Tailwind classes (e.g., `` `text-${theme}-500` ``).
2. Create a sidebar thumbnail SVG in `src/icons/<category>/<letter>.js`.
3. Register imports and entries in both `src/blocks/index.js` and `src/icons/index.js`.

## License

Code copyright 2020 Mert Cukuren. Code released under [the MIT license](https://github.com/mertjf/tailblocks/blob/master/LICENSE).
