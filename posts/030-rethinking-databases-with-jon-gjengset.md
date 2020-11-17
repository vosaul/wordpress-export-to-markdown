---
title: "Rethinking databases and Noria with Jon Gjengset"
date: "2019-04-30"
---

Can we make databases faster and remove the need for caching reads in an external cache? Can we make a distributed SQL based relational database that outperforms memcached? Jon Gjengset and the PDOS team at MIT CSAIL have done just that with Noria.

Today I talk to Jon about Noria, about building a database in Rust and his efforts to teach people intermediate Rust via live coding sessions.

Jon was great to talk to. He really was able to explain to me how Noria is able to do what it does and where it is in terms of maturity. The key, besides rust and evmap, is that Noria uses materialized views to do query optimization ahead of time, on write. The devil is in the details though, of course. And the details, in this case, are turning declarative SQL into a dataflow program that handles cache updates on new writes.

**Show notes:**

- [Noria Project](https://github.com/mit-pdos/noria)
- [pdos group at MIT](https://pdos.csail.mit.edu/)

- [Noria Paper](https://jon.thesquareplanet.com/papers/login-spring19-noria.pdf)
- [Noria Article](https://jon.thesquareplanet.com/papers/login-spring19-noria.pdf)
- [Rust at Speed](https://www.youtube.com/watch?v=s19G6n0UjsM&t=381s)
- [Jon's Rust Streaming](https://www.youtube.com/c/JonGjengset)
