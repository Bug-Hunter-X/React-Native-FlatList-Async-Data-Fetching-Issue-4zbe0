# React Native FlatList Asynchronous Data Fetching Bug

This repository demonstrates a common yet subtle bug in React Native applications involving asynchronous data fetching within a FlatList component's `renderItem` method. The problem arises from the asynchronous nature of data retrieval, causing state updates to lag behind re-renders, which results in unpredictable UI behavior.

## Bug Description:

The `bug.js` file showcases a FlatList that attempts to fetch data for each item within the `renderItem` function. Because `fetch()` is asynchronous, the component might re-render before the data is received, leading to stale data being displayed, or worse, errors. This is exacerbated by the fact that this happens *for every item* in the list, increasing the complexity and frequency of the rendering issue.

## Solution:

The `bugSolution.js` file illustrates the solution. It uses a combination of local state management (useState) and asynchronous/await to efficiently handle the fetching of data before the rendering process.

This prevents race conditions that lead to buggy rendering by ensuring the component is up-to-date before rendering each item.