# Eat your Fibers

This repository contains a POC technique written in C using Windows Fibers, a lightweight version of threads that runs in User-mode only thus achieving more stealth from kernel-level EDR detection.

## Fonctionality

Eat Your Fibers uses an existing thread to run a custom payload as a fiber.

The program converts the main running thread into a fiber before creating an execution fiber with a callback set to the payload address and switching to it.

## PROS:
- No new thread is created which means less thread api calls - which means less detection.
- Really simple implementation.
- Achieves good stealth capabilities compared to simply spawning a new (suspended / alertable) thread.
  
## CONS:
- This technique has the inconvenient of possibly crashing the local process since we aren't spawning a new thread to exec the payload from.

### NOTE: These are POC techniques, they aren't intended to be used in real-life red-teaming scenarios. The POC demonstrates the technique, but no attempt has been made to make the rest of POCs evasive (Think - obfuscation, encryption, where to write the payload...). 
