# Create init source with Nextjs

## **1/ Set up a new Next.js project**

Assuming you have Node.js and npm installed, you can create a new Next.js project using the following command:

```
npx create-next-app@12.3.4 --ts
```

## 2/ Setup testing

For testing, you can use frameworks like Jest and Testing Library. To install these, use the following command:

```bash
yarn add --dev jest ts-jest @testing-library/react @testing-library/jest-dom @testing-library/user-event
```

Set up testing scripts:

```json
"scripts": {
  "test": "jest",
  "test:watch": "jest --watch",
  "test:coverage": "jest --coverage"
},
```
