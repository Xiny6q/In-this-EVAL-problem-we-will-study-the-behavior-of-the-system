Download link :https://programming.engineering/product/in-this-eval-problem-we-will-study-the-behavior-of-the-system/


# In-this-EVAL-problem-we-will-study-the-behavior-of-the-system
In this EVAL problem, we will study the behavior of the system
In this EVAL problem, we will study the behavior of the system when multiple processors (a.k.a. threads in this case) are available to process the incoming workload. For this part, make sure to have at least w+2 processors available in your system, where w is the number of worker threads that we will start. The extra two threads are needed for the client and the parent thread, respectively.

First thing rst, determine the maximum number of CPUs that you can use for this EVAL problem. If your machine has w + 2 = 4 CPUs, you should consider w = 2, and so on. For this part, simply explain how you recovered that information for your machine.

Starting easy with w = 2, run the following command:

./server_multi -q 1000 -w 2 2222 & ./client -a 37 -s 20 -n 1500 -d 0 2222

Now, measure the utilization of each individual worker thread. To do that, rst classify the printouts by the thread ID (T0, T1, …) and then re-use the same approach to compute their utilization as in HW1, but independently for each thread.

What do you notice about the utilizations of the two threads? Can you conclude that the load is balanced between them?

Now run a similar experiment as above by considering the following template command:

./server_multi -q 1000 -w <workers> 2222 & ./client -a 37 -s 20 -n 1500 -d 0 2222

where <workers> is rst set to 4, then to 6, and nally to 8. Note, to run the command with -w 8, you need at least w + 2 = 10 CPUs on your machine. If you do not have that many CPUs, you are in luck! These are exactly the parameters used by CodeBuddy to run your code on the rst 3 test cases of server_multi. So you can post-process the output produced by CodeBuddy.

Produce a plot for the average response time of any request (y-axis)|thus, without di erentiating between threads|as a function of the number of threads (value of the -w parameter) from 2 to 8 (in increments of 2). Is the improvement in response time linear or super-linear as the number of threads increases?

Last but not least, let us study what happens to the rejection rate as more workers become available. Run two cases and compare the output.

First, re-run or reuse the output from Part 1 for the equivalent command:

./server_multi -w 1 -q 10 2222 & ./client -a 18 -s 20 -n 1500 -d 0 2222 Then, run and post-process the output of command:

./server_multi -w 2 -q 10 2222 & ./client -a 18 -s 20 -n 1500 -d 0 2222

Now look at the rejection rate and reason about the following: if X is the rejection rate with 1 worker, then X/W is the rejection rate with W workers. Is this true or not? Motivate your answer. You are not oblibged, but welcome to run additional relevant experiments to further sustain your conclusion.
