# Registry
The registry is the module that is used for configuration of the service bus. Topics, namespaces and subscriptions are registered with this module, and the registry is accessible for all other modules. There's a separate set of functions just to support the subscriber agent.  

## Namespace Functions
Namespaces are the core of the registry. Topic subscribers are registered in namespaces, and the namespaces are routing messages to subscriber canisters. Namespaces can be used to create collections of topics that are related (by topics or subscribers), and as load balancers if there's a large amount of subscribers.

### Add namespace  
```
fn namespace_register(namespace: Namespace)
```
Register a new namespace.

**Parameters**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*namespace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;- *record {*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*name: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*description: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*subscribers: vec text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*active: bool;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*};*<br/><br/>

      
**Return**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Result&lt;String, String&gt;<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;- *Ok*: Namespace ID<br/>
&nbsp;&nbsp;&nbsp;&nbsp;- *Err*: "Could not register the namespace"<br/><br/>

### Remove namespace
```
fn namespace_unregister(namespace_id: String)
```
Unregister a namespace.

**Parameters**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*namespace_id*: The ID string of the namespace to remove 

**Return**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Result&lt;String, String&gt;<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;- *Ok*: The removed namespace ID<br/>
&nbsp;&nbsp;&nbsp;&nbsp;- *Err*: "Could not unregister the namespace"<br/><br/>



## Topic functions






## Subscriber functions




### Get subscription details
```
async fn get_subscription(subscription_id: String) 
```
Get the subscription with a specific ID.

**Parameters**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;(none) 

**Return**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Subscriber<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;- *record {*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*id: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*canister_id: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*callback: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*name: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*description: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*topic: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*namespace: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*active: bool;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*};*<br/><br/>

### Get all subscriptions
```
async fn get_subscriptions() -> Vec<Subscribers> 
```
Get all subscriptions registered to this canister.

**Parameters**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;(none) 

**Return**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Vec&lt;Subscribers&gt;<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;- *vec {*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*record {*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*id: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*canister_id: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*callback: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*name: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*description: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*topic: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*namespace: text;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*active: bool;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*}*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*};*<br/>


## Whitelist functions


## Agent functions
At the moment there's no frontend for the demo dapp, but the Candid UI is an easier and more user friendly way of test the backend functionality, without having to use the command line instructions. Check the actual Candid UI URL when deployed, but for a local deployment it will most likely be:

```
http://127.0.0.1:4943/?canisterId=br5f7-7uaaa-aaaaa-qaaca-cai&id=bkyz2-fmaaa-aaaaa-qaaaq-cai
```
