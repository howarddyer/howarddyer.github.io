---
layout: post
title:  "Jasmine unit test template"
date:   2019-06-27 16:00:00
label: post
---

```javascript
{
    "Framework": "jasmine",
    "References": [
        {
            "Path": "helpers",
            "Includes": [ "**.js" ]
        },
        {
            "Path": "../",
            "Includes": [ "**.js"]
        }
    ],

    "Tests": [
        {
            "Path": "",
            "Includes": [ "**.js" ]
        }
    ]
}
```

```javascript
describe("file", function () {

    beforeAll(function () {});

    beforeEach(function () {});

    afterAll(function () {});

    describe("function", function () {

        it("expectation", function () {
            //expect().toBe(value);
            //expect().toEqual(value);
            //expect().toMatch(value);
            //expect().toContain(value);

            //expect().toBeTruthy();
            //expect().toBeFalsey();
            //expect().toBeDefined();
            //expect().toBeUndefined();
            //expect().toBeNull();

            //expect().toBeGreaterThan(number);
            //expect().toBeLessThan(number);
            //expect().toBeCloseTo(number, range);
        });

    });

})
```
