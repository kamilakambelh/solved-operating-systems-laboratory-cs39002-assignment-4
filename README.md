Download Link: https://assignmentchef.com/product/solved-operating-systems-laboratory-cs39002-assignment-4
<br>
<strong>Assignment 4: </strong>Implement a CPU scheduler on top of Linux using threads and compare scheduling algorithms

Implement a virtual CPU scheduler on top of the Linux kernel using POSIX threads, and evaluate CPU scheduling algorithms by running a synthetic job mix on the scheduler. The details of the specification are as follows.

<ol>

 <li>Create <em>N</em> concurrent threads that will be scheduled by the virtual scheduler. Each thread will be either a <strong><em>producer (P)</em></strong> or a <strong><em>consumer (C)</em></strong>, selected with equal probability. Each of the P threads will be generating 1000 pseudo-random integers, and storing them in a <strong><em>shared BUFFER</em></strong> of maximum capacity <em>M</em>; if the buffer is full, the thread will wait. Each of the C threads will be repeatedly removing an element from the BUFFER; if the buffer is empty, the thread will wait. The P and C threads are referred to as <strong><em>WORKER</em></strong></li>

 <li>Each of the WORKER threads will have <strong><em>signal handlers</em></strong> installed for handling the user-defined signals SIGUSR1 and SIGUSR2. SIGUSR1 will be used to put the thread to sleep, while SIGUSR2 will be used to wake up the thread to resume execution. The running status of all the threads will be stored in a shared data structure called <strong><em>STATUS</em></strong>.</li>

 <li>Another thread, called the <strong><em>SCHEDULER</em></strong> thread, will be created that will be sending sleep/wakeup signals to the WORKER threads. It will implement a round-robin scheduling algorithm with a specified time quantum (say, 1 second). It will run one of the <em>N </em>WORKER threads at a time, while the other <em>N-1</em> threads will be put to sleep. During context switch, the currently running thread will be put to sleep, while the next thread in the READY queue will be activated.</li>

 <li>Another thread will be created, called <strong><em>REPORTER</em></strong> thread, which will continuously monitor the <strong><em>STATUS</em></strong> data structure, and display relevant messages on the screen whenever a context switch or thread termination takes place. It will also display the number of elements in BUFFER.</li>

</ol>

<strong>Hint:       </strong><em>Use the POSIX Pthread library for creating/managing the threads.</em>

<strong>Submission Guideline:</strong>

 Create the program as a single file as <strong>Ass4_&lt;groupno&gt;.c</strong> or <strong>.cpp</strong>, and upload it.

<strong>Evaluation Guidelines: </strong>

While entering marks, the partwise break up should also be entered according to the marking guidelines given below. There is a separate component for individual assessment, based on how the student answers questions.




<table width="435">

 <tbody>

  <tr>

   <td width="26"><strong>Sl</strong></td>

   <td width="363"><strong>Items</strong></td>

   <td width="46"><strong>Marks</strong></td>

  </tr>

  <tr>

   <td width="26"><strong>(a)</strong></td>

   <td width="363">Creation of concurrent threads</td>

   <td width="46">5</td>

  </tr>

  <tr>

   <td width="26"><strong>(b)</strong></td>

   <td width="363">Storing data in a shared buffer</td>

   <td width="46">5</td>

  </tr>

  <tr>

   <td width="26"><strong>(c)</strong></td>

   <td width="363">Correctly implementation of signal handlers</td>

   <td width="46">8</td>

  </tr>

  <tr>

   <td width="26"><strong>(d)</strong></td>

   <td width="363">Correctly synchronised accesses to buffers</td>

   <td width="46">8</td>

  </tr>

  <tr>

   <td width="26"><strong>(e)</strong></td>

   <td width="363">Implementation of scheduling policy</td>

   <td width="46">8</td>

  </tr>

  <tr>

   <td width="26"><strong>(f)</strong></td>

   <td width="363">Correctly synchronised accesses to status for updating and reporting</td>

   <td width="46">10</td>

  </tr>

  <tr>

   <td width="26"><strong>(g)</strong></td>

   <td width="363">Overall correctness</td>

   <td width="46">6</td>

  </tr>

  <tr>

   <td width="26"> </td>

   <td width="363"><strong>Total</strong></td>

   <td width="46">50</td>

  </tr>

 </tbody>

</table>


