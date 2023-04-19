# Basic usage of newsdash
## With client
- import the required modules
- Create a client variable with NewsDash and pass it the api key
- make an async function and use the client to get news
- close the client when not in use
- run the function using asyncio

Here is the example code:
```python
# import required modules
import asyncio
from newsdash import NewsDash

# make a function to get news
async def get_news() -> None:
  # initialize the client using your api key
  client = NewsDash('YOUR_API_KEY')
  # get news
  print(await client.get_everything(query='apple'))
  # make sure to close client
  await client.close()
 # run the async function
asyncio.run(get_news())
```
## With async context manager
- import the required modules
- make an async function and make an async context manager and pass it the api key
- get the news
- you dont need to close the client,it automatically get closed
- run the function using asyncio
```python
# import required modules
from newsdash import NewsDash
import asyncio

# make a function to get news
async def main():
  # make an async context manager and pass it the api key
  async with NewsDash("api_key") as nd:
    # get news
    print(await nd.get_everything(query="apple"))
    # no need to close the client,it gets closed automatically
    # await nd.close() (no need to close)

asyncio.run(main())
```