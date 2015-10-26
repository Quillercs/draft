# QuillerCS - Architecture (DRAFT 1)

Quiller can be divided in three main pieces, they are:

 * The Core
 * Event Machine
 * Apps

## The Core

The core is responsible for the low level communication with the supported telecom platforms, also
is responsible for the middlewares and the models. The middleware architecture allows to
communicate with different telecom plataforms (like FreeSWITCH and Asterisk), the models are
how the core abstract the data that are common in many plataforms.

The core is exposed by HTTP, so any user with rights can access the core and manage the platform,
configure and use all apps and commands available.

Also the core can be used as important library for programming the components around, like:
the Event Machine and the Apps.

## Event Machine

Event Machine have an essenstial role, besides being able to generate network events, the event machine
will interface the communication with telecom platforms (only FreeSWITCH for now) and dispatch many
necessary events.

All components around can connect and being able to listen all events which judges necessary, his utility
go beyond generate events, the event machine will translate any events, acting like a translator
for QuillerCS events and the events from the telecom plataform.

## Apps

Apps have a very important role too, they are the workers of the system, given the functionality and adding new
features to the platform.

Apps can for example: generate calls, listen for events, generate events, create files, listen for logs,
listen streamings, connect to external services and so on.

All app must follow the rules from the basic app structure or extend the basic app structure lives inside
the core, any app can be developed using those basic structures.