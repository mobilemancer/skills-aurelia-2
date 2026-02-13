---
name: aurelia-2
description: Expert guidance for building modern web applications with Aurelia 2 framework. Use when working with Aurelia 2 projects, including project setup, component development, routing, dependency injection, templating, state management, and best practices.
---

# Aurelia 2 Skill

This skill provides expert guidance for developing web applications using the Aurelia 2 framework.

## Overview

Aurelia 2 is a modern, forward-thinking JavaScript framework for building web applications. This skill helps with:

- Project setup and configuration
- Component development and lifecycle
- Templating and data binding
- Routing and navigation
- Dependency injection
- State management
- Testing strategies
- Best practices and patterns

## Start new Project

I prefer the following steps to get started with Aurelia 2, and have a opinionated setup for projects:
```bash
npx makes aurelia new-project-name --here -s vitest,playwright,app-with-router
```

## Build and Test
To build the project, use the following command:
```bash
npm run build
```
To run the development server, use the following command:
```bash
npm start
```
To run unit tests, use the following command:
```bash
npm run test
```
To run end-to-end tests, use the following command:
```bash
npm run test:e2e
```

After every task that is implemented, make sure to write tests for it.
After every task and test implementation, make sure to build the app, then run all tests.

## Component Development

All components consists of three files, a .ts file, a .html file and a .css file.
For styling we use vanilla CSS, and we scope the styles to the component by using the component name in the .css file and then nesting all styles inside it.
```css
my-component {
  /* styles here */
}
```

Components needs to be available in the DI container, or they won't render.
There are two main ways to get components into the DI container:

```ts
DI.configure({
  register: [
    MyComponent
  ]
});
```
or
```html
<import from="./my-component"></import>
```

## Routing

Use standard Aurelia 2 routing patterns.

## Dependency Injection

Use the resolve() method to inject dependencies into components and services.
```ts
import { resolve } from 'aurelia';

private ea = resolve(IEventAggregator);
```
## Templating

The .call syntax does not work in Aurelia 2, so use the .bind syntax instead for event handlers and data binding.
```html
<agent-card repeat.for="agent of agents" agent.bind="agent" loading-agent-id.bind="loadingAgentId"
              on-edit.bind="(args) => openAgentPanel(args.agent, args.event)"
              on-chat.bind="(args) => startChat(args.agent, args.event)">
</agent-card>
```

The .delegate syntax is deprecated, use .trigger instead.
```html
<button click.trigger="handleClick()">Click Me</button>
```

## Best Practices

Use feature folders to organize components, services, and related files together.
Keep components small and focused.
Reuse components when possible, and avoid duplication.
For reused components, those should reside in a folder holding shared components.
Create services that are small and focused.
Some services will be shared across the app, and those should reside in a folder holding shared services, while other services will be specific to a feature, and those should reside in the feature folder.
Use Aurelia's dependency injection to manage dependencies and promote testability.
Use Aurelia's templating features to create clean and maintainable views, avoid complex logic in the viewmodels, when it's possible to solve in the template, do it in the template.
Cache service data when possible, be mindful of memory usage and cache invalidation strategies.
Use Aurelia's lifecycle hooks to manage component state and behavior effectively. Be mindful of the component lifecycle and use hooks like `created()`, `bind()`, `attached()`, `detached()`, and `unbind()` to manage resources and state.
Write unit tests for components and services to ensure reliability and maintainability.

Lifecycle hooks best practices:
- Prefer early exits—perform checks at the start of hooks and return early to minimise nesting.
- Clean up observers, timeouts, event listeners, or 3rd-party widgets in the opposite hook (unbinding/detaching or dispose).
- Avoid heavy work in the constructor. Move anything needing bindables or DOM to later hooks.
- Mark hooks async and await your operations instead of manually creating Promises for clarity.
- Keep hooks fast—expensive work can block the component hierarchy.

Router lifecycle hooks best practices:
Using the canLoad and canUnload hooks you can determine whether to allow or disallow navigation to and from a route respectively. The loading, loaded, and unloading hooks are meant to be used for performing setup, post-activation work, and clean up activities for a view. Note that all of these hooks can return a promise, which will be awaited by the router pipeline.

## Resources

- References: See `references/` folder for detailed documentation
- Scripts: See `scripts/` folder for helper scripts
- Assets: See `assets/` folder for templates and boilerplate
