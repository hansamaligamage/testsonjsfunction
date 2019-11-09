# Unit tests for a Azure function written in Javascript

This sample code has a http trigger function written in javascript and unit tests written in Jest.

## Jest
Jest is a javascript testing framework, you can use it to test codes written in javascript, ttypescript, angular, react, node or vue js. 

## Unit test with Jest

At first, you have to set the jest as the testing framework in your code
```
module.exports = {
    log: jest.fn()
};
```

Then lets write a Jest unit test to check whether the http trigger returns the expected output. You have to import the testing context and call the http trigger function
```
const httpFunction = require('./index');
const context = require('../testing/defaultContext')

test('Http trigger should return known text', async () => {

    const request = {
        query: { name: 'Hansamali' }
    };

    await httpFunction(context, request);

    expect(context.log.mock.calls.length).toBe(1);
    expect(context.res.body).toEqual('Hello Hansamali');
});
```
