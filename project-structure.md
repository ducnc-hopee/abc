# Project structure

## 1/ Directory tree

```
├── public
├── src
   ├── assets
   ├── components
   │   ├── elements
   │   ├── features
   │   ├── layouts
   │   │   └── elements
   │   └── templates
   ├── constants
   ├── contexts
   ├── hooks
   ├── pages
   ├── store
   │   └── slices
   ├── styles
   ├── theme
   └── utils
```

## 2/ Guide

### 2.1/ public

Used to store static assets that you want to be publicly accessible from your web application.&#x20;

### 2.2/ src

Used to manage your application's core logic.

### 2.3/ assets

Used to store resources for the project, such as icons or images.

### 2.4/ components

We construct components using an architecture that Grouping files based on a feature structure.

#### 2.4.1/ components/elements

Used to store reusable components within the project such as: button, input,...

#### 2.4.2/ components/features

The folder is used to contain project features, and each feature folder is used to store all components related to that specific feature.

#### 2.4.3/ layouts

Used to store layouts used in the project. Additionally, you can create smaller elements of the layout within the 'layouts/elements' folder.

#### 2.5/ constants

Used to store constant values, configurations, or variables that are used throughout the project.

#### 2.6/ contexts

Use to store all API context in the project

#### 2.7/ hooks

Use to store all custom hooks in the project

#### **2.8/ pages**

Pages Router has a file-system based router built on concepts of pages. When a file is added to the `pages` directory it's automatically available as a route.

#### 2.9/ Store/slices

Is a specific part of the state managed by the reducer method. The reducer function extracts the current state and an action, then returns a new state based on that action.

#### 2.10/ Styles

Config styles for CSS module

#### 2.11/ Theme

Config styles for MUI or CSSProperties

#### 2.12/ utils

Utils folder consists of some repeatedly used functions that are commonly used in the project.
