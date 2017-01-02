App Dev Cloud with JBoss Travel Agency Demo
===========================================
This demo is to install JBoss BPM Travel Agency Demo in the Cloud based on leveraging the OpenShift Container Platform (OCP)
It delivers a fully functioning JBoss BPM Travel Agency example containerized on OCP.

This is an online employee travel booking process project. It contains multiple web services for looking up data for the process
and rules to calculate pricing. Furthermore, there are several tasks that can be activated to evaluate pricing and to review the
final booking data before completing the booking.


Install JBoss Travel Agency on OpenShift
----------------------------------------
1. First ensure you have an OpenShift container based installation, such as one of the followling installed first:

  - [OCP Install Demo](https://github.com/redhatdemocentral/ocp-install-demo)

  - [CDK Install Demo](https://github.com/redhatdemocentral/cdk-install-demo)

  - or your own OpenShift installation.

2. [Download and unzip this demo.](https://github.com/redhatdemocentral/rhcs-travel-agency-demo/archive/master.zip)

3. Add products to installs directory.

4. Run 'init.sh' or 'init.bat' file. 'init.bat' must be run with Administrative privileges:
```
   # The installation needs to be pointed to a running version
   # of OpenShift, so pass an IP address such as:
   #
   $ ./init.sh 192.168.99.100  # example for OCP.

   $ ./init.sh 10.1.2.2        # example for CDK.
```

Log in to JBoss Travel Agency to start exploring an online bookings application (the address will be generated by the init script):

  - OCP example: [http://rhcs-travel-agency-demo.192.168.99.100.xip.io/business-central](http://rhcs-travel-agency-demo.192.168.99.100.xip.io/business-central)  ( u:erics / p:bpmsuite1! )

  - OCP example web app: [http://rhcs-travel-agency-demo.192.168.99.100.xip.io/external-client-ui-form-1.0](http://rhcs-travel-agency-demo.192.168.99.100.xip.io/external-client-ui-form-1.0)

  - CDK example: [http://rhcs-travel-agency-demo.10.1.2.2.xip.io/business-central](http://rhcs-travel-agency-demo.10.1.2.2.xip.io/business-central)  ( u:erics / p:bpmsuite1! )

  - CDK example web app: [http://rhcs-travel-agency-demo.10.1.2.2.xip.io/external-client-ui-form-1.0](http://rhcs-travel-agency-demo.10.1.2.2.xip.io/external-client-ui-form-1.0)


Note before running demo:
-------------------------
This project can be installed on any OpenShift platform, such as OpenShift Container Platform or Red Hat Container Development Kit.
It's possible to install it on any available installation by pointing this installer to an OpenShift IP address:
```
  $ ./init.sh IP
```

If for any reason the installation breaks or you want a new installation, just remove the project rhcs-brms-install-demo
entry in the OpenShift console and re-run the installation.

Should your local network DNS not handle the resolution of the above address, giving you page not found errors, you can apply the
following to your local hosts file:

```
$ sudo vi /etc/hosts

# add host for OCP demo resulution
192.168.99.100   rhcs-travel-agency-demo.192.168.99.100.xip.io 

# add host for CDK demo resolution.
10.1.2.2   rhcs-travel-agency-demo.10.1.2.2.xip.io 
```

Booking a trip to Edinburgh (just one scenario)
-----------------------------------------------
1. Build & deploy project.

2. Start process with following data in start form (either from JBoss BPM Suite dashboard or using external client UI):

  ```
  Name: [your-name]

  Email Adress: [any-email]

  Number of Travellers: 2  

  From Destination: London

  To Destination: Edinburgh

  Preferred Date of Departure: 2014-12-20

  Preferred Data of Arrival: 2014-12-29

  Other Details / Notes: [any-text]
  ```

3. Login to Business Central.

  ```
  - login for admin role (u:erics / p:bpmsuite1!)
  ```

4. Two web services will be run and a sub-process to calculate the cost before deciding it is not needed that this booking be
	 reviewed on pricing, so you will find a task 'Employee Booking' for you to process.

5. Navigate to the "Tasks" tab -> "Task List" and click on it. 

6. Expand the right-side pane window.   Click on the "Work" tab and click on "claim" to claim the task.

7. Fill in the form provided for the task, it allows review of all the booking data submitted, generated by services and 
   calculated by the rules. You can request a review to send it back for a pricing review or check the completed box to 
   finish the task and process (isBookingConfirmed). All tasks have automated reassignment, meaning if not completed within 1 minute
   they will be put back into the group.

8. Enter credit card details (beginning with 1234...) for compensation to be triggered., Expiry details of the 
   card (e.g. 12/12) and your full name.

9. Check the logs and you will see that the process has been compensated.

10. To trigger different path for successful booking of Flights, just change the 'Credit Card details' to use any 
    card number that does not begin with 1234....

11. For details on demoing the compensation aspects of the Travel Agency demo project, 
    see [docs/compensation-howto/README-COMPENSATION.md](docs/compensation-howto/README-COMPENSATION.md)


Supporting Articles
-------------------
- [How to help the travel industry take bookings into the Cloud](http://www.schabell.org/2016/04/how-to-help-travel-industry-take-bookings-into-cloud.html)

- [A Micro Services Migration Story with JBoss BPM Travel Agency](http://www.schabell.org/2015/05/micro-services-migration-story-with-jboss-bpm-travel-agency.html)

- [How to fly with the JBoss BPM Travel Agency (video 4 of 4)](http://www.schabell.org/2015/02/how-to-fly-with-jboss-bpm-travel-agency-part4.html)

- [How to fly with the JBoss BPM Travel Agency (video 3 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency-part3.html)

- [How to fly with the JBoss BPM Travel Agency (video 2 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency-part2.html)

- [How to fly with the JBoss BPM Travel Agency (video 1 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency.html)

- [How To Excite the Travel Industry With a BPM Story](http://www.schabell.org/2014/10/how-to-excite-travel-agencies-with-bpm-story.html)


Released versions
-----------------
See the tagged releases for the following versions of the product:

- v1.4 - JBoss BPM Suite 6.4.0 and JBoss EAP 7.0.0 with travel agency installed on any given OpenShift installation.

- v1.3 - JBoss BPM Suite 6.3.0 and JBoss EAP 6.4.7 with travel agency process installed on Red Hat CDK.

- v1.2 - JBoss BPM Suite 6.2.0-BZ-1299002 on JBoss EAP 6.4.4 with travel agency process installed on Red Hat CDK.

- v1.1 - JBoss BPM Suite 6.2.0-BZ-1299002 on JBoss EAP 6.4.4 with travel agency process updates installed on Red Hat CDK using OpenShift Enterprise image. 

- v1.0 - JBoss BPM Suite 6.2.0-BZ-1299002 on JBoss EAP 6.4.4 with travel agency installed on Red Hat CDK using OpenShift Enterprise image. 


[![Install video](https://github.com/redhatdemocentral/rhcs-travel-agency-demo/blob/master/docs/demo-images/rhcs-travel-agency-video.png?raw=true)](https://vimeo.com/ericschabell/rhcs-travel-agency-demo)

![OSE Pod](https://github.com/redhatdemocentral/rhcs-travel-agency-demo/blob/master/docs/demo-images/rhcs-travel-agency-pod.png?raw=true)

![OSE Build](https://github.com/redhatdemocentral/rhcs-travel-agency-demo/blob/master/docs/demo-images/rhcs-travel-agency-build.png?raw=true)

![Agency Process](https://github.com/redhatdemocentral/rhcs-travel-agency-demo/blob/master/docs/demo-images/agency-process.png?raw=true)

![Calculate Process](https://github.com/redhatdemocentral/rhcs-travel-agency-demo/blob/master/docs/demo-images/calculate-process.png?raw=true)

![Compensation](https://raw.githubusercontent.com/redhatdemocentral/rhcs-travel-agency-demo/master/docs/demo-images/compensation-process.png?raw=true)

![Special Trips UI Form](https://raw.githubusercontent.com/redhatdemocentral/rhcs-travel-agency-demo/master/docs/demo-images/SpecialTripsUIform.png)

![Started Process](https://raw.githubusercontent.com/redhatdemocentral/rhcs-travel-agency-demo/master/docs/demo-images/started-process.png)

