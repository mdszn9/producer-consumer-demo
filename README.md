# Producer–Consumer Race Condition Demo

An interactive, visual explanation of the **synchronization problem in the bounded-buffer (producer–consumer) problem** from Operating Systems.

**Live site:** https://mdszn9.github.io/producer-consumer-demo/

## What's inside

1. **Setup**: the textbook unsynchronized producer/consumer code that uses a shared `count`.
2. **Race step-through**: execute `count++` and `count--` one machine instruction at a time (load → modify → store). Values move between memory and the CPU registers, and a timeline shows how a bad interleaving loses an update.
3. **All 20 interleavings**: every possible schedule of the 6 instructions, with the final value of `count` for each. Only 2 of the 20 are correct. Click any one to replay it.
4. **Live bounded-buffer simulator**: an 8-slot circular buffer with 1–3 producers and 1–3 consumers, plus adjustable speed and preemption rate.
   - *No synchronization:* `count` drifts away from the real number of items. Producers overwrite unconsumed items (**lost items**), and consumers read empty slots (**empty reads**).
   - *Semaphores + mutex:* `empty` / `full` / `mutex` with blocking wait queues give zero errors.
   - Includes a live chart of `count` vs. actual items, a CPU-schedule strip, highlighted code lines for each thread, and an event log.
5. **The fix**: the semaphore solution, a comparison diagram of overlapping vs. mutually exclusive critical sections, the three critical-section requirements, and the wait-order deadlock pitfall.

## Run locally

It's a single static file with no build step and no dependencies:

```sh
open index.html
```
