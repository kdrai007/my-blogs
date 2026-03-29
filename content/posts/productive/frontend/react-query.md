---
title: "react-querty"
id: react-querty
aliases: 
tags:
  - javascript
---

# React Query

React Query is a library that simplifies data fetching and management in React applications.

## Features

. Decerlative Data fetching
. Automatic Caching
. Automatic background data refetching
. Error handling and retry strategies

## Key components

1 - QueryClientProvider -> The top level component wraps our React application, providing our application a global context of the query client instance 

`
import { QueryClientProvider } from 'react-query';
function App() {
  return (
    <QueryClientProvider>
      {/* Your application components */}
    </QueryClientProvider>
  );
}
`

2 - QueryClient -> Is the central hub for manageing queries,fetching data,caching data and handling background data refetching

`
const queryClient=new QueryClient()
`


## Links

[[tags/productive]]
