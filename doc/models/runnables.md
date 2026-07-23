# Runnables

`Runnables is a standardized unit of work that defines how a component receives input, processes data, and returns an output`

![Image](../../images/runnables-01.png)

<br/>

![Image](../../images/runnables-02.png)

<br/>

![Image](../../images/runnables-03.png)

---

## Core Methods of the Runnable Interface

`invoke`: Processes a single input and returns a single output synchronous

`ainvoke`: The asynchronous equivalent of the invoke method

`batch`: Processes a list of multiple inputs concurrently

`abatch`: The asynchronous equivalent of the batch method

`stream`: Streams back chunks of the response as they are generated

`astream`: The asynchronous equivalent of the stream method

---

## Runnables Types

![Image](../../images/runnables-04.png)

<br/>

### Sequence Runnables

Using runnables sequence
![Image](../../images/runnables-05.png)
<br/>

Using pipes
![Image](../../images/runnables-06.png)
<br/>

Using LCEL
![Image](../../images/runnables-07.png)

<br/>

### Parrarel Runnables

Using runnables sequence
![Image](../../images/runnables-08.png)
<br/>

Using pipes
![Image](../../images/runnables-09.png)
<br/>
