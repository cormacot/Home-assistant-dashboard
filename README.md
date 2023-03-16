# Home-assistant-dashboard
you can add an automation to Home Assistant that runs the Morning Commute script between 5am and 10am on weekdays. Here's an example of how you can set up the automation:

yaml
Copy code
automation:
  - alias: "Morning Commute"
    trigger:
      platform: time
      at: "05:00:00"
    condition:
      condition: and
      conditions:
        - condition: time
          weekday:
            - mon
            - tue
            - wed
            - thu
            - fri
        - condition: time
          after: "05:00:00"
          before: "10:00:00"
    action:
      service: script.morning_commute
In this example, the automation triggers at 5am and checks if it is a weekday and if the current time is between 5am and 10am. If these conditions are met, it runs the Morning Commute script.

You can also add an entity card to the Home Assistant UI that displays the morning commute options. Here's an example of how you can set up the entity card:

yaml
Copy code
type: entities
entities:
  - entity: script.morning_commute
title: Morning Commute Options
This will display the morning commute options in the Home Assistant UI, without requiring you to press a button to initiate the script.
