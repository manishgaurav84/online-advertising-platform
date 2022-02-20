### The following tasks has been accomplised in this project:

- The platform will have an interface for campaign managers to run the Ad campaign and another interface for the 
client to present the Ads and send the user action back to the advertising platform.
- Through the campaign manager, the Ad instructions (New Ad Campaign, Stopping the existing Ad campaign) will be 
published to a Kafka Queue. The ‘Ad Manager’ will read the message from that Kafka queue and update the MySQL 
store accordingly.
- An Ad Server will hold the auction of Ads for displaying the Ad to a user device. The auction winner will pay the
amount bid by the second Ad. A user simulator will hit the Ad Server API for displaying Ads and send the user
interaction feedback back to the feedback handler through API.
- Upon receiving the user interaction feedback, the feedback handler will publish that event to another Kafka queue.
- The User feedback handler will collect the feedback through the feedback API and it will be responsible for 
updating the leftover budget for the Ad campaign into MySQL. It will also publish the feedback to the internal 
Kafka queue, which will be later published to HIVE through user feedback writer for billing and archiving.
- The whole system needs to be run for an hour and after that, the report generator will generate the bill report
for all Ads displayed so far.
