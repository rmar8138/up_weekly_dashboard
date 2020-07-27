# Up Weekly Dashboard

A dashboard that displays weekly spending insights for Up Banking users. Created using the Up API v1.

## Functionality

- User will sign in with their API token, which will return a success or error message whether token is valid
- Initial home display will replicate the Up Bank weekly summary page, showing a bar graph and a list breakdown of the weekly spending of the last 12 weeks, or less of there are not enough transactions
- Users can toggle via dropdown how many weeks back they wish to display (min: 1, max: max amount of weeks)

## Data Flow

- Upon successful token verification, call the transactions API to get a list of all transactions, paginated
- Format the data so the end result is a purchases array of objects in state, where each object contains purchase data for the week
  - In terms of pagination, perform GET request if transaction GET request contains a next link
- Perform calculations that replicate the Up Weekly Summary
  - Average weekly purchases
  - Average weekly spend
  - Number of purchases per week
  - Total amount of purchases in \$AUD per week
- Week select will change the number of weeks are included in the calculation

## Components

_App_

- Main component, will hold global state and perform calculations to pass down data to child components
- Will contain week select element and log out button

_Summary_

- Contains bar graph and total summary of weeks selected

_Breakdown_

- Contain total amounts per week

_Login_

- Form where user enters token
