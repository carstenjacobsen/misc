# registry

1. Register Namespace
- name: crypto_prices
- description: Latest crypto prices


2. Register Topic
- namespaces: 1
- namespace ID: c6c7115d-a30f-5128-920f-60ccd8d9ddae - 4ca740bf-f748-5ada-bce7-f425a5b70bce
- name: pricing
- description: Publish latest crypto prices




namespace_register -> topic_register(namespace_id) 

A subscriber is the ID, a subscription is the object




The canister that wants to subscribe to a topic registers with canister id and callback function. 

Based on the topic, the system will assign the namespace

