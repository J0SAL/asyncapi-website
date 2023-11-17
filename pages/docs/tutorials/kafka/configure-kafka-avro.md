---
title: Create AsyncAPI Document for applications interacting with Kafka using Avro Schema
description: Explore configuring AsyncAPI document for Kafka messages with Avro Schema.
weight: 30
---

## Introduction
## Creating AsyncAPI document using Avro Schemas

```
asyncapi: 3.0.0
info:
  title: User Signup API
  version: 1.0.0
  description: The API notifies you whenever a new user signs up in the application.
servers:
  kafkaServer:
    host: test.mykafkacluster.org:8092
    description: Kafka Server
    protocol: kafka
operations:
  onUserSignedUp:
    action: receive
    channel:
      $ref: '#/channels/userSignedUp'
channels:
  userSignedUp:
    description: This channel contains a message per each user who signs up in our application.
    address: user_signedup
    messages:
      userSignedUp:
        $ref: '#/components/messages/userSignedUp'
components:
  messages:
    userSignedUp:
      payload:
        schemaFormat: 'application/vnd.apache.avro;version=1.9.0'
        payload: |
          type: record
          name: UserSignedUp
          namespace: com.company
          doc: User signed up information
          fields:
            - name: user-id
              type: int
              doc: This property describes the id of the user
            - name: user-email
              type: string
              doc: This property describes the email of the user
```

## Summary
## Next Steps