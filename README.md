# CST8915 Lab 1: Algonquin Pet Store on Azure VM

**Student Name**: Connor Dickson
**Student ID**: 041085826
**Course**: CST8915 Full-stack Cloud-native Development
**Semester**: Fall 2026

---

## Demo Video

🎥 [Watch Demo Video](https://youtu.be/yIqqHanPglw)

---

## Technical Explanations

### Order Service (Node.js)

The purpose of the Order service is to listen for requests for a pet food order are sent from the front end of the application. The service then adds the order to a que service on the back end. This servies makes use of Expressjs which is the framework used to build the service and make it function accordingly, and is built on top of Javascript which handles web functionality. The service also uses AMQP or Advanced Message Queueing Protocol, which is a library that facilitates communication with the RabbitMQ queueing service. Finally it also utilizes CORS middleware for the handling of cross-origin requests.
The role of this services within the architecture is to handle all orders requested on the client side of the application, by recieving JSON data from the Vue.js front end whenever a request is sent to create an order, and passing it to the RabbitMQ service to create a place in the current order queue for processing. This is necessary to isolate the queue service from the front end. 

### Product Service (Rust)

The product service written in Rust has the job of sending all stored product information to the client to allow it to be displayed on the front end service of the application. The Product service is built on Rust, a lower level language that was likely chosen as it is fast and predicatble. Warp web framework was the chosen framework to add HTTP handling functionality to the service. And the tokio runtime was integrated to allow the rust application to execute asynchronously. The role of the product service at the moment seems to be to listen for any incoming GET requests and serve a small json array of product objects. The GET requests will be sent from the Vue.js front end.

### Store Front (Vue.js)

The Store front service is the Vue.js powered front end service of the application that allows end users to interact with the web applications functions. The framework used in the creation of the service is Vue.js, which expands the functional interactability of javascript within html application, likely making adding functionality to the page elements easier. The role of this service is to add a interactive user interface so the end user does not have to interact directly with the backend services of the application. It makeshttp requests to the Product service to have the stored product information sent for display, and to the order service to create orders and have them added to an order queue.   

---

## Challenges and Learnings (Optional)

The main challenge I faced while doing the lab was getting the RabbitMQ dashboard to display in my browser. The webpage would simply throw a 404 error and not display, or be left infinitely loading. Sadly I did not find a way to fix this. 

---

## Acknowledgments

*What is vue.js*. (n.d.). W3Schools. https://www.w3schools.com/whatis/whatis_vue.asp

*Tutorial*. (n.d.). Tokio. https://tokio.rs/tokio/tutorial

Galleta, C., & Arundel, J. (2026, June 19). *What’s so great about rust?* Bitfield Consulting. https://bitfieldconsulting.com/posts/why-rust

Dsouza, M. (2018, August 6). *Warp: Rust’s new web framework*. packetpub.com. https://www.packtpub.com/en-ca/learning/tech-news/warp-rusts-new-web-framework 
