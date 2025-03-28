---
mapped_pages:
  - https://www.elastic.co/guide/en/observability/current/logs-app-fields.html
---

# Logs Explorer fields [logs-app-fields]

This section lists the required fields the **Logs Explorer** uses to display data. Please note that some of the fields listed are not [ECS fields](ecs://reference/index.md#_what_is_ecs).

`@timestamp`
:   Date/time when the event originated.

    This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events.

    type: date

    required: True

    ECS field: True

    example: `May 27, 2020 @ 15:22:27.982`


`_doc`
:   This field is used to break ties between two entries with the same timestamp.

    required: True

    ECS field: False


`container.id`
:   Unique container id.

    type: keyword

    required: True

    ECS field: True

    example: `data`


`event.dataset`
:   Name of the dataset.

    If an event source publishes more than one type of log or events (e.g. access log, error log), the dataset is used to specify which one the event comes from.

    It’s recommended but not required to start the dataset name with the module name, followed by a dot, then the dataset name.

    type: keyword

    required: True, if you want to use the {{ml-features}}.

    ECS field: True

    example: `apache.access`


`host.hostname`
:   Name of the host.

    It normally contains what the `hostname` command returns on the host machine.

    type: keyword

    required: True, if you want to enable and use the **View in Context** feature.

    ECS field: True

    example: `Elastic.local`


`host.name`
:   Name of the host.

    It can contain what `hostname` returns on Unix systems, the fully qualified domain name, or a name specified by the user. The sender decides which value to use.

    type: keyword

    required: True

    ECS field: True

    example: `MacBook-Elastic.local`


`kubernetes.pod.uid`
:   Kubernetes Pod UID.

    type: keyword

    required: True

    ECS field: False

    example: `8454328b-673d-11ea-7d80-21010a840123`


`log.file.path`
:   Full path to the log file this event came from, including the file name. It should include the drive letter, when appropriate.

    If the event wasn’t read from a log file, do not populate this field.

    type: keyword

    required: True, if you want to use the **View in Context** feature.

    ECS field: True

    example: `/var/log/demo.log`


`message`
:   For log events the message field contains the log message, optimized for viewing in a log viewer.

    For structured logs without an original message field, other fields can be concatenated to form a human-readable summary of the event.

    If multiple messages exist, they can be combined into one message.

    type: text

    required: True

    ECS field: True

    example: `Hello World`
