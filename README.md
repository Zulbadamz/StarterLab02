# Lab: Black Box Testing

## Topics

- Black-box testing
- Equivalence partitioning
- Decision table testing
- State transition testing

## Learning Objectives

- Design black-box tests without viewing the application code.
- Identify valid and invalid equivalence partitions.
- Create decision tables from conditions and expected actions.
- Identify application states, events, and transitions.
- Create test cases using equivalence partitions, decision tables, and state transitions.

# Deliverables

## Step 1: Select a Website

Choose a website that you enjoy using.

Include:

- The website's name
- The website's URL
- One or two features you will test

Do not look at the website's source code.

## Step 2: Equivalence Partitioning

Apply equivalence partitioning to one selected feature.

Include:

- Valid partitions
- Invalid partitions
- One representative value from each partition
- The expected result for each value

## Step 3: Decision Table Testing

Apply decision table testing to one selected feature.

Include:

- Conditions
- Actions
- A completed decision table
- Test cases based on the table

## Step 4: State Transition Testing

Apply state transition testing to one selected feature.

Include:

- States
- Events
- Valid and invalid transitions
- A completed state transition table
- Test cases based on the table

## What to Submit

1. Create and initialize a GitHub repository.
2. Commit and push your work to the repository.
3. Make sure the repository is public. Private repositories will not receive credit.

## AI Transparency

AI was used to clean up this file.

# Lab: Black Box Testing

## Step 1: Select a Website

**Website Name:** Beauty of Joseon

**Website URL:** https://beautyofjoseon.com/collections/shop-all

**Selected Features:**
- Product Search
- Shopping Cart

For this assignment, I selected the Beauty of Joseon website, which sells skincare and beauty products. I chose to test the product search feature and the shopping cart feature because they are important parts of an online shopping website. I will use black-box testing techniques to evaluate how the website responds to different inputs and user actions without looking at the website's source code.

## Step 2: Equivalence Partitioning

**Feature Tested:** Product Search

Equivalence partitioning is a black-box testing technique that divides inputs into valid and invalid groups. Each group represents inputs that are expected to behave similarly. I selected one representative input from each partition to check how the search feature responds.

| Test Case | Partition | Type | Representative Input | Expected Result |
|---------- | --------- | ---- | -------------------- | --------------- |
| EP1 | Existing product name | Valid | Revive Eye Serum | Matching product appears in search results |
| EP2 | Existing product category | Valid | Sunscreen | Related sunscreen products appear |
| EP3 | Nonexistent product | Invalid | xyz123notfound | No matching products are found |
| EP4 | Empty search | Invalid | Empty input | Search is not submitted or default results appear |
| EP5 | Special characters only | Invalid | @@@### | No matching products or a validation message appears |

**Explanation:**

The purpose of this test is to check whether the product search feature handles different types of input correctly. Valid inputs should display matching products, while invalid or unusual inputs should be handled without errors or crashes. Testing representative inputs from each partition reduces the number of test cases while still providing useful coverage.

## Step 3: Decision Table Testing

**Feature Tested:** Adding a Product to the Shopping Cart

Decision table testing is used to test different combinations of conditions and their expected actions. For this feature, I will check whether a product is in stock and whether any required product options have been selected.

### Conditions

- C1: Is the product in stock?
- C2: Are all required product options selected?

### Actions

- A1: Add the product to the shopping cart.
- A2: Request the customer to select the required options.
- A3: Prevent the product from being added to the cart.

### Decision Table

| Conditions and Actions | Rule 1 | Rule 2 | Rule 3 | Rule 4 |
| ---------------------- | ------ | ------ | ------ | ------ |
| Product in stock?      | Yes    | Yes    | No     | No     |
| Required options selected? |Yes | No     | Yes    | No     |
| Add product to cart    |Yes     | No     | No     | No     |
| Request option selection | No   | Yes    | No     | No     |
| Prevent adding product | No     | No     | Yes    | Yes    |

### Test Cases

| Test Case | Description | Expected Result |
| --------- | ----------- | --------------- |
| DT1 | Select an in-stock product with all required options selected | Product is successfully added to the cart |
| DT2 | Select an in-stock product without selecting a required option | Website requests the missing option |
| DT3 | Select an out-of-stock product with an option selected | Product cannot be added to the cart |
| DT4 | Select an out-of-stock product without selecting an option | Product cannot be added to the cart |

**Explanation:**

Decision table testing helps verify that the website responds correctly to different combinations of conditions. In this example, the product should only be added when it is available and all required options have been selected. The decision table includes four combinations to help identify missing rules or incorrect shopping cart behavior.

## Step 4: State Transition Testing

**Feature Tested:** Shopping Cart

State transition testing is used to verify how a system moves from one state to another when a user performs an action. For this assignment, I selected the shopping cart because its state changes when products are added, removed, or updated.

### States

- S1: Empty Cart — No products are in the cart.
- S2: Cart With Product — The cart contains one product with quantity 1.
- S3: Cart With Updated Quantity — The cart contains a product with quantity greater than 1.

### Events

- E1: Add an available product.
- E2: Increase product quantity.
- E3: Decrease product quantity.
- E4: Remove a product.
- E5: Attempt to remove a product from an empty cart.
- E6: Attempt to add an unavailable product.

### State Transition Table

| Current State | Event | Expected Next State | Valid / Invalid |
| ------------- | ----- | --------------------| ----------------|
| S1: Empty Cart | Add an available product | S2: Cart With Product | Valid |
| S1: Empty Cart | Attempt to remove a product | S1: Empty Cart | Invalid |
| S2: Cart With Product | Increase quantity from 1 to 2 | S3: Cart With Updated Quantity | Valid |
| S3: Cart With Updated Quantity | Decrease quantity from 2 to 1 | S2: Cart With Product | Valid |
| S2: Cart With Product | Remove the only product | S1: Empty Cart | Valid |
| S2: Cart With Product | Attempt to add an unavailable product | S2: Cart With Product | Invalid |

### Test Cases

| Test Case | Test Steps | Expected Result |
|---------- | ---------- | --------------- |
| ST1 | Open an empty cart and add an available product | Cart displays the product with quantity 1 |
| ST2 | Increase the quantity of the product from 1 to 2 | Quantity updates to 2 and subtotal increases |
| ST3 | Decrease the quantity from 2 to 1 | Quantity updates to 1 and subtotal decreases |
| ST4 | Remove the only product from the cart | Cart becomes empty |
| ST5 | Attempt to remove a product when the cart is empty | Cart remains empty without errors |
| ST6 | Attempt to add an out-of-stock product | Product is not added and the cart remains unchanged |

**Explanation:**

State transition testing helps verify that the shopping cart behaves correctly when users perform different actions. Adding a product should change the cart from empty to containing a product. Increasing or decreasing the quantity should update the cart correctly. Removing the last product should return the cart to the empty state. Invalid actions should not cause unexpected changes.
