---
layout: post
title:  GraphQL and Memory
summary: Some notes on GraphQL clients and odd-ball notes from a poorly cited documentary on Netflix.
date:   2019-09-16-05:17:03
categories: raw
---
## GraphQL Clients

There are a lot of GraphQL clients, but it's not always obvious what their differences are. In order to use GraphQL, we POST to the GraphQL endpoint and expect JSON back. Curl can be used for this. As far as clients, there are fetch clients and caching clients.

[Aiyer, 2018]

### Fetch Clients

A fetch client only executes POSTs to the endpoint to fetch data or run mutations. The caching client caches, but also separates concerns from the view layer. Really, a caching client fetches, caches, and manages the network. FetchQL, GraphQL Request, Apollo Fetch all work as fetch clients.

[Aiyer, 2018]

### Caching Clients

Micro GraphQL React, Lokka, URQL offer caching.

For sophisticated caching clients, Apollo Client and Relay Modern are good choices. Apollo works with bindings for all the popular frameworks like React, Angular, Ember, and Vue. Early iOS and Android clients are supported as well. Apollo isn't necessarily simple though, and large development shops have come back and simplified their GraphQL clients--probably the reason so many clients exist today is full-featured systems are complicated. For example, version 2 of Apollo Client has configuration for custom cache control and custom networking.

[Aiyer, 2018]

### Apollo Boost

Apollo Boost is a zero-configuration around Apollo to support simple setup. The network layer is http-link. The Cache is Apollo's inMemoryCache.

To build with Apollo Boost, import ApolloClient from apollo-boost, and ApolloProvider from react-apollo. Instantiate a client. Wrap the whole application with ApolloProvider, passing in the client.

A component could use gql from apollo-boost, Query from react-apollo, and a query from the queries directory. The qgl function converts the Query into a useable one, and then the component can use Query, passing in the query, and handling loading, error, and data as parameters to the function.

[Aiyer, 2018]

### Wrapping Functions

Both Apollo and URQL use wrapping functions around a query or mutation. URQL uses query. Apollo Client uses graphql-tag. This is a lot easier than manipulating strings.

[Aiyer, 2018]

### Relay Modern

Facebook developed Relay Modern to improve performance, partly through reducing the client's size. For Relay modern, you need react-relay, react-compiler, and babel-plugin-relay. Setup a cache and a network. This is often done in an environment file.

[Aiyer, 2018]

## Memory

Our memories fail us a lot, but we only think about it when it fails. 

The following is a summary of some of what we know about memory, from a documentary on Netflix that doesn't have enough information about it on IMDB or generally.

[Netflix, 2019]

### Memory Competitions

Memory competitions are amazing. In 10 minutes, learning 500 numbers. Henry Molaison received brain surgery to treat epilepsy, removing his limbic lobe. He lost memories like how to navigate his home, but kept implicit and explicit memories. Explicit memory includes semantic memory is facts, dates, numbers and words. Episodic memory, also part of explicit memory, was what Henry lost.

[Netflix, 2019]

### Use Case: Recital

Performing can demonstrate the many parts of the brain that work together to form memory. The sound is stored in the auditory cortex. The feeling of the strings on fingers is stored in posterior fossa (I think--post on the show). The face of a friend in the audience is stored in the fusiform gyrus. Stage fright is stored in the amygdala. The medial temporal lobe, including the hippocampus, pull all these parts together. The medial temporal lobe combines the elements.

[Netflix, 2019]

### 70-Year-Old Memory

With a 70 year old, the memories begin to fall off. In our 20s, we remember quite a bit--change moments that define us.

[Netflix, 2019]

### Improving Memory

We can improve our memories by living a healthier and more active life. Every study finds that meditation works. Meditation improves focus and focus improves memory. Emotion is easier to remember. The amygdala upregulates the hypocampus.

[Netflix, 2019]

### False Memories

A study of 9/11 found that people close to the World Trade Center remembered more details. Everyone remembered where they were. There seems to be a part of the hypocampus dedicated to place and time.

[Netflix, 2019]

### London Cabbies

London cabbies spend years studying for their licenses. Those that pass the test have hypocampi that grew.

[Netflix, 2019]

### Memory Tricks

People that are given words remember about 13% of 11 words. Strung together in a narrative, we remember 93%. Story, place, and emotion are our most important factors for remembering. Also, creating a memory palace adds order. Random things have a place. Memory athletes aren't smarter, but have trained their brains, generally emotional, visual learners, and all storytellers.

[Netflix, 2019]

### Peripheral Detail

Things that strengthen our memories warp them too. The peripheral details are easier to forget. With traumatic memories, we are more confident that we remember, but we're actually forgetting at the same pace as other things. When we lose these things, we fill in these gaps. Reconstruction means our episodic memories are flexible. We can get false memories planted. With leading questions, 70% of participants in a study falsely remember that they had committed a crime in their teens. DNA is used to overturn a lot of convictions, fixing the problems we've had with memories during the judicial process.

[Netflix, 2019]

### Future and Memory

Henry Molaison also had a hard time planning the future. Another patient said thinking of the future was like being told to find a chair in an empty room. Memory and imagination use nearly identical parts of the brain. In Alice in Wonderland, there is a quote, "it's a poor sort of memory that only works in the past." That turns out to be true.

[Netflix, 2019]


## References:

Aiyer, A. (2018, June 11). Exploring different GraphQL Clients. Retrieved September 16, 2019, from Medium website: https://medium.com/open-graphql/exploring-different-graphql-clients-d1bc69de305f

Netflix. (2019, September 12). The Mind Explained. In Memory.

Interestingly, this series doesn't cite a director, that I could find. I'm using it as a research source, even though it's not as good as the original sources.



