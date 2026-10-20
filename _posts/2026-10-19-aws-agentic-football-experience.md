---
layout: "post"
title: The First Tactical Decision Wasn't About Football
---

On October 17, I participated in the [Agentic Football Cup](https://agenticfootballcup.com/) organized by AWS User Group Baku.

The challenge was to build a football team consisting of five autonomous AI agents, deploy them on Amazon Bedrock AgentCore, and compete against other teams.

Each agent controls a player, receives the current game state, and decides what action to take. The game engine invokes agents roughly every two seconds, leaving a limited window for inference and returning a valid command.

## Deploying the Team

We started by accessing the AWS environments provided through Workshop Studio.

Our initial approach was to deploy all five agents through the CLI. However, we soon realized that continuing with this workflow could consume a significant portion of our available time.

We decided to change our approach and use **Amazon Bedrock AgentCore Harness**.

Compared with deploying our own agent code to AgentCore Runtime, Harness provides a managed orchestration loop. The agent can be defined through configuration, including its model, instructions, tools, and skills. AWS documents the differences in its [Harness vs. Runtime comparison](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/harness-vs-runtime.html).

We proceeded with the provided models, skills, and other required configurations using this approach.

The difference was not simply about avoiding terminal commands. We were changing the level of abstraction at which we worked.

## Choosing What to Optimize

The workshop highlighted an engineering trade-off.

A code-based deployment provides more control over an agent's implementation and execution logic. A managed harness reduces the infrastructure and orchestration work required to get an agent running.

Neither approach is inherently better. The appropriate choice depends on the constraints.

In our case, the most immediate constraint was time. Spending too much of it on deployment would leave less time for the agents themselves.

This is particularly relevant in a system where agents must respond within strict latency limits. Getting an agent deployed is only the first step; making it behave reliably is a separate problem.

## After the Final Whistle

Our team didn't finish in the top three.

Looking back, however, the most interesting part of the workshop for me wasn't the tournament result or even the football simulation itself. It was having to reconsider an implementation approach while working under a deadline.

The experience reinforced a simple engineering principle: **more control is not always more useful.**

Sometimes the important decision is not how to implement something, but which parts of the implementation are worth spending time on.

And thanks to [David](https://www.linkedin.com/in/david-a-b6991b332/) for beign a great teammate!
