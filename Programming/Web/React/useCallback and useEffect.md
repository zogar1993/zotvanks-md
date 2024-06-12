If possible, do not use them until you notice that there the rendering is slow. In such cases, you may solve any of the two following problems:
- Referential equality
- Computationally expensive calculations

Another use case for useCallback is for a complex useEffect, where you want to extract some of their functions for order and reusability sake. In such cases, a useCallback will be viable even tho it is not saving you time (it may even be a little slower, but in orders of magnitude that do not matter).

Links:
- https://kentcdodds.com/blog/usememo-and-usecallback/?ck_subscriber_id=974903139