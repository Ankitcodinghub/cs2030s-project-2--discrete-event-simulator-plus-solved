# cs2030s-project-2--discrete-event-simulator-plus-solved
**TO GET THIS SOLUTION VISIT:** [CS2030s Project #2- Discrete Event Simulator Plus Solved](https://www.ankitcodinghub.com/product/cs2030s-project-2-discrete-event-simulator-plus-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;80858&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;5&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (5 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS2030s Project #2- Discrete Event Simulator Plus Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (5 votes)    </div>
    </div>
<h4>Requirements</h4>
<ul>
<li>Immutability</li>
<li>Pure Functions</li>
<li>Randomizing the arrival and service times</li>
<li>Object-oriented design with possibly a mix of imperative/declarative (functional) implementations</li>
<li>Program style: adherance to&nbsp;<a href="https://www.comp.nus.edu.sg/~cs2030/style/" target="_blank" rel="noopener">CS2030 Java Style Guide</a></li>
<li>Java documentation: adherence to&nbsp;<a href="https://www.comp.nus.edu.sg/~cs2030/javadoc" target="_blank" rel="noopener">CS2030 Javadoc Specification</a></li>
</ul>
<h4>Problem Description</h4>
This stage of the project comprises three parts:

<ul>
<li>Dealing with side-effects</li>
<li>Randomizing arrival and service times</li>
<li>More complex behavior of shops, servers, and customers</li>
</ul>
<h4>Dealing with Side-Effects</h4>
For this part of the project, we shall first tackle the issue of&nbsp;<i>side effects</i>&nbsp;in&nbsp;<a href="https://codes.comp.nus.edu.sg/task_view.php?tid=4948">Project #1</a>. You would probably have coded something similar to the following, when processing the different&nbsp;<tt>Event</tt>s (arrive, serve, wait, leave, done, …) in the&nbsp;<tt>PriorityQueue pq</tt>.

<pre>while (!pq.isEmpty()) {
	Event e;
	e = pq.poll();
	System.out.println(e);
	Event nextEvent = e.execute();
	if (nextEvent.isValidEvent()) {
		pq.add(nextEvent);
	} 
}
</pre>
Notice that every time the&nbsp;<tt>execute</tt>&nbsp;method of an event is invoked, it not only generates the next event based on the status of the&nbsp;<tt>Servers</tt>&nbsp;(here we call it a&nbsp;<tt>Shop</tt>), it will actually change the status of the servers as a side-effect. As such, we would like to address this side-effect by re-defining event generation as follows:

<pre>e.execute(s) -&gt; (e',s') 
</pre>
That is to say, the invocation of the&nbsp;<tt>execute</tt>&nbsp;method of an&nbsp;<tt>Event e</tt>&nbsp;with the argument&nbsp;<tt>Shop s</tt>, would now generate the next&nbsp;<tt>Event e'</tt>&nbsp;and&nbsp;<tt>Shop s'</tt>&nbsp;as a pair of values. In a similar fashion,&nbsp;<tt>e'</tt>and&nbsp;<tt>s'</tt>&nbsp;can then be used to generate the next pair of values.

<h4>Randomized Arrival and Service Time</h4>
Rather than fixed arrival and service times, we will generate random times. A random number generator is an entity that generates one random number after another. Since it is not possible to generate a truly random number algorithmically, pseudo random number generation is adopted instead. A pseudo-random number generator can be initialized with a seed, such that the same seed always produces the same sequence of (seemingly random) numbers.

Although, Java provides a class&nbsp;<tt>java.util.Random</tt>, an alternative&nbsp;<tt>RandomGenerator</tt>&nbsp;class that is more suitable for discrete event simulation is provided for you that encapsulates different random number generators for use in our simulator. Each random number generator generates a different stream of random numbers. The constructor for&nbsp;<tt>RandomGenerator</tt>&nbsp;takes in three parameters:

<ul>
<li><tt>int seed</tt>&nbsp;is the base seed. Each random number generator uses its own seed that is derived from this base seed;</li>
<li><tt>double lambda</tt>&nbsp;is the arrival rate, λ;</li>
<li><tt>double mu</tt>&nbsp;is the service rate, μ.</li>
</ul>
The&nbsp;<strong>inter-arrival time</strong>&nbsp;is usually modeled as an exponential random variable, characterized by a single parameter&nbsp;<tt>λ</tt>&nbsp;denoting the arrival rate.&nbsp;The&nbsp;<tt>genInterArrivalTime()</tt>&nbsp;method of the class&nbsp;<tt>RandomGenerator</tt>&nbsp;is used for this purpose. Specifically,

<ul>
<li>start the simulation by generating the first customer arrival event with timestamp&nbsp;<tt>0</tt></li>
<li>if there are still more customers to simulate, generate the next arrival event with a timestamp of&nbsp;<tt>T + now</tt>, where&nbsp;<tt>T</tt>&nbsp;is generated with the method&nbsp;<tt>genInterArrivalTime()</tt>;</li>
</ul>
The&nbsp;<strong>service time</strong>&nbsp;is modeled as an exponential random variable, characterized by a single parameter, service rate μ. The method&nbsp;<tt>genServiceTime()</tt>&nbsp;from the class&nbsp;<tt>RandomGenerator</tt>&nbsp;can be used to generate the service time. Specifically,

<ul>
<li>each time a customer is being served, a&nbsp;<tt>DONE</tt>&nbsp;event is generated and scheduled;</li>
<li>the&nbsp;<tt>DONE</tt>&nbsp;event generated will have a timestamp of&nbsp;<tt>T + now</tt>, where&nbsp;<tt>T</tt>&nbsp;is generated with the method&nbsp;<tt>genServiceTime()</tt>.</li>
</ul>
You may refer to the API of the&nbsp;<tt>RandomGenerator</tt>&nbsp;class&nbsp;<a href="http://www.comp.nus.edu.sg/~cs2030/RandomGenerator">here</a>. The class file can be downloaded from&nbsp;<a href="http://www.comp.nus.edu.sg/~cs2030/RandomGenerator/RandomGenerator.class">here</a>.

Note that&nbsp;<tt>RandomGenerator</tt>&nbsp;class resides in the&nbsp;<tt>cs2030.simulator</tt>&nbsp;package. So,&nbsp;<tt>RandomGenerator.class</tt>&nbsp;should be saved in the&nbsp;<tt>cs2030/simulator</tt>&nbsp;directory.

<h4>More Complex Behaviour of Shops, Serves and Customers</h4>
You will extend the simulator to model the following entities.

<ul>
<li>FIFO (first-in-first-out) queues for customers with a given maximum capacity</li>
<li>Two new events
<ul>
<li><tt>SERVER_REST</tt>&nbsp;that simulates a server taking a rest, and</li>
<li><tt>SERVER_BACK</tt>&nbsp;that simulates a server returning back from rest</li>
</ul>
</li>
<li>Two types of servers,
<ul>
<li><em>human servers</em>&nbsp;who may rest after serving a customer, and</li>
<li><em>self-checkout counters</em>&nbsp;that never rest</li>
</ul>
</li>
<li>Two types of customers
<ul>
<li><em>typical</em>&nbsp;customers that joins the first queue (scanning from server 1 onwards) that is still not full, and</li>
<li><em>greedy</em>&nbsp;customers that joins the queue with the fewest waiting customers</li>
</ul>
</li>
</ul>
<h4>Customer Queues</h4>
Each human server now has a queue of customers to allow multiple customers to queue up. A customer that chooses to join a queue joins at the tail. When a server is done serving a customer, it serves the next waiting customer at the head of the queue. Hence, the queue should be a first-in-first-out (FIFO) structure.&nbsp;<strong>The self-checkout counters, however, have only a single shared queue.</strong>

<h4>Taking a Rest</h4>
The human servers are allowed to take occasional breaks. When a server finishes serving a customer, there is a probability&nbsp;<tt>P<sub>r</sub></tt>&nbsp;that the server takes a rest for a random amount of time&nbsp;<tt>T<sub>r</sub></tt>. During the break, the server does not serve the next waiting customer. Upon returning from the break, the server serves the next customer in the queue immediately.

To implement this behavior, introduce two new events,&nbsp;<tt>SERVER_REST</tt>&nbsp;and&nbsp;<tt>SERVER_BACK</tt>, to simulate taking a break, and returning. These events should be generated and scheduled in the simulator when the server decides to rest.

<h4>Self-Checkout</h4>
To reduce waiting time, self-checkout counters have been set-up.&nbsp;These self-checkout counters never need to rest. Customers queue up for the self-checkout counters in the same way as&nbsp;<em>human</em>&nbsp;servers. There is one shared queue for all self-checkout counters.

<h4>Customers’ Choice of Queue</h4>
As before, when a customer arrives, he or she first scans through the servers (in order, from&nbsp;<tt>1</tt>&nbsp;to&nbsp;<tt>k</tt>) to see if there is an idle server (i.e. not serving a customer and not resting). If there is one, the customer will go to the server to be served. Otherwise, a typical customer just chooses the first queue (while scanning from servers&nbsp;<tt>1</tt>&nbsp;to&nbsp;<tt>k</tt>) that is still not full to join. However, other than the typical customer, a&nbsp;<em>greedy</em>&nbsp;customer is introduced that always joins the queue with the fewest customers. In the case of a tie, the customer breaks the tie by choosing the first one while scanning from servers&nbsp;<tt>1</tt>&nbsp;to&nbsp;<tt>k</tt>.

If a customer cannot find any queue to join, he/she will leave the shop.

All classes dealing with the simulation should now reside in the&nbsp;<tt>cs2030.simulator</tt>&nbsp;package, with the&nbsp;<tt>Main</tt>&nbsp;class&nbsp;<b>outside</b>&nbsp;the package, but importing the necessary classes from the package.

<h4>Program Style</h4>
Check for styling errors by invoking&nbsp;<tt>checkstyle</tt>. For example, to check styling for all java files

<pre>$ java -jar checkstyle-8.2-all.jar -c cs2030_checks.xml *.java
</pre>
<h4>Writing and Generating Javadoc</h4>
You are to document your classes and methods with Javadoc comments.&nbsp;For more details, see the&nbsp;<a href="http://www.comp.nus.edu.sg/~cs2030/javadoc">javadoc</a>&nbsp;guide.

<h4>The Task</h4>
This task is divided into several levels.&nbsp;As the levels get progressively more complex, specific details will be provided in the corresponding levels.

As usual, you will need to keep track of the following statistics:

<ol>
<li>the average waiting time for customers who have been served</li>
<li>the number of customers served</li>
<li>the number of customers who left without being served</li>
</ol>
Take note of the following assumptions:

<ul>
<li><strong>There is no longer an upper bound for the number of customers</strong>;</li>
<li>The format of the input is always correct;</li>
<li>Output of a&nbsp;<tt>double</tt>&nbsp;value, say&nbsp;<tt>d</tt>, is to be formatted with&nbsp;<tt>String.format("%.3f", d)</tt>;</li>
</ul>
<b>You have to complete ALL levels.</b>

&nbsp;

<table border="1" cellpadding="10">
<tbody>
<tr>
<td>
<h4>Level 1</h4>
<b>Levels 1 and 2 are specified with very rigid requirements, primarily so that students can meet the desired learning outcomes for the project.</b>&nbsp;Do not worry if your code is packaged in&nbsp;<tt>cs2030.simulator</tt>. CodeCrunch will ignore the packages when testing in JShell.

First, we shall implement an&nbsp;<i>immutable</i>&nbsp;<tt>Shop</tt>&nbsp;class to hold the&nbsp;<tt>Servers</tt>. Recall that our&nbsp;<tt>Server</tt>&nbsp;class is defined as follows:

<pre>class Server {
    ...
    Server(int identifier, boolean isAvailable, boolean hasWaitingCustomer, double nextAvailableTime) {
        ...
    }
}
</pre>
The&nbsp;<tt>Shop</tt>&nbsp;class is to be developed using a very&nbsp;<i>functional</i>&nbsp;style. Hence&nbsp;<b>no loops are allowed</b>. Do not write explicit for-loops or while-loops or recursion; you may use implicit loops such as Java streams.

<pre><b>jshell&gt; new Shop(2)</b>
$.. ==&gt; [1 is available, 2 is available]
<b>jshell&gt; Shop shops = new Shop(List.of(new Server(1, true, false, 0), new Server(2, false, false, 1.0)))</b>
<b>jshell&gt; shops</b>
shops ==&gt; [1 is available, 2 is busy; available at 1.000]
<b>jshell&gt; shops.find(x -&gt; x.isAvailable())</b>
$.. ==&gt; Optional[1 is available]
<b>jshell&gt; new Shop(2).find(x -&gt; x.isAvailable())</b>
$.. ==&gt; Optional[1 is available]
<b>jshell&gt; shops.find(x -&gt; x.isAvailable()).ifPresent(System.out::println)</b>
1 is available
<b>jshell&gt; Server s = new Server(1, false, false, 2.0)</b>
<b>jshell&gt; shops.replace(s)</b>
$.. ==&gt; [1 is busy; available at 2.000, 2 is busy; available at 1.000]
<b>jshell&gt; shops.replace(s).find(x -&gt; x.isAvailable())</b>
$.. ==&gt; Optional.empty
<b>jshell&gt; shops</b>
shops ==&gt; [1 is available, 2 is busy; available at 1.000]
<b>jshell&gt; /exit</b>
</pre>
</td>
</tr>
<tr>
<td>
<h4>Level 2</h4>
Before proceeding to the&nbsp;<tt>Event</tt>&nbsp;class, you will first need to implement a generic&nbsp;<tt>Pair&lt;T,U&gt;</tt>&nbsp;class. This class is useful when returning multiple values from a function.

<pre><b>jshell&gt; Pair&lt;Integer,String&gt; pair = Pair.of(1, "one");</b>
<b>jshell&gt; pair.first()</b>
$.. ==&gt; 1
<b>jshell&gt; pair.second()</b>
$.. ==&gt; "one"
<b>jshell&gt; Pair&lt;Long,Long&gt; pair = Pair.of(0L, 100L);</b>
<b>jshell&gt; pair.first()</b>
$.. ==&gt; 0
<b>jshell&gt; pair.second()</b>
$.. ==&gt; 100
<b>jshell&gt; /exit</b>
</pre>
As for the&nbsp;<tt>Event</tt>&nbsp;class, previously we created different events by overridding the&nbsp;<tt>execute</tt>&nbsp;method in Event. Rather than substitution via overriding, we shall use substitution via lambdas!

The&nbsp;<tt>Event</tt>&nbsp;class is now required to have a property of type&nbsp;<tt>Function&lt;Shop, Pair&lt;Shop, Event&gt;&gt;</tt>. Different types of events shall assign this lambda to a different functionality. For example, suppose we have a&nbsp;<tt>DummyEvent</tt>&nbsp;defined with a functionality that takes in a&nbsp;<tt>Shop</tt>&nbsp;comprising some&nbsp;<tt>Servers</tt>, and creates an empty shop and another dummy event. So&nbsp;<tt>DummyEvent</tt>&nbsp;will be defined as follows (here we assume that the&nbsp;<tt>Event</tt>&nbsp;has a constructor that only takes a&nbsp;<tt>Function</tt>&nbsp;as argument):

<pre>class DummyEvent extends Event {
    DummyEvent() {
        super(x -&gt; new Pair&lt;Shop,Event&gt;(new Shop(), new DummyEvent()));
    }
    @Override
    public String toString() {
        return "DummyEvent";
    }
}

jshell&gt; Event e = new DummyEvent()
e ==&gt; DummyEvent

jshell&gt; e.execute(new Shop(1))
$.. ==&gt; Pair@........

jshell&gt; e.execute(new Shop(1)).first()
$.. ==&gt; []

jshell&gt; e.execute(new Shop(1)).second()
$.. ==&gt; DummyEvent
</pre>
Notice that the&nbsp;<tt>execute</tt>&nbsp;method of the&nbsp;<tt>Event</tt>&nbsp;class can be defined simply as:

<pre>final Pair&lt;Shop, Event&gt; execute(Shop shop) { // declared final to avoid overriding
    return this.func.apply(shop); // func is the Function property
}
</pre>
Invoking&nbsp;<tt>execute</tt>&nbsp;with a&nbsp;<tt>Shop</tt>&nbsp;will result in a&nbsp;<tt>Pair</tt>&nbsp;comprising a&nbsp;<tt>Shop</tt>&nbsp;(which is empty), and another&nbsp;<tt>DummyEvent</tt>. As you can see, other than&nbsp;<tt>Event</tt>&nbsp;itself, all specific types of events — arrive, serve, wait, done and leave, can now be fully specified with their relevant properties, and the addition of only one&nbsp;<tt>toString()</tt>&nbsp;method.&nbsp;<b>Note that this constraint shall be enforced during grading.</b>&nbsp;You still have the liberty of constructing your&nbsp;<tt>Event</tt>&nbsp;class in any way you wish.With this, you can now test the behaviour and correctness of your events by passing in a Shop and checking the returned&nbsp;<tt>Pair</tt>. Below is a snippet of how arrival events can be tested.

<pre><b>jshell&gt; // one available server with no waiting customer</b>
<b>jshell&gt; new ArriveEvent(new Customer(1, 1.0)).execute(new Shop(List.of(new Server(1,true,false,0)))).first() // (*) will not be tested</b>
$.. ==&gt; [1 is available]
<b>jshell&gt; new ArriveEvent(new Customer(1, 1.0)).execute(new Shop(List.of(new Server(1,true,false,0)))).second() // (*) will not be tested</b>
$.. ==&gt; 1.000 1 served by server 1
<b>jshell&gt; // one busy server with no waiting customer</b>
<b>jshell&gt; new ArriveEvent(new Customer(1, 1.0)).execute(new Shop(List.of(new Server(1,false,false,1.0)))).first()</b>
$.. ==&gt; [1 is busy; available at 1.000]
<b>jshell&gt; new ArriveEvent(new Customer(1, 1.0)).execute(new Shop(List.of(new Server(1,false,false,1.0)))).second()</b>
$.. ==&gt; 1.000 1 waits to be served by server 1
<b>jshell&gt; // one busy server with waiting customer</b>
<b>jshell&gt; new ArriveEvent(new Customer(1, 1.0)).execute(new Shop(List.of(new Server(1,false,true,2.0)))).first()</b>
$.. ==&gt; [1 is busy; waiting customer to be served at 2.000]
<b>jshell&gt; new ArriveEvent(new Customer(1, 1.0)).execute(new Shop(List.of(new Server(1,false,true,2.0)))).second()</b>
$.. ==&gt; 1.000 1 leaves
<b>jshell&gt; /exit</b>
</pre>
Note that an arrival event does not cause the servers in the shop to change, but only transits to another event depend on the state of the servers.

<tt><b>(*)</b></tt>&nbsp;This test case will not be tested as it is not deterministic. In the case if the server rests (level 5) in between the arrival and serve events, then the server will actually not be able to serve.

Just remember the following constraints:

<ul>
<li>every subclass of&nbsp;<tt>Event</tt>&nbsp;can only have properties, and at most&nbsp;<b>ONE</b>&nbsp;<tt>toString()</tt>&nbsp;method;</li>
<li>every subclass of&nbsp;<tt>Event</tt>&nbsp;must not contain explicit loops.</li>
</ul>
As there could be varying ways in how your specific events are constructed, there will be no test cases. That said, you should still test out this new implementation of event generation on the inputs of the final level of Project #1 and check if the behaviour is the same.
</td>
</tr>
<tr>
<td>
<h4>Level 3</h4>
<big><strong>Randomizing arrival and service times</strong></big>

<b>From this level on, we shall test your implementation with the&nbsp;<tt>Main</tt>&nbsp;class. Make sure that all other classes reside in the&nbsp;<tt>cs2030.simulator</tt>&nbsp;package.</b>

Input to the program comprises (in order of presentation):

<ul>
<li>an&nbsp;<tt>int</tt>&nbsp;value denoting the base seed for the&nbsp;<tt>RandomGenerator</tt>&nbsp;object;</li>
<li>an&nbsp;<tt>int</tt>&nbsp;value representing the number of servers</li>
<li>an&nbsp;<tt>int</tt>&nbsp;representing the number of customers (or the number of arrival events) to simulate</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the arrival rate, λ</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the service rate, μ</li>
</ul>
Remember to start the simulation by generating the first customer arrival event with timestamp&nbsp;<tt>0</tt>, and then generate the next arrival event of the next customer by adding the time generated using the method&nbsp;<tt>genInterArrivalTime()</tt>&nbsp;from the class&nbsp;<tt>RandomGenerator</tt>.

The method&nbsp;<tt>genServiceTime()</tt>&nbsp;from the class can be used to generate the service time. Intuitively, the service time ought to be generated together with the arrival time as each customer is created before the simulation starts. However, do note that the&nbsp;<tt>n<sup>th</sup></tt>&nbsp;customer to arrive might not be the&nbsp;<tt>n<sup>th</sup></tt>&nbsp;customer to be served! So service time should be generated when the customer is being served, which might entail passing the&nbsp;<tt>RandomGenerator</tt>&nbsp;along with the Customer. This need not be so!&nbsp;<i>Hint: Think Lazy…</i>

The following is a sample run of the program. Note that inputs are passed as command line arguments to&nbsp;<tt>Main</tt>.

&nbsp;

<table border="1">
<tbody>
<tr>
<td>
<pre><b>$ java Main 1 1 5 1.0 1.0</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 1
1.904 3 done serving by server 1
2.776 4 arrives
2.776 4 served by server 1
2.791 4 done serving by server 1
3.877 5 arrives
3.877 5 served by server 1
4.031 5 done serving by server 1
[0.000 5 0]
</pre>
</td>
</tr>
<tr>
<td>
<pre><b>$ java Main 1 2 10 1.0 1.0</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 1
1.904 3 done serving by server 1
2.776 4 arrives
2.776 4 served by server 1
2.791 4 done serving by server 1
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by server 2
3.922 6 done serving by server 2
4.031 5 done serving by server 1
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by server 2
9.105 9 arrives
9.105 9 waits to be served by server 1
9.160 10 arrives
9.160 10 waits to be served by server 2
10.484 7 done serving by server 1
10.484 9 served by server 1
10.781 9 done serving by server 1
11.636 8 done serving by server 2
11.636 10 served by server 2
11.688 10 done serving by server 2
[0.386 10 0]
</pre>
</td>
</tr>
</tbody>
</table>
</td>
</tr>
<tr>
<td>
<h4>Level 4</h4>
<big><strong>Implement the customer queues</strong></big>

Input to the program comprises (in order of presentation):

<ul>
<li>an&nbsp;<tt>int</tt>&nbsp;value denoting the base seed for the&nbsp;<tt>RandomGenerator</tt>&nbsp;object;</li>
<li>an&nbsp;<tt>int</tt>&nbsp;value representing the number of servers</li>
<li><b>an&nbsp;<tt>int</tt>&nbsp;value for the maximum queue length,&nbsp;<tt>Q<sub>max</sub></tt></b></li>
<li>an&nbsp;<tt>int</tt>&nbsp;representing the number of customers (or the number of arrival events) to simulate</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the arrival rate, λ</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the service rate, μ</li>
</ul>
Now, each queue has a maximum capacity&nbsp;<tt>Q<sub>max</sub></tt>, and a customer cannot join a queue that is full. Note that a customer being served is not inside the queue. When a customer arrives and all the queues are full, then the customer leaves.

Clearly, if&nbsp;<tt>Q<sub>max</sub>&nbsp;= 1</tt>, then the simulation reverts back to the one that allows only one waiting customer.

The following is a sample run of the program.

<table border="1">
<tbody>
<tr>
<td>
<pre><b>$ java Main 1 2 2 10 1.0 1.0</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 1
1.904 3 done serving by server 1
2.776 4 arrives
2.776 4 served by server 1
2.791 4 done serving by server 1
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by server 2
3.922 6 done serving by server 2
4.031 5 done serving by server 1
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by server 2
9.105 9 arrives
9.105 9 waits to be served by server 1
9.160 10 arrives
9.160 10 waits to be served by server 1
10.484 7 done serving by server 1
10.484 9 served by server 1
10.781 9 done serving by server 1
10.781 10 served by server 1
10.833 10 done serving by server 1
11.636 8 done serving by server 2
[0.300 10 0]
</pre>
</td>
</tr>
</tbody>
</table>
Notice that the number of command line inputs is different from the previous level, as well as subsequent ones. In your&nbsp;<tt>Main</tt>&nbsp;class, you will need to identify the number of inputs, so as parse the inputs correctly for the correct level.
</td>
</tr>
<tr>
<td>
<h4>Level 5</h4>
<big><strong>Implementing server breaks</strong></big>

Input to the program comprises (in order of presentation):

<ul>
<li>an&nbsp;<tt>int</tt>&nbsp;value denoting the base seed for the&nbsp;<tt>RandomGenerator</tt>&nbsp;object;</li>
<li>an&nbsp;<tt>int</tt>&nbsp;value representing the number of servers</li>
<li>an&nbsp;<tt>int</tt>&nbsp;value for the maximum queue length,&nbsp;<tt>Q<sub>max</sub></tt></li>
<li>an&nbsp;<tt>int</tt>&nbsp;representing the number of customers (or the number of arrival events) to simulate</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the arrival rate, λ</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the service rate, μ</li>
<li><strong>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the resting rate, ρ</strong></li>
<li><strong>a&nbsp;<tt>double</tt>&nbsp;parameter for the probability of resting,&nbsp;<tt>P<sub>r</sub></tt></strong></li>
</ul>
Include two events&nbsp;<tt>SERVER_REST</tt>&nbsp;and&nbsp;<tt>SERVER_BACK</tt>, to simulating taking a break, and returning. These events should be generated and scheduled in the simulator when the server decides to rest.

To decide if the server should rest, a random number uniformly drawn from&nbsp;<tt>[0, 1]</tt>&nbsp;is generated using the&nbsp;<tt>RandomGenerator</tt>&nbsp;method&nbsp;<tt>genRandomRest()</tt>. If the value returned is less than&nbsp;<tt>P<sub>r</sub></tt>, the server rests with a&nbsp;<tt>SERVER_REST</tt>&nbsp;event generated. Otherwise, the server does not rest but continues serving the next customer.

As soon as the server rests, a random rest period&nbsp;<tt>T<sub>r</sub></tt>&nbsp;is generated using the&nbsp;<tt>RandomGenerator</tt>&nbsp;method&nbsp;<tt>genRestPeriod()</tt>. This variable is an exponential random variable, governed by the resting rate, ρ. A&nbsp;<tt>SERVER_BACK</tt>&nbsp;event will be scheduled at&nbsp;<tt>T<sub>r</sub>&nbsp;+ now</tt>.

The following is a sample run of the program.

<table border="1">
<tbody>
<tr>
<td>
<pre><b>$ java Main 1 2 2 10 1.0 1.0 0 0</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 1
1.904 3 done serving by server 1
2.776 4 arrives
2.776 4 served by server 1
2.791 4 done serving by server 1
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by server 2
3.922 6 done serving by server 2
4.031 5 done serving by server 1
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by server 2
9.105 9 arrives
9.105 9 waits to be served by server 1
9.160 10 arrives
9.160 10 waits to be served by server 1
10.484 7 done serving by server 1
10.484 9 served by server 1
10.781 9 done serving by server 1
10.781 10 served by server 1
10.833 10 done serving by server 1
11.636 8 done serving by server 2
[0.300 10 0]
</pre>
</td>
</tr>
<tr>
<td>
<pre><b>$ java Main 1 2 2 20 1.0 1.0 0.1 0.5</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 2
1.904 3 done serving by server 2
2.776 4 arrives
2.776 4 served by server 2
2.791 4 done serving by server 2
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by server 2
3.922 6 done serving by server 2
4.031 5 done serving by server 1
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by server 2
9.105 9 arrives
9.105 9 waits to be served by server 1
9.160 10 arrives
9.160 10 waits to be served by server 1
9.225 11 arrives
9.225 11 waits to be served by server 2
10.148 12 arrives
10.148 12 waits to be served by server 2
10.484 7 done serving by server 1
10.484 9 served by server 1
10.781 9 done serving by server 1
11.205 13 arrives
11.205 13 waits to be served by server 1
11.636 8 done serving by server 2
11.636 11 served by server 2
11.688 11 done serving by server 2
11.688 12 served by server 2
12.429 14 arrives
12.429 14 waits to be served by server 2
13.109 15 arrives
13.109 15 waits to be served by server 2
14.644 10 served by server 1
15.013 10 done serving by server 1
15.178 12 done serving by server 2
15.178 14 served by server 2
15.264 16 arrives
15.264 16 waits to be served by server 1
15.338 14 done serving by server 2
15.338 15 served by server 2
15.524 17 arrives
15.524 17 waits to be served by server 2
15.940 18 arrives
15.940 18 waits to be served by server 2
17.793 19 arrives
17.793 19 leaves
18.207 15 done serving by server 2
18.207 17 served by server 2
18.765 20 arrives
18.765 20 waits to be served by server 2
19.103 17 done serving by server 2
19.103 18 served by server 2
20.146 18 done serving by server 2
40.474 13 served by server 1
40.480 13 done serving by server 1
40.480 16 served by server 1
41.056 16 done serving by server 1
57.110 20 served by server 2
57.852 20 done serving by server 2
[6.025 19 1]
</pre>
</td>
</tr>
</tbody>
</table>
</td>
</tr>
<tr>
<td>
<h4>Level 6</h4>
<big><strong>Include self-checkout counters</strong></big>

Input to the program comprises (in order of presentation):

<ul>
<li>an&nbsp;<tt>int</tt>&nbsp;value denoting the base seed for the&nbsp;<tt>RandomGenerator</tt>&nbsp;object;</li>
<li>an&nbsp;<tt>int</tt>&nbsp;value representing the number of servers</li>
<li><strong>an&nbsp;<tt>int</tt>&nbsp;value representing the number of self-checkout counters,&nbsp;<tt>N<sub>self</sub></tt></strong></li>
<li>an&nbsp;<tt>int</tt>&nbsp;value for the maximum queue length,&nbsp;<tt>Q<sub>max</sub></tt></li>
<li>an&nbsp;<tt>int</tt>&nbsp;representing the number of customers (or the number of arrival events) to simulate</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the arrival rate, λ</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the service rate, μ</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the resting rate, ρ</li>
<li>a&nbsp;<tt>double</tt>&nbsp;parameter for the probability of resting,&nbsp;<tt>P<sub>r</sub></tt></li>
</ul>
There are&nbsp;<tt>N<sub>self</sub></tt>&nbsp;self-checkout counters set up. In particular, if there are&nbsp;<tt>k</tt>&nbsp;human servers, then the self-checkout counters are identified from&nbsp;<tt>k + 1</tt>&nbsp;onwards. All self-checkout counters share the same queue. When we print out the wait event, we always say that the customer is waiting for the self-checkout counter&nbsp;<tt>k + 1</tt>, even though this customer may eventually be served by another self-checkout counter.

The following is a sample run of the program.

<table border="1">
<tbody>
<tr>
<td>
<pre><b>$ java Main 1 2 0 2 20 1.0 1.0 0.1 0.5</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 2
1.904 3 done serving by server 2
2.776 4 arrives
2.776 4 served by server 2
2.791 4 done serving by server 2
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by server 2
3.922 6 done serving by server 2
4.031 5 done serving by server 1
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by server 2
9.105 9 arrives
9.105 9 waits to be served by server 1
9.160 10 arrives
9.160 10 waits to be served by server 1
9.225 11 arrives
9.225 11 waits to be served by server 2
10.148 12 arrives
10.148 12 waits to be served by server 2
10.484 7 done serving by server 1
10.484 9 served by server 1
10.781 9 done serving by server 1
11.205 13 arrives
11.205 13 waits to be served by server 1
11.636 8 done serving by server 2
11.636 11 served by server 2
11.688 11 done serving by server 2
11.688 12 served by server 2
12.429 14 arrives
12.429 14 waits to be served by server 2
13.109 15 arrives
13.109 15 waits to be served by server 2
14.644 10 served by server 1
15.013 10 done serving by server 1
15.178 12 done serving by server 2
15.178 14 served by server 2
15.264 16 arrives
15.264 16 waits to be served by server 1
15.338 14 done serving by server 2
15.338 15 served by server 2
15.524 17 arrives
15.524 17 waits to be served by server 2
15.940 18 arrives
15.940 18 waits to be served by server 2
17.793 19 arrives
17.793 19 leaves
18.207 15 done serving by server 2
18.207 17 served by server 2
18.765 20 arrives
18.765 20 waits to be served by server 2
19.103 17 done serving by server 2
19.103 18 served by server 2
20.146 18 done serving by server 2
40.474 13 served by server 1
40.480 13 done serving by server 1
40.480 16 served by server 1
41.056 16 done serving by server 1
57.110 20 served by server 2
57.852 20 done serving by server 2
[6.025 19 1]
</pre>
</td>
</tr>
<tr>
<td>
<pre><b>$ java Main 1 2 1 2 20 1.0 1.0 0.1 0.5</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 2
1.904 3 done serving by server 2
2.776 4 arrives
2.776 4 served by server 2
2.791 4 done serving by server 2
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by server 2
3.922 6 done serving by server 2
4.031 5 done serving by server 1
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by server 2
9.105 9 arrives
9.105 9 served by self-check 3
9.160 10 arrives
9.160 10 waits to be served by server 1
9.225 11 arrives
9.225 11 waits to be served by server 1
9.402 9 done serving by self-check 3
10.148 12 arrives
10.148 12 served by self-check 3
10.200 12 done serving by self-check 3
10.484 7 done serving by server 1
10.484 10 served by server 1
11.205 13 arrives
11.205 13 served by self-check 3
11.574 13 done serving by self-check 3
11.636 8 done serving by server 2
12.429 14 arrives
12.429 14 served by self-check 3
12.589 14 done serving by self-check 3
13.109 15 arrives
13.109 15 served by self-check 3
13.974 10 done serving by server 1
13.974 11 served by server 1
14.869 11 done serving by server 1
15.264 16 arrives
15.264 16 served by server 1
15.524 17 arrives
15.524 17 served by server 2
15.531 17 done serving by server 2
15.940 18 arrives
15.940 18 waits to be served by server 1
15.978 15 done serving by self-check 3
16.307 16 done serving by server 1
16.307 18 served by server 1
16.883 18 done serving by server 1
17.793 19 arrives
17.793 19 served by server 1
18.535 19 done serving by server 1
18.765 20 arrives
18.765 20 served by server 1
21.773 20 done serving by server 1
[0.322 20 0]
</pre>
</td>
</tr>
<tr>
<td>
<pre><b>$ java Main 1 1 2 2 20 1.0 0.1 0.1 0.5</b>
0.000 1 arrives
0.000 1 served by server 1
0.314 2 arrives
0.314 2 served by self-check 2
1.205 3 arrives
1.205 3 served by self-check 3
1.351 2 done serving by self-check 2
2.776 4 arrives
2.776 4 served by self-check 2
2.919 4 done serving by self-check 2
3.131 1 done serving by server 1
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by self-check 2
4.036 6 done serving by self-check 2
5.419 5 done serving by server 1
8.200 3 done serving by self-check 3
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by self-check 2
9.105 9 arrives
9.105 9 served by self-check 3
9.160 10 arrives
9.160 10 waits to be served by server 1
9.225 11 arrives
9.225 11 waits to be served by server 1
10.148 12 arrives
10.148 12 waits to be served by self-check 2
11.205 13 arrives
11.205 13 waits to be served by self-check 2
12.074 9 done serving by self-check 3
12.074 12 served by self-check 3
12.429 14 arrives
12.429 14 waits to be served by self-check 2
12.591 12 done serving by self-check 3
12.591 13 served by self-check 3
13.109 15 arrives
13.109 15 waits to be served by self-check 2
15.264 16 arrives
15.264 16 leaves
15.524 17 arrives
15.524 17 leaves
15.940 18 arrives
15.940 18 leaves
17.793 19 arrives
17.793 19 leaves
18.765 20 arrives
18.765 20 leaves
23.784 7 done serving by server 1
24.631 10 served by server 1
28.318 10 done serving by server 1
28.318 11 served by server 1
29.923 11 done serving by server 1
34.974 8 done serving by self-check 2
34.974 14 served by self-check 2
47.487 13 done serving by self-check 3
47.487 15 served by self-check 3
56.445 15 done serving by self-check 3
63.665 14 done serving by self-check 2
[6.320 15 5]
</pre>
</td>
</tr>
</tbody>
</table>
</td>
</tr>
<tr>
<td>
<h4>Level 7</h4>
<big><strong>Include greedy customers</strong></big>

Input to the program comprises (in order of presentation):

<ul>
<li>an&nbsp;<tt>int</tt>&nbsp;value denoting the base seed for the&nbsp;<tt>RandomGenerator</tt>&nbsp;object;</li>
<li>an&nbsp;<tt>int</tt>&nbsp;value representing the number of servers</li>
<li>an&nbsp;<tt>int</tt>&nbsp;value representing the number of self-checkout counters,&nbsp;<tt>N<sub>self</sub></tt></li>
<li>an&nbsp;<tt>int</tt>&nbsp;value for the maximum queue length,&nbsp;<tt>Q<sub>max</sub></tt></li>
<li>an&nbsp;<tt>int</tt>&nbsp;representing the number of customers (or the number of arrival events) to simulate</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the arrival rate, λ</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the service rate, μ</li>
<li>a positive&nbsp;<tt>double</tt>&nbsp;parameter for the resting rate, ρ</li>
<li>a&nbsp;<tt>double</tt>&nbsp;parameter for the probability of resting,&nbsp;<tt>P<sub>r</sub></tt></li>
<li><strong>a&nbsp;<tt>double</tt>&nbsp;parameter for the probability of a greedy customer occurring,&nbsp;<tt>P<sub>g</sub></tt></strong></li>
</ul>
An arriving customer is a greedy customer with probability&nbsp;<tt>P<sub>g</sub></tt>. To decide whether a typical or greedy customer is created, a random number uniformly drawn from&nbsp;<tt>[0, 1]</tt>&nbsp;is generated with the&nbsp;<tt>RandomGenerator</tt>&nbsp;method&nbsp;<tt>genCustomerType()</tt>. If the value returned is less than&nbsp;<tt>P<sub>g</sub></tt>, a greedy customer is generated, otherwise, a typical customer is generated.The following is a sample run of the program.

<table border="1">
<tbody>
<tr>
<td>
<pre><b>$ java Main 1 2 1 2 20 1.0 1.0 0.1 0.5 0</b>
0.000 1 arrives
0.000 1 served by server 1
0.313 1 done serving by server 1
0.314 2 arrives
0.314 2 served by server 1
0.417 2 done serving by server 1
1.205 3 arrives
1.205 3 served by server 2
1.904 3 done serving by server 2
2.776 4 arrives
2.776 4 served by server 2
2.791 4 done serving by server 2
3.877 5 arrives
3.877 5 served by server 1
3.910 6 arrives
3.910 6 served by server 2
3.922 6 done serving by server 2
4.031 5 done serving by server 1
9.006 7 arrives
9.006 7 served by server 1
9.043 8 arrives
9.043 8 served by server 2
9.105 9 arrives
9.105 9 served by self-check 3
9.160 10 arrives
9.160 10 waits to be served by server 1
9.225 11 arrives
9.225 11 waits to be served by server 1
9.402 9 done serving by self-check 3
10.148 12 arrives
10.148 12 served by self-check 3
10.200 12 done serving by self-check 3
10.484 7 done serving by server 1
10.484 10 served by server 1
11.205 13 arrives
11.205 13 served by self-check 3
11.574 13 done serving by self-check 3
11.636 8 done serving by server 2
12.429 14 arrives
12.429 14 served by self-check 3
12.589 14 done serving by self-check 3
13.109 15 arrives
13.109 15 served by self-check 3
13.974 10 done serving by server 1
13.974 11 served by server 1
14.869 11 done serving by server 1
15.264 16 arrives
15.264 16 served by server 1
15.524 17 arrives
15.524 17 served by server 2
15.531 17 done serving by server 2
15.940 18 arrives
15.940 18 waits to be served by server 1
15.978 15 done serving by self-check 3
16.307 16 done serving by server 1
16.307 18 served by server 1
16.883 18 done serving by server 1
17.793 19 arrives
17.793 19 served by server 1
18.535 19 done serving by server 1
18.765 20 arrives
18.765 20 served by server 1
21.773 20 done serving by server 1
[0.322 20 0]
</pre>
</td>
</tr>
<tr>
<td>
<pre><b>$ java Main 1 2 1 2 20 1.0 1.0 0.1 0.5 0.9</b>
0.000 1(greedy) arrives
0.000 1(greedy) served by server 1
0.313 1(greedy) done serving by server 1
0.314 2(greedy) arrives
0.314 2(greedy) served by server 1
0.417 2(greedy) done serving by server 1
1.205 3(greedy) arrives
1.205 3(greedy) served by server 2
1.904 3(greedy) done serving by server 2
2.776 4(greedy) arrives
2.776 4(greedy) served by server 2
2.791 4(greedy) done serving by server 2
3.877 5(greedy) arrives
3.877 5(greedy) served by server 1
3.910 6(greedy) arrives
3.910 6(greedy) served by server 2
3.922 6(greedy) done serving by server 2
4.031 5(greedy) done serving by server 1
9.006 7(greedy) arrives
9.006 7(greedy) served by server 1
9.043 8(greedy) arrives
9.043 8(greedy) served by server 2
9.105 9(greedy) arrives
9.105 9(greedy) served by self-check 3
9.160 10 arrives
9.160 10 waits to be served by server 1
9.225 11(greedy) arrives
9.225 11(greedy) waits to be served by server 2
9.402 9(greedy) done serving by self-check 3
10.148 12(greedy) arrives
10.148 12(greedy) served by self-check 3
10.200 12(greedy) done serving by self-check 3
10.484 7(greedy) done serving by server 1
10.484 10 served by server 1
11.205 13(greedy) arrives
11.205 13(greedy) served by self-check 3
11.574 13(greedy) done serving by self-check 3
11.636 8(greedy) done serving by server 2
12.429 14(greedy) arrives
12.429 14(greedy) served by self-check 3
12.589 14(greedy) done serving by self-check 3
13.109 15(greedy) arrives
13.109 15(greedy) served by self-check 3
13.974 10 done serving by server 1
15.264 16 arrives
15.264 16 served by server 1
15.500 11(greedy) served by server 2
15.524 17(greedy) arrives
15.524 17(greedy) waits to be served by server 1
15.940 18(greedy) arrives
15.940 18(greedy) waits to be served by server 2
15.978 15(greedy) done serving by self-check 3
16.159 16 done serving by server 1
16.159 17(greedy) served by server 1
16.166 17(greedy) done serving by server 1
16.543 11(greedy) done serving by server 2
16.543 18(greedy) served by server 2
17.119 18(greedy) done serving by server 2
17.793 19(greedy) arrives
17.793 19(greedy) served by server 2
18.535 19(greedy) done serving by server 2
18.765 20(greedy) arrives
18.765 20(greedy) served by server 2
21.773 20(greedy) done serving by server 2
[0.442 20 0]
</pre>
</td>
</tr>
</tbody>
</table>
</td>
</tr>
</tbody>
</table>
