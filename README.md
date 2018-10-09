# FruityDC
## Dynamic Callbacks

Maintaining persistence and communication between C2 infrastructure and compromised hosts is a fundamental element for successful red team campaigns. This is well understood by defenders, and so effort and time is invested by SOCs in improving their detection and blocking capabilities to reduce the time that persistence and communication can be maintained. But what if the communication and persistence can be re-established dynamically after it is blocked?

Dynamic Callbacks can be used for re-establishing communication with C2 infrastructure and for achieving persistence by using different methods incorporating communication with popular websites, domain fronting and multiple protocols.

<img src="https://i.imgur.com/0Km6j9U.png" width="720">


The following is an example of how Dynamic Callbacks can be used during post-exploitation phase abusing emails as a trigger.

<img src="https://i.imgur.com/8ORnsqd.png" width="720">

## Demo: Dynamic Callbacks Implementation - Email 1/2

- A new folder is created (inbox/_MOVE).
- A new rule is created on Outlook. (HideMe).
- Send 1, sets the email with HASH on method GSearch.
- An email is sent to the target.
- Subject matches the rule and the email is moved to _MOVE.
- Dynamic Callback methods are triggered.
- Payload is patched with Dynamic Callback.
- C2 communication is established (FruityDC simulation).

<br>
<a href="https://youtu.be/H6GnUTDJWCg" target="_blank"><img src="https://i.imgur.com/EavEWoC.png" width="640"></a>
<br>



## Demo: Dynamic Callbacks Implementation - Email 2/2

- The folder _MOVE is hidden.
- Send 3, sets the email with HASH on method Youtube.
- An email is sent to the target.
- Subject matches the rule and the email is moved to _MOVE.
- Dynamic Callback methods are triggered.
- Payload is patched with Dynamic Callback.
- C2 communication is established (FruityDC simulation).

<br>
<a href="https://youtu.be/bhpi42Oywr4" target="_blank"><img src="https://i.imgur.com/g3JvMDP.png" width="640"></a>
<br>

