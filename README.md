# GCLive

This repo contains my findings for building a GC visualization using real data from Go heap dumps.

## Why?

For fun and curiousity, a live GC viewer would be fun. (I've been doing some research on this since late 2022, in short spurts)

**What value does it provide?** Nothing. Absolutely nothing. You get a live view of the GC (hopefully) once the implementation is complete.

## Proposed solution

The three components to build a live visualization of the GC would involve:

- [x] parsing the Go heap dump
    - Completed! Built [heaputil](https://github.com/burntcarrot/heaputil) for this.
- [x] generate an object graph
    - Completed! Built [heapview](https://github.com/burntcarrot/heapview) for this; it has an object graph view which generates a GraphViz graph.
- [x] determine object liveness
    - Completed? I did some research but the only possible way to achieve this would be to:
        - take two heap dumps at different timestamps
        - compare the object graphs of both the heaps
        - objects that don't exist the recent graph are assumed to be "unalive" or collected.
- [ ] color code individual nodes in the object graph (mark stage)
    - Partially completed! Color objects without pointers as gray, and objects with pointers as black.
    - Not the most perfect way to do this, but gives us a basic head start to color-coding and providing the foundation for the GC visualization.

## Where can I learn more?

I'll publish a detailed blog post soon.

## Contributing

All sorts of contributions are welcome!

Please create issues related to improvements, etc.