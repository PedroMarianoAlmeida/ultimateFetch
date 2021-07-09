# ultimateFetch

JavaScript function to handle asynchronous code. Simple but efficient, can replace simple fetch requests e standardize the way you treat errors and the response data. 

```javascript
const ultimateFetch = async (
  resource,
  init = null,
  dataTreatment = (data) => data
) => {
  try {
    const res = await fetch(resource, init);
    if (res.ok) {
      const data = await res.json();
      const dataTreated = dataTreatment(data);
      return [dataTreated, null];
    } else {
      return [null, res.statusText];
    }
  } catch (error) {
    return [null, error];
  }
};
```
