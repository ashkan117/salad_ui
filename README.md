# SaladUI

This library is my attemp to port [shadcn ui](https://ui.shadcn.com/) to Phoenix Liveview Component.

**Warning: this library is under heavy development and not ready for production**

## [Demo at https://salad-storybook.fly.dev](https://salad-storybook.fly.dev/)

## Installation

1. Adding `salad_ui` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:salad_ui, github: "bluzky/salad_ui"}
  ]
end
```

2. Add custom color
- Goto [https://ui.shadcn.com/themes](https://ui.shadcn.com/themes).
- Choose a color → Copy code → Paste to your `app.css` file
- Create new file `tailwind.colors.json` in your assets directory and paste following content
```
{
  "accent": {
    "DEFAULT": "hsl(var(--accent))",
    "foreground": "hsl(var(--accent-foreground))"
  },
  "background": "hsl(var(--background))",
  "border": "hsl(var(--border))",
  "card": {
    "DEFAULT": "hsl(var(--card))",
    "foreground": "hsl(var(--card-foreground))"
  },
  "destructive": {
    "DEFAULT": "hsl(var(--destructive))",
    "foreground": "hsl(var(--destructive-foreground))"
  },
  "foreground": "hsl(var(--foreground))",
  "input": "hsl(var(--input))",
  "muted": {
    "DEFAULT": "hsl(var(--muted))",
    "foreground": "hsl(var(--muted-foreground))"
  },
  "popover": {
    "DEFAULT": "hsl(var(--popover))",
    "foreground": "hsl(var(--popover-foreground))"
  },
  "primary": {
    "DEFAULT": "hsl(var(--primary))",
    "foreground": "hsl(var(--primary-foreground))"
  },
  "ring": "hsl(var(--ring))",
  "secondary": {
    "DEFAULT": "hsl(var(--secondary))",
    "foreground": "hsl(var(--secondary-foreground))"
  }
}
```

3. Configure tailwind
- Tell tailwind to extract class from `SaladUI`
- Add custom color
- Add tailwind plugin
```
module.exports = {
  content: [
    "../deps/salad_ui/lib/**/*.ex",
    ],
  theme: {
    extend: {
      colors: require("./tailwind.colors.json"),
    },
  },
  plugins: [
    require("@tailwindcss/forms"),
    require("@tailwindcss/typography"),
    require("tailwindcss-animate"),
    ...
  ]
}
```

- Install `tailwindcss-animate`
```
cd assets
npm i -D tailwindcss-animate
# or yarn
yarn add -D tailwindcss-animate
```

4. Configure `tails`
SaladUI use `tails` to properly merge Tailwindcss classes

```elixir
# config/config.exs

config :tails, colors_file: Path.join(File.cwd!(), "assets/tailwind.colors.json")
```


## Development

Here is how to start develop SaladUI on local machine.

1. Clone this repo
2. Clone `https://github.com/bluzky/salad_storybook` in the same directory with `SaladUI`
3. Start storybook
```
cd salad_storybook
mix phx.server
```


## List of components

- [ ] Accordion
- [x] Alert
- [ ] Alert Dialog
- [x] Avatar
- [x] Badge
- [ ] Breadcrumb
- [x] Button
- [x] Card
- [ ] Carousel
- [x] Checkbox
- [ ] Collapsible
- [ ] Combobox
- [ ] Command
- [ ] Context Menu
- [x] Dialog
- [ ] Drawer
- [x] Dropdown Menu
- [x] Form
- [ ] Hover Card
- [x] Input
- [ ] Input OTP
- [x] Label
- [ ] Pagination
- [ ] Popover
- [ ] Progress
- [ ] Radio Group
- [ ] Scroll Area
- [x] Select
- [x] Separator
- [x] Sheet
- [ ] Skeleton
- [ ] Slider
- [ ] Switch
- [x] Table
- [x] Tabs
- [x] Textarea
- [ ] Tooltip
