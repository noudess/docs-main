Note that NATS is currently on an experimental branch

PUB and SUB are from the perspective of a third party client. So, if PUB is yes, that means it is expected that a third party client will publish messages to this channel, and it is the emulator's responsibility to subscribe to the message (and reply if the channel is designed this way).

### Global Scoped
* **global.admin_message.out** - eqproto::AdminMessage - Admin related communication. This is called from both zone and world, and may contain sensitive information, designed to be sent to an administrator-only channel. (hacker, zone bootup, new account creations, etc)

### World Scoped
* **world.command_message.in** - eqproto::CommandMessage - Send a command. Commands are as follows:
* who - Who is currently online

### Zone Scoped

**Channel**|**IN**|**OUT**|**Proto**|**Description**
:---|:---|:---|:---|:-----
world.command_message|Yes|No|CommandMessage|Request a reply of executing a command message
world.channel_message|Yes|Yes|ChannelMessage|Send a channel message to world, which will then relay to all zones
zone.admin_message|Yes|No|AdminMessage|Request reply of executing an admin message
zone.channel_message|Yes|No|ChannelMessage|Send a channel message to all zones. NOTE: it is recommended to use world.channel_message instead.
zone.ecommons.channel_message|Yes|No|ChannelMessage|Send a channel message to ecommons
zone.ecommons.command_message|Yes|No|ChannelMessage|Send a channel message to ecommons
zone.ecommons.entity.event_subscribe.all|Yes|No|EntityEvent|Request a reply of triggering to get events for all entities in zone. Send ID > 0 to turn on, and 0 to turn off. Note: This is costly, and should be avoided, it will turn off when the zone goes to sleep or you disable
zone.ecommons.entity.event_subscribe.entity|Yes|No|EntityEvent|Request a reply to get publishings for entity 101 until entity dies
zone.ecommons.entity.event.#|No|Yes|EntityEvent|Subscribe to events from entity #
zone.ecommons.entity.list|Yes|No|Entities|Request reply of a list of all entities in a zone