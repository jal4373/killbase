Killbase is a job board for international assassins. Assassins and their clients can register with Killbase, and enter or sign up for jobs. Assassins can have one or more code names, and can sign up for any number of contracts; a contract may also be open to any number of assassins.

Assassins have:
  * a full fame
  * one or more codenames
  * a weapon of choice
  * contact information
  * a minimum price they charge
  * a float rating from 1-10
  * number of kills
  * an age

Contracts have:
  * a target
  * a client
  * a budget (maximum price for the job)
  * whether it's completed or not
  * who completed it, if completed

Clients have:
  * a name

Targets have:
  * a name
  * a location
  * a photo
  * a security level

```
     +------------------------------------+
     |            ASSASSINS               |
     +----------+-------------------------+         +---------------------------------+
     | id       | serial primary key      |         |              CODENAMES          |
     | fullname | text                    |        /+------------+--------------------+
     | codename | foreign key (codenames) +---------+ assassinid | serial primary key |
    /| weapon   | text                    |        \| codename   | text               |
+----+ contact  | text                    |         +------------+--------------------+
|   \| price    | integer                 |
|    | rating   | float                   |
|    | kills    | integer                 |
|    | age      | integer                 |         +---------------------------+
|    +----------+-------------------------+         |        CLIENTS            |
|                                                   +------+--------------------+
|                                                   | id   | serial primary key +----------------+
|                                                   | name | text               |                |
|        +-------------------------------+          +------+--------------------+                |
|        |            TARGETS            |                                                       |
|        +----------+--------------------+                                                       |
|        | id       | serial primary key +----+     +---------------------------------------+    |
|        | name     | text               |    |     |               CONTRACTS               |    |
|        | location | text               |    |     +-------------+-------------------------+    |
|        | photo    | text               |    |     | id          | serial primary key      |    |
|        | seclevel | integer            |    +-----+ targetid    | foreign key (targets)   |\   |
|        +----------+--------------------+          | clientid    | foreign key (clients)   +----+
|                                                   | budget      | integer                 |/
|                                                  /| completed   | boolean                 |
+---------------------------------------------------+ completedby | foreign key (assassins) |
                                                   \+-------------+-------------------------+
```                                                   