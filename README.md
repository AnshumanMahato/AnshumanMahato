<div>
 
# 💫 About Me:
 
I am an aspiring developer and mainly focus on web technology. Till now, I have acquired proficiency in HTML, CSS, JavaScript, Bootstrap, NodeJS, Express, and MongoDB. I am currently learning TypeScript and Web Design.<br><br>That's it from my side! I would love to connect with you.
	
## 🌐 Socials:
 
[![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?logo=Facebook&logoColor=white)](https://facebook.com/anshuman.mahato.0935) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/anshuman_mahato) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/anshuman-mahato) [![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?logo=Twitter&logoColor=white)](https://twitter.com/AnshumanMahato_) 

# 💻 Tech Stack:
 
<div align="center">
	<img src="https://skillicons.dev/icons?i=html,css,sass,tailwind,bootstrap,js,react,redux,nodejs,express,mongodb,docker" alt="skills"/>
</div>

# Blog posts

<!-- BLOG-POST-LIST:START -->
 - 💫[Managing Event Flow: A Deep Dive into JavaScript Event Propagation](https://dev.to/anshumanmahato/managing-event-flow-a-deep-dive-into-javascript-event-propagation-2gha) 
 - &lt;p&gt;Before we begin, let&#39;s consider a scenario. Say we&#39;re building a User card. It has the photo of the user, their name and a button to send a message to them. If we click anywhere on the card, a description of the user appears. If we click the send message button, a textbox appears to send them a message.&lt;/p&gt;

&lt;p&gt;The design is simple. We develop the structure with HTML and CSS. As for the interactions, we add a click handler to the card, which opens the user details and a click handler to the button in the card that opens the message panel.&lt;/p&gt;

&lt;p&gt;Yeah, that should work, right? Let&#39;s try it out and see for ourselves.&lt;/p&gt;

&lt;p&gt;&lt;iframe height=&quot;600&quot; src=&quot;https://codepen.io/anshumanmahato/embed/JjVNBxy?height=600&amp;amp;default-tab=result&amp;amp;embed-version=2&quot;&gt;
&lt;/iframe&gt;
&lt;/p&gt;

&lt;p&gt;Well, it didn&#39;t work. You&#39;re right if you think that by clicking the button, we are indirectly clicking the card. Both the event handlers are executed when we click the send message button. So, how do we implement this?&lt;/p&gt;

&lt;p&gt;To figure this out, we must first understand how JavaScript tracks the events in the DOM. We must determine when JavaScript executes the event handlers. We must learn about &lt;strong&gt;Event Propagation in JavaScript DOM&lt;/strong&gt;.&lt;/p&gt;

&lt;h2&gt;
  
  
  Event Propagation - movement of Events through the DOM
&lt;/h2&gt;

&lt;p&gt;JavaScript uses &lt;strong&gt;Event Propagation&lt;/strong&gt; to handle how events travel through the Document Object Model &lpar;DOM&rpar; when an event occurs and reaches the target element, triggering further actions based on the event.&lt;/p&gt;

&lt;p&gt;It happens in three phases - Capturing, Targeting and Bubbling.&lt;/p&gt;

&lt;p&gt;&lt;strong&gt;1. Capturing&lt;/strong&gt; - This is the first phase in the event propagation process. When an event is triggered, it starts from the root of the DOM tree and then moves down towards the target element. &lt;u&gt;By default, event handlers are not executed in this phase&lt;/u&gt;.&lt;/p&gt;

&lt;p&gt;&lt;strong&gt;2. Targeting&lt;/strong&gt; - This phase starts once the event reaches the element where the event was triggered. Any event handlers associated with the target element for the particular event get executed in this phase.&lt;/p&gt;

&lt;p&gt;&lt;strong&gt;3. Bubbling&lt;/strong&gt; - After targeting, the event traces back its path and moves back up to the root of the DOM. It is in this phase that the event handlers execute. JavaScript executes the associated event handlers in order as the event moves up the DOM tree.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F5dczl4ynpgto6xrduxom.jpg&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F5dczl4ynpgto6xrduxom.jpg&quot; alt=&quot;Event Propagation&quot; width=&quot;800&quot; height=&quot;914&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;If you got this, you must have figured out what is happening in our example. When we click the button, the click event starts capturing. It first captures the &lt;strong&gt;&lt;code&gt;.user&lt;/code&gt;&lt;/strong&gt; element, then the &lt;strong&gt;&lt;code&gt;.user__description&lt;/code&gt;&lt;/strong&gt; and then the &lt;strong&gt;&lt;code&gt;.user__cta&lt;/code&gt;&lt;/strong&gt;, which is the button. Upon targeting the button, it renders the message panel as per the event handler. Then, it starts bubbling, and when it reaches the &lt;strong&gt;&lt;code&gt;.user&lt;/code&gt;&lt;/strong&gt; element, it executes the associated event handler and renders the details, replacing the message panel.&lt;/p&gt;

&lt;p&gt;Now, we have figured out what is happening here. Let&#39;s see how we can deal with this.&lt;/p&gt;

&lt;h2&gt;
  
  
  Manipulating Event Propagation
&lt;/h2&gt;

&lt;p&gt;As you must have understood, to make our example work, we must stop the propagation once the event handler for the button executes. We have two utilities for this - &lt;strong&gt;&lt;code&gt;event.stopPropagation&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; and &lt;strong&gt;&lt;code&gt;event.stopImmediatePropagation&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt;. Both of them block the propagation of the event once encountered. There is only one difference in their work.&lt;/p&gt;

&lt;p&gt;The &lt;strong&gt;&lt;code&gt;event.stopPropagation&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; stops the event from going to the next element. All handlers associated with the current element for that particular event will still get executed. This does not happen in &lt;strong&gt;&lt;code&gt;event.stopImmediatePropagation&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; where propagation stops immediately, and no event handlers execute even if they belong to the current element.&lt;/p&gt;

&lt;p&gt;With this knowledge, let&#39;s update our solution.&lt;/p&gt;

&lt;p&gt;&lt;iframe height=&quot;600&quot; src=&quot;https://codepen.io/anshumanmahato/embed/OJGgJed?height=600&amp;amp;default-tab=result&amp;amp;embed-version=2&quot;&gt;
&lt;/iframe&gt;
&lt;/p&gt;

&lt;h2&gt;
  
  
  Executing in the Capture Phase.
&lt;/h2&gt;

&lt;p&gt;I said earlier that event handlers do not execute during the capture phase by default. You must be thinking if there is some way to do that. True, there is a way to do this. Ironically, the solution to this problem is also &lt;strong&gt;&lt;code&gt;true&lt;/code&gt;&lt;/strong&gt;.&lt;/p&gt;

&lt;p&gt;You must have used the &lt;strong&gt;&lt;code&gt;addEventListener&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; utility with two parameters to attach events to elements - the event type and the handler function. It also takes a third parameter called &lt;strong&gt;&lt;code&gt;useCapture&lt;/code&gt;&lt;/strong&gt;. Its default value is &lt;strong&gt;&lt;code&gt;false&lt;/code&gt;&lt;/strong&gt;. If we pass &lt;strong&gt;&lt;code&gt;true&lt;/code&gt;&lt;/strong&gt; to this, then the handler will be executed at capturing instead of bubbling.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;nx&quot;&gt;element&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nf&quot;&gt;addEventListener&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;click&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;handlerFn&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;kc&quot;&gt;true&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Well, here&#39;s a question for you folks. What will happen if we call &lt;strong&gt;&lt;code&gt;event.stopPropagation&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; in a handler executed during the capture phase? Comment down the answers in the comment section 😉.&lt;/p&gt;

&lt;h2&gt;
  
  
  Optimization with Event Delegation
&lt;/h2&gt;

&lt;p&gt;&lt;strong&gt;Event delegation&lt;/strong&gt; is a technique where you delegate the event listener to the parent element to listen to events triggered by its children. We usually do this when the children perform similar actions upon an event.&lt;/p&gt;

&lt;p&gt;Think of a Navbar with many links. Upon clicking a link, an associated dropdown menu opens. The direct way to do this will be to attach a listener to every link. But that would result in too many event handlers all doing almost the same task.&lt;/p&gt;

&lt;p&gt;We can implement event delegation here to optimize this. We can attach the listener to the direct parent of the links. So, instead of having multiple listeners, we will have a single listener that will listen to clicks on any child link. &lt;/p&gt;

&lt;p&gt;But how do we determine which link we clicked? For that, we look at the &lt;strong&gt;&lt;code&gt;target&lt;/code&gt;&lt;/strong&gt; property of the &lt;strong&gt;&lt;code&gt;event&lt;/code&gt;&lt;/strong&gt;. This property holds the node where the event was triggered. With it, we can determine the link we clicked and then open the respective dropdown accordingly.&lt;/p&gt;

&lt;p&gt;That&#39;s how Event Delegation works. Here&#39;s the demonstration for the above example.&lt;/p&gt;

&lt;p&gt;&lt;iframe height=&quot;600&quot; src=&quot;https://codepen.io/anshumanmahato/embed/bGJRbLr?height=600&amp;amp;default-tab=result&amp;amp;embed-version=2&quot;&gt;
&lt;/iframe&gt;
&lt;/p&gt;

&lt;h2&gt;
  
  
  That&#39;s all I had to say
&lt;/h2&gt;

&lt;p&gt;Hey there, we&#39;ve come to the end of this article! I hope it was helpful and informative for you. I&#39;m excited to hear your thoughts and feedback, so don&#39;t hesitate to drop a comment below.&lt;/p&gt;

&lt;p&gt;By the way, if you want to connect with me outside of this platform, you can find me on Twitter, LinkedIn, and GitHub. Here are the links:&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://twitter.com/AnshumanMahato_&quot;&gt;Twitter&lt;/a&gt;    &lt;a href=&quot;https://www.linkedin.com/in/anshuman-mahato/&quot;&gt;LinkedIn&lt;/a&gt;    &lt;a href=&quot;https://github.com/AnshumanMahato&quot;&gt;GitHub&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;Thanks for reading this far, and keep exploring new things!🌟&lt;/p&gt;

 

 - 🚀[For intricate state handling, try out the useReducer&lpar;&rpar; Hook](https://dev.to/anshumanmahato/for-intricate-state-handling-try-out-the-usereducer-hook-1952) 
 - &lt;p&gt;So, lately, I have been working on a form component. It was a registration form that had quite a few fields in it. The state management for this was not complex, but it was repetitive. Creating a state for each input field and updating it whenever the user interacts with them, I was writing the same code with minor differences.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;let&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;fname&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;setFname&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;kd&quot;&gt;let&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;lname&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;setLname&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;kd&quot;&gt;let&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;email&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;setEmail&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;...&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Also, I felt that all these pieces must be related to one another rather than being separate entities. So, I switched to using a single state with an object storing all input fields.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;let&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;formData&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;setFormData&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt;
   &lt;span class=&quot;na&quot;&gt;fname&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
   &lt;span class=&quot;na&quot;&gt;lname&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
   &lt;span class=&quot;na&quot;&gt;email&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
   &lt;span class=&quot;p&quot;&gt;...&lt;/span&gt; 
&lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Even though the state was centralized, the event handlers still managed the state update logic.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;changeEmail&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;e&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
     &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;regex&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/^&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;a-zA-Z0-9.!#$%&amp;amp;&#39;*+&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;=?^_`{|}~-&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;]&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;+@&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;a-zA-Z0-9-&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;]&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;+&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;&lpar;?:\.[&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;a-zA-Z0-9-&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;]&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;+&lt;/span&gt;&lt;span class=&quot;se&quot;&gt;&rpar;&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;*$/&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

     &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;e&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;target&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nf&quot;&gt;match&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;regex&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&rpar;&lt;/span&gt;
         &lt;span class=&quot;nf&quot;&gt;setFormData&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{...&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;email&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;e&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;target&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;I was looking for some way to centralize this as well. That&#39;s when I came across the &lt;strong&gt;&lt;code&gt;useReducer&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; hook, a utility for complex state management. &lt;/p&gt;

&lt;p&gt;Want to know about this? Just follow along with me.&lt;/p&gt;

&lt;h2&gt;
  
  
  What is this useReducer&lpar;&rpar; hook, and how does it work?
&lt;/h2&gt;

&lt;p&gt;The &lt;strong&gt;&lt;code&gt;useReducer&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; hook is an alternative to the &lt;strong&gt;&lt;code&gt;useState&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; hook that helps to manage complex states in a React application. In fact, the useState&lpar;&rpar; hook uses the useReducer&lpar;&rpar; hook behind the scenes itself.&lt;/p&gt;

&lt;p&gt;The useReducer&lpar;&rpar; hook takes a &lt;strong&gt;&lt;code&gt;reducer&lt;/code&gt;&lt;/strong&gt; function and the &lt;strong&gt;&lt;code&gt;initial state&lt;/code&gt;&lt;/strong&gt; as its parameter and returns an array. The first element of this array is the &lt;strong&gt;&lt;code&gt;state&lt;/code&gt;&lt;/strong&gt; object, and the second element is the &lt;strong&gt;&lt;code&gt;dispatch&lt;/code&gt;&lt;/strong&gt; function. At first, it might look very similar to useState&lpar;&rpar;. But the working is very different here.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;dispatch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useReducer&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;reducer&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;initialState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;The &lt;strong&gt;&lt;code&gt;state&lt;/code&gt;&lt;/strong&gt; and the &lt;strong&gt;&lt;code&gt;initialState&lt;/code&gt;&lt;/strong&gt; is obvious. But, what is &lt;strong&gt;&lt;code&gt;dispatch&lt;/code&gt;&lt;/strong&gt; and &lt;strong&gt;&lt;code&gt;reducer&lt;/code&gt;&lt;/strong&gt;? Let&#39;s try to understand how all this works.&lt;/p&gt;

&lt;h2&gt;
  
  
  Reducer, Actions and Dispatch
&lt;/h2&gt;

&lt;p&gt;The &lt;strong&gt;&lt;code&gt;dispatch&lt;/code&gt;&lt;/strong&gt; is analogous to the update function returned by the useState&lpar;&rpar; hook. Both are used to update the state. The difference lies in how they work. Unlike the update function, where we pass the next state directly, we pass an &lt;strong&gt;&lt;code&gt;Action&lt;/code&gt;&lt;/strong&gt; here.&lt;/p&gt;

&lt;p&gt;Now, you may ask, &quot;What is this Action?&quot;. Well, An &lt;strong&gt;&lt;code&gt;Action&lt;/code&gt;&lt;/strong&gt; is an object that specifies how we want to update our state. You may structure your Action object as you wish. But conventionally, we have two fields in this object - &lt;strong&gt;&lt;code&gt;type&lt;/code&gt;&lt;/strong&gt; and &lt;strong&gt;&lt;code&gt;payload&lt;/code&gt;&lt;/strong&gt;. The type specifies the kind of update that we want to perform. The payload takes any external values that might be needed for the update.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;nf&quot;&gt;dispatch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt;&lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ACTION TYPE&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;payload&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;values to pass&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;What does the dispatch do with this Action object? It passes it to its associated reducer. The &lt;strong&gt;&lt;code&gt;reducer&lt;/code&gt;&lt;/strong&gt; is a function that maintains the logic for state updates for every action type. It takes the current state and an Action object as arguments and returns the updated state per the requested action. After this, the component is rendered according to the update state.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fo6i2fi0eumvkvnm2mxgq.jpg&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fo6i2fi0eumvkvnm2mxgq.jpg&quot; alt=&quot;State update flow in useReducer&lpar;&rpar; hook&quot; width=&quot;800&quot; height=&quot;445&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;h2&gt;
  
  
  Let&#39;s try this out
&lt;/h2&gt;

&lt;p&gt;Let us build a simple &lt;strong&gt;&lt;code&gt;Counter App&lt;/code&gt;&lt;/strong&gt; to see this working &lpar;cliche, I know&rpar;. The application will have four functions -&lt;/p&gt;

&lt;ol&gt;
&lt;li&gt;We can increment the count by 1.&lt;/li&gt;
&lt;li&gt;We can decrease the count by 1.&lt;/li&gt;
&lt;li&gt;We can add some value to the count.&lt;/li&gt;
&lt;li&gt;We can subtract some value from the count.&lt;/li&gt;
&lt;/ol&gt;

&lt;p&gt;Let&#39;s begin with our initial state. It will only contain a field for the &lt;strong&gt;&lt;code&gt;count&lt;/code&gt;&lt;/strong&gt;.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;initState&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;na&quot;&gt;count&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;0&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Now, we implement our reducer function.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;reducer&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;action&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
   &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;payload&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;action&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
   &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;count&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
   &lt;span class=&quot;k&quot;&gt;switch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;INCREMENT&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{...&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;count&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;count&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;+&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;1&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;DECREMENT&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{...&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;count&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;count&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;1&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ADD&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{...&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;count&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;count&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;+&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;payload&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;SUBTRACT&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{...&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;count&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;count&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;payload&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;
      &lt;span class=&quot;nl&quot;&gt;default&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
   &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;It&#39;s time to implement our Counter component.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;Counter&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;dispatch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useReducer&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;reducer&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;initState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;setValue&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;0&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
  &lt;span class=&quot;k&quot;&gt;return &lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;h1&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;state&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;count&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;h1&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;onClick&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;dispatch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;INCREMENT&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;Increment&lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;onClick&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;dispatch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;DECREMENT&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;Decrement&lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;input&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;&quot;number&quot;&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;onChange&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;e&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;setValue&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nf&quot;&gt;parseInt&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;e&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;target&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&rpar;&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;onClick&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;dispatch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ADD&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;payload&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
          Add
        &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;onClick&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;dispatch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;SUBTRACT&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;payload&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
          Subtract
        &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;button&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;export&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;default&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Counter&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;And with this, our component is complete. Copy this code and play around with it to understand things better.&lt;/p&gt;

&lt;h2&gt;
  
  
  Things to consider
&lt;/h2&gt;

&lt;p&gt;Here are some points to remember when working with the &lt;strong&gt;&lt;code&gt;useReducer&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; hook.&lt;/p&gt;

&lt;ol&gt;
&lt;li&gt;&lt;p&gt;Do not use them anywhere and everywhere. Use it only where the structure of the state is somewhat complex. Otherwise, you&#39;ll be writing unnecessarily lengthy codes. For simple states, stick to the useState&lpar;&rpar; hook.&lt;/p&gt;&lt;/li&gt;
&lt;li&gt;&lt;p&gt;Storing action types as constants is better than using literals. It helps in avoiding bugs due to typos.&lt;/p&gt;&lt;/li&gt;
&lt;li&gt;&lt;p&gt;Always return a new object from the reducer when updating the state. React makes a &lt;strong&gt;&lt;code&gt;shallow comparison&lt;/code&gt;&lt;/strong&gt; when comparing new and old states. Updating a particular field will not trigger re-renders.&lt;/p&gt;&lt;/li&gt;
&lt;/ol&gt;

&lt;h2&gt;
  
  
  That&#39;s all Folks
&lt;/h2&gt;

&lt;p&gt;That&#39;s a wrap for now, folks! I hope this article was insightful to you. I look forward to your insights and feedback. Let&#39;s keep this conversation going in the comments below!&lt;/p&gt;

&lt;p&gt;And hey, if you want to connect beyond these pages, these are the places where you can find me!&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://twitter.com/AnshumanMahato_&quot;&gt;Twitter&lt;/a&gt;    &lt;a href=&quot;https://www.linkedin.com/in/anshuman-mahato/&quot;&gt;LinkedIn&lt;/a&gt;    &lt;a href=&quot;https://github.com/AnshumanMahato&quot;&gt;GitHub&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;Until next time, stay curious and keep exploring!🌟 Thank You for reading this far. 😊&lt;/p&gt;

 

 - 💯[Mastering React Context: Simplifying State Management and Prop Drilling](https://dev.to/anshumanmahato/mastering-react-context-simplifying-state-management-and-prop-drilling-2k0f) 
 - &lt;p&gt;Many times, in react, state information is used by multiple components. Information in React is usually shared using props. We use it for this purpose as well. &lt;/p&gt;

&lt;p&gt;To resolve such situations, we define that data/function at a common parent component and then move it down using props. We call it &lt;strong&gt;lifting the state&lt;/strong&gt;.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Foh8lslonzfw5pktya98h.jpg&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Foh8lslonzfw5pktya98h.jpg&quot; alt=&quot;Independent states vs lift up&quot; width=&quot;800&quot; height=&quot;360&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;The &lt;strong&gt;Context API&lt;/strong&gt; is an alternative to this. A context defines a scope with some information. All the components placed in this scope can use that information directly. In my opinion, it is similar to namespaces in C++.&lt;/p&gt;

&lt;h2&gt;
  
  
  The Problem with Props
&lt;/h2&gt;

&lt;p&gt;Although passing props is a perfectly valid solution, it often creates an issue. There might be situations where the common parent is far from the actual component. So, we will need to move the data very deep down the UI tree and make it unnecessarily verbose. This issue is called &lt;strong&gt;&quot;Prop Drilling&quot;&lt;/strong&gt;.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F47d3k29bkbeea5q46ue0.jpg&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F47d3k29bkbeea5q46ue0.jpg&quot; alt=&quot;Prop Drilling&quot; width=&quot;800&quot; height=&quot;443&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;Let&#39;s take an example to understand this. Let&#39;s say we have a CRUD app related to Books. Following is the structure of this application.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fg4qeth0hhh6hrzeeev6l.jpg&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fg4qeth0hhh6hrzeeev6l.jpg&quot; alt=&quot;Books app using prop drilling&quot; width=&quot;800&quot; height=&quot;884&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;&lt;code&gt;&amp;lt;BookCreate /&amp;gt;&lt;/code&gt; - Creates entry for the book.&lt;br&gt;
&lt;code&gt;&amp;lt;BookList /&amp;gt;&lt;/code&gt; - Shows all the Books&lt;br&gt;
&lt;code&gt;&amp;lt;BookShow /&amp;gt;&lt;/code&gt; - Display component for each book.&lt;br&gt;
&lt;code&gt;&amp;lt;BookEdit /&amp;gt;&lt;/code&gt; - Component to editing book information.&lt;/p&gt;

&lt;p&gt;The &lt;strong&gt;&lt;code&gt;books&lt;/code&gt;&lt;/strong&gt; array is a state variable that contains all the books, and &lt;strong&gt;&lt;code&gt;createBook&lt;/code&gt;&lt;/strong&gt;, &lt;strong&gt;&lt;code&gt;editBook&lt;/code&gt;&lt;/strong&gt;, and &lt;strong&gt;&lt;code&gt;deleteBook&lt;/code&gt;&lt;/strong&gt; are functions that manipulate the state.&lt;/p&gt;

&lt;p&gt;As we can see, all the components use the &lt;strong&gt;&lt;code&gt;books&lt;/code&gt;&lt;/strong&gt; state. So, we declare in the App component. So are the functions that manipulate it.&lt;/p&gt;

&lt;p&gt;Now, these functions need to be moved way down the component tree. We will require a lot of props, resulting in prop drilling.&lt;/p&gt;

&lt;p&gt;We can avoid this issue using Contexts. Context lets a parent component provide data to the entire tree below it.&lt;/p&gt;
&lt;h2&gt;
  
  
  Implementing Context
&lt;/h2&gt;

&lt;p&gt;To implement a Context, you need to do the following three steps:&lt;/p&gt;

&lt;ol&gt;
&lt;li&gt;Creating a context&lt;/li&gt;
&lt;li&gt;Provide the context scope&lt;/li&gt;
&lt;li&gt;Use the Context&lt;/li&gt;
&lt;/ol&gt;
&lt;h3&gt;
  
  
  Creating a Context object
&lt;/h3&gt;

&lt;p&gt;We use the &lt;strong&gt;&lt;code&gt;createContext&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; method for this.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;createContext&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Context&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;createContext&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;defaultvalue&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;This method returns a &lt;strong&gt;&lt;code&gt;context&lt;/code&gt;&lt;/strong&gt; object. &lt;/p&gt;

&lt;h3&gt;
  
  
  Providing the Context
&lt;/h3&gt;

&lt;p&gt;Now, we create a scope using this &lt;strong&gt;&lt;code&gt;context&lt;/code&gt;&lt;/strong&gt; object. Here, we define the values to pass to the child components. The &lt;strong&gt;&lt;code&gt;context&lt;/code&gt;&lt;/strong&gt; object has a provider component for this purpose.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;valueToShare&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;children&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;This component has a &lt;strong&gt;&lt;code&gt;value&lt;/code&gt;&lt;/strong&gt; prop through which we associate values with the scope. The value of this prop becomes available to all the children components of the &lt;strong&gt;&lt;code&gt;Provider&lt;/code&gt;&lt;/strong&gt; component.&lt;/p&gt;

&lt;h3&gt;
  
  
  Using the &lt;code&gt;context&lt;/code&gt; object
&lt;/h3&gt;

&lt;p&gt;The children components extract these values using the &lt;strong&gt;&lt;code&gt;useContext&lpar;&rpar;&lt;/code&gt;&lt;/strong&gt; hook.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;useContext&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useContext&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;This hook takes the &lt;strong&gt;&lt;code&gt;context&lt;/code&gt;&lt;/strong&gt; object as an argument and returns the values that are associated with it. &lt;/p&gt;

&lt;p&gt;Here&#39;s an example with a simple implementation using contexts.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;c1&quot;&gt;//Context.jsx&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createContext&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Context&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;createContext&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;1&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;export&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;default&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;





&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;c1&quot;&gt;//Container.jsx&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;React&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;useContext&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Context&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;./Context&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;Container&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;useContext&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
  &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;export&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;default&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Container&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;





&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;c1&quot;&gt;//App.jsx&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;React&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Context&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;./Context&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;./Container&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;App&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;k&quot;&gt;return &lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;5&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;export&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;default&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;App&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;&lt;a href=&quot;https://codesandbox.io/s/context-example-fu8ndo?fontsize=14&amp;amp;hidenavigation=1&amp;amp;module=%2Fsrc%2Fcomponents%2FApp.jsx,%2Fsrc%2Fcomponents%2FContainer.jsx,%2Fsrc%2Fcomponents%2FContext.jsx&amp;amp;theme=dark&amp;amp;moduleview=1&amp;amp;view=split&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--1rJFNpIB--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://codesandbox.io/static/img/play-codesandbox.svg&quot; alt=&quot;Edit context-example&quot; width=&quot;201&quot; height=&quot;42&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;This way, information is shared between components without using any prop for passing data.&lt;/p&gt;

&lt;h2&gt;
  
  
  Some Extra bits on contexts
&lt;/h2&gt;

&lt;ul&gt;
&lt;li&gt;We can create multiple scopes using the same context object. We can provide each of them with different context values that the components within them can access. Replace the App code with the following code in the above example to see it live.
&lt;/li&gt;
&lt;/ul&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;   &lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;App&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
     &lt;span class=&quot;k&quot;&gt;return &lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
       &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
         &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;3&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
           &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
         &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
         &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;7&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
           &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
         &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
       &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
     &lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
   &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;ul&gt;
&lt;li&gt; We can also define a scope within another scope of the same context object, and both will provide different values to their child components. Here, a child can access all the data values belonging to the nearest parent Provider. Replace the App code with the following code in the above example to see it live.
&lt;/li&gt;
&lt;/ul&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;App&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;k&quot;&gt;return &lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;3&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;7&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
          &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;ul&gt;
&lt;li&gt;If a non-child component tries to use it, it gets the default value passed during the &lt;strong&gt;&lt;code&gt;createContext&lpar;defaultValue&rpar;&lt;/code&gt;&lt;/strong&gt; call. In such a situation, React searches for a parent provider for it. But as it does not find one, it returns the default value as a fallback. Replace the App code with the following code in the above example to see it live.
&lt;/li&gt;
&lt;/ul&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight jsx&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;App&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;k&quot;&gt;return &lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;3&lt;/span&gt;&lt;span class=&quot;si&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Context&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Provider&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;Container&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;/&amp;gt;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;&amp;lt;/&lt;/span&gt;&lt;span class=&quot;nt&quot;&gt;div&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&amp;gt;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;h2&gt;
  
  
  Practical Use Case
&lt;/h2&gt;

&lt;p&gt;The most common use of contexts is &lt;strong&gt;State Management&lt;/strong&gt;. Prop drilling often happens due to the sharing of state information between components. What would be better is to create a context for the state and put the component tree associated with that state within that.&lt;/p&gt;

&lt;p&gt;Let&#39;s see our book example again. We declared the &lt;strong&gt;&lt;code&gt;books&lt;/code&gt;&lt;/strong&gt; state and associated methods in the &lt;strong&gt;&lt;code&gt;App&lt;/code&gt;&lt;/strong&gt; component. We then moved them to the actual location via props.&lt;/p&gt;

&lt;p&gt;Alternatively, we can define the &lt;strong&gt;&lt;code&gt;books&lt;/code&gt;&lt;/strong&gt; state and the methods in a context and provide it to the App component. This way, the App and all its children components have access to the &lt;strong&gt;&lt;code&gt;books&lt;/code&gt;&lt;/strong&gt; state directly.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fhyg0ilmf2tt6vbobsljd.jpg&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fhyg0ilmf2tt6vbobsljd.jpg&quot; alt=&quot;Books app using context&quot; width=&quot;800&quot; height=&quot;872&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;Here&#39;s the code for it&lt;/p&gt;

&lt;p&gt;&lt;iframe src=&quot;https://codesandbox.io/embed/bs3rzk&quot;&gt;
&lt;/iframe&gt;
&lt;/p&gt;

&lt;h2&gt;
  
  
  Some Consideration
&lt;/h2&gt;

&lt;p&gt;Contexts are great tools for passing data deeply in a UI tree without tending to prop drilling. They are simple to implement, making it very tempting to use them. Thus, we may end up overusing them. To avoid this, we must understand the association between the information and the components using it.&lt;/p&gt;

&lt;ul&gt;
&lt;li&gt;&lt;p&gt;If the information is associated with components which are related and mutually dependent on one another, it might be better to use the prop system as it would make the data flow explicit between them. For example, let&#39;s say we have a Form component with multiple form controls. Different form controls may depend upon the states of one another and thus require the sharing of information. Here, using props would be better as it would depict how data flows within the Form component.&lt;/p&gt;&lt;/li&gt;
&lt;li&gt;&lt;p&gt;On the flip side, if the information is associated with mutually independent components, it is better to use contexts. An example of this could be login information. We can use this in the navbar to show the username. We can use this on the profile page to display user details. We can use it application-wide, irrespective of the relationship between the components.&lt;/p&gt;&lt;/li&gt;
&lt;/ul&gt;

&lt;h2&gt;
  
  
  That&#39;s all folks
&lt;/h2&gt;

&lt;p&gt;Contexts are great for sharing information when it needs to be moved deeply in a component tree. It is simple to implement and helps in clubbing data in one place.&lt;/p&gt;

&lt;p&gt;This article is my understanding of the context API. You may give your insights in the comments. I would appreciate your feedback.&lt;/p&gt;

&lt;p&gt;And hey, if you want to connect beyond these pages, catch me on Twitter! My handle is &lt;a href=&quot;https://twitter.com/AnshumanMahato_&quot;&gt;@AnshumanMahato_&lt;/a&gt;. &lt;/p&gt;

&lt;p&gt;With this, I would like to conclude this post. Until next time, stay curious and keep exploring! 🌟Thank You for reading this far. 😊&lt;/p&gt;

 
<!-- BLOG-POST-LIST:END -->
 
# 📊 GitHub Stats:

<div align="center">
<!-- 	<img src="https://github-readme-stats.vercel.app/api?username=AnshumanMahato&theme=react&hide_border=false&include_all_commits=false&count_private=false"><br/> -->
	<img src="https://github-readme-streak-stats.herokuapp.com/?user=AnshumanMahato&theme=react&hide_border=false"><br/>
<!-- 	test <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=AnshumanMahato&theme=react&hide_border=false&include_all_commits=false&count_private=false&layout=compact"> -->
</div>
	


## 🏆 GitHub Trophies
 
![](https://github-profile-trophy.vercel.app/?username=AnshumanMahato&theme=nord&no-frame=true&margin-w=4&title=Stars,Followers,Commits,Issues,Repositories,PR)

## ✍️ Random Dev Quote
 
![](https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight)
 
<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
</div>
