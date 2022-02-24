
---
title: "Demystifying Spring Task Executor"
description: "A blog about what and how to configure Spring Task executor core pool size, max pool size and queue capacity"
date: 2020-08-31T13:09:42-06:00
draft: false
image: "images/github-pagesLightBlue.jpeg"
tags: ["Spring", "Threads", "Java"]
categories: ["Tech"]
GHissueID: 2
toc: true
---

`corePoolSize` vs. `maxPoolSize` vs. `queueCapacity`

```java
  @Bean
  @Primary
  public TaskExecutor taskExecutor() {
    ThreadPoolTaskExecutor executor = new ThreadPoolTaskExecutor();
    executor.setCorePoolSize(3);
    executor.setMaxPoolSize(6);
    executor.setQueueCapacity(4);
    executor.setWaitForTasksToCompleteOnShutdown(false);
    executor.setThreadNamePrefix("my-async");
    executor.initialize();
    return executor;
  }
```

#### Core pool size
In a nut shell, `Core pool size` is the happy path.
When a new task is submitted and fewer than Core Pool Size threads are running, a new thread is created to handle the request, even if other threads are idle. If there are greater than Core Pool Size but fewer than Max Pool Size threads running, a new thread is created only if no threads are idle.

#### Max pool size
It defines the upper limit of threads that can ever be created! Once limit is reached(no thread is available), no more tasks are accepted.

#### Queue capacity
Defines the number of tasks to queue when all core pool are filled. Threads will be scalable to maximum pool size when queue is full.

#### Explain to me like I'm 5 years old

A simple and efficient way to get this is by considering yourself being in a bank.

You ever stood in a line even though there is a window available?
Why would the bank keep a customer in a queue if there are available cash-window? That's exactly the case with `core pool size`. If there are un-used threads, new tasks are directly allocated to them.

[![enter image description here][1]][1]

One the available window(core pool size) is full, customers are asked to wait in the queue. This is where the `queue-capacity` comes in picture! New tasks are keep on queueing until no more tasks can be queued.

[![enter image description here][2]][2]

What if the wait-lounge is full of customers? Bank can allocate/open new cash-windows as they see spike in number of customers(tasks). They had 3 more in reserve.
Here comes the `max pool size` in context.

Once these windows(threads) are all occupied, Bank can no longer server any new customers(tasks). Agree? And henceforth, new tasks are not accepted!

[![enter image description here][3]][3]



[1]: https://i.stack.imgur.com/SnOAz.jpg
[2]: https://i.stack.imgur.com/hyael.jpg
[3]: https://i.stack.imgur.com/UfvHK.jpg