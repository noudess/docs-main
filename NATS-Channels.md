Note that NATS is currently on an experimental branch

IN and OUT are from the perspective of a eqemu. So, if IN is yes, that means it is expected that a third party client will request messages to this channel, If OUT is yes, that means you can subscribe as a third party and get a feed of data.

### Global Scoped
* **global.admin_message.out** - eqproto::AdminMessage - Admin related communication. This is called from both zone and world, and may contain sensitive information, designed to be sent to an administrator-only channel. (hacker, zone bootup, new account creations, etc)

### World Scoped
* **world.command_message.in** - eqproto::CommandMessage - Send a command. Commands are as follows:
* who - Who is currently online

### Zone Scoped
zone.ecommons.channel_message|Yes|No|ChannelMessage|Send a channel message to ecommons
zone.ecommons.command_message|Yes|No|ChannelMessage|Send a channel message to ecommons
zone.ecommons.entity.event_subscribe.all|Yes|No|EntityEvent|Request a reply of triggering to get events for all entities in zone. Send ID > 0 to turn on, and 0 to turn off. Note: This is costly, and should be avoided, it will turn off when the zone goes to sleep or you disable
zone.ecommons.entity.event_subscribe.entity|Yes|No|EntityEvent|Request a reply to get publishings for entity 101 until entity dies
zone.ecommons.entity.event.#|No|Yes|EntityEvent|Subscribe to events from entity #
zone.ecommons.entity.list|Yes|No|Entities|Request reply of a list of all entities
zone.ecommons.channel_message|Yes|No|ChannelMessage|Send a channel message to all provided zone