# Set Up Development Environment

**Date:** March 23, 2025

## Tasks Completed

- Installed JDK 11, followed the steps in: [Using Homebrew to Install JDK 11](https://medium.com/@kirebyte/using-homebrew-to-install-java-jdk11-on-macos-2021-4a90aa276f1c), but used the brew suggested symlink:
  ```sh
  sudo ln -sfn /opt/homebrew/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk
  ```
- Installed Spark (3.5.5, latest version), followed: [Install Apache Spark on macOS](https://justinjbird.com/blog/2024/install-apache-spark-on-macos/)
- Installed Scala (2.12):
  ```sh
  brew install scala@2.12
  ```
  (Follow "first in PATH" instructions on install to symlink)
- Installed Kafka (2.8.2), followed: [Install Apache Kafka on Mac](https://learn.conduktor.io/kafka/how-to-install-apache-kafka-on-mac/), after moving into the root folder of Kafka and navigating to it.
- Installed Docker (28.0.1), followed: [Docker for Mac with Homebrew](https://www.cprime.com/resources/blog/docker-for-mac-with-homebrew-a-step-by-step-tutorial/)

## Challenges Faced

- Ensuring correct versions of each software for compatibility
- Adding JDK and Scala to system path following Homebrew instructions
- Homebrew does not have Kafka 2.8.2

## Solutions/Next Steps

- Kafka 2.8.2 was downloaded manually (binary)

## Learnings

- For immediate compatibility with Apache Spark 3.5.5 and to avoid potential issues with libraries, it is generally safer to use Scala 2.12. Some libraries may not yet fully support Scala 2.13.
- Don’t forget to run:
  ```sh
  source ~/.zshrc
  ```
  after updating the path as suggested by Homebrew.
- For Apache Spark 3.5.5 with Scala 2.12 and Java 11, Apache Kafka 2.8.x or later is well-tested and compatible.
- Setting variables in the `~/.zshrc` file ensures they persist across terminal sessions.
- To start Kafka:
  1. Start the Zookeeper server.
  2. Start the Kafka server.
  3. Since the Kafka variables are set in `~/.zshrc`, `kafka-topics.sh` can be run from anywhere.

## Notes

```sh
# Set Java Home
echo 'export JAVA_HOME="/opt/homebrew/opt/openjdk@11/libexec/openjdk.jdk/Contents/Home"' >> ~/.zshrc

# Set Scala Path
echo 'export PATH="/opt/homebrew/opt/scala@2.12/bin:$PATH"' >> ~/.zshrc

# Move Kafka download folder to /opt/homebrew/opt
mv kafka_2.12-2.8.2 /opt/homebrew/opt/kafka

# Set Kafka Home
echo 'export KAFKA_HOME="/usr/local/kafka"' >> ~/.zshrc

# Add Kafka to Path
echo 'export PATH="$KAFKA_HOME/bin:$PATH"' >> ~/.zshrc
