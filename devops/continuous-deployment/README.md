
# devops - continuous deployment


## principles
* keep producing valuable software in short cycles and ensure that the software can be reliably released at any time
* automate and improve the process of software delivery


* techniques such as automated testing and continuous integration (CI) allow software to be developed to a high standard and easily packaged and deployed to test environments, resulting in the ability to rapidly, reliably and repeatedly push out enhancements and bug fixes to customers at low risk and with minimal manual overhead.
* continuous deployment (CD) builds on CI by adding regular deployments to production as part of the process, however CD is not a requirement of CI


## process diagram
![continuous deployment process diagram](continuous-delivery-process-diagram.png "continuous deployment process diagram")


* developers used to a long cycle time may need to change their mindset when working in a CD environment. 
* it is important to understand that any code commit may be released to customers at any point. 
Patterns such as feature toggles can be very useful for committing code early which is not yet ready for use by end users.

"the job of a continous delivery pipeline is to kill a release candidate. you cannot prove that software is good. you can absolutely prove that it is bad. so the job of a continous delivery pipeline is to prove that it is not good enough."


## links

* [Continuous Delivery In Agile | Jez Humble](https://vimeo.com/229954108)
* [How to move from CI to CD with Jenkins](https://jaxenter.com/how-to-move-from-ci-to-cd-with-jenkins-workflow-128135.html)
* [Continuous Delivery with Docker and Kubernetes](https://youtu.be/xAziflV3ah4)
* [Acceptance Testing for Continuous Delivery | Dave Farley](https://youtu.be/SBhgteA2szg)
* [Why You Need a Software Delivery Machine | Rod Johnson | GOTO 2018](https://youtu.be/obDhNejPM9M)
* [Architecting for Continuous Delivery | Jez Humble | DOES15](https://youtu.be/_wnd-eyPoMo)

