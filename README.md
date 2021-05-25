<img src="img/robopeer.png" height="100" alt="robopeer logo" />

<!-- Works with

<a href='https://github.com/local-first-web/relay'>
<img src="https://raw.githubusercontent.com/local-first-web/branding/main/svg/relay-h.svg" height="50" alt="@localfirst/relay logo" />
</a>
&nbsp;&nbsp;

and

<a href='https://github.com/automerge/automerge'>
<img src="https://github.com/automerge/automerge/raw/main/img/sign.svg" height="50" alt="automergelogo" />
</a>
&nbsp; or &nbsp;
<a href='https://github.com/local-first-web/auth'>
<img src="https://raw.githubusercontent.com/local-first-web/branding/main/svg/auth-v.svg" height="100" alt="@localfirst/auth logo" />
</a>
&nbsp; or &nbsp;
<a href='https://github.com/inkandswitch/backchannel'>
<img src="https://tevidobiodevices.com/wp-content/uploads/2019/09/backchannel-300x98.png" height="75" alt="@localfirst/auth logo" />
</a> -->

## Why?

👩🏾 Alice and 👨🏻‍🦲 Bob can connect via a [relay](https://github.com/local-first-web/relay) for
**peer-to-peer communication** when they are both online. The relay **doesn't have any memory**,
though. So what happens if they're **not online at the same time?**

![](img/robopeer-without.png)

🤖 **Robopeer** is a peer, like Alice or Bob. But unlike Alice and Bob, Robopeer **never goes offline**.

![](img/robopeer-with.png)

Robopeer never contributes messages of its own; it only passes on messages it has received from
human peers.

## What?

Robopeer is a very small server that instantiates a peer-to-peer client on request, and connects it
to a [@localfirst/relay](https://github.com/local-first-web/relay) server.

On its own, Robopeer can't do anything: It needs to be paired with a peer-to-peer synchronization
protocol.

You can choose from one of these implementations, or create your own.

- [ ] [robopeer-automerge]() (implements the [Automerge](http://github.com/automerge/automerge) sync
      protocol)
- [ ] [robopeer-localfirstauth]() (implements the
      [@localfirst/auth](http://github.com/local-first-web/auth) connection protocol)
- [ ] [robopeer-backchannel]() (implements the [Backchannel]() protocol)

## How?

### Creating a server

```js

```

### Server endpoints

#### Create a Robopeer

`POST /create`

**`accessKey`** <small>required</small>  
The access key with which the server was instantiated.

**`documentId`** <small>required</small>  
A unique identifier for the document or topic that this robopeer will use to
connect to the relay. This can also be thought of as a "discovery key" or a "channel ID".

**`clientId`** <small>required</small>  
A unique identifier for the Robopeer's client. Depending on the protocol you are using, this might
be a username or a device ID that the other peers might recognize.

> Your request body might also include parameters for the use of the specific protocol you are using.
> For example, the `@localfirst/auth` implementation requires an invitation code.

#### Destroy a Robopeer

`POST /destroy`

### Storage

By default Robopeer keeps messages in memory and doesn't persist to storage.

<!-- ![](img/robopeer-member.png)

![](img/robopeer-device.png)

![](img/robopeer-details.png) -->
