# AI Development Rules

This document outlines the technical stack and specific rules for developing this web application. Following these guidelines ensures consistency, maintainability, and leverages the strengths of our chosen libraries.

## Tech Stack Overview

This is a modern web application built with the following technologies:

-   **Framework:** React with Vite for a fast and efficient development environment.
-   **Language:** TypeScript for robust type-checking and improved code quality.
-   **Styling:** Tailwind CSS is used exclusively for utility-first styling.
-   **UI Components:** We use `shadcn/ui`, a collection of beautifully designed, accessible, and reusable components built on Radix UI.
-   **Routing:** `react-router-dom` handles all client-side navigation and routing.
-   **Server State:** `@tanstack/react-query` is used for fetching, caching, and managing data from APIs.
-   **Forms:** `react-hook-form` is the standard for building forms, paired with `zod` for schema validation.
-   **Icons:** `lucide-react` provides a comprehensive and consistent set of icons.

## Library Usage Rules

### 1. UI and Styling

-   **Component Library:** **ALWAYS** use components from `shadcn/ui` (located in `src/components/ui`). Do not build custom components for common elements like buttons, cards, dialogs, or inputs unless a design requirement cannot be met by composing existing `shadcn/ui` components.
-   **Styling:** **NEVER** use custom CSS files, CSS Modules, or CSS-in-JS libraries. All styling **MUST** be done using Tailwind CSS utility classes.
-   **Conditional Classes:** Use the `cn` utility function from `src/lib/utils.ts` to conditionally apply or merge Tailwind CSS classes.

### 2. Routing and File Structure

-   **Routing:** All application routes must be defined within `src/App.tsx` using `<BrowserRouter>`, `<Routes>`, and `<Route>` from `react-router-dom`.
-   **Pages:** Components that represent a full page or view should be placed in the `src/pages/` directory.
-   **Reusable Components:** Smaller, reusable components that are not pages should be placed in `src/components/`.
-   **Hooks & Utilities:** Custom hooks go into `src/hooks/`, and general utility functions go into `src/lib/`.

### 3. State Management

-   **Local State:** For state that is local to a single component, use React's built-in `useState` and `useReducer` hooks.
-   **Server State:** For any data fetched from an API, **ALWAYS** use `@tanstack/react-query`. This handles caching, refetching, and loading/error states automatically.
-   **Global State:** Avoid introducing global state management libraries like Redux or Zustand. If state needs to be shared between components, prefer lifting state up or using React Context for simple cases.

### 4. Notifications

-   **Toasts:** To display notifications (e.g., success messages, errors), use the `useToast` hook provided in `src/components/ui/use-toast.ts`. Do not use `alert()` or other notification libraries.

### 5. Icons

-   **Icon Set:** All icons **MUST** come from the `lucide-react` package to ensure visual consistency.