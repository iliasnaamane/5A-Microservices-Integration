# SOA, Microservices & Integration

  * Author: Sébastien Mosser [(email)](mosser@i3s.unice.fr)
  * Version: 2017.08 
  * Reviewer: [Mireille Blay-Fornarino](blay@i3s.unice.fr)

## Technological Stack

  * Service Development: 
    * Application server: [TomEE+](http://openejb.apache.org/apache-tomee.html)
    * REST-based service stack: JAX-RS
    * SOAP-based service stack: JAX-WS
  * Integration: 
    * Enterprise Service Bus: [Apache Service Mix](http://servicemix.apache.org/) (7.0.1)
    * Message Broker: [Apache ActiveMQ](http://activemq.apache.org/)
    * Routing: [Apache Camel](http://camel.apache.org/) (2.19.2)
  * Storage: 
    * Database: [MongoDB](https://www.mongodb.com) (3.4)
    * Java Mapping: [Jongo](http://jongo.org/)
  * Deployment: 
    * [Docker Community Engine](https://www.docker.com/community-edition) (17.07.0-rc1)
    * [Docker Compose](https://docs.docker.com/compose/) (1.15.0)
  * Testing:
    * Acceptance testing: [Cucumber](https://cucumber.io/) 
    * Stress testing: [Gatling](http://gatling.io/)
  * Monitoring:
    * ESB: [HawtIO](http://hawt.io/)
    * Services: [cAdvisor](https://github.com/google/cadvisor)  
  * Continuous Integration: [Travis](https://travis-ci.org/)  

## Case study: The Tax Computation Service

We consider here a simple case study, the _Tax Computation Service_. The key idea is simple: creating a service-based architecture to support the computation of income taxes for a relatively small country (_i.e._, Norway, 5 millions inhabitants).

### Personas & Stories

  * _Thor_ is a simple tax payer, working as a software engineer in Oslo, the biggest city of the country; As Thor ...
    * I want to receive an email containing my tax return form when my taxes were processed, so that I can know the amount of taxes I paid this year;
    * I want to submit my cousin's name to the system, so that I can see how many taxes he is paying this year.
  * _Anders_ is Thor's cousin. He works as a farmer living in Fredvang, a small village located inside the Lofoten archipelago; As Anders, ...
    * I want my taxes to be handled as a farmer so that I can benefit from the special tax computation associated to this status;
    * I want to receive my tax return form by snail mail, so that I can read it without using a computer;
    * I want to receive a text message  indicating that my tax return was processed. 
  * _Eva_ is working at Skatteetaten, the Norwegian Tax Administration. She is supervising the tax payment process at the kingdom level; As Eva, ...
    * I want to respect the Norwegian law, stating that all processing must be done in an anonymous way; 
    * I want to know how many tax return forms were processed .
  * _Camilla_ is an IT engineer, also working at Skatteetaten. She is ensuring that the computation load will not kill the tax collection process. As Camilla, ...
    * I want to supervise the operational system to monitor how the tax processing is going.

## Development Timeline

### Phase #1: Deploying services

  1. Service development
    * Creating the Tax Computation System as an RPC service;
    * Creating the Anonymous Generator as a Resource service;
    * Creating the Snail Mail processor as a Document service.
  2. Service deployment
    * Using containers to deploy services;
    * Composing containers into a global system.
    * Monitoring containers
  3. Service testing
    * Acceptance testing using scenarios
    * Stress testing

### Phase #2: Integrating services

  1. Message broker
    * Using asynchronous messages to assemble services;
    * Monitoring the broker 
  2. Legacy integration
    * Leveraging adapters to integrate legacy systems together

