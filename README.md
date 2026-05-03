[![Build Status](https://github.com/elastic/ecs-logging-java/actions/workflows/test.yml/badge.svg)](https://github.com/elastic/ecs-logging-java/actions/workflows/test.yml)
[![Maven Central](https://img.shields.io/maven-central/v/co.elastic.logging/ecs-logging-java-parent.svg)](https://search.maven.org/search?q=g:co.elastic.logging)

# ECS-based logging for Java applications

Centralized logging for Java applications with the Elastic stack made easy

## Fork changes

This fork adds the following on top of upstream [`elastic/ecs-logging-java`](https://github.com/elastic/ecs-logging-java):

### `event.sequence` support in logback-ecs-encoder ([PR #410](https://github.com/elastic/ecs-logging-java/pull/410))

The logback encoder now emits the ECS [`event.sequence`](https://www.elastic.co/guide/en/ecs/current/ecs-event.html#field-event-sequence) field when a `SequenceNumberGenerator` is configured on the Logback `LoggerContext`. This enables sub-millisecond log ordering in aggregators like CloudWatch.

- **Opt-in via Logback config** — add `<sequenceNumberGenerator class="ch.qos.logback.classic.spi.BasicSequenceNumberGenerator"/>` to your `logback.xml`
- **Backward compatible** — uses reflection to detect `ILoggingEvent.getSequenceNumber()` (logback 1.3+). On logback 1.2.x, the field is silently omitted with zero overhead.
- **No new dependencies or config knobs**

## Release announcements

To get notified about new releases, watch this repository for `Releases only`.

## Getting Help

If you need help or hit an issue, please start by opening a topic on our [discuss forums](https://discuss.elastic.co/c/observability/logs/69).
Please note that we reserve GitHub tickets for confirmed bugs and enhancement requests.

## Documentation

Docs are located on [elastic.co](https://www.elastic.co/guide/en/ecs-logging/java/current/index.html).

## License

ECS Logging Java is licensed under [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).
