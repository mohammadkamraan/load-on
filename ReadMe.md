# Load-on

Load-on is a React package that manages which components should be downloaded and rendered for different device sizes. It ensures that each device downloads and uses only the files and styles that are needed, making it perfect for large-scale apps with different styling requirements for responsive design.

## Features

- **Responsive Design Management**: Load-on simplifies responsive design by allowing you to specify components for different device sizes, ensuring optimal rendering for each screen.
- **Efficient Resource Loading**: Only the necessary components and styles for the target device sizes are downloaded, optimizing the performance of your application.

- **Perfect for Large-Scale Apps**: Ideal for large-scale applications with diverse styling requirements for responsive design.

- **Component Lazy Loading**: Load-on supports lazy loading for components using the `lazy` function from React, enhancing the overall performance and user experience.

- **Intuitive API**: With a straightforward API, Load-on makes it easy to manage which components should be displayed based on the user's device size.

- **Fallback Component Support**: Include fallback components to display while the specified component is being downloaded.

- **Customizable Size Ranges**: Define your responsive design size ranges using intuitive size descriptors like `sm`, `md`, `lg`, `xl`, and `2xl`.

## Props

- **`children`**: `ReactNode` (required) - The component that will be rendered for the specified device size.
- **`fallback`**: `ReactNode` (optional) - The fallback component to show when the specified component is still downloading.
- **`from`**: `"sm" | "md" | "lg" | "xl" | "2xl"` (required) - The starting size for responsive design.
- **`to`**: `"sm" | "md" | "lg" | "xl" | "2xl"` (required) - The ending size for responsive design.

### Size Ranges

- `sm` range: 1px to 640px
- `md` range: 640px to 748px
- `lg` range: 768px to 1024px
- `xl` range: 1024px to 1280px
- `2xl` range: 1280px to 5000px

## Installation

Install `load-on` using npm:

```
npm install load-on
```

## Usage

```bash
import lazy from 'react';
import LoadOn from 'load-on';

const WebComponents = lazy(() => import('./components/web'));
const MobileComponent = lazy(() => import('./components/mobile'));

const App = () => {
  return (
    <>
      <LoadOn from='md' to='lg'>
        <WebComponents />
      </LoadOn>
      <LoadOn from='sm' to='sm'>
        <MobileComponent />
      </LoadOn>
    </>
  );
}
```

## Important Note

Your components that are passed as children to `LoadOn` should be imported lazily using `lazy` from React; otherwise, the `load-on` package won't work as expected.
