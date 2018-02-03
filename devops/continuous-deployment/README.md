
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


