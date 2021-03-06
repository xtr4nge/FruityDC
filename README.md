# FruityDC
FruityDC project and Dynamic Callbacks methods will be released soon! 
<br>
As part of the initial release, Dynamic Callbacks will be implemented on <a href="https://github.com/xtr4nge/FruityC2" target="_blank">FruityC2</a> ps-stager and ps-agent.


## Dynamic Callbacks

Maintaining persistence and communication between C2 infrastructure and compromised hosts is a fundamental element for successful red team campaigns. This is well understood by defenders, and so effort and time is invested by SOCs in improving their detection and blocking capabilities to reduce the time that persistence and communication can be maintained. But what if the communication and persistence can be re-established dynamically after it is blocked?

Dynamic Callbacks can be used for re-establishing communication with C2 infrastructure and for achieving persistence by using different methods incorporating communication with popular websites, domain fronting and multiple protocols.

<img src="https://i.imgur.com/0Km6j9U.png?1" width="720">

## Basic Flow

The idea is simple, store the content on a website that will be potentially reachable through the corporate proxy, such as Google, Youtube, Google Maps, or any other. For obtaining the content, we can use the following flow as an example:

<img src="https://i.imgur.com/rtLEcsQ.png" width="720">

- A request is made from the compromised machine, searching for a HASH
- The DC method (Hash+Site) returns the content (page source code)
- The content is parsed (and decoded and/or decrypted)
- The payload is patched with the new destination (ip/domain)
- C2 communication is established with the new address
- The initial HASH is replaced with the new HASH
- The next search will used the new HASH

<br>
<b>Note:</b> This is the basic concept, and it can be implemented by many different ways.
<br><br>

## Methods

The Methods are the places were the Dynamic Callbacks can be stored for the payloads to obtain them. The idea is to use common sites, that usually are are not blocked. There are some Methods that can be manipulated using API, therefore, the content can be changed from FruityDC directly.

<img src="https://i.imgur.com/8QMFvig.png" width="720">

<br>

<table>
  <tr>
    <td>Method</td>
    <td>API</td>
    <td>API_DC</td>
  </tr>
  <tr>
    <td>Youtube</td>
    <td>*</td>
    <td>*</td>
  </tr>
  <tr>
    <td>Google Sites</td>
    <td>*</td>
    <td></td>
  </tr>
  <tr>
    <td>Google Drive</td>
    <td>*</td>
    <td>*</td>
  </tr>
  <tr>
    <td>Google Maps</td>
    <td>*</td>
    <td>*</td>
  </tr>
  <tr>
    <td>Google Search</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Github</td>
    <td>*</td>
    <td>*</td>
  </tr>
  <tr>
    <td>DF Google</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DF Amazon</td>
    <td>*</td>
    <td></td>
  </tr>
  <tr>
    <td>TXT</td>
    <td>*</td>
    <td>*</td>
  </tr>
</table>

<br>

## Dynamic Callbacks: Emails

The following is an example of how Dynamic Callbacks can be used during post-exploitation phase, abusing emails as a trigger.

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

