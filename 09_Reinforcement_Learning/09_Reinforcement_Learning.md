**Volume 06. AMR AI and Embodied Intelligence**


# Chapter 09. Reinforcement Learning

##  

## 09.1 Reinforcement Learning Basics

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Reinforcement learning is a machine learning paradigm in which an autonomous agent learns how to make decisions by interacting with an environment. Unlike supervised learning, where correct answers are provided during training, reinforcement learning relies on experience. The agent observes the consequences of its actions, receives feedback in the form of rewards, and gradually improves its behavior to maximize long-term success. This learning process closely resembles how humans and animals acquire new skills through trial, error, and adaptation.

The central objective of reinforcement learning is not simply to perform well on individual decisions but to discover a strategy that consistently produces the highest cumulative reward over time. Every decision influences future opportunities, making reinforcement learning fundamentally different from traditional optimization methods. The agent must balance immediate gains against future benefits while continuously adapting to changing situations.

A reinforcement learning system consists of several essential components. The environment represents the world in which the agent operates. The agent is the decision-making entity responsible for selecting actions. A state describes the current situation observed by the agent. Actions represent the available choices, while rewards provide numerical feedback indicating whether an action was beneficial or harmful. Together, these components create a continuous interaction loop that drives learning.

The interaction cycle begins when the environment provides the current state to the agent. Based on this information, the agent selects an action according to its current decision strategy. The environment responds by changing to a new state and returning a reward. This new experience becomes part of the agent\'s accumulated knowledge, allowing future decisions to become increasingly effective.

Unlike supervised learning datasets, reinforcement learning rarely provides explicit examples of correct behavior. Instead, the agent must independently discover which actions lead to desirable outcomes. This characteristic makes reinforcement learning particularly valuable for solving complex sequential decision problems where optimal behavior cannot easily be specified by human experts.

One of the defining characteristics of reinforcement learning is delayed reward. Many actions do not produce immediate feedback. Instead, their consequences appear much later after several additional decisions have been made. The learning algorithm must therefore identify which earlier actions contributed to eventual success or failure despite long time delays between decisions and rewards.

Consider an autonomous mobile robot navigating a warehouse. Moving toward the destination may require temporarily taking a longer path to avoid congestion or obstacles. Although the longer route appears less efficient initially, it may ultimately reduce travel time and improve safety. Reinforcement learning enables the robot to recognize these long-term advantages through accumulated experience.

The learning objective is often described as maximizing cumulative reward rather than maximizing individual rewards. A greedy decision that produces an immediate positive reward may prevent the agent from achieving much larger rewards later. Consequently, reinforcement learning emphasizes long-term planning instead of short-term optimization.

Exploration and exploitation form one of the most important trade-offs in reinforcement learning. Exploration involves trying unfamiliar actions to discover potentially better strategies. Exploitation focuses on using existing knowledge to maximize current performance. Successful reinforcement learning requires balancing these competing objectives throughout the learning process.

If an agent explores excessively, learning becomes inefficient because many poor decisions are repeated unnecessarily. If it exploits too early, it may converge to a suboptimal strategy without discovering superior alternatives. Designing algorithms that maintain an appropriate balance between exploration and exploitation remains a central research challenge.

Another fundamental concept is the policy. A policy defines how an agent selects actions based on its current state. Policies may be represented by simple mathematical rules, probability distributions, lookup tables, or deep neural networks. During training, the policy gradually evolves as the agent gains experience from interacting with the environment.

The value function estimates how beneficial a particular state or action is in terms of future cumulative reward. Rather than evaluating only immediate outcomes, the value function predicts expected long-term returns. This prediction helps the agent distinguish between actions that appear attractive now and those that generate greater future benefits.

Closely related to the value function is the concept of return. Return represents the total accumulated reward expected from a given point onward. Because future rewards are often uncertain, reinforcement learning introduces discounting to reduce the influence of distant rewards. Discounting reflects the practical reality that immediate outcomes are generally more certain than distant ones.

The discount factor determines how much importance is assigned to future rewards. A high discount factor encourages long-term planning by emphasizing future consequences. A lower discount factor prioritizes immediate rewards and produces more short-sighted behavior. Selecting an appropriate discount factor depends on the characteristics of the application.

The environment may be deterministic or stochastic. In deterministic environments, the same action always produces the same result. In stochastic environments, identical actions may lead to different outcomes because of uncertainty, noise, or interactions with external factors. Most real robotic systems operate in stochastic environments where uncertainty is unavoidable.

Reinforcement learning is particularly attractive for robotics because many robotic tasks involve sequential decision making under uncertainty. Mobile robots, industrial manipulators, humanoid robots, drones, and autonomous vehicles all require continuous adaptation to dynamic environments. Traditional rule-based controllers often struggle to handle these highly variable situations.

For autonomous mobile robots, reinforcement learning can improve navigation efficiency by learning collision avoidance strategies, optimizing path selection, minimizing energy consumption, and adapting to changing traffic conditions. Rather than relying entirely on manually designed rules, the robot gradually discovers effective behaviors through repeated interaction with its environment.

Industrial robotic manipulation provides another important application. Grasping unknown objects, inserting components into assemblies, opening doors, or manipulating deformable materials often require complex control strategies that are difficult to model analytically. Reinforcement learning enables robots to improve these skills through extensive practice in simulation before deployment.

Deep reinforcement learning combines reinforcement learning with deep neural networks capable of representing highly complex policies and value functions. Instead of manually engineering features, deep networks automatically learn meaningful representations directly from images, LiDAR scans, force sensors, or multimodal observations. This capability has significantly expanded the range of solvable robotic problems.

Modern reinforcement learning algorithms can process high-dimensional sensor inputs while simultaneously learning sophisticated decision strategies. Vision-based robotic control, dexterous manipulation, autonomous driving, and legged locomotion have all benefited from advances in deep reinforcement learning during the past decade.

Simulation plays a critical role in reinforcement learning because real-world training is often expensive, slow, and potentially unsafe. Robots can perform millions of simulated interactions without damaging hardware or creating hazardous situations. After acquiring useful policies in simulation, the learned behaviors may be transferred to physical robots through carefully designed adaptation techniques.

Despite its advantages, reinforcement learning presents several significant challenges. Training frequently requires enormous amounts of experience, making data efficiency an ongoing research problem. Sparse rewards can slow learning because useful feedback occurs only occasionally. Poorly designed reward functions may unintentionally encourage undesirable behavior that technically maximizes the specified objective.

Another limitation involves safety during learning. Random exploration may produce dangerous actions when operating physical robots. Consequently, industrial reinforcement learning often incorporates safety constraints, supervised initialization, simulation-based training, and human oversight to reduce operational risk. Safe reinforcement learning has therefore become an important research direction.

Generalization also remains difficult. Policies trained under specific environmental conditions may perform poorly when transferred to unfamiliar settings. Variations in lighting, weather, terrain, sensor noise, payload, or mechanical wear can significantly affect performance. Improving robustness across diverse environments continues to be an active area of research.

Recent advances increasingly combine reinforcement learning with imitation learning, foundation models, world models, and large language models. Instead of learning entirely through trial and error, robots can begin with prior knowledge obtained from demonstrations or pretrained representations. This hybrid approach reduces training time while improving sample efficiency and overall performance.

Embodied intelligence further extends reinforcement learning by considering the interaction between perception, reasoning, and physical action. Intelligent behavior emerges not only from optimizing policies but also from continuously integrating sensory information, environmental understanding, memory, and motor control. Reinforcement learning therefore becomes one component within a broader intelligent robotic architecture.

As autonomous robots become more capable, reinforcement learning is expected to play an increasingly important role in enabling adaptive, experience-driven behavior. Rather than executing fixed programs, future robots will continually improve through interaction with their environments while maintaining safety, efficiency, and robustness. This ability to learn from experience represents one of the defining characteristics of next-generation intelligent robotic systems.

강화 학습(Reinforcement Learning)은 에이전트(Agent)가 환경(Environment)과 상호작용하면서 의사결정을 학습하는 머신러닝(Machine Learning) 방법론이다. 지도 학습(Supervised Learning)처럼 정답이 미리 제공되는 것이 아니라, 경험을 통해 학습한다. 에이전트는 자신의 행동 결과를 관찰하고, 보상(Reward)이라는 형태의 피드백을 받으며, 장기적으로 더 나은 행동을 수행하도록 점진적으로 개선한다. 이러한 학습 과정은 인간과 동물이 시행착오를 통해 새로운 기술을 익히는 방식과 매우 유사하다.

강화 학습의 핵심 목표는 개별적인 의사결정을 잘 수행하는 것이 아니라, 장기적으로 가장 높은 누적 보상(Cumulative Reward)을 얻을 수 있는 전략을 발견하는 것이다. 하나의 행동은 이후의 선택 기회에도 영향을 미치므로, 강화 학습은 기존의 최적화 기법과 근본적으로 다르다. 에이전트는 현재의 이익과 미래의 이익을 동시에 고려하면서 변화하는 환경에 지속적으로 적응해야 한다.

강화 학습 시스템은 몇 가지 핵심 구성 요소로 이루어진다. 환경(Environment)은 에이전트가 활동하는 세계를 의미한다. 에이전트(Agent)는 의사결정을 수행하는 주체이다. 상태(State)는 현재 상황을 나타내며, 행동(Action)은 에이전트가 선택할 수 있는 결정이다. 보상(Reward)은 행동의 결과가 얼마나 바람직했는지를 수치로 표현한 피드백이다. 이러한 요소들이 지속적인 상호작용을 형성하며 학습을 이끌어 간다.

상호작용 과정은 환경이 현재 상태(State)를 에이전트에게 제공하는 것으로 시작된다. 에이전트는 현재의 정책(Policy)에 따라 행동(Action)을 선택한다. 환경은 그 행동에 반응하여 새로운 상태(State)로 전이되고 보상(Reward)을 반환한다. 이러한 경험은 에이전트의 지식에 축적되며, 시간이 지날수록 더욱 효과적인 의사결정을 가능하게 한다.

지도 학습(Supervised Learning)의 데이터셋(Dataset)과 달리, 강화 학습에서는 올바른 행동 예시가 거의 제공되지 않는다. 대신 에이전트는 어떤 행동이 바람직한 결과를 만드는지를 스스로 발견해야 한다. 이러한 특성 때문에 강화 학습은 사람이 최적의 행동을 명확하게 정의하기 어려운 복잡한 순차적 의사결정 문제를 해결하는 데 매우 적합하다.

강화 학습의 가장 중요한 특징 가운데 하나는 지연 보상(Delayed Reward)이다. 많은 행동은 즉각적인 피드백을 제공하지 않는다. 대신 여러 번의 추가적인 행동 이후에 결과가 나타난다. 따라서 학습 알고리즘은 긴 시간이 지난 후 얻어진 성공이나 실패가 과거의 어떤 행동에서 비롯되었는지를 추론해야 한다.

예를 들어 자율주행 이동 로봇(Autonomous Mobile Robot)이 물류창고를 이동한다고 가정해 보자. 목적지까지 가는 과정에서 혼잡이나 장애물을 피하기 위해 더 긴 경로를 선택할 수도 있다. 처음에는 비효율적으로 보일 수 있지만, 결과적으로는 이동 시간을 줄이고 안전성을 높일 수 있다. 강화 학습은 반복적인 경험을 통해 이러한 장기적인 이점을 학습할 수 있도록 해준다.

강화 학습의 목표는 개별 보상을 최대화하는 것이 아니라 누적 보상(Cumulative Reward)을 최대화하는 것이다. 즉시 높은 보상을 주는 행동이 이후 더 큰 보상을 얻을 기회를 잃게 만들 수도 있다. 따라서 강화 학습은 단기적인 최적화보다 장기적인 계획(Long-Term Planning)을 더욱 중요하게 고려한다.

탐험(Exploration)과 활용(Exploitation)의 균형은 강화 학습에서 가장 중요한 개념 중 하나이다. 탐험은 새로운 행동을 시도하여 더 나은 전략을 발견하는 과정이다. 활용은 이미 알고 있는 최선의 전략을 사용하여 현재 성능을 최대화하는 과정이다. 성공적인 강화 학습은 이 두 가지를 적절하게 균형 있게 수행해야 한다.

탐험이 지나치게 많으면 비효율적인 행동을 반복하게 되어 학습 속도가 느려진다. 반대로 활용만 지나치게 수행하면 더 우수한 전략을 발견하지 못한 채 지역 최적해(Local Optimum)에 머무를 수 있다. 따라서 탐험과 활용의 균형을 유지하는 알고리즘 설계는 강화 학습 연구의 핵심 과제 중 하나이다.

또 다른 핵심 개념은 정책(Policy)이다. 정책은 현재 상태(State)를 기반으로 어떤 행동(Action)을 선택할 것인지를 정의하는 규칙이다. 정책은 단순한 수학적 규칙일 수도 있고, 확률 모델, 테이블(Lookup Table), 또는 심층 신경망(Deep Neural Network)으로 표현될 수도 있다. 학습이 진행될수록 정책은 점차 개선된다.

가치 함수(Value Function)는 특정 상태(State)나 행동(Action)이 미래의 누적 보상 측면에서 얼마나 유리한지를 추정한다. 즉각적인 결과만 평가하는 것이 아니라 장기적인 기대 보상을 예측한다. 이를 통해 에이전트는 현재는 좋아 보이지만 장기적으로는 불리한 행동과, 당장은 손해처럼 보여도 미래에 더 큰 이익을 가져오는 행동을 구분할 수 있다.

가치 함수와 밀접한 개념으로 반환값(Return)이 있다. 반환값은 특정 시점 이후에 기대되는 총 누적 보상을 의미한다. 미래의 보상은 불확실성이 존재하기 때문에 강화 학습에서는 할인(Discounting)을 적용하여 먼 미래의 보상 영향력을 감소시킨다. 이는 가까운 미래일수록 예측의 신뢰도가 높다는 현실적인 특성을 반영한다.

할인 계수(Discount Factor)는 미래 보상을 얼마나 중요하게 고려할지를 결정한다. 할인 계수가 높을수록 장기적인 계획을 중시하게 되며, 낮을수록 즉각적인 보상을 우선시하는 경향을 가진다. 적절한 할인 계수는 적용 분야의 특성과 문제의 성격에 따라 달라진다.

환경(Environment)은 결정론적(Deterministic)일 수도 있고 확률론적(Stochastic)일 수도 있다. 결정론적 환경에서는 동일한 행동이 항상 동일한 결과를 만든다. 반면 확률론적 환경에서는 노이즈(Noise), 불확실성, 외부 요인 등으로 인해 같은 행동이라도 서로 다른 결과가 발생할 수 있다. 실제 로봇 시스템은 대부분 이러한 확률론적 환경에서 동작한다.

강화 학습은 순차적인 의사결정이 필요한 로봇 분야에서 특히 높은 활용 가치를 가진다. 자율이동로봇(AMR), 산업용 로봇, 휴머노이드(Humanoid), 드론(Drone), 자율주행차(Autonomous Vehicle)는 모두 불확실한 환경에서 지속적인 적응 능력이 요구된다. 기존의 규칙 기반 제어기는 이러한 복잡한 상황을 처리하는 데 한계를 보이는 경우가 많다.

자율이동로봇에서는 강화 학습을 통해 충돌 회피(Collision Avoidance), 경로 선택(Path Selection), 에너지 소비 최소화, 변화하는 교통 상황 적응 등을 개선할 수 있다. 사람이 모든 규칙을 설계하는 대신, 로봇은 반복적인 경험을 통해 더욱 효과적인 이동 전략을 스스로 학습하게 된다.

산업용 로봇의 조작(Manipulation) 역시 중요한 응용 분야이다. 다양한 형태의 물체를 집거나, 부품을 조립하거나, 문을 열거나, 변형 가능한 물체를 다루는 작업은 수학적으로 모델링하기 어렵다. 강화 학습은 시뮬레이션(Simulation)에서 충분한 반복 학습을 수행한 뒤 실제 로봇으로 이전함으로써 이러한 복잡한 기술을 향상시킬 수 있다.

심층 강화 학습(Deep Reinforcement Learning)은 강화 학습과 심층 신경망(Deep Neural Network)을 결합한 기술이다. 사람이 특징(Feature)을 직접 설계하는 대신, 신경망이 이미지(Image), 라이다(LiDAR), 힘 센서(Force Sensor), 멀티모달(Multimodal) 센서 데이터로부터 의미 있는 표현을 자동으로 학습한다. 이러한 발전은 해결 가능한 로봇 문제의 범위를 크게 확장하였다.

최신 강화 학습 알고리즘은 고차원 센서 데이터를 처리하면서 동시에 복잡한 의사결정 전략을 학습할 수 있다. 비전 기반 로봇 제어(Vision-Based Robot Control), 정밀 조작(Dexterous Manipulation), 자율주행(Autonomous Driving), 다리형 로봇 이동(Legged Locomotion) 등은 최근 심층 강화 학습의 발전으로 큰 성과를 얻고 있다.

시뮬레이션은 강화 학습에서 매우 중요한 역할을 수행한다. 실제 로봇에서의 학습은 비용이 높고 시간이 오래 걸리며 안전 문제도 발생할 수 있기 때문이다. 시뮬레이션에서는 하드웨어 손상이나 사고 위험 없이 수백만 번 이상의 상호작용을 수행할 수 있다. 이후 학습된 정책은 적응 기법을 이용하여 실제 로봇으로 이전될 수 있다.

강화 학습은 많은 장점을 가지고 있지만 여러 가지 한계도 존재한다. 학습에는 매우 많은 경험 데이터가 필요하며, 데이터 효율성(Data Efficiency)은 여전히 중요한 연구 과제이다. 또한 희소 보상(Sparse Reward) 환경에서는 보상이 드물게 발생하므로 학습 속도가 매우 느려질 수 있다. 잘못 설계된 보상 함수(Reward Function)는 의도하지 않은 행동을 유도할 수도 있다.

또 다른 중요한 문제는 학습 과정의 안전성(Safety)이다. 무작위 탐험 과정에서 실제 로봇은 위험한 행동을 수행할 가능성이 있다. 따라서 산업용 강화 학습에서는 안전 제약(Safety Constraint), 지도 학습 기반 초기화(Supervised Initialization), 시뮬레이션 기반 학습, 그리고 인간의 감독(Human Supervision)을 함께 적용하여 위험을 최소화한다. 이러한 이유로 안전 강화 학습(Safe Reinforcement Learning)은 중요한 연구 분야로 발전하고 있다.

일반화(Generalization) 역시 해결해야 할 과제이다. 특정 환경에서 학습한 정책은 새로운 환경에서는 성능이 크게 저하될 수 있다. 조명, 날씨, 지형, 센서 노이즈, 적재 중량, 기계 마모 등의 변화는 모두 성능에 영향을 미친다. 다양한 환경에서도 안정적인 성능을 유지하는 강인성(Robustness)을 향상시키는 연구가 활발하게 진행되고 있다.

최근에는 강화 학습을 모방 학습(Imitation Learning), 파운데이션 모델(Foundation Model), 월드 모델(World Model), 대규모 언어 모델(Large Language Model, LLM)과 결합하는 연구가 활발하다. 시행착오만으로 학습하는 대신, 시연 데이터(Demonstration Data)나 사전학습된 표현(Pretrained Representation)을 활용하면 학습 시간을 크게 줄이고 데이터 효율성과 성능을 동시에 향상시킬 수 있다.

체화 지능(Embodied Intelligence)은 강화 학습을 더욱 확장한 개념이다. 지능은 단순히 정책을 최적화하는 것이 아니라, 지각(Perception), 추론(Reasoning), 기억(Memory), 환경 이해(Environment Understanding), 그리고 물리적 행동(Action)이 지속적으로 상호작용하면서 형성된다. 따라서 강화 학습은 더 큰 지능형 로봇 아키텍처(Intelligent Robot Architecture)를 구성하는 핵심 요소 가운데 하나로 이해할 수 있다.

자율 로봇의 성능이 지속적으로 발전함에 따라 강화 학습은 경험 기반의 적응형 지능을 구현하는 핵심 기술로 자리 잡을 것으로 예상된다. 미래의 로봇은 고정된 프로그램만 실행하는 것이 아니라, 환경과의 상호작용을 통해 지속적으로 학습하고 성능을 향상시키면서도 안전성, 효율성, 강인성을 동시에 유지하게 될 것이다. 이러한 경험 기반 학습 능력은 차세대 지능형 로봇을 대표하는 가장 중요한 특징 가운데 하나가 될 것이다.

##  

## 09.2 MDP and Reward Design

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

A Markov Decision Process, commonly abbreviated as MDP, is a mathematical framework used to describe sequential decision-making problems. It provides a structured way to represent how an agent interacts with an environment, how actions change the situation, and how rewards guide the agent toward desirable long-term behavior.

An MDP is widely used as the theoretical foundation of reinforcement learning. It converts a complex control problem into a formal model composed of states, actions, transition probabilities, rewards, and a discount factor. These elements allow learning algorithms to evaluate present decisions in relation to their future consequences.

The state represents the information required to describe the current situation of the environment. In an autonomous mobile robot, a state may include the robot position, heading, velocity, battery level, obstacle locations, destination, traffic conditions, and the operational status of nearby robots.

A well-designed state should contain enough information for the agent to make an effective decision. If important variables are missing, the agent may select inappropriate actions because it cannot distinguish between situations that require different responses. This issue is known as state aliasing.

The Markov property assumes that the current state contains all information needed to predict the next state. In other words, once the present state is known, earlier states do not provide additional information about the immediate future. This assumption simplifies both mathematical analysis and algorithm design.

Real robotic systems do not always satisfy the Markov property perfectly. Sensor noise, hidden obstacles, communication delays, mechanical wear, and unobserved human intentions may influence future outcomes. Engineers therefore attempt to construct state representations that approximate the Markov property as closely as possible.

When the agent cannot directly observe the complete state, the problem is often modeled as a Partially Observable Markov Decision Process, or POMDP. In that case, the agent receives observations rather than complete states and must estimate hidden information using memory, belief states, sensor fusion, or recurrent neural networks.

The action is the decision selected by the agent. For a mobile robot, actions may include moving forward, turning, slowing down, stopping, selecting a route, requesting passage, docking, or waiting. Actions can be discrete, continuous, or a combination of both depending on the control problem.

Discrete action spaces contain a limited set of choices. A navigation agent might select among forward, left, right, stop, and reverse. Discrete actions are easier to model, but they may produce rough or inefficient control when a robot requires precise velocity, acceleration, steering, or actuator commands.

Continuous action spaces allow the agent to choose real-valued control signals. Examples include linear velocity, angular velocity, steering angle, wheel torque, braking force, and joint position. Continuous control provides smoother behavior but usually requires more advanced reinforcement learning algorithms.

The transition model describes how the environment changes after the agent selects an action. It defines the probability of reaching a new state given the current state and action. In deterministic environments, one state-action pair always produces the same next state.

Most real robotic environments are stochastic. The same command may generate slightly different results because of wheel slip, uneven terrain, payload variation, actuator delay, localization error, wind, sensor noise, or unexpected human movement. Transition probabilities represent this uncertainty.

The reward is a numerical signal that evaluates the immediate consequence of an action. A positive reward indicates desirable progress, while a negative reward represents an undesirable result or cost. The agent learns a policy that attempts to maximize the expected sum of rewards over time.

Reward design is one of the most important and difficult tasks in reinforcement learning. The reward function defines what the agent is encouraged to achieve, but it does not directly specify how the objective should be accomplished. The agent may discover strategies that satisfy the reward mathematically while violating the designer's intention.

For an autonomous mobile robot, reaching the destination may produce a large positive reward. Collisions, emergency stops, unstable motion, excessive energy consumption, unsafe proximity to humans, and mission failure may generate negative rewards. Smaller rewards can be assigned for safe progress toward the goal.

A sparse reward provides feedback only when a major event occurs. The robot may receive a positive reward after reaching the destination and a negative reward after a collision, while receiving no reward during most of the journey. Sparse rewards are easy to define but often make learning slow and inefficient.

A dense reward provides frequent feedback during the task. The robot may receive a small positive reward whenever it reduces the distance to the destination and a small penalty for unnecessary movement. Dense feedback can accelerate learning, but it may also introduce unintended shortcuts.

Reward shaping refers to adding intermediate rewards that guide the agent toward useful behavior. For example, a navigation agent can receive additional rewards for maintaining clearance from obstacles, following a smooth trajectory, reducing travel time, and preserving sufficient battery energy.

Reward shaping must be applied carefully because poorly designed intermediate rewards can change the true objective. A robot rewarded only for moving toward a goal may become trapped behind an obstacle while repeatedly attempting to move directly forward instead of selecting a longer but feasible route.

A common reward design uses multiple weighted terms. The total reward may combine destination progress, collision avoidance, energy efficiency, motion smoothness, time efficiency, path deviation, human comfort, and rule compliance. Each term represents a different aspect of the desired behavior.

The relative weights of reward terms strongly influence the learned policy. If collision penalties are too small, the robot may accept unsafe risk to reduce travel time. If safety penalties are excessively large, the robot may become overly cautious, stop frequently, or refuse to move in crowded areas.

Reward scales also affect learning stability. Extremely large rewards can produce unstable value estimates and large gradient updates. Very small rewards may generate weak learning signals. Normalization, clipping, scaling, and careful weight tuning are often required to maintain numerical stability.

Terminal rewards are assigned when an episode ends. Successful completion may produce a large positive terminal reward, while collision, timeout, localization failure, or departure from the permitted area may generate a negative terminal reward. Terminal conditions define the practical boundaries of the task.

An episode is a sequence of interactions from an initial state to a terminal state. A warehouse navigation episode may begin when a mission is assigned and end when the robot reaches the destination, exceeds the time limit, requests human assistance, or encounters a safety-critical event.

Some robotic tasks are naturally continuing rather than episodic. A patrol robot may operate for many hours without a clear terminal state. In such cases, artificial episode boundaries can be introduced based on time, battery cycles, mission completion, shift changes, or periodic policy evaluation.

The discount factor determines the importance of future rewards. A value close to zero encourages the agent to focus on immediate outcomes. A value close to one gives greater importance to long-term consequences. The appropriate setting depends on the duration and structure of the task.

For navigation, a high discount factor encourages the robot to consider how current motion affects future safety and route efficiency. However, a value that is too high may increase training instability because distant rewards become highly influential even when predictions are uncertain.

The return is the discounted sum of future rewards expected after a state or action. Reinforcement learning algorithms estimate this return to evaluate decisions. A policy is considered better when it produces higher expected returns across the distribution of possible starting states and environmental conditions.

The state-value function estimates the expected return from a state when the agent follows a particular policy. It answers the question of how favorable the current situation is. States near the destination with safe and open paths usually have higher values than states near hazards or dead ends.

The action-value function estimates the expected return of selecting a specific action in a particular state and then following the policy. It allows the agent to compare available actions. Algorithms such as Q-learning learn action values directly and select actions with the highest expected return.

The Bellman principle expresses a recursive relationship between current value and future value. The value of a state depends on the immediate reward and the discounted value of the next state. This relationship allows long-term decision problems to be solved through repeated local updates.

The Bellman equation is fundamental because it connects short-term experience with long-term planning. Each interaction provides information about the reward received and the next state reached. The learning algorithm uses this information to improve estimates of future return.

A policy defines the agent's action-selection strategy. A deterministic policy selects one action for each state, while a stochastic policy assigns probabilities to multiple actions. Stochastic policies are useful when uncertainty, exploration, or behavioral diversity is required.

In robotic navigation, a stochastic policy may choose among several safe routes rather than always following the same path. This can reduce congestion, support multi-robot coordination, and improve robustness when the environment changes. However, randomness must be limited in safety-critical situations.

The initial state distribution specifies where episodes begin. If training always starts from a small set of easy states, the policy may fail in unfamiliar situations. Effective training therefore includes diverse starting locations, orientations, payload conditions, battery levels, and environmental configurations.

MDP design requires careful selection of time steps. A short time step provides precise control but creates longer episodes and higher computational cost. A long time step reduces computation but may hide important dynamics or cause the agent to react too slowly to obstacles and safety events.

The action duration must also match the physical system. If a velocity command is applied for too long, the robot may move beyond a safe region before the next decision. If commands change too frequently, actuators may oscillate, energy use may increase, and control may become unstable.

Hierarchical reinforcement learning can divide a complex MDP into multiple levels. A high-level policy selects goals, routes, or behaviors, while a low-level controller generates motion commands. This separation is especially useful in AMR systems where mission planning and real-time control operate at different rates.

A high-level action may instruct the robot to navigate to a station, wait at a checkpoint, or begin docking. The low-level controller then handles steering, velocity regulation, and obstacle avoidance. Hierarchical design reduces the complexity of the action space and improves interpretability.

Reward functions can also be separated by control level. Mission-level rewards may emphasize task completion and throughput, while navigation-level rewards focus on safety and travel efficiency. Motion-level rewards may encourage smooth acceleration, low tracking error, and stable actuator behavior.

Multi-objective reward design is necessary when several operational goals must be considered simultaneously. Industrial robots must balance productivity, safety, energy use, equipment wear, passenger comfort, traffic rules, and mission priority. These objectives may conflict with one another.

A single weighted reward combines all objectives into one scalar value, but this approach may hide trade-offs. Small changes in weights can produce large changes in behavior. Engineers should therefore evaluate each reward component separately rather than relying only on the total return.

Constrained MDPs provide another approach by treating safety or resource limits as explicit constraints. The agent maximizes reward while keeping collision probability, energy use, temperature, speed, or human proximity within acceptable limits. This is often more appropriate for industrial robotics.

Safety constraints should not depend solely on learned behavior. A practical AMR architecture normally includes independent emergency stops, safety scanners, speed limits, collision monitors, geofences, and fallback controllers. Reinforcement learning operates within these protected boundaries rather than replacing them.

Reward hacking occurs when the agent exploits weaknesses in the reward function. For example, a robot rewarded for remaining close to a target may circle around it without completing the task. A robot rewarded for speed may create unsafe motion unless safety and terminal conditions are defined correctly.

Specification gaming is a broader form of reward hacking in which the agent follows the literal reward specification but violates the intended purpose. Preventing this behavior requires adversarial testing, scenario diversity, runtime monitoring, and evaluation metrics that are independent of the training reward.

Inverse reward design recognizes that a reward function is an imperfect description of the designer's intention. Instead of assuming the reward is always correct, the system treats it as evidence about the true objective. This perspective encourages cautious behavior when the agent encounters unfamiliar conditions.

Human feedback can support reward design by providing preferences between different robot behaviors. Rather than manually assigning exact numerical values, a human evaluator can compare two trajectories and indicate which one is safer, smoother, or more efficient. A reward model can then learn from these preferences.

Imitation learning can also reduce dependence on complex reward engineering. Demonstrations from skilled operators provide examples of desirable behavior. Reinforcement learning can then refine the initial policy using rewards, while preserving useful patterns learned from expert data.

Simulation is commonly used to test MDP and reward designs before physical deployment. Engineers can visualize trajectories, compare reward components, detect unintended strategies, and generate rare failure scenarios. Simulation allows unsafe policies to be rejected before they reach real hardware.

Domain randomization improves robustness by varying friction, mass, sensor noise, obstacle behavior, lighting, latency, and terrain during training. The resulting MDP represents a family of environments rather than a single fixed model. This helps the policy transfer from simulation to the real world.

Offline reinforcement learning constructs policies from previously collected datasets instead of unrestricted online interaction. In this setting, the reward function may be recalculated for stored trajectories. Offline learning is attractive for AMRs because real operational data can be reused without dangerous exploration.

However, offline reinforcement learning is limited by the coverage of the dataset. The policy may be unreliable when it selects actions that are poorly represented in the training data. Conservative learning methods are therefore used to discourage decisions that move far beyond known experience.

Reward evaluation should include more than average return. A policy with high average reward may still produce rare but unacceptable failures. Engineers should measure collision rates, near misses, timeout frequency, energy consumption, intervention count, path efficiency, and performance under abnormal conditions.

Sensitivity analysis examines how behavior changes when reward weights, discount factors, transition noise, and initial states are modified. A robust policy should not collapse under small parameter changes. Large behavioral changes may indicate that the MDP or reward design is poorly conditioned.

The reward function should remain aligned with operational requirements throughout the product lifecycle. Changes in robot payload, speed, environment, customer workflow, or safety policy may invalidate earlier assumptions. Reward definitions and evaluation scenarios must therefore be version-controlled and reviewed.

Production systems also require runtime monitoring for reward-related failures. The deployed robot does not usually calculate training rewards for control, but equivalent metrics can be logged. Unexpected changes in these metrics may reveal model drift, environmental change, or emerging unsafe behavior.

MDP modeling and reward design are therefore not merely theoretical preparation for selecting an algorithm. They define the meaning of the learning problem itself. Even a powerful reinforcement learning algorithm cannot produce reliable behavior when the state, action, transition, or reward model is poorly designed.

For autonomous mobile robots, a successful MDP must represent the physical environment, operational mission, safety boundaries, uncertainty, and long-term consequences of action. A successful reward function must encourage useful performance without creating unsafe shortcuts or overly conservative behavior.

The most effective designs combine formal modeling, simulation, expert knowledge, field data, safety engineering, and continuous validation. Through this integrated process, reinforcement learning can develop policies that are not only high-performing in simulation but also stable, understandable, and dependable in real robotic operations.

마르코프 결정 과정(Markov Decision Process, MDP)은 순차적인 의사결정 문제를 수학적으로 표현하기 위한 프레임워크(Framework)이다. 이는 에이전트(Agent)가 환경(Environment)과 어떻게 상호작용하는지, 행동(Action)이 환경을 어떻게 변화시키는지, 그리고 보상(Reward)이 장기적으로 바람직한 행동을 어떻게 유도하는지를 체계적으로 표현하는 방법을 제공한다.

MDP는 강화 학습(Reinforcement Learning)의 이론적 기반으로 가장 널리 사용된다. 복잡한 제어 문제를 상태(State), 행동(Action), 상태 전이 확률(Transition Probability), 보상(Reward), 할인 계수(Discount Factor)로 구성된 수학적 모델로 변환한다. 이러한 요소들은 학습 알고리즘이 현재의 의사결정을 미래의 결과와 연결하여 평가할 수 있도록 해준다.

상태(State)는 현재 환경을 설명하는 데 필요한 정보를 의미한다. 자율이동로봇(Autonomous Mobile Robot, AMR)에서는 로봇의 위치(Position), 방향(Heading), 속도(Velocity), 배터리(Battery) 상태, 장애물 위치, 목적지, 교통 상황, 그리고 주변 로봇들의 운용 상태 등이 상태를 구성할 수 있다.

잘 설계된 상태(State)는 에이전트가 올바른 의사결정을 내릴 수 있을 만큼 충분한 정보를 포함해야 한다. 중요한 변수가 누락되면 서로 다른 대응이 필요한 상황을 구별하지 못하게 되어 부적절한 행동을 선택할 수 있다. 이러한 문제를 상태 혼동(State Aliasing)이라고 한다.

마르코프 성질(Markov Property)은 현재 상태(State)에 미래를 예측하는 데 필요한 모든 정보가 포함되어 있다고 가정한다. 즉, 현재 상태를 알고 있다면 과거의 상태는 다음 상태를 예측하는 데 추가적인 정보를 제공하지 않는다. 이러한 가정은 수학적 분석과 알고리즘 설계를 크게 단순화한다.

실제 로봇 시스템은 마르코프 성질을 완벽하게 만족하지 않는 경우가 많다. 센서 노이즈(Sensor Noise), 숨겨진 장애물, 통신 지연, 기계적 마모, 사람의 의도를 관측할 수 없는 상황 등은 미래 결과에 영향을 미칠 수 있다. 따라서 엔지니어는 가능한 한 마르코프 성질을 만족하도록 상태를 설계하려고 노력한다.

에이전트가 전체 상태를 직접 관측할 수 없는 경우에는 부분 관측 마르코프 결정 과정(Partially Observable Markov Decision Process, POMDP)으로 모델링한다. 이 경우 에이전트는 완전한 상태 대신 관측값(Observation)을 입력받으며, 메모리(Memory), 신념 상태(Belief State), 센서 융합(Sensor Fusion), 순환 신경망(Recurrent Neural Network)을 이용하여 숨겨진 정보를 추정한다.

행동(Action)은 에이전트가 선택하는 의사결정이다. 이동 로봇에서는 전진, 회전, 감속, 정지, 경로 선택, 통행 요청, 도킹(Docking), 대기 등이 행동이 될 수 있다. 문제의 특성에 따라 행동은 이산형(Discrete), 연속형(Continuous), 또는 이 둘의 조합으로 구성된다.

이산 행동 공간(Discrete Action Space)은 선택 가능한 행동의 개수가 제한되어 있다. 예를 들어 전진, 좌회전, 우회전, 정지, 후진과 같은 명령이 이에 해당한다. 구현은 단순하지만 정밀한 속도나 조향 제어에는 한계가 있을 수 있다.

연속 행동 공간(Continuous Action Space)은 실수값 기반의 제어 명령을 선택한다. 선속도(Linear Velocity), 각속도(Angular Velocity), 조향각(Steering Angle), 휠 토크(Wheel Torque), 제동력(Braking Force), 관절 위치(Joint Position) 등이 대표적인 예이다. 보다 부드러운 제어가 가능하지만 일반적으로 더 복잡한 강화 학습 알고리즘이 요구된다.

상태 전이 모델(Transition Model)은 행동 이후 환경이 어떻게 변화하는지를 설명한다. 이는 현재 상태와 행동이 주어졌을 때 다음 상태에 도달할 확률을 정의한다. 결정론적(Deterministic) 환경에서는 하나의 상태와 행동이 항상 동일한 다음 상태를 만든다.

대부분의 실제 로봇 환경은 확률론적(Stochastic)이다. 동일한 명령이라도 바퀴 미끄러짐, 노면 상태, 적재 중량, 액추에이터 지연, 위치 추정 오차, 바람, 센서 노이즈, 사람의 움직임 등에 의해 서로 다른 결과가 발생할 수 있다. 이러한 불확실성을 상태 전이 확률이 표현한다.

보상(Reward)은 행동의 결과를 수치적으로 평가하는 신호이다. 양의 보상은 바람직한 결과를 의미하고, 음의 보상은 비용(Cost)이나 바람직하지 않은 결과를 의미한다. 에이전트는 장기적으로 기대되는 보상의 합을 최대화하는 정책(Policy)을 학습한다.

보상 설계(Reward Design)는 강화 학습에서 가장 중요하면서도 어려운 작업 가운데 하나이다. 보상 함수(Reward Function)는 무엇을 달성해야 하는지를 정의하지만, 어떻게 달성할지는 직접 알려주지 않는다. 따라서 에이전트는 수학적으로는 보상을 최대화하지만 설계자의 의도와는 다른 전략을 발견할 수도 있다.

자율이동로봇에서는 목적지 도착에 큰 양의 보상을 부여할 수 있다. 충돌(Collision), 비상 정지(Emergency Stop), 불안정한 주행, 과도한 에너지 소비, 사람과의 위험한 근접, 임무 실패에는 음의 보상을 줄 수 있다. 목적지를 향해 안전하게 이동하는 과정에도 작은 보상을 부여할 수 있다.

희소 보상(Sparse Reward)은 중요한 사건이 발생할 때만 보상을 제공한다. 목적지에 도착하면 큰 보상을 받고, 충돌하면 큰 패널티(Penalty)를 받으며, 이동 중 대부분의 시간에는 보상이 없다. 설계는 단순하지만 학습 속도가 매우 느려질 수 있다.

밀집 보상(Dense Reward)은 학습 과정에서 지속적으로 피드백을 제공한다. 예를 들어 목적지와의 거리가 줄어들 때마다 작은 보상을 주고, 불필요한 이동에는 작은 패널티를 줄 수 있다. 학습 속도는 빨라지지만 의도하지 않은 행동을 유도할 위험도 존재한다.

보상 형성(Reward Shaping)은 학습을 돕기 위해 중간 보상을 추가하는 기법이다. 장애물과 충분한 거리를 유지하거나, 부드러운 경로를 따라 이동하거나, 이동 시간을 줄이거나, 배터리를 효율적으로 사용하는 행동에 추가 보상을 부여할 수 있다.

보상 형성은 매우 신중하게 적용해야 한다. 예를 들어 목적지 방향으로만 이동하는 것에 보상을 주면, 로봇은 장애물 뒤에서 계속 앞으로만 이동하려고 시도하면서 실제로는 우회 경로를 선택하지 못할 수 있다.

실제 보상 함수는 여러 개의 가중치(Weight)를 가진 항목들의 합으로 구성되는 경우가 많다. 목적지 접근, 충돌 회피, 에너지 효율, 주행의 부드러움, 시간 효율, 경로 이탈 정도, 사람의 승차감, 규칙 준수 등이 각각 하나의 보상 요소가 될 수 있다.

각 보상 항목의 상대적인 가중치는 최종 정책에 매우 큰 영향을 준다. 충돌 패널티가 너무 작으면 로봇은 시간을 줄이기 위해 위험을 감수할 수 있다. 반대로 안전 패널티가 너무 크면 로봇은 지나치게 조심스러워져 혼잡한 환경에서 자주 멈추거나 움직이기를 거부할 수도 있다.

보상의 크기(Reward Scale) 역시 학습 안정성에 영향을 준다. 지나치게 큰 보상은 가치 함수(Value Function)의 추정을 불안정하게 만들고, 매우 작은 보상은 학습 신호가 약해질 수 있다. 따라서 정규화(Normalization), 클리핑(Clipping), 스케일링(Scaling), 가중치 조정이 필요하다.

종료 보상(Terminal Reward)은 하나의 에피소드(Episode)가 끝날 때 부여된다. 임무를 성공적으로 완료하면 큰 양의 보상을 받을 수 있으며, 충돌, 시간 초과, 위치 추정 실패, 허용 구역 이탈 등은 큰 음의 보상을 받을 수 있다. 종료 조건은 작업의 경계를 정의한다.

에피소드(Episode)는 초기 상태부터 종료 상태까지 이어지는 상호작용의 연속이다. 물류창고에서의 이동 임무는 작업이 시작되어 목적지에 도착하거나, 시간 제한을 초과하거나, 사람의 개입이 필요하거나, 안전 문제가 발생할 때 종료될 수 있다.

일부 로봇 작업은 종료가 없는 연속적인(Continuing) 작업이다. 순찰 로봇은 수 시간 동안 계속 운용될 수 있다. 이러한 경우에는 시간, 배터리 주기, 임무 완료, 근무 교대, 정책 평가 등의 기준으로 인위적인 에피소드 경계를 설정할 수 있다.

할인 계수(Discount Factor)는 미래 보상의 중요도를 결정한다. 값이 작으면 현재의 즉각적인 결과를 중시하고, 값이 크면 미래의 장기적인 결과를 더욱 중요하게 고려한다. 적절한 값은 작업의 특성에 따라 달라진다.

경로 계획에서는 높은 할인 계수를 사용하면 현재의 이동이 미래의 안전성과 경로 효율에 어떤 영향을 미치는지를 고려하게 된다. 그러나 지나치게 높은 값은 먼 미래의 불확실한 보상이 과도하게 반영되어 학습이 불안정해질 수 있다.

반환값(Return)은 특정 상태나 행동 이후에 기대되는 할인된 누적 보상이다. 강화 학습 알고리즘은 이 값을 추정하여 의사결정을 평가한다. 다양한 초기 상태와 환경에서도 더 높은 반환값을 만드는 정책이 더 우수한 정책으로 평가된다.

상태 가치 함수(State-Value Function)는 특정 정책을 따를 때 하나의 상태가 얼마나 유리한지를 평가한다. 안전하고 목적지와 가까운 상태는 일반적으로 높은 가치(Value)를 가지며, 위험 지역이나 막다른 길은 낮은 가치를 가진다.

행동 가치 함수(Action-Value Function)는 특정 상태에서 특정 행동을 선택했을 때의 기대 반환값을 추정한다. 이를 통해 가능한 여러 행동을 비교할 수 있다. Q-러닝(Q-Learning)과 같은 알고리즘은 이러한 행동 가치 함수를 직접 학습한다.

벨만 원리(Bellman Principle)는 현재의 가치와 미래의 가치가 재귀적으로 연결된다는 개념이다. 현재 상태의 가치는 즉시 받은 보상과 다음 상태의 할인된 가치에 의해 결정된다. 이를 통해 장기적인 의사결정 문제를 반복적인 계산으로 해결할 수 있다.

벨만 방정식(Bellman Equation)은 단기 경험과 장기 계획을 연결하는 핵심 수학식이다. 매번의 상호작용은 현재 받은 보상과 다음 상태에 대한 정보를 제공하며, 알고리즘은 이를 이용하여 미래 보상의 추정을 지속적으로 개선한다.

정책(Policy)은 에이전트의 행동 선택 전략이다. 결정론적 정책(Deterministic Policy)은 하나의 상태에서 항상 동일한 행동을 선택한다. 확률적 정책(Stochastic Policy)은 여러 행동에 확률을 부여하여 선택한다. 확률적 정책은 탐험과 불확실성이 필요한 상황에서 유용하다.

로봇 내비게이션에서는 확률적 정책을 이용하여 여러 개의 안전한 경로를 선택할 수 있다. 이는 교통 혼잡을 줄이고 다중 로봇 협업을 지원하며 환경 변화에 대한 강인성을 높여준다. 다만 안전이 중요한 상황에서는 무작위성이 제한되어야 한다.

초기 상태 분포(Initial State Distribution)는 학습이 시작되는 위치를 정의한다. 항상 쉬운 환경에서만 학습하면 새로운 상황에서는 성능이 급격히 저하될 수 있다. 따라서 다양한 시작 위치, 방향, 적재 중량, 배터리 상태, 환경 조건을 포함하는 것이 중요하다.

MDP 설계에서는 시간 간격(Time Step)도 신중하게 결정해야 한다. 시간이 너무 짧으면 정밀한 제어는 가능하지만 계산량이 증가하고 에피소드가 길어진다. 반대로 너무 길면 중요한 동적 특성을 놓치거나 장애물에 늦게 반응할 수 있다.

행동 지속 시간(Action Duration)도 실제 시스템과 일치해야 한다. 하나의 속도 명령이 너무 오래 유지되면 다음 의사결정 이전에 위험 구역까지 이동할 수 있다. 반대로 지나치게 자주 명령을 변경하면 진동(Oscillation), 에너지 증가, 제어 불안정이 발생할 수 있다.

계층형 강화 학습(Hierarchical Reinforcement Learning)은 복잡한 MDP를 여러 계층으로 분리한다. 상위 정책은 목표, 경로, 행동 전략을 결정하고, 하위 제어기는 실제 속도와 조향 명령을 생성한다. 이러한 구조는 AMR에서 임무 계획과 실시간 제어를 효과적으로 분리한다.

상위 수준의 행동은 특정 작업장으로 이동하거나, 체크포인트에서 대기하거나, 도킹을 시작하는 것일 수 있다. 이후 하위 제어기는 조향, 속도 제어, 장애물 회피를 수행한다. 이러한 계층 구조는 행동 공간(Action Space)의 복잡성을 줄이고 시스템의 이해 가능성을 높인다.

보상 함수도 계층별로 분리하여 설계할 수 있다. 임무 수준에서는 작업 완료와 생산성을 중시하고, 내비게이션 수준에서는 안전과 이동 효율을 중시하며, 모션 제어 수준에서는 부드러운 가속, 작은 추종 오차, 안정적인 액추에이터 제어를 목표로 할 수 있다.

다목적 보상 설계(Multi-Objective Reward Design)는 여러 운영 목표를 동시에 만족해야 하는 산업용 로봇에서 매우 중요하다. 생산성, 안전성, 에너지 소비, 장비 마모, 승차감, 교통 규칙, 임무 우선순위 등은 서로 충돌할 수도 있다.

단일 가중치 기반 보상은 모든 목표를 하나의 값으로 통합하지만, 목표 간의 절충 관계(Trade-off)를 숨길 수 있다. 작은 가중치 변화만으로도 로봇의 행동이 크게 달라질 수 있으므로 각 보상 요소를 개별적으로 분석해야 한다.

제약 마르코프 결정 과정(Constrained Markov Decision Process, CMDP)은 안전이나 자원 제한을 명시적인 제약 조건으로 다룬다. 에이전트는 충돌 확률, 에너지 소비, 온도, 속도, 사람과의 거리 등을 제한하면서 보상을 최대화한다. 이는 산업용 로봇에 더욱 적합한 접근 방식이다.

안전 제약은 학습된 정책에만 의존해서는 안 된다. 실제 AMR 시스템은 독립적인 비상 정지(Emergency Stop), 안전 라이다(Safety Scanner), 속도 제한(Speed Limit), 충돌 감시(Collision Monitor), 지오펜스(Geofence), 백업 제어기(Fallback Controller)를 함께 사용한다. 강화 학습은 이러한 안전 장치 안에서 동작해야 한다.

보상 해킹(Reward Hacking)은 에이전트가 보상 함수의 허점을 이용하는 현상이다. 예를 들어 목표 근처에 머무르는 것에만 보상을 주면 실제 작업을 완료하지 않고 계속 목표 주변만 맴돌 수도 있다. 속도만 보상하면 위험한 주행을 수행할 수도 있다.

명세 악용(Specification Gaming)은 보상 함수의 문자 그대로는 만족하지만 설계자의 실제 의도는 위반하는 행동을 의미한다. 이를 방지하려면 적대적 테스트(Adversarial Testing), 다양한 시나리오, 런타임 모니터링(Runtime Monitoring), 독립적인 평가 지표가 함께 사용되어야 한다.

역보상 설계(Inverse Reward Design)는 보상 함수가 설계자의 의도를 완벽하게 표현하지 못한다고 가정한다. 보상 함수를 절대적인 목표가 아니라 설계 의도를 나타내는 하나의 단서로 해석함으로써, 새로운 환경에서는 보다 신중하게 행동하도록 유도한다.

사람의 피드백(Human Feedback)은 보상 설계를 지원할 수 있다. 사람이 두 개의 로봇 행동을 비교하여 어느 쪽이 더 안전하고, 부드럽고, 효율적인지를 선택하면, 보상 모델(Reward Model)은 이러한 선호 데이터를 이용하여 적절한 보상을 학습할 수 있다.

모방 학습(Imitation Learning)은 복잡한 보상 설계의 부담을 줄일 수 있다. 숙련자의 시연(Demonstration)을 통해 바람직한 행동을 먼저 학습하고, 이후 강화 학습을 통해 정책을 더욱 개선하면서 전문가의 행동 특성을 유지할 수 있다.

시뮬레이션(Simulation)은 실제 로봇에 적용하기 전에 MDP와 보상 설계를 검증하는 가장 중요한 도구이다. 다양한 경로를 시각화하고, 보상 요소를 비교하며, 의도하지 않은 전략을 발견하고, 드문 실패 상황까지 생성할 수 있다. 이를 통해 위험한 정책을 실제 장비에 적용하기 전에 제거할 수 있다.

도메인 랜덤화(Domain Randomization)는 마찰, 질량, 센서 노이즈, 장애물 행동, 조명, 통신 지연, 지형 등을 지속적으로 변경하면서 학습하는 방법이다. 그 결과 하나의 환경이 아니라 다양한 환경을 포함하는 MDP가 만들어지며, 시뮬레이션에서 실제 환경으로의 이전 성능이 향상된다.

오프라인 강화 학습(Offline Reinforcement Learning)은 기존에 수집된 데이터셋(Dataset)을 이용하여 정책을 학습한다. 저장된 주행 데이터를 이용해 보상을 다시 계산할 수 있으며, 위험한 탐험 없이 실제 운용 데이터를 활용할 수 있다는 점에서 AMR에 매우 적합하다.

그러나 오프라인 강화 학습은 데이터셋의 범위에 제한된다. 학습 데이터에 거의 존재하지 않는 행동을 선택하면 정책의 신뢰성이 크게 떨어질 수 있다. 따라서 기존 경험을 크게 벗어나지 않도록 하는 보수적 학습(Conservative Learning)이 함께 적용된다.

보상 평가는 평균 반환값(Average Return)만으로 수행해서는 안 된다. 평균 성능이 높더라도 드물게 발생하는 치명적인 실패는 산업 현장에서 허용될 수 없다. 충돌률, 근접 사고, 시간 초과, 에너지 소비, 사람의 개입 횟수, 경로 효율, 비정상 상황에서의 성능 등을 함께 평가해야 한다.

민감도 분석(Sensitivity Analysis)은 보상 가중치, 할인 계수, 전이 확률의 노이즈, 초기 상태 등을 변경했을 때 정책이 얼마나 안정적으로 유지되는지를 분석하는 과정이다. 작은 변화에도 행동이 크게 변한다면 MDP나 보상 설계가 충분히 안정적이지 않음을 의미한다.

보상 함수는 제품의 전체 수명 주기(Product Lifecycle) 동안 운영 요구사항과 일치해야 한다. 로봇의 적재 중량, 속도, 작업 환경, 고객 프로세스, 안전 정책이 변경되면 기존 보상 설계도 다시 검토되어야 한다. 따라서 보상 정의와 평가 시나리오는 버전 관리(Version Control)를 수행하는 것이 바람직하다.

실제 운영 환경에서는 보상과 관련된 이상 현상을 지속적으로 모니터링해야 한다. 실제 로봇은 학습 시의 보상을 직접 계산하지 않더라도 이에 대응되는 운영 지표를 기록할 수 있다. 이러한 지표의 변화는 모델 드리프트(Model Drift), 환경 변화, 또는 새로운 안전 문제를 조기에 발견하는 데 도움이 된다.

따라서 MDP 모델링과 보상 설계는 단순히 강화 학습 알고리즘을 선택하기 위한 준비 과정이 아니다. 이는 학습해야 할 문제 자체를 정의하는 핵심 과정이다. 상태, 행동, 상태 전이, 보상 모델이 올바르게 설계되지 않으면 아무리 우수한 강화 학습 알고리즘이라도 신뢰성 있는 정책을 만들어낼 수 없다.

자율이동로봇에서는 성공적인 MDP가 물리적 환경, 임무 목표, 안전 경계, 환경의 불확실성, 행동의 장기적인 영향을 모두 적절하게 표현해야 한다. 또한 보상 함수는 높은 성능을 유도하면서도 위험한 지름길이나 지나치게 보수적인 행동을 만들지 않도록 설계되어야 한다.

가장 효과적인 설계는 수학적 모델링(Formal Modeling), 시뮬레이션(Simulation), 전문가 지식(Expert Knowledge), 현장 데이터(Field Data), 안전 공학(Safety Engineering), 지속적인 검증(Continuous Validation)을 함께 활용하는 것이다. 이러한 통합적인 접근을 통해 강화 학습은 시뮬레이션에서뿐만 아니라 실제 로봇 환경에서도 안정적이고 이해 가능하며 신뢰할 수 있는 정책을 학습할 수 있다.

##  

## 09.3 RL for Navigation

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Reinforcement learning for navigation applies experience-driven decision making to the movement of autonomous robots through complex environments. Instead of relying only on fixed rules, the robot learns a policy that maps observations or states to motion decisions that maximize long-term mission performance.

Navigation is naturally a sequential decision problem. A movement command changes the robot's position, orientation, speed, and future options. A decision that appears efficient at one moment may create congestion, increase collision risk, or lead the robot into a dead end several steps later.

Traditional navigation systems usually separate global path planning, local obstacle avoidance, and motion control. Reinforcement learning can improve one of these components or learn a combined navigation strategy. In practical systems, it is often integrated with classical planners rather than used as a complete replacement.

The agent in a navigation problem is the robot or the learned navigation policy. The environment includes the map, obstacles, pedestrians, vehicles, terrain, traffic rules, and other robots. The agent observes the environment, selects an action, receives a reward, and repeats this interaction.

The state represents information needed for navigation decisions. It may contain the robot pose, velocity, goal direction, remaining distance, obstacle locations, local map, planned route, battery condition, and nearby traffic. The quality of this state representation strongly affects the learned behavior.

A compact state may use the relative angle and distance to the goal together with a sequence of LiDAR measurements. This representation is computationally efficient and commonly used for local navigation experiments. However, it may not provide enough semantic context for complex industrial environments.

A richer state can include camera images, depth data, semantic maps, human motion estimates, and predicted obstacle trajectories. Deep neural networks can extract useful features from these high-dimensional inputs, but training becomes more expensive and requires greater data diversity.

The robot may also receive incomplete observations rather than a complete state. Obstacles can be hidden behind walls, people may suddenly enter the path, and sensors may have limited range. Navigation is therefore often closer to a partially observable decision process than a fully observable one.

Memory helps the agent reason under partial observability. Recurrent networks, temporal transformers, occupancy histories, or short sequences of sensor frames can capture how the environment has changed. This allows the robot to distinguish between stationary structures and moving objects.

The action space determines what the reinforcement learning policy controls. A discrete policy may choose actions such as move forward, rotate left, rotate right, slow down, stop, or reverse. Discrete actions simplify training but may create abrupt or inefficient motion.

A continuous policy can directly generate linear velocity, angular velocity, steering angle, acceleration, or wheel torque. This provides smoother control and allows more precise responses. Continuous action spaces are often used with policy-gradient or actor-critic algorithms.

In many AMR systems, reinforcement learning does not directly control motors. Instead, the policy outputs a desired velocity, local waypoint, or short trajectory. A conventional controller then converts this command into wheel or steering control while enforcing actuator limits and stability requirements.

This layered structure separates learned decision making from deterministic control. It reduces the risk that the policy will generate physically impossible commands. It also allows proven low-level control software to remain in use while the navigation intelligence is improved.

The reward function defines the behavior the robot is encouraged to learn. A positive reward is usually assigned for reaching the destination. Negative rewards may be assigned for collisions, unsafe proximity, excessive travel time, unnecessary rotation, energy consumption, or mission failure.

Progress toward the destination often provides a dense reward. The robot receives a small positive value when its distance to the goal decreases and a penalty when it moves away. This gives frequent learning feedback, but it can also encourage shortsighted behavior around obstacles.

For example, a robot may repeatedly approach a wall because the goal lies directly behind it. Although each step reduces the straight-line distance, the robot does not learn to take the necessary detour. Reward design must therefore account for feasible paths rather than only geometric distance.

Collision penalties are normally large because safety is more important than small improvements in travel time. However, a collision penalty alone may not be sufficient. The policy should also be discouraged from near misses, sudden braking, oscillation, and uncomfortable proximity to people.

Smoothness rewards can penalize rapid changes in linear or angular velocity. These terms improve ride quality, reduce mechanical stress, and make robot behavior easier for humans to predict. Excessive smoothness penalties, however, may prevent the robot from reacting quickly in emergencies.

Time penalties encourage efficient motion by assigning a small cost at every step. The robot then learns that unnecessarily long episodes reduce total return. If the time penalty is too strong, the policy may choose aggressive shortcuts that reduce safety margins.

Energy-aware rewards can discourage frequent acceleration, excessive turning, wheel slip, or unnecessary detours. Such rewards are valuable for battery-powered AMRs that must complete many missions before charging. Energy optimization must remain subordinate to safety and mission completion.

Social navigation requires additional reward terms. The robot may be encouraged to maintain personal space, avoid passing too closely, approach people from visible directions, and move consistently with local traffic flow. Human comfort cannot be represented only by collision avoidance.

A successful reward function balances goal achievement, safety, efficiency, smoothness, and operational rules. Each term should be logged separately during training. A high total reward may otherwise hide poor performance in one critical safety component.

The policy determines how actions are selected from the current state. A deterministic policy always produces the same action for the same input. A stochastic policy produces a probability distribution, supporting exploration and allowing several valid responses to similar situations.

Value-based methods estimate how beneficial each action is in a given state. Q-learning and Deep Q-Networks are common examples for discrete navigation problems. They can learn effective obstacle avoidance, but they become difficult to apply when the action space is large or continuous.

Policy-gradient methods directly optimize the parameters of the navigation policy. They are suitable for continuous motion control and stochastic policies. However, their gradient estimates may have high variance and may require many environment interactions.

Actor-critic methods combine a policy model with a value estimator. The actor selects navigation actions, while the critic evaluates their expected long-term return. Algorithms such as PPO, SAC, TD3, and A2C are widely used in simulated robotic navigation research.

Proximal Policy Optimization is popular because it offers relatively stable updates and is straightforward to implement. Soft Actor-Critic is useful for continuous control and encourages exploration through entropy. The best algorithm depends on the state, action, reward, and training environment.

Model-based reinforcement learning learns or uses a model of environmental dynamics. The robot can predict how actions may change its state and plan using simulated future outcomes. This approach can improve sample efficiency but becomes difficult when human and obstacle behavior is highly uncertain.

Global navigation decides how to move across a large map from a start point to a distant goal. Classical algorithms such as A\* or Dijkstra remain reliable for this task. Reinforcement learning can help select routes based on congestion, energy, risk, or long-term fleet conditions.

A learned global policy may choose among several corridors or zones rather than directly generating every motion command. It can avoid frequently blocked areas, select elevators, prefer safer crossings, and adapt routes according to mission priority or battery state.

Local navigation reacts to nearby obstacles and converts the global route into immediate motion. This is a common target for reinforcement learning because local environments are dynamic and difficult to model with fixed rules. The policy can learn flexible avoidance behaviors from repeated experience.

The local policy may receive a LiDAR scan, relative goal vector, current velocity, and previous action. It then outputs the next velocity command. Training episodes expose the policy to walls, corners, narrow passages, moving obstacles, and different goal locations.

Dynamic obstacle avoidance requires predicting how nearby objects may move. A purely reactive policy may avoid the current position of a pedestrian but fail to account for the person's future trajectory. Temporal observations and trajectory prediction can improve decision quality.

The robot should not only avoid collision but also avoid creating conflict. Entering a narrow passage at the wrong time may force another robot to stop or reverse. Reinforcement learning can learn yielding, waiting, and negotiation behaviors when these outcomes are represented in the reward.

Multi-robot navigation extends the problem from one agent to several agents sharing the same environment. Each robot's action changes the conditions faced by the others. This creates a non-stationary learning problem because the behavior of other agents may evolve during training.

Centralized training with decentralized execution is frequently used for multi-robot reinforcement learning. During training, a centralized critic can access information about all robots. During operation, each robot selects actions using only locally available observations and shared messages.

Fleet-level rewards can encourage total throughput, balanced traffic, low congestion, and fair task distribution. However, purely global rewards may make it difficult for an individual robot to understand how its actions affected the result. Credit assignment becomes a major challenge.

Communication can improve cooperative navigation. Robots may share intended paths, local obstacle information, right-of-way requests, and estimated arrival times. Reinforcement learning can determine when communication is useful and how shared information should influence motion decisions.

Navigation policies are usually trained in simulation because real-world exploration is slow and unsafe. A simulator can generate millions of interactions involving collisions, blocked routes, sensor errors, and unusual traffic patterns without damaging physical hardware.

Simulation should reproduce the robot's kinematics, sensor field of view, actuator delay, acceleration limits, and collision geometry. Unrealistic simulation may produce policies that perform well virtually but fail when deployed on the physical platform.

Domain randomization varies environmental and robot parameters during training. Friction, mass, payload, sensor noise, latency, obstacle speed, lighting, and map layout can be changed across episodes. The policy learns to handle a distribution of conditions rather than one fixed simulator.

Procedural environment generation can create many different maps automatically. Training in only a small number of layouts often causes memorization. Random rooms, corridors, intersections, shelves, slopes, and obstacle placements improve generalization to unseen environments.

Curriculum learning begins with simple navigation tasks and gradually increases difficulty. The robot may first learn to reach goals in open space, then avoid static obstacles, pass through narrow corridors, and finally handle dense moving traffic.

A curriculum can significantly reduce training time because the policy develops basic skills before facing complex situations. However, the transition between difficulty levels must be managed carefully to prevent the agent from forgetting previously learned behavior.

Imitation learning can initialize the policy using demonstrations from a classical planner or human operator. The robot first learns to reproduce reasonable navigation behavior. Reinforcement learning then improves the policy through interaction and reward optimization.

This combination reduces unsafe random exploration and improves sample efficiency. It is particularly useful when good navigation logs already exist. Demonstrations should include difficult and recovery situations rather than only successful nominal trajectories.

Offline reinforcement learning can train from recorded navigation data without additional online interaction. Historical AMR logs may contain states, actions, next states, and mission outcomes. Rewards can be reconstructed from collision, travel time, energy, and safety records.

The main limitation of offline learning is incomplete coverage. The dataset may not contain enough examples of rare hazards or unusual actions. A policy that moves outside the recorded behavior distribution may produce unreliable predictions and unsafe decisions.

Safe reinforcement learning introduces explicit limits on risk. The policy may optimize navigation efficiency while maintaining constraints on collision probability, speed, braking distance, or human proximity. Safety constraints are more reliable than expressing every requirement as a reward weight.

A learned navigation policy should always operate within an independent safety architecture. Safety LiDAR, emergency stops, speed monitoring, protective fields, geofences, and certified safety controllers must be able to override the learned command when necessary.

A safety shield can inspect the action proposed by the policy before execution. If the action violates a constraint, the shield replaces it with a safe alternative such as braking or reducing speed. This allows learning-based navigation without giving the policy unrestricted control.

Fallback behavior is necessary when sensor inputs are invalid or the policy becomes uncertain. The robot may stop, return to a classical planner, reduce speed, request remote assistance, or enter a degraded mode. A policy should never be the only available decision mechanism.

Uncertainty estimation helps determine when the policy is outside its training distribution. Ensemble models, Bayesian approximations, observation-distance measures, or confidence predictors can detect unfamiliar states. High uncertainty should trigger conservative actions or fallback control.

Sim-to-real transfer remains one of the greatest challenges. Real sensors contain noise, missing data, reflections, motion distortion, and calibration errors. Real humans and vehicles also behave less predictably than simulated agents.

Fine-tuning on real data can reduce the simulation gap, but online exploration must be tightly controlled. A practical strategy is to deploy the policy in shadow mode, compare its proposed actions with the existing navigation stack, and collect disagreement cases before activation.

Shadow-mode evaluation allows engineers to measure what the learned policy would have done without giving it control. High-risk disagreements can be reviewed and added to future training scenarios. This creates a safer path from simulation to production deployment.

Navigation evaluation should include more than success rate. Important metrics include collision rate, minimum obstacle distance, travel time, path length, energy use, intervention frequency, motion smoothness, deadlock rate, and recovery performance.

Performance should be measured across easy, difficult, and adversarial scenarios. Narrow passages, sudden pedestrian entry, sensor dropout, localization jumps, communication loss, slippery surfaces, blocked routes, and dense robot traffic should all be tested.

Generalization should be evaluated on maps and obstacle configurations that were not used during training. A policy that performs well only on familiar layouts has learned memorized patterns rather than transferable navigation principles.

Long-duration testing is also important. Small oscillations or inefficient choices may appear harmless in short episodes but create energy loss, mechanical wear, congestion, or repeated mission delays during continuous operation.

Explainability is difficult because deep reinforcement learning policies may not provide clear reasons for their actions. Engineers can analyze attention maps, state sensitivity, value estimates, trajectory comparisons, and counterfactual scenarios to understand policy behavior.

Logging is essential for field deployment. Sensor inputs, policy outputs, safety overrides, confidence values, reward-related metrics, and final executed commands should be recorded. These logs support debugging, incident analysis, and controlled policy improvement.

Navigation environments change over time. New shelves, construction zones, seasonal weather, worn floors, and different pedestrian patterns can reduce policy performance. Continuous monitoring is needed to detect distribution shift and emerging failure cases.

Policy updates should follow a controlled validation process. A new model must be tested in simulation, replayed on recorded data, evaluated in shadow mode, and deployed gradually. Rollback must be possible when performance or safety metrics deteriorate.

Reinforcement learning is most effective when it complements reliable navigation engineering. Classical global planners offer predictability, while learned local policies can provide adaptation in complex situations. Safety controllers enforce non-negotiable physical constraints.

A hybrid architecture may use A\* for global route planning, reinforcement learning for local motion selection, a model predictive controller for trajectory tracking, and an independent safety layer for collision prevention. Each component addresses the problem at an appropriate level.

Such separation improves interpretability and makes validation more manageable. It also allows the learned policy to be replaced or updated without redesigning the entire navigation stack. Production AMRs generally benefit from this modular approach.

Reinforcement learning can provide significant advantages when navigation involves uncertainty, dynamic interaction, and competing long-term objectives. It can learn behaviors that are difficult to express through manually designed rules, including yielding, adaptive speed selection, and congestion-aware routing.

However, high simulated reward does not automatically imply safe real-world navigation. Reliable deployment requires careful state design, realistic action limits, aligned rewards, diverse training scenarios, uncertainty monitoring, independent safety systems, and continuous field validation.

The long-term role of reinforcement learning in AMR navigation is therefore not simply to replace planners. Its deeper value is to add adaptive decision making to a structured autonomous system, allowing robots to learn from experience while remaining constrained by physical, operational, and safety requirements.

강화 학습 기반 내비게이션(Reinforcement Learning for Navigation)은 경험 기반 의사결정을 자율 로봇의 이동에 적용하는 기술이다. 로봇은 고정된 규칙에만 의존하지 않고, 환경과의 상호작용을 통해 장기적인 임무 성능을 최대화하는 정책(Policy)을 학습한다.

내비게이션(Navigation)은 본질적으로 순차적 의사결정(Sequential Decision Making) 문제이다. 하나의 이동 명령은 로봇의 위치(Position), 방향(Orientation), 속도(Velocity), 그리고 이후 선택 가능한 행동에 영향을 미친다. 현재는 효율적으로 보이는 결정이라도 이후에는 혼잡, 충돌 위험, 또는 막다른 길로 이어질 수 있다.

기존 내비게이션 시스템은 일반적으로 전역 경로 계획(Global Path Planning), 지역 장애물 회피(Local Obstacle Avoidance), 그리고 모션 제어(Motion Control)를 각각 독립적으로 수행한다. 강화 학습은 이러한 구성 요소 중 하나를 개선하거나, 여러 기능을 통합한 내비게이션 전략을 학습할 수 있다. 실제 시스템에서는 기존 알고리즘을 완전히 대체하기보다는 함께 사용하는 경우가 많다.

내비게이션 문제에서 에이전트(Agent)는 로봇 자체 또는 학습된 내비게이션 정책이다. 환경(Environment)은 지도(Map), 장애물(Obstacle), 보행자(Pedestrian), 차량(Vehicle), 지형(Terrain), 교통 규칙(Traffic Rules), 그리고 다른 로봇들을 포함한다. 에이전트는 환경을 관찰하고 행동(Action)을 선택한 뒤 보상(Reward)을 받으며 이러한 과정을 반복한다.

상태(State)는 내비게이션 의사결정에 필요한 정보를 표현한다. 여기에는 로봇의 위치와 자세(Pose), 속도, 목표 방향, 남은 거리, 장애물 위치, 지역 지도(Local Map), 계획된 경로, 배터리 상태, 주변 교통 상황 등이 포함될 수 있다. 상태 표현의 품질은 학습된 정책의 성능을 크게 좌우한다.

간단한 상태 표현은 목표까지의 상대 거리와 방향, 그리고 라이다(LiDAR) 거리 측정값만 사용할 수도 있다. 이러한 방식은 계산량이 적고 지역 내비게이션 연구에서 자주 사용된다. 그러나 복잡한 산업 환경에서는 충분한 의미 정보를 제공하지 못할 수 있다.

더 풍부한 상태 표현은 카메라(Camera) 영상, 깊이 정보(Depth Data), 의미 지도(Semantic Map), 사람의 이동 예측, 장애물의 미래 궤적 등을 포함할 수 있다. 심층 신경망(Deep Neural Network)은 이러한 고차원 입력에서 유용한 특징을 추출할 수 있지만, 학습 비용과 데이터 요구량이 크게 증가한다.

로봇은 항상 완전한 상태를 관찰할 수 있는 것은 아니다. 장애물이 벽 뒤에 숨어 있을 수도 있고, 사람이 갑자기 나타날 수도 있으며, 센서의 탐지 범위도 제한적이다. 따라서 실제 내비게이션은 완전 관측보다 부분 관측(Partial Observation)에 더 가까운 경우가 많다.

메모리(Memory)는 부분 관측 환경에서 매우 중요한 역할을 한다. 순환 신경망(Recurrent Neural Network), 시계열 트랜스포머(Temporal Transformer), 점유 이력(Occupancy History), 또는 연속적인 센서 프레임을 이용하면 환경의 변화를 기억할 수 있다. 이를 통해 로봇은 정적인 구조물과 움직이는 객체를 구별할 수 있다.

행동 공간(Action Space)은 강화 학습 정책이 무엇을 제어하는지를 결정한다. 이산형 정책(Discrete Policy)은 전진, 좌회전, 우회전, 감속, 정지, 후진과 같은 행동을 선택한다. 구현은 단순하지만 움직임이 부자연스럽거나 비효율적일 수 있다.

연속형 정책(Continuous Policy)은 선속도(Linear Velocity), 각속도(Angular Velocity), 조향각(Steering Angle), 가속도(Acceleration), 휠 토크(Wheel Torque) 등을 직접 생성한다. 보다 부드럽고 정밀한 제어가 가능하며, 일반적으로 정책 경사(Policy Gradient) 또는 액터-크리틱(Actor-Critic) 계열 알고리즘과 함께 사용된다.

많은 AMR 시스템에서는 강화 학습이 모터를 직접 제어하지 않는다. 대신 원하는 속도(Velocity), 지역 웨이포인트(Local Waypoint), 또는 짧은 궤적(Trajectory)을 생성한다. 이후 기존의 제어기가 이를 실제 휠 제어나 조향 명령으로 변환하면서 액추에이터의 물리적 한계를 보장한다.

이러한 계층 구조는 학습 기반 의사결정과 결정론적 제어를 분리한다. 이를 통해 정책이 물리적으로 불가능한 명령을 생성하는 위험을 줄일 수 있으며, 이미 검증된 저수준 제어 소프트웨어를 그대로 유지하면서 내비게이션 지능만 향상시킬 수 있다.

보상 함수(Reward Function)는 로봇이 어떤 행동을 학습해야 하는지를 정의한다. 일반적으로 목적지 도착에는 큰 양의 보상을 부여하며, 충돌, 위험한 근접, 긴 이동 시간, 불필요한 회전, 과도한 에너지 소비, 임무 실패에는 음의 보상을 부여한다.

목적지까지의 거리 감소는 흔히 밀집 보상(Dense Reward)으로 사용된다. 로봇은 목표에 가까워질 때마다 작은 보상을 받고 멀어질 때는 패널티(Penalty)를 받는다. 이는 학습을 빠르게 하지만 장애물 주변에서 잘못된 행동을 유도할 수도 있다.

예를 들어 목적지가 벽 뒤에 있는 경우, 로봇은 벽을 향해 계속 접근하는 것이 보상을 증가시키므로 우회 경로를 선택하지 못할 수도 있다. 따라서 보상 설계는 단순한 직선 거리뿐 아니라 실제 이동 가능한 경로까지 고려해야 한다.

충돌 패널티는 일반적으로 매우 크게 설정된다. 안전성은 이동 시간보다 훨씬 중요하기 때문이다. 그러나 단순한 충돌 패널티만으로는 충분하지 않다. 사람과의 근접 통과, 급제동, 진동(Oscillation), 사람에게 불편함을 주는 행동도 함께 억제해야 한다.

부드러운 주행(Smooth Motion)에 대한 보상은 선속도와 각속도의 급격한 변화를 줄이는 역할을 한다. 이는 승차감을 향상시키고 기계적 마모를 줄이며 사람에게 예측 가능한 움직임을 제공한다. 반면 지나치게 큰 부드러움 보상은 긴급 상황에서 빠른 회피를 방해할 수도 있다.

시간 패널티(Time Penalty)는 매 스텝마다 작은 비용을 부여하여 효율적인 이동을 유도한다. 그러나 시간 패널티가 너무 크면 로봇은 안전성을 희생하면서까지 가장 빠른 경로만 선택하려고 할 수 있다.

에너지 기반 보상(Energy-Aware Reward)은 급가속, 과도한 회전, 바퀴 미끄러짐, 불필요한 우회를 줄이는 데 사용된다. 이는 배터리 기반 AMR에서 매우 중요하지만, 에너지 절감은 항상 안전성과 임무 수행보다 우선되어서는 안 된다.

사회적 내비게이션(Social Navigation)은 추가적인 보상 요소가 필요하다. 로봇은 사람과 적절한 개인 공간(Personal Space)을 유지하고, 시야가 확보된 방향에서 접근하며, 주변 사람들의 이동 흐름과 조화를 이루도록 학습해야 한다. 이는 단순한 충돌 회피만으로는 구현할 수 없다.

성공적인 보상 함수는 목표 달성, 안전성, 효율성, 부드러운 움직임, 운영 규칙을 균형 있게 고려해야 한다. 각 보상 항목은 학습 과정에서 개별적으로 기록하고 분석해야 한다. 총 보상이 높더라도 특정 안전 항목의 성능이 낮을 수 있기 때문이다.

정책(Policy)은 현재 상태에서 어떤 행동을 선택할지를 결정한다. 결정론적 정책(Deterministic Policy)은 항상 동일한 행동을 선택하고, 확률적 정책(Stochastic Policy)은 여러 행동에 확률을 부여한다. 확률적 정책은 탐험(Exploration)에 유리하다.

가치 기반(Value-Based) 알고리즘은 각 행동의 가치를 추정한다. 대표적으로 Q-러닝(Q-Learning)과 심층 Q 네트워크(Deep Q-Network, DQN)가 있다. 이러한 알고리즘은 이산 행동 공간에서는 효과적이지만 연속 행동 공간에서는 적용이 어려워진다.

정책 경사(Policy Gradient) 알고리즘은 정책 자체를 직접 최적화한다. 연속 제어에 적합하지만 기울기(Gradient)의 분산이 커질 수 있으며 많은 학습 데이터가 필요하다.

액터-크리틱(Actor-Critic) 알고리즘은 정책과 가치 추정기를 함께 사용한다. 액터(Actor)는 행동을 생성하고, 크리틱(Critic)은 장기적인 반환값(Return)을 평가한다. PPO, SAC, TD3, A2C와 같은 알고리즘은 로봇 내비게이션 연구에서 널리 활용된다.

근접 정책 최적화(Proximal Policy Optimization, PPO)는 비교적 안정적인 학습 특성 때문에 널리 사용된다. 소프트 액터 크리틱(Soft Actor-Critic, SAC)은 연속 제어에 적합하며 엔트로피(Entropy)를 활용하여 탐험 능력을 향상시킨다. 어떤 알고리즘이 가장 적합한지는 상태, 행동, 보상, 환경에 따라 달라진다.

모델 기반 강화 학습(Model-Based Reinforcement Learning)은 환경의 동역학 모델을 학습하거나 활용한다. 로봇은 행동 이후의 미래 상태를 예측하면서 계획을 수행할 수 있다. 이는 데이터 효율성을 높일 수 있지만 사람이나 이동 장애물처럼 예측이 어려운 환경에서는 모델 구축이 쉽지 않다.

전역 내비게이션(Global Navigation)은 시작 위치에서 먼 목적지까지 이동하는 문제를 해결한다. A\*(A-Star), 다익스트라(Dijkstra)와 같은 기존 알고리즘은 여전히 매우 신뢰성이 높다. 강화 학습은 혼잡도, 에너지 소비, 위험도, 차량 흐름 등을 고려한 경로 선택을 개선하는 데 활용될 수 있다.

학습된 전역 정책은 모든 이동 명령을 생성하는 대신, 여러 개의 통로 가운데 하나를 선택하거나 엘리베이터를 이용하거나, 위험 지역을 우회하거나, 배터리 상태에 따라 경로를 변경하는 등의 고수준 의사결정을 수행할 수 있다.

지역 내비게이션(Local Navigation)은 주변 장애물을 회피하면서 전역 경로를 실제 움직임으로 변환한다. 동적인 환경에서는 기존 규칙 기반 알고리즘보다 강화 학습이 더 유연한 회피 전략을 학습할 수 있다.

지역 정책은 라이다 스캔(LiDAR Scan), 목표 방향, 현재 속도, 이전 행동 등을 입력받아 다음 속도 명령을 생성할 수 있다. 학습 과정에서는 벽, 모서리, 좁은 통로, 이동 장애물 등 다양한 상황을 반복적으로 경험한다.

동적 장애물 회피(Dynamic Obstacle Avoidance)는 장애물의 미래 움직임까지 고려해야 한다. 단순히 현재 위치만 회피하는 정책은 보행자의 이동 방향을 고려하지 못한다. 따라서 시계열 정보와 궤적 예측(Trajectory Prediction)이 함께 활용된다.

로봇은 단순히 충돌을 피하는 것뿐 아니라 다른 로봇이나 사람의 움직임을 방해하지 않아야 한다. 좁은 통로에서 먼저 양보하거나 잠시 대기하는 행동도 강화 학습을 통해 학습할 수 있다.

다중 로봇 내비게이션(Multi-Robot Navigation)은 여러 대의 로봇이 동일한 공간을 공유하는 문제이다. 하나의 로봇 행동은 다른 로봇의 상태에도 영향을 미치므로 환경 자체가 계속 변화하는 비정상성(Non-Stationarity)을 가진다.

중앙집중형 학습과 분산 실행(Centralized Training with Decentralized Execution)은 이러한 문제를 해결하는 대표적인 방법이다. 학습 시에는 모든 로봇의 정보를 활용하지만, 실제 운용 시에는 각 로봇이 자신의 센서와 공유된 정보만을 이용하여 의사결정을 수행한다.

플릿(Fleet) 수준의 보상은 전체 처리량, 교통 혼잡 감소, 작업 균형 등을 최적화할 수 있다. 그러나 개별 로봇이 자신의 행동이 전체 성과에 어떤 영향을 미쳤는지를 학습하기 어렵다는 문제가 존재한다.

로봇 간 통신(Communication)은 협력 내비게이션을 향상시킨다. 계획된 경로, 장애물 정보, 통행 우선권 요청, 예상 도착 시간을 공유함으로써 보다 효율적인 이동이 가능하다. 강화 학습은 이러한 정보가 언제 필요한지도 함께 학습할 수 있다.

대부분의 내비게이션 정책은 시뮬레이션(Simulation)에서 학습된다. 실제 환경에서 수백만 번의 탐험을 수행하는 것은 비용이 크고 위험하기 때문이다. 시뮬레이션은 다양한 충돌, 막힌 경로, 센서 오류, 비정상 상황을 안전하게 생성할 수 있다.

시뮬레이터는 로봇의 운동학(Kinematics), 센서 시야(Field of View), 액추에이터 지연, 가속도 제한, 충돌 모델 등을 현실적으로 반영해야 한다. 그렇지 않으면 시뮬레이션에서는 성공하지만 실제 환경에서는 실패하는 정책이 만들어질 수 있다.

도메인 랜덤화(Domain Randomization)는 마찰, 질량, 적재 중량, 센서 노이즈, 통신 지연, 장애물 속도, 조명 등을 지속적으로 변경하며 학습하는 방법이다. 이를 통해 정책은 다양한 환경에 적응할 수 있게 된다.

절차적 환경 생성(Procedural Environment Generation)은 다양한 지도와 장애물 배치를 자동으로 생성한다. 동일한 환경만 반복 학습하면 단순 암기(Memorization)가 발생할 수 있으므로 새로운 구조를 지속적으로 생성하는 것이 중요하다.

커리큘럼 학습(Curriculum Learning)은 쉬운 문제부터 어려운 문제까지 단계적으로 학습을 진행한다. 처음에는 장애물이 없는 공간에서 목표 도달을 학습하고, 이후 좁은 통로, 움직이는 장애물, 복잡한 교통 환경으로 점진적으로 난이도를 높인다.

커리큘럼 학습은 학습 시간을 크게 줄일 수 있지만, 난이도 변화가 너무 급격하면 이전에 학습한 능력을 잊어버릴 수도 있다.

모방 학습(Imitation Learning)은 기존의 경로 계획기나 사람의 시연(Demonstration)을 이용하여 초기 정책을 생성할 수 있다. 이후 강화 학습이 이를 더욱 개선하여 성능을 향상시킨다.

이러한 방식은 무작위 탐험을 줄이고 데이터 효율성을 높인다. 특히 이미 많은 주행 데이터가 존재하는 산업용 AMR에서 매우 효과적이다.

오프라인 강화 학습(Offline Reinforcement Learning)은 기존의 운행 로그(Log)를 이용하여 정책을 학습한다. 충돌 기록, 이동 시간, 에너지 소비, 안전 정보 등을 기반으로 보상을 다시 계산할 수 있다.

그러나 데이터셋(Dataset)에 포함되지 않은 희귀한 상황에서는 성능이 크게 저하될 수 있다. 따라서 기존 데이터의 범위를 크게 벗어나지 않도록 하는 보수적 학습(Conservative Learning)이 필요하다.

안전 강화 학습(Safe Reinforcement Learning)은 위험에 대한 명시적인 제약 조건을 포함한다. 충돌 확률, 속도 제한, 제동 거리, 사람과의 거리 등을 만족하면서 이동 효율을 최적화한다.

학습된 정책은 반드시 독립적인 안전 시스템 안에서 동작해야 한다. 안전 라이다(Safety LiDAR), 비상 정지(Emergency Stop), 속도 제한, 보호 구역(Protective Field), 지오펜스(Geofence), 인증된 안전 제어기 등이 항상 우선적으로 동작해야 한다.

안전 실드(Safety Shield)는 정책이 생성한 행동을 실행 전에 검사한다. 위험한 명령이면 자동으로 감속하거나 정지하도록 변경한다. 이를 통해 강화 학습 정책이 전체 시스템을 직접 지배하지 않도록 한다.

센서 오류나 정책의 불확실성이 높아질 경우에는 백업 동작(Fallback Behavior)이 필요하다. 로봇은 정지하거나, 기존 경로 계획기로 전환하거나, 속도를 낮추거나, 원격 지원을 요청하는 방식으로 안전성을 확보해야 한다.

불확실성 추정(Uncertainty Estimation)은 현재 상황이 학습 범위를 벗어났는지를 판단하는 데 사용된다. 앙상블 모델(Ensemble Model), 베이지안(Bayesian) 기법, 신뢰도 예측 등을 이용하여 위험 상황을 탐지할 수 있다.

시뮬레이션에서 실제 환경으로 이전(Sim-to-Real Transfer)은 여전히 가장 어려운 문제 가운데 하나이다. 실제 센서는 노이즈, 반사, 데이터 누락, 왜곡, 보정 오차를 포함하며, 사람과 차량의 행동도 시뮬레이션보다 훨씬 예측하기 어렵다.

실제 데이터를 이용한 미세 조정(Fine-Tuning)은 성능을 향상시킬 수 있지만, 온라인 탐험은 엄격히 제한되어야 한다. 일반적으로는 기존 내비게이션 시스템과 정책을 동시에 실행하는 섀도우 모드(Shadow Mode)를 먼저 사용한다.

섀도우 모드는 실제 제어는 기존 시스템이 수행하고, 강화 학습 정책은 무엇을 했을지를 기록한다. 두 시스템이 크게 다른 판단을 내린 상황을 분석하여 이후 학습 데이터에 추가할 수 있다.

내비게이션 평가는 성공률만으로 수행해서는 안 된다. 충돌률, 최소 장애물 거리, 이동 시간, 경로 길이, 에너지 소비, 사람의 개입 횟수, 움직임의 부드러움, 교착 상태(Deadlock), 복구 능력 등을 함께 평가해야 한다.

쉬운 환경뿐 아니라 어려운 환경과 적대적 환경(Adversarial Scenario)에서도 평가해야 한다. 좁은 통로, 갑작스러운 보행자 등장, 센서 오류, 위치 추정 실패, 통신 장애, 미끄러운 노면, 막힌 경로, 높은 교통 밀도 등을 포함해야 한다.

학습에 사용되지 않은 새로운 지도에서도 일반화(Generalization) 성능을 반드시 평가해야 한다. 특정 지도에서만 잘 동작한다면 진정한 내비게이션 능력을 학습한 것이 아니라 단순히 환경을 암기한 것이다.

장시간 운용(Long-Term Operation) 테스트도 중요하다. 짧은 시간에는 문제가 없어 보이는 작은 진동이나 비효율적인 행동도 장기간 운용에서는 에너지 손실, 장비 마모, 교통 혼잡, 임무 지연을 유발할 수 있다.

설명 가능성(Explainability)은 심층 강화 학습에서 여전히 어려운 문제이다. 주의 지도(Attention Map), 상태 민감도, 가치 함수 분석, 경로 비교 등을 통해 정책의 의사결정을 이해하려는 연구가 진행되고 있다.

현장 운용에서는 로그(Logging)가 매우 중요하다. 센서 입력, 정책 출력, 안전 시스템 개입, 신뢰도, 실제 실행 명령 등을 모두 기록해야 디버깅과 사고 분석, 지속적인 정책 개선이 가능하다.

내비게이션 환경은 시간이 지나면서 계속 변화한다. 새로운 선반, 공사 구역, 계절 변화, 노면 마모, 보행 패턴 변화는 모두 정책 성능을 저하시킬 수 있다. 따라서 지속적인 모니터링이 필요하다.

새로운 정책은 반드시 단계적인 검증 절차를 거쳐야 한다. 시뮬레이션 검증, 기록 데이터 재생, 섀도우 모드 평가, 점진적 배포를 수행해야 하며, 문제가 발생하면 즉시 이전 버전으로 롤백(Rollback)할 수 있어야 한다.

강화 학습은 기존 내비게이션 기술을 대체하기보다는 보완하는 것이 가장 효과적이다. 기존 전역 경로 계획기는 높은 신뢰성을 제공하고, 강화 학습은 동적인 환경에서 적응 능력을 제공하며, 안전 제어기는 절대적인 안전을 보장한다.

대표적인 하이브리드(Hybrid) 구조는 A\*가 전역 경로를 생성하고, 강화 학습이 지역 이동을 결정하며, 모델 예측 제어(Model Predictive Control, MPC)가 실제 궤적을 추종하고, 독립적인 안전 계층이 충돌을 방지하는 방식이다.

이러한 계층적 구조는 시스템의 이해 가능성과 검증 가능성을 높여준다. 또한 전체 시스템을 다시 설계하지 않고도 강화 학습 정책만 교체하거나 개선할 수 있다. 실제 산업용 AMR은 대부분 이러한 모듈형 구조를 채택한다.

강화 학습은 불확실성, 동적인 상호작용, 장기적인 목표가 존재하는 내비게이션에서 큰 장점을 제공한다. 사람이 규칙으로 정의하기 어려운 양보 행동, 적응형 속도 조절, 혼잡 회피 경로 선택 등을 스스로 학습할 수 있다.

그러나 시뮬레이션에서 높은 보상을 얻었다고 해서 실제 환경에서도 안전한 내비게이션이 보장되는 것은 아니다. 신뢰성 있는 배포를 위해서는 적절한 상태 설계(State Design), 현실적인 행동 제한(Action Limit), 올바른 보상 설계(Reward Design), 다양한 학습 환경, 불확실성 모니터링, 독립적인 안전 시스템, 지속적인 현장 검증이 반드시 필요하다.

따라서 AMR 내비게이션에서 강화 학습의 장기적인 역할은 기존 경로 계획기를 완전히 대체하는 것이 아니다. 핵심 가치는 기존의 안정적인 자율주행 시스템 위에 경험 기반의 적응형 의사결정 능력을 추가하여, 로봇이 실제 환경에서 지속적으로 학습하고 발전하면서도 물리적 제약, 운영 요구사항, 그리고 안전 규정을 항상 만족하도록 만드는 데 있다.

##  

## 09.4 RL for Control

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Reinforcement learning for control applies experience-based learning to the generation of physical control actions. Instead of relying only on manually derived control laws, the agent learns how to regulate motion by interacting with a dynamic system and observing the effects of its commands over time.

Control problems differ from high-level planning because actions directly influence physical variables such as position, velocity, acceleration, torque, force, steering angle, and joint motion. Small errors can accumulate quickly, so the learned policy must react accurately, smoothly, and within strict timing limits.

In a reinforcement learning control system, the agent is usually the control policy. The environment includes the robot body, actuators, sensors, payload, terrain, external forces, and surrounding physical conditions. The agent observes the current state, selects a command, receives a reward, and updates its behavior.

The state should describe the physical condition of the system with enough detail to support stable control. It may include position, orientation, velocity, acceleration, joint angles, motor current, wheel speed, contact force, battery voltage, actuator temperature, and tracking error.

For an autonomous mobile robot, the state may contain linear velocity, angular velocity, steering angle, wheel rotation, chassis orientation, lateral error, heading error, and desired trajectory. For a manipulator, it may include joint positions, joint velocities, end-effector pose, and contact forces.

A complete state is not always directly available. Sensor delays, noise, mechanical backlash, wheel slip, unmeasured forces, and hidden contact conditions may create partial observability. The controller may therefore require state estimation, temporal memory, or sensor fusion before selecting an action.

Kalman filters, observers, recurrent networks, and learned latent-state models can reconstruct hidden variables. Accurate state estimation is especially important for high-speed control because even a small delay or estimation error can reduce stability and tracking accuracy.

The action space determines the level at which the policy controls the robot. At a high level, the policy may generate desired velocity or target position. At a lower level, it may produce torque, motor current, braking force, steering rate, or actuator voltage.

Direct torque control offers high flexibility because the policy can shape the physical behavior of the system in detail. However, it also increases risk. Incorrect torque commands may cause oscillation, instability, overheating, excessive force, or hardware damage.

For this reason, industrial reinforcement learning often uses an intermediate action interface. The policy generates a target velocity, acceleration, impedance, or short trajectory, while a conventional controller converts that target into safe actuator commands.

This separation preserves proven motor-control and servo-control functions. The learned policy handles adaptation and optimization, while deterministic low-level controllers enforce current limits, torque limits, velocity bounds, and actuator protection.

Continuous action spaces are common in control because physical commands are usually real-valued. Algorithms must therefore generate smooth numerical outputs rather than selecting from a small set of discrete actions. Actor-critic and policy-gradient methods are widely used for this purpose.

Discrete control can still be useful for mode selection. A policy may choose among accelerate, maintain speed, decelerate, stop, or reverse. Another controller then generates the exact continuous command required for the selected mode.

The reward function defines the desired control behavior. It may reward small tracking error, stable motion, low energy use, fast response, smooth acceleration, and successful task completion. It may penalize oscillation, excessive torque, wheel slip, impact, overheating, and unsafe states.

Tracking error is often the main reward component. The policy receives a higher reward when the robot follows the desired position, velocity, orientation, or trajectory closely. A simple error term is easy to design, but it may not fully represent control quality.

A controller that minimizes tracking error aggressively may use excessive torque or rapid actuator changes. It may achieve accurate motion while increasing energy consumption and mechanical stress. Additional reward terms are therefore needed to balance performance and durability.

Control effort penalties discourage unnecessarily large commands. Penalizing torque, current, acceleration, or steering rate can reduce energy use and hardware wear. However, excessive penalties may produce weak control responses and slow recovery from disturbances.

Smoothness penalties discourage rapid changes between consecutive actions. They reduce vibration, improve ride quality, and make motion more predictable. Smoothness is especially important for robots carrying fragile goods, medical materials, or human passengers.

Jerk, which is the rate of change of acceleration, is an important measure of comfort and mechanical quality. A policy that limits jerk can produce more natural movement. However, jerk reduction must not prevent emergency braking or rapid stabilization when safety is threatened.

Energy-aware reward design can use electrical power, battery current, motor losses, or estimated mechanical work. This allows the policy to discover efficient control strategies. For AMRs, energy optimization can extend operating time and reduce charging frequency.

Stability must be represented explicitly or indirectly. A balancing robot may receive rewards for maintaining body orientation and penalties for large tilt angles. A legged robot may be rewarded for stable contact patterns and penalized for falls or loss of support.

For vehicle-like robots, lateral stability may depend on yaw rate, sideslip, steering angle, and speed. The reward can discourage aggressive steering that increases rollover risk or causes tire slip. These terms become especially important on uneven or low-friction surfaces.

Terminal penalties are assigned when the system reaches unacceptable conditions. An episode may end after a collision, fall, actuator limit violation, unstable oscillation, excessive temperature, or departure from the permitted operating region.

Reward shaping can accelerate control learning by providing intermediate feedback. For example, a manipulator may receive rewards for moving closer to a target pose before completing the task. A mobile robot may receive rewards for reducing lateral and heading errors along a trajectory.

Poor reward shaping can create unintended strategies. A robot rewarded mainly for reducing position error may ignore velocity limits. A controller rewarded only for speed may become unstable. Every reward term should therefore be tested against possible shortcuts.

The discount factor determines how strongly the policy values future control outcomes. In fast control loops, many small time steps may occur within a short physical period. The discount factor must be selected in relation to the control frequency and task duration.

A high discount factor encourages the controller to consider long-term stability, energy use, and future tracking quality. A lower value emphasizes immediate error correction. If it is too low, the controller may become shortsighted and repeatedly create future disturbances.

Control frequency strongly affects the design of reinforcement learning. A policy running at ten hertz behaves differently from one running at one kilohertz. Higher frequencies allow rapid response but increase computational requirements and sensitivity to delay.

The inference time of the neural network must remain below the control period. If the policy response is delayed, the command may be based on an outdated state. Real-time execution therefore requires deterministic latency, efficient models, and reliable hardware.

Timing jitter can also degrade performance. Even when average inference time is acceptable, irregular delays may destabilize a tightly controlled system. Production deployment must measure worst-case latency rather than only average speed.

Traditional control systems often use proportional-integral-derivative control, state feedback, model predictive control, or optimal control. These methods provide strong theoretical foundations and predictable behavior when accurate models are available.

Reinforcement learning is attractive when the system is difficult to model, highly nonlinear, affected by changing payloads, or exposed to complex contact and friction. It can learn control strategies directly from interaction without requiring a perfect analytical model.

However, reinforcement learning does not automatically outperform classical control. For simple linear systems with well-known dynamics, conventional controllers are often more efficient, easier to verify, and more reliable. RL is most useful when adaptation or complex optimization is required.

A hybrid control architecture combines learned and classical methods. The reinforcement learning policy may generate references, adapt controller gains, estimate disturbances, or select operating modes. A conventional controller then guarantees basic stability and constraint handling.

Gain tuning is a practical application. The policy can adjust PID gains according to speed, payload, terrain, or battery state. This allows the control system to adapt while retaining the familiar structure of the underlying controller.

Residual reinforcement learning is another useful approach. A classical controller generates the main command, and the learned policy adds a small corrective term. The residual policy improves performance without taking complete control of the system.

This method reduces learning complexity because the agent does not need to discover basic control from the beginning. It also provides a safer baseline, since the conventional controller continues to operate even when the learned correction is imperfect.

Model predictive control can also be combined with reinforcement learning. RL may learn the cost function, terminal value, disturbance model, or model parameters used by MPC. MPC then performs constrained optimization at runtime.

Such combinations are attractive for industrial robotics because they preserve explicit constraints. Speed, torque, acceleration, and safety limits can remain within the MPC formulation while reinforcement learning improves prediction or long-term decision quality.

Value-based methods are less common for direct continuous control because they require evaluating many possible actions. Discretizing the action space is possible, but fine discretization increases complexity and coarse discretization reduces control quality.

Policy-gradient methods directly optimize a parameterized control policy. They can produce continuous actions but may require many interactions and careful tuning. Their performance depends strongly on reward scaling, normalization, and exploration noise.

Actor-critic methods use an actor to generate actions and a critic to estimate expected return. This structure is well suited to continuous control. Common algorithms include DDPG, TD3, SAC, PPO, and A2C.

Deep Deterministic Policy Gradient can learn continuous deterministic policies, but it may be sensitive to hyperparameters and value overestimation. Twin Delayed DDPG reduces this issue by using multiple critics and delayed policy updates.

Soft Actor-Critic introduces entropy into the objective, encouraging broad exploration. It often provides strong sample efficiency and robust continuous control. The resulting stochastic policy can later be evaluated in a more deterministic mode.

Proximal Policy Optimization is widely used because of its stable update mechanism. It is especially popular in simulation-based robotics. However, it is usually an on-policy method and may require more samples than off-policy algorithms.

Model-based reinforcement learning learns a dynamic model and uses it to predict future physical behavior. The policy can improve through simulated rollouts generated by the learned model. This can reduce the amount of real interaction required.

The challenge is model error. Small prediction errors can accumulate over long horizons and produce unrealistic control strategies. Model uncertainty should therefore be estimated, and planning should remain conservative when predictions are unreliable.

System identification supports both classical and learned control. Data from the robot can be used to estimate mass, inertia, friction, delay, actuator response, and contact dynamics. These estimates improve simulation quality and policy transfer.

Simulation is essential for reinforcement learning control because real-world exploration may damage hardware. A simulator allows millions of control steps, failures, disturbances, and extreme conditions to be tested without physical risk.

The simulator must accurately represent dynamics, actuator saturation, friction, delay, sensor noise, collision, and contact. A visually realistic simulator is not sufficient if its physical behavior differs from the real robot.

For control, small dynamic mismatches can be more important than visual differences. Incorrect tire friction, motor response, damping, or payload inertia may cause a policy to fail even when the simulated environment looks realistic.

Domain randomization improves robustness by changing physical parameters during training. Mass, friction, center of gravity, motor strength, delay, sensor bias, battery voltage, and external disturbances can be varied across episodes.

The resulting policy learns to control a family of systems rather than one exact model. This supports transfer to real robots, where physical parameters change because of manufacturing tolerance, wear, temperature, and payload variation.

Curriculum learning can begin with ideal dynamics and gradually introduce noise, delay, disturbances, and constraints. The policy first learns the basic task and later develops robustness. This often improves convergence compared with training under full difficulty from the start.

Imitation learning can initialize a control policy using data from a conventional controller or skilled human operator. The policy begins with reasonable behavior and then uses reinforcement learning to improve energy efficiency, adaptation, or disturbance rejection.

Offline reinforcement learning can use recorded control data from existing systems. This is attractive when online exploration is unsafe. However, the dataset must contain sufficient variation in states, actions, disturbances, and recovery behavior.

A dataset collected only under normal operation may not teach the policy how to recover from large errors. Rare disturbances, actuator faults, and boundary conditions should be represented through simulation or carefully designed experiments.

Exploration is difficult in physical control because random actions can be dangerous. Noise added to torque or steering commands may create instability. Exploration should therefore be constrained, simulated, or limited to safe operating regions.

Safe exploration can use action bounds, control barrier functions, safety filters, or backup controllers. The proposed action is checked before execution, and unsafe commands are modified or rejected.

A safety shield may enforce limits on speed, torque, current, tilt, braking distance, temperature, or contact force. It operates independently of the learned policy and prevents the agent from violating non-negotiable constraints.

Control barrier functions provide a mathematical method for maintaining the system inside a safe region. They can adjust the RL action while preserving as much of the intended command as possible.

Lyapunov-based approaches can introduce stability considerations into reinforcement learning. A Lyapunov function measures whether the system is moving toward or away from a stable condition. It can guide policy updates or constrain unsafe actions.

Formal stability guarantees for deep reinforcement learning remain difficult. Neural policies are nonlinear and may behave unpredictably outside the training distribution. Independent monitoring and conservative deployment are therefore essential.

Uncertainty estimation helps detect unfamiliar states. If the robot experiences an unusual payload, surface, or actuator response, the policy may be outside its training range. High uncertainty should trigger reduced speed, fallback control, or operator assistance.

Fallback control should always be available. If inference fails, sensors become invalid, or the policy output becomes abnormal, the robot should switch to a verified controller, stop safely, or enter a degraded mode.

Shadow-mode testing is useful before activation. The learned controller runs in parallel with the existing controller but does not command the hardware. Engineers compare proposed actions, identify risky disagreements, and collect new training cases.

After shadow-mode validation, deployment can proceed gradually. The policy may first operate only in low-risk conditions, at reduced speed, or on a limited number of robots. Expansion should depend on measured performance and safety data.

Control evaluation must include more than cumulative reward. Tracking error, overshoot, settling time, rise time, energy use, control effort, jerk, oscillation, thermal load, and constraint violations should all be measured.

Robustness testing should include changes in payload, friction, battery voltage, slope, wind, sensor bias, actuator delay, and component wear. The policy should maintain acceptable performance across the expected operating range.

Disturbance rejection is a key control metric. The system should recover from pushes, wheel slip, sudden load changes, surface transitions, or external forces. Recovery time and peak deviation are often more informative than average performance.

Long-duration testing reveals problems that short episodes may miss. Small biases can cause drift, repeated actuator corrections can create heat, and minor oscillations can accelerate mechanical wear over many hours.

Hardware-in-the-loop testing provides an intermediate stage between simulation and full deployment. Real controllers, communication interfaces, and timing behavior are connected to a simulated plant. This allows integration issues to be detected safely.

Real-time logging is essential. State estimates, policy outputs, actuator commands, safety interventions, latency, reward-related metrics, and physical responses should be recorded for debugging and incident analysis.

Policy versioning must be controlled. Every deployed model should have a unique version, documented training configuration, validated operating range, and rollback path. Uncontrolled model replacement is unacceptable in industrial control systems.

Changes in hardware may require retraining or revalidation. New motors, tires, payload structures, battery systems, or firmware can alter system dynamics. A policy validated on one configuration should not automatically be trusted on another.

Continual learning may allow the controller to improve from field data, but direct online updating creates serious safety and reproducibility risks. In most production systems, data should be collected in operation and policies updated offline under a controlled approval process.

For AMRs, reinforcement learning control can improve traction management, steering response, trajectory tracking, energy efficiency, docking accuracy, and adaptation to changing payloads or terrain.

On slippery surfaces, a learned controller may detect patterns of wheel slip and reduce torque before conventional thresholds are exceeded. On slopes, it may adjust acceleration and braking according to load and battery condition.

During docking, the policy can learn fine corrections based on position error, heading, sensor confidence, and mechanical alignment. The learned behavior may handle small calibration errors better than a fixed sequence of commands.

For manipulators, RL can improve force control, contact-rich assembly, grasp stabilization, and compliant motion. These tasks involve nonlinear contact and uncertainty that are difficult to model precisely.

For legged robots, reinforcement learning has demonstrated strong performance in balancing, locomotion, terrain adaptation, and disturbance recovery. Simulation enables enormous amounts of training that would be impractical on physical hardware.

Nevertheless, industrial reliability requires more than impressive demonstrations. The controller must operate predictably over long periods, recover from faults, respect hardware limits, and provide evidence that safety mechanisms remain effective.

The most practical role of reinforcement learning for control is often adaptive enhancement rather than total replacement. It can improve a stable baseline through residual correction, parameter adaptation, energy optimization, or learned disturbance compensation.

A successful architecture separates learning, control, and safety responsibilities. The learned policy provides adaptive intelligence, the deterministic controller manages physical execution, and the independent safety layer enforces strict limits.

Reinforcement learning for control is therefore not only an algorithmic problem. It requires coordinated design of state estimation, action interfaces, reward functions, real-time computing, simulation, safety systems, validation, deployment, and monitoring.

When these elements are integrated carefully, reinforcement learning can produce controllers that adapt to nonlinear dynamics, uncertainty, and changing operating conditions. Its value lies in improving physical performance while remaining bounded by stable control principles and robust engineering safeguards.

강화 학습 기반 제어(Reinforcement Learning for Control)는 경험 기반 학습을 이용하여 물리적인 제어 명령을 생성하는 기술이다. 기존의 수학적으로 유도된 제어 법칙(Control Law)에만 의존하는 대신, 에이전트(Agent)는 동적인 시스템과 상호작용하면서 자신의 명령이 시스템에 미치는 영향을 학습하여 점차 더 나은 제어 정책(Policy)을 획득한다.

제어(Control) 문제는 고수준 계획(High-Level Planning)과는 다르다. 하나의 행동(Action)은 위치(Position), 속도(Velocity), 가속도(Acceleration), 토크(Torque), 힘(Force), 조향각(Steering Angle), 관절 운동(Joint Motion)과 같은 물리량에 직접 영향을 준다. 작은 오차도 빠르게 누적될 수 있으므로, 정책은 정확하고 부드러우며 엄격한 실시간 제약 안에서 동작해야 한다.

강화 학습 기반 제어 시스템에서 에이전트는 일반적으로 제어 정책 자체를 의미한다. 환경(Environment)은 로봇 본체, 액추에이터(Actuator), 센서(Sensor), 적재물(Payload), 지형(Terrain), 외력(External Force), 그리고 주변 물리 환경으로 구성된다. 에이전트는 현재 상태(State)를 관찰하고 명령을 생성하며 보상(Reward)을 받은 후 자신의 정책을 개선한다.

상태(State)는 안정적인 제어를 수행할 수 있도록 시스템의 물리적 상태를 충분히 표현해야 한다. 여기에는 위치, 자세(Orientation), 속도, 가속도, 관절 각도(Joint Angle), 모터 전류(Motor Current), 휠 속도(Wheel Speed), 접촉력(Contact Force), 배터리 전압(Battery Voltage), 액추에이터 온도, 그리고 추종 오차(Tracking Error) 등이 포함될 수 있다.

자율이동로봇(Autonomous Mobile Robot, AMR)의 경우 상태에는 선속도(Linear Velocity), 각속도(Angular Velocity), 조향각(Steering Angle), 휠 회전 속도, 차체 자세, 횡방향 오차(Lateral Error), 방향 오차(Heading Error), 목표 궤적(Desired Trajectory) 등이 포함될 수 있다. 매니퓰레이터(Manipulator)는 관절 위치, 관절 속도, 말단효과기(End-Effector)의 자세와 접촉력을 상태로 사용할 수 있다.

완전한 상태를 항상 직접 측정할 수 있는 것은 아니다. 센서 지연(Sensor Delay), 노이즈(Noise), 기계적 백래시(Backlash), 휠 슬립(Wheel Slip), 측정되지 않는 외력, 숨겨진 접촉 조건 등으로 인해 부분 관측(Partial Observation)이 발생할 수 있다. 따라서 제어 정책은 상태 추정(State Estimation), 시계열 메모리(Temporal Memory), 또는 센서 융합(Sensor Fusion)을 함께 사용할 필요가 있다.

칼만 필터(Kalman Filter), 상태 관측기(Observer), 순환 신경망(Recurrent Neural Network), 잠재 상태 모델(Latent-State Model)은 보이지 않는 상태를 추정하는 데 사용된다. 특히 고속 제어에서는 작은 지연이나 추정 오차도 제어 안정성과 추종 성능을 크게 저하시킬 수 있으므로 정확한 상태 추정이 매우 중요하다.

행동 공간(Action Space)은 정책이 어느 수준까지 제어를 수행할지를 결정한다. 고수준에서는 목표 속도(Target Velocity)나 목표 위치(Target Position)를 생성할 수 있고, 저수준에서는 토크, 모터 전류, 제동력, 조향 속도, 액추에이터 전압 등을 직접 출력할 수도 있다.

직접 토크 제어(Direct Torque Control)는 매우 높은 자유도를 제공한다. 정책은 시스템의 동작을 세밀하게 조정할 수 있지만 동시에 위험도도 증가한다. 잘못된 토크 명령은 진동(Oscillation), 불안정성(Instability), 과열(Overheating), 과도한 힘, 심지어 하드웨어 손상을 유발할 수도 있다.

이러한 이유로 산업용 강화 학습에서는 중간 수준의 제어 인터페이스를 사용하는 경우가 많다. 정책은 목표 속도, 목표 가속도, 임피던스(Impedance), 또는 짧은 궤적(Trajectory)을 생성하고, 기존 제어기가 이를 안전한 액추에이터 명령으로 변환한다.

이와 같은 구조는 이미 검증된 모터 제어(Motor Control)와 서보 제어(Servo Control)를 그대로 유지할 수 있게 한다. 강화 학습 정책은 적응과 최적화를 담당하고, 기존 제어기는 전류 제한(Current Limit), 토크 제한(Torque Limit), 속도 제한(Velocity Limit), 액추에이터 보호 기능을 수행한다.

제어에서는 대부분 연속 행동 공간(Continuous Action Space)을 사용한다. 실제 물리 명령은 연속적인 실수값이기 때문이다. 따라서 정책은 단순한 이산 행동을 선택하는 것이 아니라 부드러운 수치 명령을 생성해야 하며, 일반적으로 액터-크리틱(Actor-Critic)이나 정책 경사(Policy Gradient) 계열 알고리즘이 사용된다.

반면 이산 제어(Discrete Control)는 동작 모드 선택에 유용할 수 있다. 예를 들어 가속, 유지, 감속, 정지, 후진 가운데 하나를 선택한 뒤, 별도의 제어기가 이를 실제 연속 제어 명령으로 변환할 수 있다.

보상 함수(Reward Function)는 원하는 제어 성능을 정의한다. 작은 추종 오차, 안정적인 움직임, 낮은 에너지 소비, 빠른 응답, 부드러운 가속, 성공적인 작업 수행에는 보상을 부여하고, 진동, 과도한 토크, 휠 슬립, 충격, 과열, 위험 상태에는 패널티(Penalty)를 부여할 수 있다.

추종 오차(Tracking Error)는 가장 대표적인 보상 요소이다. 로봇이 목표 위치, 속도, 자세, 또는 궤적을 정확하게 따라갈수록 더 높은 보상을 받는다. 하지만 추종 오차만으로는 제어 품질 전체를 충분히 표현하지 못한다.

추종 오차를 최소화하기 위해 지나치게 큰 토크를 사용할 수도 있다. 이 경우 움직임은 정확하지만 에너지 소비와 기계적 마모가 크게 증가한다. 따라서 성능과 내구성을 동시에 고려하는 추가적인 보상 항목이 필요하다.

제어 입력(Control Effort)에 대한 패널티는 불필요하게 큰 명령을 억제한다. 토크, 전류, 가속도, 조향 속도 등에 패널티를 부여하면 에너지 소비와 장비 마모를 줄일 수 있다. 반대로 패널티가 너무 크면 응답성이 떨어지고 외란(Disturbance)에 대한 복원력이 감소할 수 있다.

부드러움(Smoothness) 보상은 연속적인 제어 명령 사이의 급격한 변화를 줄인다. 이는 진동을 감소시키고 승차감을 향상시키며 사람에게 예측 가능한 움직임을 제공한다. 특히 깨지기 쉬운 물품이나 의료 장비를 운반하는 로봇에서는 매우 중요한 요소이다.

저크(Jerk)는 가속도의 변화율을 의미하며 승차감과 기계적 품질을 나타내는 중요한 지표이다. 저크를 줄이는 정책은 더욱 자연스럽고 부드러운 움직임을 만들 수 있다. 하지만 긴급 제동이나 위험 회피까지 제한해서는 안 된다.

에너지 기반 보상(Energy-Aware Reward)은 전력(Power), 배터리 전류(Battery Current), 모터 손실(Motor Loss), 기계적 일(Mechanical Work) 등을 이용하여 계산할 수 있다. 이를 통해 정책은 보다 효율적인 제어 전략을 스스로 학습할 수 있으며, AMR에서는 운행 시간 연장과 충전 횟수 감소에 도움이 된다.

안정성(Stability)은 직접 또는 간접적으로 보상에 포함되어야 한다. 균형 로봇(Balancing Robot)은 몸체의 기울기를 유지할 때 보상을 받고, 넘어질 위험이 커질수록 패널티를 받을 수 있다. 보행 로봇(Legged Robot)은 안정적인 발 접촉(Contact Pattern)에 보상을 받을 수 있다.

차량형 로봇에서는 횡방향 안정성(Lateral Stability)이 요 레이트(Yaw Rate), 사이드 슬립(Sideslip), 조향각, 속도 등에 의해 결정된다. 보상은 과도한 조향을 억제하여 전복 위험이나 타이어 슬립을 줄일 수 있다. 이러한 요소는 경사로나 미끄러운 노면에서 특히 중요하다.

종료 패널티(Terminal Penalty)는 시스템이 허용 범위를 벗어날 경우 부여된다. 충돌, 전도(Fall), 액추에이터 한계 초과, 불안정한 진동, 과열, 허용 영역 이탈 등이 발생하면 에피소드(Episode)가 종료될 수 있다.

보상 형성(Reward Shaping)은 중간 보상을 추가하여 학습 속도를 높이는 방법이다. 예를 들어 매니퓰레이터는 목표 자세(Target Pose)에 가까워질수록 추가 보상을 받을 수 있고, 이동 로봇은 횡방향 오차와 방향 오차를 줄일 때마다 보상을 받을 수 있다.

그러나 잘못된 보상 형성은 의도하지 않은 행동을 유발할 수 있다. 위치 오차만 줄이도록 학습하면 속도 제한을 무시할 수 있고, 속도만 강조하면 제어가 불안정해질 수 있다. 따라서 모든 보상 요소는 다양한 상황에서 충분히 검증되어야 한다.

할인 계수(Discount Factor)는 미래 제어 결과를 얼마나 중요하게 고려할지를 결정한다. 고속 제어 루프(Control Loop)는 매우 짧은 시간 동안 수많은 스텝을 수행하므로, 제어 주기(Control Frequency)와 작업 시간에 맞는 할인 계수를 선택해야 한다.

높은 할인 계수는 장기적인 안정성, 에너지 효율, 미래의 추종 성능을 고려하도록 만든다. 낮은 할인 계수는 즉각적인 오차 수정에 집중한다. 값이 너무 낮으면 현재의 오차만 줄이고 미래의 불안정성을 반복적으로 만드는 단기적인 정책이 될 수 있다.

제어 주기(Control Frequency)는 강화 학습 설계에 큰 영향을 준다. 10Hz에서 동작하는 정책과 1kHz에서 동작하는 정책은 완전히 다른 특성을 가진다. 높은 주기는 빠른 응답을 제공하지만 계산량과 지연 민감도가 크게 증가한다.

신경망의 추론 시간(Inference Time)은 반드시 제어 주기보다 짧아야 한다. 추론이 늦어지면 이미 오래된 상태를 기반으로 명령을 생성하게 되어 성능이 크게 저하된다. 따라서 실시간성(Real-Time), 일정한 지연(Deterministic Latency), 효율적인 모델이 요구된다.

평균 추론 시간이 충분하더라도 지연 변동(Timing Jitter)이 크면 제어 성능은 크게 악화될 수 있다. 실제 시스템에서는 평균 속도보다 최악의 응답 시간(Worst-Case Latency)을 더욱 중요하게 평가해야 한다.

기존 제어 시스템은 비례-적분-미분 제어(Proportional-Integral-Derivative Control, PID), 상태 피드백(State Feedback), 모델 예측 제어(Model Predictive Control, MPC), 최적 제어(Optimal Control) 등을 사용한다. 이러한 기법은 정확한 모델이 존재할 때 매우 높은 신뢰성과 예측 가능성을 제공한다.

강화 학습은 시스템 모델을 만들기 어렵거나, 강한 비선형성(Nonlinearity), 적재물 변화, 복잡한 접촉(Contact), 마찰(Friction)이 존재할 때 특히 유용하다. 완전한 수학적 모델 없이도 상호작용을 통해 제어 전략을 학습할 수 있기 때문이다.

그러나 강화 학습이 항상 기존 제어보다 우수한 것은 아니다. 단순한 선형 시스템에서는 기존 제어기가 더 효율적이고 검증도 쉬우며 신뢰성이 높다. 강화 학습은 적응성(Adaptation)이나 복잡한 최적화가 필요한 경우에 가장 큰 장점을 가진다.

하이브리드 제어(Hybrid Control)는 기존 제어와 강화 학습을 결합하는 방식이다. 강화 학습은 목표값(Reference)을 생성하거나, 제어기 이득(Gain)을 조정하거나, 외란을 추정하거나, 운전 모드를 선택하고, 기존 제어기는 안정성과 제약 조건을 보장한다.

PID 이득(Gain) 자동 조정은 대표적인 응용 사례이다. 강화 학습은 속도, 적재물, 지형, 배터리 상태에 따라 PID 파라미터를 자동으로 조절할 수 있다. 이를 통해 기존 제어기의 구조는 유지하면서 적응성을 높일 수 있다.

잔차 강화 학습(Residual Reinforcement Learning)은 기존 제어기가 기본 명령을 생성하고, 강화 학습 정책이 작은 보정값만 추가하는 방식이다. 기본적인 안정성은 유지하면서 성능을 향상시킬 수 있다.

이 방법은 에이전트가 처음부터 모든 제어를 학습할 필요가 없으므로 학습이 훨씬 쉬워진다. 또한 기존 제어기가 계속 동작하기 때문에 강화 학습 보정이 완벽하지 않더라도 안전성을 유지할 수 있다.

모델 예측 제어(MPC) 역시 강화 학습과 결합할 수 있다. 강화 학습은 MPC의 비용 함수(Cost Function), 종료 비용(Terminal Value), 외란 모델(Disturbance Model), 또는 시스템 모델을 학습하고, MPC는 실제 운용 중 제약 조건을 고려한 최적화를 수행한다.

이러한 구조는 산업용 로봇에서 매우 유용하다. 속도, 토크, 가속도, 안전 한계는 MPC가 보장하고, 강화 학습은 예측 성능과 장기적인 제어 품질을 향상시킨다.

가치 기반(Value-Based) 알고리즘은 연속 제어에서는 자주 사용되지 않는다. 가능한 모든 연속 행동의 가치를 계산하기 어렵기 때문이다. 행동 공간을 이산화할 수도 있지만, 너무 세분화하면 계산량이 증가하고 너무 거칠면 제어 품질이 떨어진다.

정책 경사(Policy Gradient) 알고리즘은 연속 정책을 직접 최적화한다. 연속 제어에 적합하지만 많은 학습 데이터와 신중한 하이퍼파라미터(Hyperparameter) 조정이 필요하다. 또한 보상 스케일링(Reward Scaling), 정규화(Normalization), 탐험 노이즈(Exploration Noise)에 매우 민감하다.

액터-크리틱(Actor-Critic)은 액터가 행동을 생성하고 크리틱이 기대 반환값(Expected Return)을 추정한다. DDPG, TD3, SAC, PPO, A2C 등이 대표적인 알고리즘이다.

심층 결정론적 정책 경사(Deep Deterministic Policy Gradient, DDPG)는 연속 제어 정책을 학습할 수 있지만 하이퍼파라미터에 민감하며 가치 함수 과대평가(Value Overestimation)가 발생할 수 있다. TD3(Twin Delayed DDPG)는 두 개의 크리틱과 지연된 정책 업데이트를 사용하여 이러한 문제를 완화한다.

소프트 액터 크리틱(Soft Actor-Critic, SAC)은 엔트로피(Entropy)를 포함하여 탐험을 촉진한다. 높은 데이터 효율성과 강인한 성능을 제공하며, 학습 후에는 보다 결정론적인 정책으로 사용할 수도 있다.

근접 정책 최적화(Proximal Policy Optimization, PPO)는 안정적인 업데이트 방식으로 인해 시뮬레이션 기반 로봇 제어에서 널리 사용된다. 다만 온-폴리시(On-Policy) 알고리즘이므로 오프-폴리시(Off-Policy) 알고리즘보다 더 많은 데이터가 필요한 경우가 많다.

모델 기반 강화 학습(Model-Based Reinforcement Learning)은 시스템 동역학 모델을 학습하여 미래의 물리적 상태를 예측한다. 이를 이용하여 시뮬레이션 롤아웃(Rollout)을 수행하므로 실제 데이터 요구량을 줄일 수 있다.

하지만 모델 오차(Model Error)는 큰 문제이다. 작은 예측 오차도 장기적으로 누적되어 비현실적인 제어 전략을 만들 수 있다. 따라서 모델의 불확실성을 함께 추정하고 보수적인 계획을 수행해야 한다.

시스템 식별(System Identification)은 기존 제어와 강화 학습 모두에 중요하다. 실제 로봇 데이터를 이용하여 질량(Mass), 관성(Inertia), 마찰(Friction), 지연(Delay), 액추에이터 응답, 접촉 특성 등을 추정하면 시뮬레이션의 정확성과 실제 환경으로의 이전 성능이 향상된다.

강화 학습 제어에서는 시뮬레이션이 필수적이다. 실제 장비에서 수백만 번의 실패를 경험할 수 없기 때문이다. 시뮬레이션은 다양한 외란, 실패, 극한 조건을 안전하게 반복할 수 있다.

시뮬레이터는 시스템 동역학, 액추에이터 포화(Saturation), 마찰, 지연, 센서 노이즈, 충돌, 접촉 등을 정확하게 모델링해야 한다. 단순히 시각적으로만 현실적인 시뮬레이터는 충분하지 않다.

제어에서는 시각적인 차이보다 동역학 오차가 훨씬 중요하다. 타이어 마찰, 모터 응답, 감쇠(Damping), 적재물 관성 등이 실제와 다르면 정책은 실제 로봇에서 쉽게 실패할 수 있다.

도메인 랜덤화(Domain Randomization)는 질량, 마찰, 무게 중심, 모터 출력, 지연, 센서 오차, 배터리 전압, 외란 등을 반복적으로 변경하며 학습한다.

이를 통해 정책은 하나의 시스템이 아니라 다양한 시스템을 제어하는 능력을 학습한다. 제조 오차, 장비 마모, 온도 변화, 적재물 변화가 존재하는 실제 환경으로의 이전 성능이 크게 향상된다.

커리큘럼 학습(Curriculum Learning)은 이상적인 동역학에서 시작하여 점차 노이즈, 지연, 외란, 제약 조건을 추가하는 방식이다. 처음부터 어려운 환경에서 학습하는 것보다 일반적으로 수렴 속도가 빠르다.

모방 학습(Imitation Learning)은 기존 제어기나 숙련자의 데이터를 이용하여 초기 정책을 생성한다. 이후 강화 학습이 이를 더욱 개선하여 에너지 효율, 적응성, 외란 제거 성능을 향상시킨다.

오프라인 강화 학습(Offline Reinforcement Learning)은 기존 제어 로그를 이용하여 학습한다. 온라인 탐험이 위험한 시스템에서는 매우 유용하지만, 데이터셋에는 다양한 상태, 행동, 외란, 복구 상황이 충분히 포함되어야 한다.

정상 운용 데이터만 존재하면 큰 오차에서 복구하는 능력을 학습하지 못한다. 따라서 드문 외란과 고장 상황도 시뮬레이션이나 별도의 실험으로 충분히 포함해야 한다.

물리 제어에서는 탐험(Exploration)이 매우 어렵다. 무작위 토크나 조향 명령은 시스템을 위험하게 만들 수 있기 때문이다. 따라서 탐험은 반드시 제한된 안전 영역에서 수행하거나 시뮬레이션에서 수행해야 한다.

안전 탐험(Safe Exploration)은 행동 제한(Action Bound), 제어 장벽 함수(Control Barrier Function), 안전 필터(Safety Filter), 백업 제어기(Backup Controller)를 이용하여 구현할 수 있다. 위험한 행동은 실행 전에 수정되거나 거부된다.

안전 실드(Safety Shield)는 속도, 토크, 전류, 기울기, 제동 거리, 온도, 접촉력 등의 제한을 항상 검사한다. 이는 강화 학습 정책과 독립적으로 동작하며 절대로 위반해서는 안 되는 안전 제약을 보장한다.

제어 장벽 함수(Control Barrier Function)는 시스템을 안전 영역 안에 유지하는 수학적 기법이다. 강화 학습의 행동을 가능한 한 유지하면서도 안전을 보장하도록 명령을 수정한다.

리아프노프 기반(Lyapunov-Based) 방법은 안정성(Stability)을 강화 학습에 포함하는 방법이다. 리아프노프 함수(Lyapunov Function)는 시스템이 안정 상태에 가까워지는지를 측정하며 정책 업데이트나 안전 제약에 활용될 수 있다.

심층 강화 학습에서는 아직 수학적인 안정성 보장이 쉽지 않다. 신경망 정책은 비선형이며 학습 범위를 벗어난 상황에서는 예측하기 어려운 행동을 보일 수 있다. 따라서 독립적인 감시 시스템과 보수적인 배포 전략이 반드시 필요하다.

불확실성 추정(Uncertainty Estimation)은 학습하지 않은 상태를 탐지하는 데 사용된다. 새로운 적재물, 노면, 액추에이터 특성을 만나면 정책의 신뢰도가 낮아질 수 있으며, 이러한 경우에는 감속, 백업 제어기 전환, 또는 사람의 개입이 필요하다.

백업 제어(Fallback Control)는 항상 준비되어 있어야 한다. 추론이 실패하거나 센서에 문제가 발생하거나 정책 출력이 비정상적이면 검증된 기존 제어기로 즉시 전환하거나 안전하게 정지해야 한다.

섀도우 모드(Shadow Mode)는 실제 적용 전에 매우 유용한 검증 방법이다. 강화 학습 제어기는 기존 제어기와 동시에 동작하지만 실제 하드웨어는 기존 제어기가 제어한다. 엔지니어는 두 제어기의 차이를 분석하여 위험한 상황을 학습 데이터에 추가할 수 있다.

섀도우 모드 검증이 끝난 후에도 단계적으로 배포해야 한다. 처음에는 저속 환경이나 위험이 낮은 작업에서만 사용하고, 충분한 성능과 안전성이 확인된 후 적용 범위를 확대해야 한다.

제어 성능 평가는 누적 보상만으로는 충분하지 않다. 추종 오차, 오버슈트(Overshoot), 정착 시간(Settling Time), 상승 시간(Rise Time), 에너지 소비, 제어 입력, 저크, 진동, 열 부하(Thermal Load), 제약 조건 위반 등을 모두 함께 평가해야 한다.

강인성(Robustness) 평가는 적재물 변화, 마찰 변화, 배터리 전압 변화, 경사, 바람, 센서 오차, 액추에이터 지연, 장비 마모 등 다양한 조건에서 수행되어야 한다.

외란 제거 능력(Disturbance Rejection)은 매우 중요한 평가 항목이다. 외부 충격, 휠 슬립, 급격한 적재물 변화, 노면 변화 등에서 얼마나 빠르게 회복하는지가 평균 성능보다 더욱 중요한 경우가 많다.

장시간 운용(Long-Term Operation) 테스트는 단기 테스트에서 발견되지 않는 문제를 찾아낸다. 작은 오차도 장기간 누적되면 드리프트(Drift), 과열, 장비 마모를 유발할 수 있다.

하드웨어-인-더-루프(Hardware-in-the-Loop, HIL) 시험은 시뮬레이션과 실제 운용 사이의 중요한 단계이다. 실제 제어기와 통신 장치는 그대로 사용하면서 플랜트(Plant)만 시뮬레이션으로 대체하여 시스템 통합 문제를 안전하게 검증할 수 있다.

실시간 로깅(Real-Time Logging)은 필수적이다. 상태 추정값, 정책 출력, 액추에이터 명령, 안전 개입, 지연 시간, 보상 관련 지표, 실제 응답을 모두 기록해야 디버깅과 사고 분석이 가능하다.

정책 버전 관리(Policy Versioning)는 엄격하게 수행되어야 한다. 모든 정책은 고유한 버전 번호, 학습 환경, 검증 범위, 롤백(Rollback) 절차를 가져야 한다. 산업용 시스템에서는 검증되지 않은 모델 교체는 허용되지 않는다.

하드웨어 변경도 재검증이 필요하다. 새로운 모터, 타이어, 적재 구조, 배터리, 펌웨어는 시스템 동역학을 변화시킬 수 있으므로 기존 정책을 그대로 신뢰해서는 안 된다.

지속 학습(Continual Learning)은 현장 데이터를 이용하여 성능을 향상시킬 수 있지만, 실시간 온라인 업데이트는 안전성과 재현성 측면에서 매우 위험하다. 대부분의 산업 시스템에서는 데이터를 수집한 후 오프라인에서 검증을 거쳐 정책을 업데이트한다.

AMR에서는 강화 학습 제어를 이용하여 구동력 관리(Traction Management), 조향 응답(Steering Response), 궤적 추종(Trajectory Tracking), 에너지 효율, 도킹 정확도(Docking Accuracy), 적재물과 지형 변화에 대한 적응성을 향상시킬 수 있다.

미끄러운 노면에서는 휠 슬립 패턴을 미리 감지하여 기존 제어기보다 빠르게 토크를 줄일 수 있다. 경사로에서는 적재물과 배터리 상태에 맞추어 가속과 제동을 자동으로 조절할 수 있다.

도킹 과정에서는 위치 오차, 방향 오차, 센서 신뢰도, 기계 정렬 상태를 고려하여 더욱 정밀한 보정을 수행할 수 있다. 이러한 적응 능력은 고정된 제어 시퀀스보다 우수한 성능을 보일 수 있다.

매니퓰레이터에서는 강화 학습이 힘 제어(Force Control), 접촉 기반 조립(Contact-Rich Assembly), 파지 안정화(Grasp Stabilization), 순응 제어(Compliant Motion)를 향상시킬 수 있다. 이러한 작업은 비선형 접촉 특성 때문에 기존 모델링이 매우 어렵다.

보행 로봇(Legged Robot)은 균형 유지(Balancing), 보행(Locomotion), 지형 적응(Terrain Adaptation), 외란 회복(Disturbance Recovery) 분야에서 강화 학습이 뛰어난 성능을 보여주고 있다. 시뮬레이션을 통해 실제 장비에서는 불가능한 수준의 대규모 학습이 가능하다.

그러나 산업 현장에서 요구되는 것은 뛰어난 시연(Demonstration)이 아니라 장기간의 신뢰성(Reliability)이다. 제어기는 오랜 시간 안정적으로 동작하고, 고장을 복구하며, 하드웨어 한계를 준수하고, 안전 시스템이 항상 정상적으로 동작함을 보장해야 한다.

실제 산업에서는 강화 학습 제어가 기존 제어를 완전히 대체하기보다는 적응형 성능 향상(Adaptive Enhancement)에 가장 적합하다. 잔차 보정(Residual Correction), 파라미터 적응(Parameter Adaptation), 에너지 최적화(Energy Optimization), 외란 보상(Disturbance Compensation) 등이 대표적인 활용 방식이다.

성공적인 시스템은 학습(Learning), 제어(Control), 안전(Safety)의 역할을 명확히 분리한다. 강화 학습 정책은 적응형 지능을 제공하고, 결정론적 제어기는 물리적 실행을 담당하며, 독립적인 안전 계층(Safety Layer)은 절대적인 안전 제약을 유지한다.

따라서 강화 학습 기반 제어는 단순히 알고리즘만의 문제가 아니다. 상태 추정(State Estimation), 행동 인터페이스(Action Interface), 보상 함수(Reward Function), 실시간 컴퓨팅(Real-Time Computing), 시뮬레이션(Simulation), 안전 시스템(Safety System), 검증(Validation), 배포(Deployment), 모니터링(Monitoring)이 모두 함께 설계되어야 한다.

이러한 요소들이 유기적으로 통합될 때 강화 학습은 비선형 동역학, 환경의 불확실성, 변화하는 운용 조건에 적응하는 뛰어난 제어기를 구현할 수 있다. 강화 학습의 진정한 가치는 기존의 안정적인 제어 원리를 유지하면서도 물리적 성능을 지속적으로 향상시키는 적응형 지능을 제공하는 데 있다.

##  

## 09.5 Simulation-Based RL

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Simulation-based reinforcement learning trains an agent inside a virtual environment before deploying the learned policy to a physical robot. The simulator reproduces the robot, sensors, actuators, obstacles, terrain, and task conditions so that the agent can gain experience without risking real hardware. This approach is especially valuable in robotics because reinforcement learning often requires millions of interactions. Collecting the same amount of experience with a physical robot would consume excessive time, energy, labor, and equipment life while creating repeated safety risks.

A simulated robot can fail thousands of times without causing physical damage. It can collide, fall, lose balance, select inefficient paths, or apply poor control commands while the learning algorithm gradually discovers more effective behavior. Simulation also accelerates experimentation. Many virtual environments can run faster than real time, and multiple copies can operate in parallel. This allows a training system to generate far more experience than a single physical robot could collect during the same period.

The agent interacts with the simulator through the same reinforcement learning loop used in the real world. It observes a state or sensor input, selects an action, receives a reward, and transitions to a new state. The accumulated experience is used to update the policy or value function. The simulator acts as the environment in this loop. It calculates how the robot moves after each action, how sensors respond, whether contact occurs, and how the task progresses. The quality of these calculations strongly influences the usefulness of the learned policy.

A simulation environment can represent a mobile robot navigating through corridors, a manipulator assembling components, a legged robot walking over terrain, or a drone maintaining stable flight. The same general training principle applies across these systems. For an autonomous mobile robot, the simulator may include maps, shelves, doors, ramps, pedestrians, other robots, charging stations, and traffic rules. The agent can learn navigation, control, docking, collision avoidance, or fleet coordination within this virtual space.

The simulated state should contain information equivalent to what will be available during real operation. It may include robot pose, velocity, LiDAR scans, camera images, depth data, battery state, wheel speed, local maps, target direction, and nearby obstacle motion. Using privileged information during training can be helpful but must be handled carefully. A simulator knows exact positions, velocities, and contact states that real sensors cannot measure perfectly. A policy that depends on this hidden information may fail when transferred to the real robot.

Privileged information is often used only by the critic, teacher model, or reward calculation. The deployed policy receives realistic observations that match the physical system. This allows efficient training without creating an impossible runtime dependency. The action interface must also match the intended deployment architecture. A policy may output wheel torque, steering angle, target velocity, local waypoint, joint command, or desired trajectory. Mismatch between simulated and real action interfaces can make policy transfer difficult.

Simulation-based reinforcement learning can operate at several control levels. A high-level policy may select goals or routes, while a lower-level policy generates motion. Another policy may control torque or force directly for manipulation, locomotion, or stabilization. The reward function evaluates the agent\'s behavior in simulation. It may encourage task completion, safety, smoothness, speed, energy efficiency, tracking accuracy, and rule compliance. It may penalize collisions, unstable motion, excessive force, timeout, or constraint violation.

Simulation makes reward design easier to inspect because every internal variable is available. Engineers can calculate exact distances, contact forces, energy use, trajectory errors, or success conditions. They can also visualize why a policy receives a particular reward. However, a reward that works well in simulation may still produce undesirable behavior. The agent may exploit a modeling weakness or a reward shortcut that does not exist in reality. Careful scenario review is therefore required throughout training.

A navigation policy may learn to pass extremely close to obstacles because the simulator models collision geometry too generously. A manipulator may exploit unrealistic contact behavior. A legged robot may use motions that are physically impossible for the real actuators. These failures show that simulation accuracy involves more than appearance. A visually realistic environment can still have incorrect friction, delay, mass, collision response, sensor noise, or actuator dynamics. Physical realism is essential for policies that control real machines.

The simulator should represent the robot\'s kinematics and dynamics at the required level of detail. Kinematic simulation may be sufficient for high-level path planning, while torque control, balance, contact, and traction require accurate dynamic simulation. Robot mass, inertia, center of gravity, wheel radius, suspension, joint limits, motor strength, braking force, and damping influence physical behavior. Incorrect values may cause a policy to learn control strategies that cannot work on the real platform.

Actuator models should include saturation, delay, dead zones, rate limits, current limits, and thermal effects when relevant. Real actuators cannot change output instantly or produce unlimited force. Ignoring these limits creates unrealistic policies. Sensor simulation is equally important. Real sensors contain noise, bias, quantization, missing values, limited range, occlusion, motion distortion, and timing differences. Policies trained on perfect sensor data often become fragile in actual environments.

A simulated LiDAR should represent range limits, angular resolution, dropout, reflection errors, and obstacle occlusion. Camera simulation may require realistic lighting, texture, blur, exposure changes, and lens effects when visual perception is part of the policy. Depth cameras may produce missing values near reflective or transparent surfaces. Inertial sensors may contain bias and drift. Wheel odometry may be affected by slip. Adding such imperfections helps the policy learn robust behavior. Communication and computation should also be modeled.

Control messages may experience network delay, packet loss, scheduling variation, or asynchronous sensor arrival. These effects are important in distributed robots, fleet systems, and cloud-connected control architectures. The simulation time step determines how often the environment updates. A small step provides accurate dynamics but increases computation. A larger step runs faster but may miss collisions, rapid contacts, or unstable motion. The policy update frequency does not always need to match the physics frequency.

The simulator may calculate dynamics at a high rate while the reinforcement learning policy acts at a lower rate. This mirrors real systems where motor control and decision making operate at different frequencies. Parallel simulation is one of the greatest advantages of simulation-based reinforcement learning. Hundreds or thousands of environment instances can generate experience simultaneously on CPUs or GPUs. This significantly reduces the wall-clock time required for training. Each environment can begin from different positions, maps, payloads, or physical parameters.

The resulting experience is more diverse than repeatedly running one fixed scenario. Diversity improves robustness and reduces memorization. Vectorized simulation executes many environments using shared operations. GPU-based simulators can update large numbers of robots in parallel, especially when the physics and neural network calculations are optimized for the same hardware. High-throughput simulation is useful for on-policy algorithms such as PPO, which require fresh experience after each policy update.

It also benefits off-policy methods by rapidly filling replay buffers with varied transitions. Faster simulation does not automatically produce better policies. If the virtual environment is too simplified, the agent may learn quickly but transfer poorly. Training speed and simulation fidelity must therefore be balanced according to the task. A high-fidelity simulator may be necessary for direct control, manipulation, contact, or rough-terrain locomotion. A lighter simulator may be sufficient for route selection, task allocation, or strategic fleet behavior.

Multi-stage simulation can combine different levels of fidelity. Early learning may occur in a simplified environment, while later training and validation use more detailed physics. This reduces training cost while preserving transfer quality. Curriculum learning is commonly used with simulation. The agent begins with simple tasks and gradually encounters more difficult conditions. A mobile robot may first navigate open space, then static obstacles, narrow passages, moving people, and dense traffic.

A manipulator may first reach a target without contact, then grasp objects, handle pose variation, and finally perform precise assembly. A legged robot may begin on flat ground before learning slopes, steps, loose surfaces, and external disturbances. The curriculum should increase difficulty at a rate that supports learning. If the environment becomes difficult too quickly, the agent may fail to receive useful rewards. If it remains easy for too long, the policy may overfit to simple behavior. Automatic curriculum methods adjust difficulty based on performance.

When the agent succeeds consistently, the simulator increases obstacle density, disturbance strength, task precision, or initial-state variation. Procedural generation creates new environments automatically. Random maps, rooms, corridors, obstacle arrangements, object poses, terrain profiles, or traffic patterns can be generated for every episode. This prevents the agent from memorizing a limited set of layouts. A policy that succeeds only in familiar scenes has not learned general navigation or control principles. Procedural diversity encourages transferable behavior.

Domain randomization varies the parameters of the simulated world. Instead of trying to build one perfectly accurate model, the training system exposes the policy to a wide range of possible models. Physical randomization may change mass, friction, inertia, center of gravity, motor strength, wheel radius, suspension properties, damping, payload, battery voltage, and actuator delay. Sensor randomization may vary noise, bias, range, field of view, resolution, calibration, dropout, lighting, texture, and latency.

Environmental randomization may alter terrain, obstacle behavior, weather, traffic density, or map structure. The objective is to make the real system appear as one possible environment within the randomized distribution. A policy that succeeds across broad variation is less likely to depend on exact simulator assumptions. Randomization must remain realistic. If parameter ranges are excessively wide, learning may become unstable or the policy may become unnecessarily conservative. If the ranges are too narrow, the policy may still fail under real variation.

System identification helps choose appropriate randomization ranges. Measurements from the physical robot can estimate motor response, friction, latency, sensor noise, and dynamic parameters. These estimates guide simulator calibration. Domain randomization can be combined with domain adaptation. Randomization encourages broad robustness, while adaptation uses real observations to align simulated and physical representations more precisely. A major challenge is the simulation-to-reality gap, often called the sim-to-real gap.

It refers to differences between the virtual environment and the real system that cause policy performance to degrade after deployment. The gap may result from incorrect physics, sensor differences, actuator delay, unmodeled wear, environmental complexity, human behavior, communication timing, or incomplete task definitions. For perception-based policies, the visual gap can be significant. Real images contain lighting variation, reflections, dirt, blur, shadows, and objects not represented during training. Photorealistic rendering or representation learning can reduce this difference.

For control policies, the dynamic gap is often more important. A small error in friction, delay, inertia, or torque response may destabilize a controller even when the visual environment looks highly realistic. Sim-to-real transfer can use several strategies. These include domain randomization, simulator calibration, robust control objectives, real-data fine-tuning, residual learning, adaptation networks, and progressive deployment. Residual learning is useful when a conventional controller already performs the basic task. The simulated policy learns only a correction to the baseline command.

This reduces dependence on perfect simulation and provides a stable fallback. Teacher-student learning can also support transfer. A teacher policy uses complete simulated state information, while a student learns from realistic sensor observations. The student imitates the teacher and is deployed on the real robot. Asymmetric actor-critic methods follow a similar principle. The critic uses privileged simulator information to estimate value accurately, while the actor receives only observations available during real operation.

Representation learning can transform simulated and real sensor data into a shared feature space. If the policy acts on robust features rather than raw pixels, the visual domain gap may be reduced. Fine-tuning with real data may improve performance after simulation training. However, unrestricted reinforcement learning on physical hardware is often unsafe and expensive. Real-world updates should therefore be limited and carefully monitored. Offline reinforcement learning can use recorded real trajectories to refine a simulated policy.

This avoids dangerous exploration but depends on the quality and coverage of the operational dataset. A policy may also be deployed in shadow mode. It receives live sensor data and generates proposed actions, but the existing controller remains in charge. Engineers compare decisions and identify situations where the policy behaves unexpectedly. Shadow mode provides valuable real-world data without control risk. Disagreement cases can be recreated in simulation, added to the training distribution, and used to improve the next policy version.

Hardware-in-the-loop testing creates an intermediate validation stage. Real computers, controllers, communication interfaces, and timing behavior are connected to a simulated robot or environment. This allows engineers to test inference latency, message timing, software integration, safety overrides, and hardware interfaces without moving the physical robot. It reveals issues that are not visible in pure software simulation. Software-in-the-loop testing runs the actual robot software stack against the simulator.

The navigation, perception, control, and mission software use simulated sensor messages and produce normal commands. This approach validates system integration and reduces the difference between training code and deployment code. It is particularly valuable for ROS2-based robots and distributed control systems. Simulation can also generate rare and dangerous scenarios. Sudden pedestrian entry, sensor failure, localization loss, brake degradation, blocked exits, communication loss, or extreme terrain can be tested repeatedly.

Such events may be too rare to collect from normal field operation but too important to ignore. Simulation makes it possible to build a broad safety-validation library. Adversarial scenarios intentionally search for policy weaknesses. Obstacles, disturbances, sensor errors, or initial states are selected to maximize failure probability. This reveals fragile behavior that random testing may miss. Scenario coverage should be measured systematically. Engineers should track which combinations of speed, payload, terrain, traffic, sensor condition, and mission type have been tested.

A policy with high average performance may still fail in a narrow region of the operating domain. Coverage analysis helps identify these untested or weak areas. Training evaluation and deployment evaluation should remain separate. The training reward is used to improve the policy, but validation should include independent metrics that the agent cannot exploit. For navigation, these metrics may include success rate, collision rate, minimum clearance, path length, travel time, deadlock frequency, energy consumption, intervention count, and motion smoothness.

For control, metrics may include tracking error, overshoot, settling time, stability margin, torque usage, jerk, energy, thermal load, and constraint violations. For manipulation, evaluation may measure grasp success, force peaks, placement accuracy, cycle time, object damage, and recovery from pose error. Policies should be tested on environments not used during training. New maps, textures, payloads, disturbances, and obstacle behaviors provide a more honest measure of generalization.

Long-duration simulation can reveal drift, repeated oscillation, energy inefficiency, or rare state accumulation. Short episodes may hide these problems even when immediate performance appears strong. Simulation should also model policy failure handling. The robot must know what to do when observations are invalid, confidence is low, the model crashes, or commands violate safety constraints. An independent safety layer should remain active during simulated training and real deployment. It may enforce speed limits, torque limits, geofences, collision boundaries, or emergency stopping.

Training with the safety layer included helps the policy understand the actual operational constraints. Otherwise, the policy may repeatedly request actions that are always overridden after deployment. A safety shield can modify unsafe commands before execution. The training system can log these interventions and penalize policies that rely excessively on the shield. Fallback controllers should also be tested in simulation. The system may switch to a classical planner, verified controller, reduced-speed mode, or safe stop when the learned policy becomes uncertain.

Uncertainty estimation can be trained and evaluated using simulation. The environment can generate out-of-distribution states, sensor failures, or parameter combinations that were not included in nominal training. A reliable system should reduce speed or request fallback control when uncertainty becomes high. The goal is not merely to maximize performance but to recognize when the policy should not be trusted. Simulation-based reinforcement learning requires careful data and experiment management.

Training configurations, random seeds, simulator versions, policy checkpoints, reward definitions, and parameter ranges should all be recorded. Without strict version control, it becomes difficult to reproduce a result or understand why two policy versions behave differently. Reproducibility is essential for industrial validation. Simulator changes can alter learned behavior even when the reinforcement learning code remains unchanged. Physics engines, sensor models, collision meshes, and timing settings should therefore be versioned like software.

Training logs should include reward components, episode outcomes, safety violations, environment parameters, action distributions, and learning curves. These records help detect unstable learning or unintended strategies. Model checkpoints should be evaluated periodically rather than only at the end of training. The policy with the highest training reward may not provide the best robustness or safety. Automated evaluation pipelines can test each checkpoint across a fixed scenario suite. This allows direct comparison of success, safety, efficiency, and generalization.

Simulation cost must also be considered. Large-scale training may require substantial GPU or CPU resources, storage, and engineering effort. High-fidelity rendering and physics can make experiments expensive. Efficient environment design, parallel execution, mixed-fidelity training, and targeted scenario generation can reduce cost. The objective is not maximum realism everywhere, but sufficient realism for the learned behavior. Different simulation tools serve different purposes.

Some emphasize rigid-body physics, others photorealistic perception, large-scale parallel training, traffic simulation, or ROS integration. Tool selection should follow the task requirements. A mobile robot navigation project may prioritize map generation, LiDAR simulation, pedestrian motion, and ROS2 interfaces. A manipulation project may require accurate contact, force, friction, and articulated-object models. A legged robot project may prioritize fast GPU physics and parallel training.

An autonomous driving project may require traffic behavior, road networks, cameras, radar, LiDAR, and large scenario libraries. Simulation-based reinforcement learning works best as part of a broader engineering process. It should connect requirements, system modeling, training, safety design, validation, deployment, monitoring, and field-data feedback. The simulator should evolve as real-world data becomes available. Failures, near misses, sensor artifacts, and unusual operating conditions should be reproduced virtually and added to future training. This creates a closed improvement loop.

Field operation identifies weaknesses, simulation recreates them safely, reinforcement learning improves the policy, and staged validation confirms whether the update is ready for deployment. For AMRs, this process can improve navigation, docking, traction control, energy management, traffic interaction, and recovery behavior without exposing the physical fleet to uncontrolled exploration. The most important benefit of simulation is not simply faster training.

It is the ability to explore a wide range of conditions, including failures and edge cases, within a repeatable and measurable environment. The most important limitation is that the simulator is never identical to reality. A policy should therefore be treated as a candidate behavior that requires transfer engineering, safety protection, and real-world validation. Successful simulation-based reinforcement learning depends on realistic interfaces, calibrated dynamics, diverse scenarios, controlled randomization, independent metrics, staged deployment, and continuous feedback from the physical system.

When these elements are integrated, simulation becomes more than a training tool. It becomes a development and validation platform that connects learning algorithms with reliable robotic products. The final goal is not to create a policy that performs impressively in a virtual world. The goal is to produce a robot that behaves safely, efficiently, and robustly under the uncertainty and variation of real operation.

시뮬레이션 기반 강화 학습(Simulation-Based Reinforcement Learning)은 실제 로봇에 정책(Policy)을 적용하기 전에 가상 환경(Virtual Environment)에서 에이전트(Agent)를 학습시키는 방법이다. 시뮬레이터(Simulator)는 로봇, 센서(Sensor), 액추에이터(Actuator), 장애물(Obstacle), 지형(Terrain), 작업 환경(Task Condition)을 재현하여 실제 하드웨어를 위험에 노출시키지 않고도 충분한 경험을 축적할 수 있도록 한다. 이 접근법은 로봇 분야에서 특히 중요하다. 강화 학습은 일반적으로 수백만 번 이상의 상호작용이 필요하기 때문이다.

이러한 경험을 실제 로봇으로 수집하려면 막대한 시간과 에너지, 인력, 장비 수명이 소모될 뿐 아니라 반복적인 안전 위험도 발생한다. 시뮬레이션 속의 로봇은 수천 번 실패하더라도 물리적인 손상이 발생하지 않는다. 충돌하거나 넘어지고, 균형을 잃거나, 비효율적인 경로를 선택하거나, 잘못된 제어 명령을 생성하더라도 학습 알고리즘은 이러한 시행착오를 통해 점차 더 나은 행동을 학습한다. 시뮬레이션은 실험 속도도 크게 향상시킨다. 많은 가상 환경은 실제 시간보다 빠르게 실행될 수 있으며, 여러 개의 환경을 동시에 병렬 실행할 수도 있다. 따라서 하나의 실제 로봇보다 훨씬 많은 경험을 동일한 시간 안에 생성할 수 있다.

에이전트는 실제 환경과 동일한 강화 학습 루프(Reinforcement Learning Loop)를 통해 시뮬레이터와 상호작용한다. 상태(State) 또는 센서 입력을 관찰하고, 행동(Action)을 선택하며, 보상(Reward)을 받은 후 새로운 상태(State)로 전이된다. 축적된 경험은 정책(Policy)이나 가치 함수(Value Function)를 업데이트하는 데 사용된다. 이 과정에서 시뮬레이터는 환경(Environment)의 역할을 수행한다. 각 행동 이후 로봇이 어떻게 움직이는지, 센서가 어떤 값을 반환하는지, 접촉(Contact)이 발생했는지, 작업이 어떻게 진행되는지를 계산한다. 이러한 계산의 정확성이 학습된 정책의 품질을 크게 좌우한다.

시뮬레이션 환경은 복도를 이동하는 자율이동로봇(Autonomous Mobile Robot, AMR), 부품을 조립하는 매니퓰레이터(Manipulator), 다양한 지형을 걷는 보행 로봇(Legged Robot), 또는 안정적인 비행을 수행하는 드론(Drone) 등 다양한 로봇 시스템을 표현할 수 있다. 학습 원리는 모두 동일하다. 자율이동로봇의 경우 시뮬레이터에는 지도(Map), 선반(Shelf), 문(Door), 경사로(Ramp), 보행자(Pedestrian), 다른 로봇, 충전기(Charging Station), 교통 규칙(Traffic Rule) 등이 포함될 수 있다.

에이전트는 이 환경에서 내비게이션(Navigation), 제어(Control), 도킹(Docking), 충돌 회피(Collision Avoidance), 플릿 협업(Fleet Coordination)을 학습할 수 있다. 시뮬레이션의 상태(State)는 실제 운용 시 사용할 수 있는 정보와 동일해야 한다. 여기에는 로봇의 위치와 자세(Pose), 속도(Velocity), 라이다(LiDAR), 카메라(Camera), 깊이 정보(Depth Data), 배터리 상태(Battery State), 휠 속도, 지역 지도(Local Map), 목표 방향, 주변 장애물의 움직임 등이 포함될 수 있다. 학습 과정에서는 특권 정보(Privileged Information)를 사용할 수도 있지만 매우 신중해야 한다.

시뮬레이터는 실제 센서가 정확하게 측정할 수 없는 위치, 속도, 접촉 상태 등을 완벽하게 알고 있다. 정책이 이러한 정보에 의존하면 실제 환경에서는 정상적으로 동작하지 못할 수 있다. 특권 정보는 일반적으로 크리틱(Critic), 교사 모델(Teacher Model), 또는 보상 계산에만 사용된다. 실제 배포되는 정책은 현실적인 센서 관측값만 입력으로 사용한다. 이를 통해 효율적인 학습과 현실적인 운용을 동시에 달성할 수 있다. 행동 인터페이스(Action Interface) 역시 실제 시스템과 일치해야 한다.

정책은 휠 토크(Wheel Torque), 조향각(Steering Angle), 목표 속도(Target Velocity), 지역 웨이포인트(Local Waypoint), 관절 명령(Joint Command), 또는 목표 궤적(Trajectory)을 생성할 수 있다. 시뮬레이션과 실제 시스템의 인터페이스가 다르면 정책 이전(Policy Transfer)이 어려워진다. 시뮬레이션 기반 강화 학습은 여러 수준(Level)의 제어를 수행할 수 있다. 상위 정책은 목표나 경로를 선택하고, 하위 정책은 실제 이동을 생성한다. 또 다른 정책은 조작(Manipulation), 보행(Locomotion), 균형 유지(Balancing)를 위한 토크(Torque)나 힘(Force)을 직접 제어할 수도 있다.

보상 함수(Reward Function)는 시뮬레이션에서 에이전트의 행동을 평가한다. 작업 완료(Task Completion), 안전(Safety), 부드러운 움직임(Smoothness), 속도(Speed), 에너지 효율(Energy Efficiency), 추종 정확도(Tracking Accuracy), 규칙 준수(Rule Compliance)에 보상을 주고, 충돌(Collision), 불안정한 움직임, 과도한 힘, 시간 초과, 제약 조건 위반에는 패널티(Penalty)를 줄 수 있다. 시뮬레이션에서는 모든 내부 변수에 접근할 수 있으므로 보상 설계를 더욱 쉽게 분석할 수 있다.

정확한 거리, 접촉력(Contact Force), 에너지 소비(Energy Consumption), 궤적 오차(Trajectory Error), 성공 여부를 계산할 수 있으며, 정책이 특정 보상을 받는 이유도 시각적으로 확인할 수 있다. 그러나 시뮬레이션에서 잘 동작하는 보상 함수가 실제 환경에서도 반드시 좋은 결과를 만드는 것은 아니다. 에이전트는 시뮬레이터의 모델링 오류나 보상 함수의 허점을 이용할 수 있으므로 학습 과정에서 지속적인 검토가 필요하다. 예를 들어 내비게이션 정책은 시뮬레이터의 충돌 모델이 지나치게 관대하면 장애물에 매우 가까이 지나가는 전략을 학습할 수 있다.

매니퓰레이터는 비현실적인 접촉 모델을 이용할 수도 있으며, 보행 로봇은 실제 액추에이터로는 수행할 수 없는 움직임을 학습할 수도 있다. 이러한 사례는 시뮬레이션의 정확성이 단순히 시각적인 품질만을 의미하지 않는다는 점을 보여준다. 화면이 현실적으로 보이더라도 마찰(Friction), 지연(Delay), 질량(Mass), 충돌 응답(Collision Response), 센서 노이즈(Sensor Noise), 액추에이터 동역학(Actuator Dynamics)이 잘못되면 실제 시스템에서는 실패할 수 있다. 시뮬레이터는 로봇의 운동학(Kinematics)과 동역학(Dynamics)을 필요한 수준으로 정확하게 표현해야 한다.

고수준 경로 계획에는 운동학 모델만으로 충분할 수 있지만, 토크 제어, 균형 유지, 접촉, 구동력(Traction) 제어에는 정확한 동역학 모델이 필요하다. 로봇의 질량(Mass), 관성(Inertia), 무게 중심(Center of Gravity), 바퀴 반지름(Wheel Radius), 서스펜션(Suspension), 관절 한계(Joint Limit), 모터 출력(Motor Strength), 제동력(Braking Force), 감쇠(Damping)는 모두 실제 움직임에 영향을 준다. 이러한 값이 잘못되면 정책은 실제 로봇에서 사용할 수 없는 제어 전략을 학습하게 된다.

액추에이터 모델은 포화(Saturation), 지연, 데드존(Dead Zone), 변화율 제한(Rate Limit), 전류 제한(Current Limit), 열 특성(Thermal Effect) 등을 포함해야 한다. 실제 액추에이터는 무한한 힘을 즉시 생성할 수 없으므로 이러한 특성을 무시하면 비현실적인 정책이 만들어진다. 센서 시뮬레이션도 매우 중요하다. 실제 센서는 노이즈, 바이어스(Bias), 양자화(Quantization), 데이터 누락(Missing Value), 제한된 탐지 거리, 가림(Occlusion), 움직임 왜곡(Motion Distortion), 시간 오차 등을 포함한다. 완벽한 센서 데이터만으로 학습된 정책은 실제 환경에서 쉽게 성능이 저하된다.

라이다 시뮬레이션은 거리 제한(Range Limit), 각도 해상도(Angular Resolution), 데이터 누락(Dropout), 반사 오류, 장애물 가림 등을 표현해야 한다. 카메라 시뮬레이션은 조명(Lighting), 질감(Texture), 블러(Blur), 노출(Exposure), 렌즈 효과 등을 포함해야 한다. 깊이 카메라(Depth Camera)는 반사체나 투명한 물체에서 데이터가 누락될 수 있다. 관성 센서(IMU)는 바이어스와 드리프트(Drift)를 가지며, 휠 오도메트리(Wheel Odometry)는 슬립(Slip)의 영향을 받는다. 이러한 현실적인 특성을 추가하면 정책의 강인성(Robustness)이 향상된다.

통신(Communication)과 계산(Computation)도 모델링되어야 한다. 제어 명령은 네트워크 지연(Network Delay), 패킷 손실(Packet Loss), 스케줄링 변동(Scheduling Variation), 비동기 센서 입력 등의 영향을 받을 수 있다. 이는 플릿 시스템(Fleet System)이나 클라우드 기반 로봇에서 특히 중요하다. 시뮬레이션 시간 간격(Time Step)은 환경이 얼마나 자주 업데이트되는지를 결정한다. 작은 시간 간격은 높은 정확도를 제공하지만 계산량이 증가한다. 반대로 큰 시간 간격은 실행 속도는 빠르지만 충돌이나 빠른 접촉을 놓칠 수 있다. 정책의 업데이트 주기는 물리 시뮬레이션 주기와 반드시 같을 필요는 없다.

시뮬레이터는 높은 주기로 동역학을 계산하고, 강화 학습 정책은 더 낮은 주기로 행동을 선택할 수 있다. 이는 실제 시스템에서 모터 제어와 의사결정이 서로 다른 주기로 동작하는 것과 유사하다. 병렬 시뮬레이션(Parallel Simulation)은 시뮬레이션 기반 강화 학습의 가장 큰 장점 가운데 하나이다. 수백에서 수천 개의 환경을 CPU나 GPU에서 동시에 실행할 수 있으며, 학습 시간을 획기적으로 단축할 수 있다. 각 환경은 서로 다른 시작 위치, 지도, 적재물, 물리 파라미터를 사용할 수 있다. 이러한 다양한 경험은 하나의 고정된 환경만 반복하는 것보다 훨씬 높은 일반화(Generalization) 성능을 제공한다.

벡터화 시뮬레이션(Vectorized Simulation)은 동일한 연산을 여러 환경에 동시에 적용한다. GPU 기반 시뮬레이터는 물리 계산과 신경망 추론을 병렬 수행하여 매우 높은 학습 처리량을 제공할 수 있다. 이러한 고속 시뮬레이션은 PPO(Proximal Policy Optimization)와 같은 온-폴리시(On-Policy) 알고리즘에서 특히 유용하며, 오프-폴리시(Off-Policy) 알고리즘에서도 다양한 경험을 빠르게 리플레이 버퍼(Replay Buffer)에 저장할 수 있다. 그러나 시뮬레이션이 빠르다고 해서 반드시 좋은 정책이 만들어지는 것은 아니다. 환경이 지나치게 단순하면 학습은 빠르지만 실제 환경으로 이전되는 성능은 매우 낮을 수 있다.

따라서 학습 속도와 시뮬레이션 정확성 사이의 균형이 중요하다. 직접 제어, 조작, 접촉, 험지 주행과 같은 작업은 높은 정확도의 시뮬레이터가 필요하다. 반면 경로 선택, 작업 할당, 플릿 관리와 같은 고수준 작업은 상대적으로 단순한 시뮬레이터로도 충분할 수 있다. 다단계 시뮬레이션(Multi-Stage Simulation)은 이러한 두 가지를 결합한다. 초기 학습은 단순한 환경에서 수행하고, 이후에는 더욱 현실적인 물리 모델을 사용하여 최종 검증을 수행함으로써 학습 비용과 이전 성능을 동시에 향상시킬 수 있다. 커리큘럼 학습(Curriculum Learning)은 시뮬레이션에서 널리 사용된다. 에이전트는 쉬운 문제부터 시작하여 점차 어려운 환경을 경험한다.

예를 들어 이동 로봇은 열린 공간에서 시작하여 정적 장애물, 좁은 통로, 움직이는 사람, 복잡한 교통 환경으로 난이도를 높일 수 있다. 매니퓰레이터는 먼저 목표 위치에 도달하는 작업을 학습한 뒤, 물체를 잡고, 자세 오차를 처리하며, 최종적으로 정밀 조립 작업을 수행하도록 학습할 수 있다. 보행 로봇은 평지에서 시작하여 경사로, 계단, 자갈길, 외란 환경으로 확장할 수 있다. 커리큘럼은 학습을 지원할 수 있는 속도로 난이도를 증가시켜야 한다. 너무 빠르게 어려워지면 보상을 거의 받지 못하고, 너무 오랫동안 쉬운 문제만 수행하면 단순한 행동에 과적합(Overfitting)될 수 있다. 자동 커리큘럼(Automatic Curriculum)은 에이전트의 성능에 따라 난이도를 자동으로 조절한다.

성공률이 높아질수록 장애물 밀도, 외란 크기, 정밀도 요구사항, 초기 상태 다양성을 점차 증가시킨다. 절차적 환경 생성(Procedural Generation)은 새로운 환경을 자동으로 생성한다. 지도(Map), 방(Room), 복도(Corridor), 장애물 배치, 물체 위치, 지형(Terrain), 교통 상황(Traffic Pattern)을 매 에피소드마다 새롭게 생성할 수 있다. 이를 통해 에이전트는 특정 환경을 단순히 암기(Memorization)하는 것이 아니라 일반적인 내비게이션과 제어 원리를 학습하게 된다. 도메인 랜덤화(Domain Randomization)는 하나의 정확한 모델을 만드는 대신 다양한 환경을 생성하는 방법이다. 정책은 여러 종류의 환경을 경험하면서 보다 강인한 행동을 학습한다.

물리 파라미터 랜덤화는 질량, 마찰, 관성, 무게 중심, 모터 출력, 바퀴 크기, 서스펜션, 적재물, 배터리 전압, 액추에이터 지연 등을 변화시킨다. 센서 랜덤화는 노이즈, 바이어스, 탐지 거리, 시야(Field of View), 해상도, 보정 오차(Calibration Error), 데이터 누락, 조명, 질감, 지연 등을 변화시킨다. 환경 랜덤화는 지형, 장애물 행동, 날씨, 교통 밀도, 지도 구조 등을 변경한다. 목표는 실제 환경이 이러한 다양한 시뮬레이션 환경 가운데 하나처럼 보이도록 만드는 것이다. 다양한 조건에서 학습한 정책은 실제 환경의 변화에도 더욱 강인하다. 하지만 랜덤화 범위는 현실적이어야 한다.

범위가 너무 넓으면 학습이 어려워지고 정책이 지나치게 보수적으로 될 수 있으며, 너무 좁으면 실제 환경에서 쉽게 실패할 수 있다. 시스템 식별(System Identification)은 적절한 랜덤화 범위를 설정하는 데 사용된다. 실제 로봇에서 측정한 모터 응답, 마찰, 지연, 센서 노이즈 등을 이용하여 시뮬레이터를 보정한다. 도메인 랜덤화는 도메인 적응(Domain Adaptation)과 함께 사용할 수 있다. 랜덤화는 넓은 범위의 강인성을 제공하고, 도메인 적응은 실제 환경과 시뮬레이션의 차이를 더욱 정밀하게 줄여준다. 가장 큰 문제는 시뮬레이션-현실 간 차이(Simulation-to-Reality Gap, Sim-to-Real Gap)이다.

이는 가상 환경과 실제 환경의 차이 때문에 정책 성능이 저하되는 현상을 의미한다. 이 차이는 물리 모델 오류, 센서 차이, 액추에이터 지연, 장비 마모, 환경 복잡성, 사람의 행동, 통신 시간, 작업 정의 부족 등 다양한 원인으로 발생한다. 비전 기반 정책에서는 시각적 차이(Visual Gap)가 매우 중요하다. 실제 영상에는 조명 변화, 반사, 먼지, 그림자, 블러 등이 존재한다. 광사실적 렌더링(Photorealistic Rendering)이나 표현 학습(Representation Learning)은 이러한 차이를 줄이는 데 도움이 된다. 제어 정책에서는 동역학 차이(Dynamic Gap)가 더욱 중요하다. 마찰, 지연, 관성, 토크 응답의 작은 오차도 실제 시스템에서는 제어 실패를 유발할 수 있다.

Sim-to-Real 이전은 도메인 랜덤화, 시뮬레이터 보정, 강인한 제어 목표, 실제 데이터 기반 미세 조정(Fine-Tuning), 잔차 학습(Residual Learning), 적응 네트워크(Adaptation Network), 단계적 배포(Progressive Deployment) 등을 이용하여 수행할 수 있다. 잔차 학습은 기존 제어기가 기본 동작을 수행하는 경우 특히 유용하다. 강화 학습은 기존 명령을 조금만 수정하면 되므로 완벽한 시뮬레이션에 의존하지 않으며 안전성도 높다. 교사-학생 학습(Teacher-Student Learning)은 교사 정책이 완전한 상태를 이용하여 학습하고, 학생 정책은 실제 센서 입력만을 사용하여 교사를 모방하는 방식이다.

비대칭 액터-크리틱(Asymmetric Actor-Critic) 역시 같은 개념을 사용한다. 크리틱은 특권 정보를 이용하여 가치(Value)를 추정하고, 액터는 실제 환경에서 사용할 수 있는 관측값만 이용한다. 표현 학습(Representation Learning)은 시뮬레이션과 실제 데이터를 공통된 특징 공간(Feature Space)으로 변환하여 정책이 원시 영상(Raw Image)이 아닌 안정적인 특징을 기반으로 의사결정을 수행하도록 한다. 실제 데이터를 이용한 미세 조정은 시뮬레이션 이후 성능을 향상시킬 수 있지만, 실제 환경에서 무제한으로 강화 학습을 수행하는 것은 매우 위험하고 비용도 크다. 따라서 실제 환경에서의 업데이트는 엄격하게 제한되어야 한다.

오프라인 강화 학습(Offline Reinforcement Learning)은 실제 운행 데이터를 이용하여 시뮬레이션 정책을 개선할 수 있다. 위험한 탐험을 피할 수 있지만 데이터셋의 품질과 다양성에 크게 의존한다. 섀도우 모드(Shadow Mode)는 실제 센서를 입력받아 정책이 행동을 생성하지만 실제 제어는 기존 시스템이 수행하는 방식이다. 이를 통해 정책이 예상하지 못한 행동을 하는 상황을 분석할 수 있다. 섀도우 모드는 제어 위험 없이 실제 데이터를 수집할 수 있는 매우 유용한 방법이다. 문제가 되는 상황을 시뮬레이션에서 다시 재현하여 다음 학습에 사용할 수 있다.

하드웨어-인-더-루프(Hardware-in-the-Loop, HIL)는 실제 컴퓨터, 제어기, 통신 장치는 그대로 사용하고 로봇만 시뮬레이션하는 방식이다. 이를 통해 추론 지연(Inference Latency), 메시지 타이밍(Message Timing), 소프트웨어 통합, 안전 시스템, 하드웨어 인터페이스를 실제와 동일한 환경에서 검증할 수 있다. 소프트웨어-인-더-루프(Software-in-the-Loop, SIL)는 실제 로봇 소프트웨어를 시뮬레이터와 연결하여 실행하는 방식이다. ROS2 기반 로봇에서는 매우 중요한 검증 방법이다. 시뮬레이션은 드물지만 위험한 상황도 쉽게 생성할 수 있다.

갑작스러운 보행자 출현, 센서 고장, 위치 추정 실패(Localization Loss), 브레이크 성능 저하, 통신 장애, 극한 지형 등을 반복적으로 테스트할 수 있다. 이러한 상황은 실제 환경에서는 거의 발생하지 않지만 안전성 측면에서는 반드시 검증되어야 한다. 시뮬레이션은 이러한 안전 시나리오를 구축하는 가장 효율적인 방법이다. 적대적 시나리오(Adversarial Scenario)는 정책의 약점을 찾기 위해 의도적으로 실패를 유도하는 환경이다. 장애물, 외란, 센서 오류 등을 조합하여 정책의 취약점을 찾아낼 수 있다. 시나리오 커버리지(Scenario Coverage)도 체계적으로 관리해야 한다. 속도, 적재물, 지형, 교통량, 센서 상태, 작업 종류의 다양한 조합이 충분히 검증되었는지 확인해야 한다.

평균 성능이 아무리 높더라도 특정 환경에서 실패한다면 산업 현장에서는 허용되기 어렵다. 커버리지 분석은 이러한 취약 영역을 찾는 데 매우 중요하다. 학습 평가와 실제 배포 평가는 구분되어야 한다. 학습은 보상 함수를 이용하지만, 실제 검증에서는 정책이 조작할 수 없는 독립적인 성능 지표를 사용해야 한다. 내비게이션에서는 성공률, 충돌률, 최소 안전 거리, 이동 거리, 이동 시간, 교착 상태(Deadlock), 에너지 소비, 사람의 개입 횟수, 부드러운 움직임 등을 평가해야 한다.

제어에서는 추종 오차, 오버슈트(Overshoot), 정착 시간(Settling Time), 안정성(Stability), 토크 사용량, 저크(Jerk), 에너지 소비, 열 부하(Thermal Load), 제약 조건 위반 등을 평가해야 한다. 조작에서는 파지 성공률(Grasp Success), 최대 접촉력, 배치 정확도, 작업 시간, 물체 손상, 자세 오차 복원 능력 등을 측정해야 한다. 정책은 학습하지 않은 새로운 지도, 적재물, 장애물, 외란 환경에서도 평가되어야 한다. 이것이 일반화(Generalization) 능력을 평가하는 가장 중요한 방법이다. 장시간 시뮬레이션(Long-Term Simulation)은 드리프트(Drift), 반복 진동, 에너지 비효율, 드문 오류 누적 등을 발견할 수 있다.

짧은 에피소드에서는 이러한 문제가 나타나지 않을 수도 있다. 시뮬레이션에서는 정책의 실패 처리(Failure Handling)도 함께 검증해야 한다. 센서가 고장 나거나 신뢰도가 낮아지거나 모델이 종료되는 경우 로봇이 어떻게 대응하는지를 확인해야 한다. 독립적인 안전 계층(Safety Layer)은 시뮬레이션과 실제 환경 모두에서 항상 활성화되어야 한다. 속도 제한, 토크 제한, 지오펜스(Geofence), 충돌 방지, 비상 정지 등을 지속적으로 감시해야 한다. 정책이 실제 운용 환경의 제약 조건을 이해하도록 하기 위해서는 학습 과정에서도 안전 계층을 포함하는 것이 바람직하다.

안전 실드(Safety Shield)는 위험한 행동을 실행 전에 수정하며, 이러한 개입은 로그로 기록되고 과도한 의존은 보상에서 패널티를 받을 수 있다. 백업 제어기(Fallback Controller)도 시뮬레이션에서 충분히 검증해야 한다. 정책이 불확실하면 기존 경로 계획기, 기존 제어기, 저속 모드, 안전 정지로 자동 전환할 수 있어야 한다. 불확실성 추정(Uncertainty Estimation)은 학습하지 않은 상태나 센서 오류를 생성하여 함께 평가할 수 있다. 신뢰성 있는 시스템은 불확실성이 높아질수록 속도를 줄이고 백업 제어기를 사용하거나 사람의 개입을 요청해야 한다. 목표는 단순히 성능을 높이는 것이 아니라 정책을 신뢰해서는 안 되는 상황을 스스로 인식하는 것이다.

시뮬레이션 기반 강화 학습에서는 데이터와 실험 관리도 매우 중요하다. 학습 설정, 랜덤 시드(Random Seed), 시뮬레이터 버전, 정책 체크포인트(Checkpoint), 보상 함수, 랜덤화 범위 등을 모두 기록해야 한다. 엄격한 버전 관리가 없으면 결과를 재현하기 어렵고 서로 다른 정책의 차이를 분석하기도 어렵다. 재현성(Reproducibility)은 산업용 시스템에서 매우 중요한 요구사항이다. 시뮬레이터의 물리 엔진, 센서 모델, 충돌 메시(Collision Mesh), 시간 설정 등이 변경되면 정책의 행동도 달라질 수 있으므로 소프트웨어와 동일한 수준의 버전 관리가 필요하다.

학습 로그에는 보상 요소, 에피소드 결과, 안전 위반, 환경 파라미터, 행동 분포(Action Distribution), 학습 곡선(Learning Curve) 등이 포함되어야 한다. 모든 체크포인트는 학습 종료 후가 아니라 학습 과정에서도 지속적으로 평가해야 한다. 가장 높은 보상을 얻은 정책이 항상 가장 안전하거나 가장 강인한 정책은 아니다. 자동 평가 파이프라인(Evaluation Pipeline)은 모든 체크포인트를 동일한 시나리오에서 비교하여 안전성, 효율성, 일반화 능력을 객관적으로 평가할 수 있도록 해준다. 시뮬레이션 비용도 고려해야 한다. 대규모 학습은 GPU, CPU, 저장 공간, 그리고 상당한 개발 비용을 요구한다. 매우 정교한 물리 엔진과 렌더링은 실험 비용을 크게 증가시킨다.

효율적인 환경 설계, 병렬 실행, 다중 수준 시뮬레이션(Mixed-Fidelity Simulation), 목표 지향적 시나리오 생성(Targeted Scenario Generation)을 이용하면 이러한 비용을 줄일 수 있다. 시뮬레이션 도구마다 목적이 다르다. 어떤 도구는 물리 엔진에 강점을 가지고 있고, 어떤 도구는 광사실적 렌더링, 대규모 병렬 학습, 교통 시뮬레이션, ROS 통합 등에 특화되어 있다. AMR 프로젝트는 지도 생성, 라이다 시뮬레이션, 보행자 모델, ROS2 인터페이스를 중시할 수 있으며, 매니퓰레이션 프로젝트는 접촉, 힘, 마찰, 관절 모델을 더욱 중요하게 고려해야 한다.

보행 로봇 프로젝트는 GPU 기반의 고속 물리 엔진을, 자율주행 프로젝트는 교통 흐름, 도로망, 카메라, 레이더(Radar), 라이다, 다양한 시나리오 라이브러리를 더욱 중요하게 사용할 수 있다. 시뮬레이션 기반 강화 학습은 전체 로봇 개발 프로세스의 일부로 사용될 때 가장 큰 효과를 발휘한다. 요구사항, 시스템 모델링, 학습, 안전 설계, 검증, 배포, 모니터링, 현장 데이터 피드백이 모두 연결되어야 한다. 실제 환경에서 수집된 데이터가 증가할수록 시뮬레이터도 함께 발전해야 한다. 실패 사례, 근접 사고, 센서 오류, 특이 상황을 시뮬레이션에서 재현하고 이후 학습에 반영해야 한다. 이러한 과정은 폐쇄형 개선 루프(Closed Improvement Loop)를 형성한다.

실제 환경에서 문제를 발견하고, 시뮬레이션에서 재현하며, 강화 학습으로 정책을 개선하고, 단계적인 검증을 통해 다시 현장에 배포하는 순환 구조가 만들어진다. AMR에서는 이러한 과정을 통해 내비게이션, 도킹, 구동력 제어, 에너지 관리, 교통 상호작용, 복구 행동을 실제 장비를 위험에 노출시키지 않고 지속적으로 개선할 수 있다. 시뮬레이션의 가장 큰 장점은 단순히 학습 속도가 빠르다는 것이 아니다. 실패 상황과 엣지 케이스(Edge Case)를 포함한 매우 다양한 환경을 반복 가능하고 측정 가능한 방식으로 실험할 수 있다는 점이다. 반대로 가장 큰 한계는 시뮬레이터가 결코 실제 환경과 완전히 동일할 수 없다는 점이다.

따라서 시뮬레이션에서 학습한 정책은 실제 환경으로 이전하기 위한 추가적인 공학적 검증과 안전 설계가 반드시 필요하다. 성공적인 시뮬레이션 기반 강화 학습은 현실적인 인터페이스, 정확한 동역학, 다양한 시나리오, 적절한 랜덤화, 독립적인 평가 지표, 단계적인 배포, 그리고 실제 환경으로부터의 지속적인 피드백을 기반으로 한다. 이러한 요소들이 통합될 때 시뮬레이션은 단순한 학습 도구를 넘어, 강화 학습 알고리즘과 실제 산업용 로봇 제품을 연결하는 핵심 개발 및 검증 플랫폼으로 발전할 수 있다. 궁극적인 목표는 가상 환경에서 뛰어난 성능을 보이는 정책을 만드는 것이 아니다.

실제 환경의 불확실성과 다양한 변화 속에서도 안전하고 효율적이며 강인하게 동작하는 로봇을 구현하는 것이 시뮬레이션 기반 강화 학습의 최종 목표이다.

##  

## 09.6 Sim-to-Real Transfer

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

Sim-to-real transfer is the process of moving a policy, model, or controller trained in simulation into a physical robot. The goal is to preserve the performance learned in the virtual environment despite differences in sensors, actuators, dynamics, timing, and operating conditions. Simulation allows reinforcement learning agents to collect large amounts of experience safely and quickly.

However, a policy that succeeds in simulation may fail on a real robot because the simulated world is only an approximation of reality. The difference between simulation and physical operation is called the sim-to-real gap. This gap includes every mismatch that can change how the robot observes, decides, and acts after deployment.

The gap may originate from inaccurate physics, imperfect sensor models, actuator delays, communication latency, environmental variability, unmodeled disturbances, or differences between the simulated task and the real operational objective. A simulator may reproduce the robot\'s appearance accurately while still representing its dynamics poorly.

For reinforcement learning control, errors in friction, mass, inertia, damping, motor response, or contact behavior can be more damaging than visual differences. For perception-based policies, the visual gap is often critical.

Real images contain shadows, reflections, dirt, blur, exposure changes, lens distortion, weather effects, and objects that may never appear in the simulated training environment. LiDAR data also differs between simulation and reality. Real scans may contain missing returns, multipath reflections, varying intensity, limited range, motion distortion, dust, rain, or partial occlusion.

Depth sensors may fail near reflective, dark, transparent, or distant surfaces. Policies trained on perfect depth images can become highly unreliable when deployed in industrial or outdoor environments. Actuator behavior introduces another major source of mismatch. Real motors have delay, saturation, dead zones, current limits, temperature effects, backlash, and manufacturing variation.

A simulated command may produce an immediate and exact response, while the physical robot may respond slowly or differently because of battery voltage, payload, tire condition, or mechanical wear. Timing mismatch also affects transfer.

Sensor messages may arrive asynchronously, neural network inference may vary in latency, and control commands may be delayed by software scheduling or communication networks. A policy trained with perfectly synchronized inputs may become unstable when real sensor streams contain different timestamps. Time synchronization and delay modeling are therefore central to successful transfer.

The physical environment is also more complex than simulation. Real floors may be uneven, slippery, damaged, wet, dusty, or covered with small objects that were not modeled during training. Human behavior is difficult to simulate accurately. Pedestrians may hesitate, change direction suddenly, ignore expected traffic patterns, or react differently to the robot.

Other robots, forklifts, doors, elevators, carts, and temporary construction zones further increase the uncertainty of real operation. The transfer process must account for this diversity. The first step in sim-to-real engineering is to define the operational domain. Engineers must specify the expected terrain, payload, speed, lighting, weather, sensor condition, traffic density, and task range.

A transfer strategy should focus on this defined domain rather than attempting to prepare the policy for every possible situation. An excessively broad objective may increase training cost and reduce policy performance. System identification is used to reduce model mismatch.

Engineers collect data from the real robot and estimate parameters such as mass, inertia, friction, motor response, delay, steering behavior, and braking characteristics. The estimated parameters are then used to calibrate the simulator. Calibration does not make the simulator perfect, but it improves the accuracy of the most important physical relationships.

Different experiments may be required for different parameters. Straight-line acceleration can reveal motor response, turning tests can identify steering dynamics, and slope tests can provide information about traction and braking. Sensor calibration is equally important.

Camera intrinsics, LiDAR alignment, depth scale, IMU bias, wheel radius, and time offsets should match the real platform as closely as possible. Even after calibration, physical parameters continue to vary. Payload changes, tire wear, battery condition, temperature, and component aging make one fixed simulator insufficient.

Domain randomization addresses this problem by varying simulation parameters during training. The agent learns to succeed across a distribution of environments rather than relying on one exact model. Physical randomization may change mass, friction, center of gravity, inertia, motor strength, wheel radius, suspension, damping, braking force, or actuator delay.

Sensor randomization may vary noise, bias, dropout, field of view, calibration, resolution, latency, and range. Visual randomization may alter lighting, texture, color, shadow, object appearance, and camera exposure. Environmental randomization can change map structure, terrain, obstacle placement, traffic behavior, weather, and starting conditions.

The real world should ideally fall within the range represented during training. Randomization must be carefully bounded. Unrealistically wide ranges can make learning unstable and cause the policy to become excessively conservative. Ranges that are too narrow provide little protection against real variation.

Real measurements should therefore guide the center and width of each randomized parameter. Automatic domain randomization can adjust variation according to policy performance. As the agent becomes successful, the training system gradually introduces more difficult parameter combinations. This creates a curriculum in which the policy first learns the basic task and later learns robustness.

It prevents excessive uncertainty from overwhelming the early learning process. Domain randomization is especially effective when the real system is only one of many plausible physical models. It encourages the policy to focus on stable relationships rather than simulator-specific details. Domain adaptation provides another transfer method.

It attempts to reduce the difference between simulated and real data distributions after training or during deployment. For visual policies, adaptation may transform simulated images to resemble real images or learn a representation in which both domains appear similar. Feature-level adaptation is often safer than direct image translation.

The policy acts on shared latent features rather than depending on exact pixel appearance. Representation learning can produce features that are invariant to lighting, texture, weather, or sensor noise. Pretraining on diverse real and simulated data can support this objective. Teacher-student learning is another common strategy.

A teacher policy is trained using privileged simulator information, while a student learns to reproduce its behavior using realistic observations. The teacher may access exact position, velocity, contact state, or obstacle trajectory. The student receives only the sensor inputs available on the physical robot.

This approach allows efficient learning while preserving a deployable observation interface. The student benefits from the teacher\'s strong policy without depending on unavailable information. Asymmetric actor-critic methods follow a similar structure. The critic uses full simulated state to estimate value accurately, while the actor receives only realistic observations.

The actor is the component deployed on the robot. The critic is used only during training and may depend on information that cannot be measured in operation. Residual reinforcement learning reduces transfer risk by combining a conventional controller with a learned correction. The baseline controller handles the main task, while the RL policy improves performance.

The learned residual may compensate for model error, friction changes, payload variation, or small tracking errors. Since the policy does not control the entire system, transfer becomes easier and safer. A well-designed residual is usually limited in magnitude. The baseline controller remains responsible for basic stability and the RL policy makes bounded adjustments.

Hybrid control can also combine reinforcement learning with model predictive control. RL may learn a cost function, disturbance estimate, dynamic correction, or terminal value. The model predictive controller then produces actions while enforcing speed, acceleration, torque, or safety constraints. This structure preserves explicit control limits during deployment.

Robust control objectives can improve transfer. Instead of optimizing performance under one nominal model, the policy is trained to perform well under uncertainty and disturbance. The reward may include penalties for sensitivity, oscillation, excessive control effort, unstable contact, or dependence on exact state values.

Policies that use large, aggressive commands may perform well in ideal simulation but transfer poorly. More moderate control often tolerates model error better. Action smoothing and rate limits can reduce sensitivity to timing and actuator mismatch. They also lower mechanical stress and improve predictability. Observation normalization must be consistent between simulation and deployment.

Differences in units, scaling, clipping, or coordinate conventions can cause immediate policy failure. Every sensor and state variable should use the same definition in both environments. Frame conventions, angle direction, velocity sign, and timestamp interpretation must be verified. The action interface must also match exactly.

A target velocity in simulation should correspond to the same physical meaning, update rate, limits, and downstream controller behavior on the real robot. Software integration errors can create a larger gap than the learning algorithm itself. Message formats, coordinate frames, timing, safety overrides, and actuator commands require end-to-end verification.

Software-in-the-loop testing connects the actual robot software stack to the simulator. The real navigation, control, and communication software processes simulated sensor data and generates normal commands. This test reveals interface errors while keeping the physical robot safe. It also reduces the difference between the training pipeline and production software.

Hardware-in-the-loop testing adds real computers, controllers, networks, or embedded devices to the simulated environment. The robot body may remain virtual, but the actual inference hardware and communication paths are used. This allows realistic testing of latency, scheduling, and integration behavior. Hardware-in-the-loop testing is particularly useful for edge AI systems.

It can reveal thermal throttling, memory limits, network delay, and timing jitter before physical movement begins. Real-time performance must be validated before deployment. Average inference speed is not enough because occasional long delays may destabilize control. Worst-case latency, missed deadlines, and message jitter should be measured under realistic CPU, GPU, network, and logging loads.

A policy should also be tested with sensor dropout and delayed inputs. It must either remain stable or trigger a safe fallback when the observation quality becomes unacceptable. Uncertainty estimation supports safer transfer. The policy or a separate model estimates whether the current state is similar to the training distribution.

High uncertainty may indicate an unfamiliar payload, unusual terrain, damaged sensor, rare obstacle, or incorrect environmental condition. When uncertainty increases, the robot can reduce speed, use a classical controller, request assistance, or enter a safe-stop mode. Ensemble models are one way to estimate uncertainty.

Several policies or predictors are trained, and disagreement between their outputs indicates low confidence. Distance-based methods compare current features with the training data distribution. Bayesian approximations and dedicated confidence networks can also be used. Uncertainty estimates should not be treated as perfect guarantees.

They are additional signals that support conservative decision making and runtime monitoring. Shadow mode is an important stage of sim-to-real deployment. The learned policy receives live sensor data and generates proposed actions, but it does not control the robot. The existing controller remains active while engineers compare the proposed RL commands with the actual commands.

Shadow mode reveals how the policy behaves under real sensor noise, timing, traffic, and environment conditions without creating movement risk. Disagreement cases should be reviewed carefully. Some differences may represent useful improvements, while others may reveal unsafe or unfamiliar behavior. These cases can be replayed or recreated in simulation.

They become valuable scenarios for retraining and validation. After shadow testing, the policy may enter pilot deployment. It should operate only under limited speed, restricted areas, selected payloads, or low-risk missions. A safety operator or remote supervisor may remain available during the pilot stage. Detailed logs should be collected for every action and intervention.

The deployment scope should expand gradually only after the policy meets predefined performance and safety criteria. Progressive rollout may begin with one robot, then a small group, and finally a larger fleet. Each stage should support immediate rollback. A rollback mechanism must restore the previous verified controller or policy version when abnormal behavior is detected.

Independent safety systems must remain active throughout transfer and deployment. Reinforcement learning should not replace emergency stops, safety scanners, geofences, speed limits, or certified safety control. A safety shield can examine the proposed RL action before execution. Unsafe commands are modified, limited, or rejected.

The shield may enforce braking distance, collision boundaries, torque limits, joint limits, slope limits, human clearance, or maximum speed. Training should include the same safety shield used in deployment. Otherwise, the policy may repeatedly request actions that are always overridden in the real system.

Frequent safety intervention indicates that the policy is poorly aligned with operational constraints. Intervention frequency should therefore be monitored as a deployment metric. Fallback control is another essential component. When the policy fails, becomes uncertain, or receives invalid input, the robot should switch to a verified alternative.

Fallback options include a classical planner, PID controller, MPC controller, reduced-speed mode, controlled stop, or remote assistance. The transition between RL and fallback control must be smooth. Sudden switching can create discontinuous commands and instability. Blending methods can gradually reduce the RL contribution while increasing the baseline controller contribution.

State machines can define when RL control is allowed and when deterministic behavior must take priority. Real-world fine-tuning may improve performance after initial transfer. However, unrestricted online reinforcement learning is rarely acceptable for industrial robots. Exploration on physical hardware can cause collisions, wear, overheating, or unsafe interaction.

Real-world updates should therefore be limited and controlled. Offline reinforcement learning can use recorded real trajectories to refine the policy without executing new exploratory actions. The dataset may include normal operation, safety interventions, near misses, difficult docking events, wheel slip, and recovery behavior. The coverage of the dataset is critical.

A policy cannot reliably learn behavior for states and actions that are absent from the data. Conservative offline methods reduce the tendency to select actions far outside the recorded behavior distribution. Fine-tuning may also use supervised learning. The policy can imitate a trusted controller or human correction in situations where its simulated behavior is inadequate.

A small amount of carefully selected real data may be more valuable than a large amount of repetitive nominal data. Active data selection identifies situations with high uncertainty, high disagreement, or poor performance. These cases are prioritized for labeling, simulation reconstruction, or retraining. Evaluation after transfer must use independent metrics.

The training reward alone does not prove safe or useful real-world behavior. For navigation, metrics may include mission success, collision rate, near misses, minimum clearance, travel time, path length, energy use, intervention count, and deadlock frequency.

For control, metrics may include tracking error, overshoot, settling time, jerk, torque use, thermal load, stability, and constraint violations. For docking, evaluation may include final pose error, alignment success, contact force, retry count, and charging connection reliability.

For manipulation, important metrics include grasp success, placement accuracy, force peaks, object damage, cycle time, and recovery performance. Testing should include nominal, difficult, and adversarial scenarios. Policies that perform well only under normal conditions are not ready for deployment.

Payload variation, worn tires, low battery, sensor bias, communication loss, lighting change, rain, dust, floor transition, and unexpected obstacles should all be evaluated. Long-duration operation is required because some transfer failures appear slowly. Small bias may cause drift, repeated corrections may create heat, and minor inefficiency may reduce battery life.

A policy should be evaluated across multiple physical robots. Manufacturing variation may cause different behavior even among nominally identical units. Fleet-level deployment can reveal interactions not visible during single-robot testing. Congestion, communication load, right-of-way conflicts, and shared-resource delays may affect performance. Logging is essential during every transfer stage.

The system should record observations, policy actions, final executed commands, safety overrides, uncertainty, latency, and system response. Logs support failure analysis, model comparison, and reproduction of real events in simulation. Policy versioning must be strict.

Every deployed model should have a unique identifier, training configuration, simulator version, randomization range, evaluation record, and approved operating domain. Changes to robot hardware, firmware, sensors, payload structure, or network architecture may invalidate previous validation. A policy approved for one configuration should not automatically be trusted on another.

Recalibration, regression testing, or retraining may be required. Simulator versioning is equally important. Changes in physics, sensor models, collision geometry, time step, or reward logic can alter policy behavior. The complete transfer pipeline should be reproducible. Engineers should be able to identify exactly how a deployed policy was trained and validated.

Real-world failures should be converted into simulation scenarios. A near miss, docking failure, sensor artifact, or terrain problem can be reconstructed virtually. The updated scenario becomes part of a permanent regression suite. Future policies must pass it before deployment. This creates a continuous sim-to-real improvement loop.

Field data reveals weaknesses, simulation reproduces them, training improves the policy, and staged testing confirms the update. For AMRs, sim-to-real transfer may support local navigation, docking, traction control, steering adaptation, energy optimization, and traffic interaction.

A navigation policy may require realistic LiDAR noise, pedestrian behavior, floor friction, control delay, and map uncertainty. A docking policy may require accurate geometry, sensor offset, wheel slip, charging-station tolerance, and contact modeling. A traction policy may require randomized payload, tire friction, motor response, slope, battery voltage, and surface condition.

A fleet policy may require realistic communication delay, congestion, task demand, shared zones, and behavior of other robots. The transfer strategy should match the policy\'s level of authority. High-level route selection generally requires less physical fidelity than direct torque control.

Policies that directly control force, torque, or balance require much stronger simulation accuracy, safety protection, and real-world validation. The most practical approach is often hybrid. Simulation-trained RL provides adaptation, while conventional planning, control, and safety systems provide predictable structure.

A successful transfer architecture clearly separates perception, learning, control, monitoring, and safety responsibilities. The learned policy should operate only within a defined envelope of speed, payload, terrain, sensor health, and uncertainty. When the robot leaves this envelope, it should degrade gracefully rather than attempting to maintain full autonomous performance.

Sim-to-real transfer is therefore not a single technical trick. It is an engineering process involving calibration, randomization, adaptation, testing, safety design, staged deployment, monitoring, and continuous improvement. A strong policy in simulation is only the starting point. Real-world reliability depends on how carefully the gap is measured and managed.

The final objective is not to make simulation identical to reality, which is impossible. The objective is to create policies that remain useful despite unavoidable differences. When the simulator captures the important dynamics, randomization covers realistic variation, interfaces remain consistent, and safety systems constrain deployment, reinforcement learning can transfer effectively to physical robots.

Successful sim-to-real transfer converts virtual experience into dependable real-world behavior. It enables robots to benefit from large-scale learning while preserving the safety, predictability, and robustness required for industrial operation.

시뮬레이션-현실 이전(Sim-to-Real Transfer)은 시뮬레이션(Simulation)에서 학습된 정책(Policy), 모델(Model), 또는 제어기(Controller)를 실제 물리 로봇(Physical Robot)에 적용하는 과정이다. 목표는 센서, 액추에이터, 동역학, 시간 지연, 운용 환경이 달라지더라도 가상 환경에서 학습한 성능을 최대한 유지하는 것이다. 시뮬레이션은 강화 학습(Reinforcement Learning) 에이전트가 안전하고 빠르게 대량의 경험을 수집할 수 있도록 해준다. 그러나 시뮬레이션에서 성공한 정책이 실제 로봇에서는 실패할 수 있다. 이는 가상 환경이 현실을 완벽하게 재현하지 못하기 때문이다.

시뮬레이션과 실제 환경의 차이를 시뮬레이션-현실 간 차이(Sim-to-Real Gap)라고 한다. 이 차이는 로봇이 환경을 인식하고, 의사결정을 내리며, 행동하는 모든 과정에 영향을 미칠 수 있다. 이러한 차이는 부정확한 물리 모델(Physics Model), 불완전한 센서 모델(Sensor Model), 액추에이터 지연(Actuator Delay), 통신 지연(Communication Latency), 환경 변화(Environmental Variability), 모델링되지 않은 외란(Unmodeled Disturbance), 그리고 시뮬레이션 작업과 실제 작업의 차이 등에서 발생한다. 시뮬레이터는 로봇의 외형을 매우 정확하게 표현할 수 있지만, 동역학(Dynamics)은 충분히 정확하지 않을 수 있다.

강화 학습 기반 제어에서는 마찰(Friction), 질량(Mass), 관성(Inertia), 감쇠(Damping), 모터 응답(Motor Response), 접촉(Contact) 모델의 작은 오차도 시각적인 차이보다 훨씬 큰 영향을 미칠 수 있다. 비전 기반 정책(Vision-Based Policy)에서는 시각적 차이(Visual Gap)가 매우 중요하다. 실제 영상에는 그림자(Shadow), 반사(Reflection), 먼지(Dirt), 블러(Blur), 노출 변화(Exposure Change), 렌즈 왜곡(Lens Distortion), 날씨 효과, 그리고 학습 중 한 번도 등장하지 않은 물체들이 포함될 수 있다. 라이다(LiDAR) 데이터도 시뮬레이션과 실제 환경에서 차이가 존재한다.

실제 스캔은 데이터 누락(Missing Return), 다중 반사(Multipath Reflection), 반사 강도(Intensity) 변화, 제한된 탐지 거리, 움직임 왜곡(Motion Distortion), 먼지, 비, 그리고 부분적인 가림(Occlusion)을 포함할 수 있다. 깊이 센서(Depth Sensor)는 반사율이 높은 물체, 어두운 물체, 투명한 물체, 또는 먼 거리의 대상에서 정상적으로 동작하지 않을 수 있다. 완벽한 깊이 영상만으로 학습한 정책은 실제 산업 환경이나 야외 환경에서는 매우 불안정해질 수 있다. 액추에이터(Actuator)의 동작 역시 중요한 차이를 만든다.

실제 모터는 지연, 포화(Saturation), 데드존(Dead Zone), 전류 제한(Current Limit), 온도 변화, 백래시(Backlash), 제조 편차(Manufacturing Variation)를 가진다. 시뮬레이션에서는 명령이 즉시 정확하게 실행되지만, 실제 로봇에서는 배터리 전압, 적재물(Payload), 타이어 상태, 기계적 마모 때문에 응답이 느리거나 다르게 나타날 수 있다. 시간 지연(Timing Mismatch) 역시 이전 성능에 큰 영향을 준다. 센서 메시지는 서로 다른 시점에 도착할 수 있고, 신경망 추론(Inference)의 지연도 일정하지 않으며, 제어 명령은 운영체제 스케줄링이나 통신 네트워크 때문에 늦게 전달될 수 있다.

완벽하게 동기화된 입력만으로 학습한 정책은 실제 환경에서 센서의 타임스탬프(Timestamp)가 달라지면 쉽게 불안정해질 수 있다. 따라서 시간 동기화(Time Synchronization)와 지연 모델링(Delay Modeling)은 성공적인 Sim-to-Real 이전의 핵심 요소이다. 실제 물리 환경은 시뮬레이션보다 훨씬 복잡하다. 실제 바닥은 울퉁불퉁하거나 미끄럽고, 손상되어 있거나, 젖어 있거나, 먼지가 쌓여 있거나, 작은 물체들이 흩어져 있을 수 있다. 사람의 행동(Human Behavior)은 시뮬레이션하기가 특히 어렵다. 사람은 갑자기 멈추거나 방향을 바꾸고, 예상과 다른 방식으로 움직이며, 로봇에 대해 매우 다양한 반응을 보인다.

다른 로봇, 지게차(Forklift), 문(Door), 엘리베이터(Elevator), 카트(Cart), 공사 구역 역시 실제 환경의 불확실성을 증가시킨다. Sim-to-Real 이전은 이러한 다양한 환경 변화까지 고려해야 한다. Sim-to-Real 엔지니어링의 첫 단계는 운용 영역(Operational Domain)을 정의하는 것이다. 예상되는 지형, 적재물, 속도, 조명, 날씨, 센서 상태, 교통 밀도, 작업 범위를 명확하게 정의해야 한다. 모든 상황을 학습하려 하기보다 정의된 운용 영역에 집중하는 것이 효과적이다. 지나치게 넓은 목표는 학습 비용을 증가시키고 정책 성능을 저하시킬 수 있다. 시스템 식별(System Identification)은 모델 차이를 줄이는 대표적인 방법이다.

실제 로봇 데이터를 이용하여 질량, 관성, 마찰, 모터 응답, 지연, 조향 특성, 제동 특성을 추정한다. 이렇게 추정한 파라미터(Parameter)를 시뮬레이터에 반영하면 시뮬레이션의 정확성을 크게 향상시킬 수 있다. 완벽한 모델은 아니더라도 중요한 물리 관계를 훨씬 현실적으로 표현할 수 있다. 각 물리 파라미터는 서로 다른 실험으로 측정할 수 있다. 직선 가속 실험은 모터 응답을, 회전 실험은 조향 특성을, 경사로 실험은 구동력(Traction)과 제동 특성을 추정하는 데 사용될 수 있다. 센서 보정(Sensor Calibration)도 매우 중요하다.

카메라 내부 파라미터(Camera Intrinsics), 라이다 정렬, 깊이 스케일, IMU 바이어스, 휠 반지름, 시간 오프셋(Time Offset)은 실제 시스템과 최대한 일치해야 한다. 하지만 아무리 정확하게 보정하더라도 실제 환경은 계속 변한다. 적재물 변화, 타이어 마모, 배터리 상태, 온도 변화, 부품 노화 때문에 하나의 고정된 시뮬레이터만으로는 충분하지 않다. 도메인 랜덤화(Domain Randomization)는 이러한 문제를 해결하기 위해 학습 과정에서 시뮬레이션 파라미터를 지속적으로 변경한다. 정책은 하나의 모델이 아니라 다양한 환경에서 성공하는 방법을 학습한다.

물리 파라미터 랜덤화는 질량, 마찰, 무게 중심(Center of Gravity), 관성, 모터 출력, 바퀴 반지름, 서스펜션(Suspension), 감쇠, 제동력, 액추에이터 지연 등을 변화시킨다. 센서 랜덤화는 노이즈, 바이어스(Bias), 데이터 누락(Dropout), 시야(Field of View), 보정 오차, 해상도, 지연, 탐지 거리 등을 변화시킨다. 시각 랜덤화(Visual Randomization)는 조명, 질감(Texture), 색상(Color), 그림자, 물체 형태, 카메라 노출 등을 변경한다. 환경 랜덤화(Environmental Randomization)는 지도 구조, 지형, 장애물 위치, 교통 행동, 날씨, 시작 위치 등을 변화시킨다.

실제 환경이 이러한 다양한 환경 가운데 하나가 되도록 만드는 것이 목표이다. 랜덤화 범위는 적절해야 한다. 너무 넓으면 학습이 어려워지고 정책이 지나치게 보수적이 되며, 너무 좁으면 실제 환경 변화에 대응하지 못한다. 따라서 랜덤화 범위는 실제 로봇에서 측정한 데이터를 기반으로 설정하는 것이 바람직하다. 자동 도메인 랜덤화(Automatic Domain Randomization)는 정책의 성능이 향상될수록 점차 더 어려운 환경을 자동으로 생성한다. 이러한 방식은 커리큘럼 학습(Curriculum Learning)과 유사하다. 정책은 먼저 기본 작업을 학습하고 이후 점차 다양한 환경 변화에 적응하게 된다. 도메인 랜덤화는 실제 환경이 다양한 가능한 물리 모델 가운데 하나라고 가정한다.

정책은 특정 시뮬레이터에 의존하지 않고 보다 일반적인 물리 법칙을 학습하게 된다. 도메인 적응(Domain Adaptation)은 또 다른 Sim-to-Real 기법이다. 학습 후 또는 실제 운용 중에 시뮬레이션과 실제 데이터의 차이를 줄이는 것을 목표로 한다. 비전 기반 정책에서는 시뮬레이션 이미지를 실제 이미지처럼 변환하거나, 두 환경이 동일한 특징 공간(Feature Space)을 공유하도록 학습할 수 있다. 픽셀(Pixel) 자체를 변환하는 것보다 특징 공간을 공유하는 특징 수준 적응(Feature-Level Adaptation)이 더욱 안정적인 경우가 많다. 표현 학습(Representation Learning)은 조명, 질감, 날씨, 센서 노이즈에 영향을 적게 받는 특징을 생성한다.

실제 데이터와 시뮬레이션 데이터를 함께 사용하여 사전 학습(Pretraining)할 수도 있다. 교사-학생 학습(Teacher-Student Learning)은 매우 널리 사용되는 방법이다. 교사 정책은 시뮬레이션의 모든 정보를 이용하여 학습하고, 학생 정책은 실제 센서 입력만으로 교사를 모방한다. 교사는 정확한 위치, 속도, 접촉 상태, 장애물 궤적 등을 사용할 수 있지만, 학생은 실제 로봇에서 사용할 수 있는 센서 입력만을 사용한다. 이 방식은 학습 효율성을 높이면서도 실제 배포 가능한 정책을 생성할 수 있다. 비대칭 액터-크리틱(Asymmetric Actor-Critic)도 동일한 원리를 사용한다.

크리틱(Critic)은 시뮬레이터의 전체 상태를 이용하지만, 액터(Actor)는 실제 센서 입력만 사용한다. 실제로 배포되는 것은 액터이며, 크리틱은 학습 과정에서만 사용된다. 잔차 강화 학습(Residual Reinforcement Learning)은 기존 제어기와 강화 학습을 결합하여 이전 위험을 줄인다. 기존 제어기가 기본 명령을 생성하고 강화 학습은 작은 보정값만 추가한다. 잔차 정책은 모델 오차, 마찰 변화, 적재물 변화, 작은 추종 오차를 보정하는 역할을 수행한다. 시스템 전체를 직접 제어하지 않기 때문에 이전이 훨씬 쉽고 안전하다. 잘 설계된 잔차는 항상 크기가 제한되어 있으며, 기존 제어기가 안정성을 책임지고 강화 학습은 제한된 범위에서만 성능을 향상시킨다.

하이브리드 제어(Hybrid Control)는 강화 학습과 모델 예측 제어(Model Predictive Control, MPC)를 결합할 수도 있다. 강화 학습은 비용 함수(Cost Function), 외란 추정, 동역학 보정, 종료 비용(Terminal Value)을 학습한다. MPC는 속도, 가속도, 토크, 안전 제약을 만족하는 최적 제어를 수행한다. 이를 통해 실제 운용에서도 물리적 제약을 명확하게 유지할 수 있다. 강인한 제어 목표(Robust Control Objective)는 Sim-to-Real 성능을 향상시킨다. 하나의 모델에서 최고의 성능을 얻기보다 다양한 불확실성에서도 안정적으로 동작하도록 학습한다.

보상 함수에는 민감도(Sensitivity), 진동(Oscillation), 과도한 제어 입력(Control Effort), 불안정한 접촉, 특정 상태에 대한 과도한 의존성을 줄이는 항목을 포함할 수 있다. 이상적인 시뮬레이션에서 매우 공격적인 제어를 사용하는 정책은 실제 환경에서는 오히려 성능이 나쁠 수 있다. 보다 부드럽고 안정적인 제어가 실제 환경에서는 더 강인한 경우가 많다. 행동 스무딩(Action Smoothing)과 변화율 제한(Rate Limit)은 시간 지연과 액추에이터 차이에 대한 민감도를 줄이고 기계적 스트레스도 감소시킨다. 관측값 정규화(Observation Normalization)는 시뮬레이션과 실제 환경에서 반드시 동일해야 한다.

단위(Unit), 스케일(Scale), 좌표계(Coordinate Frame)가 조금만 달라도 정책은 즉시 실패할 수 있다. 모든 센서와 상태 변수는 동일한 정의를 가져야 한다. 좌표계 방향, 각도 정의, 속도 부호, 타임스탬프 해석 등을 철저하게 검증해야 한다. 행동 인터페이스(Action Interface)도 완전히 동일해야 한다. 시뮬레이션의 목표 속도(Target Velocity)는 실제 시스템에서도 동일한 의미와 동일한 업데이트 주기를 가져야 한다. 소프트웨어 통합 오류는 강화 학습 알고리즘보다 더 큰 문제를 일으킬 수 있다. 메시지 형식, 좌표계, 타이밍, 안전 시스템, 액추에이터 인터페이스는 전체 시스템 차원에서 검증해야 한다.

소프트웨어-인-더-루프(Software-in-the-Loop, SIL)는 실제 로봇 소프트웨어를 시뮬레이터와 연결하여 검증하는 방법이다. 이를 통해 인터페이스 오류를 실제 로봇을 움직이지 않고도 발견할 수 있으며, 학습 코드와 실제 운용 코드의 차이도 줄일 수 있다. 하드웨어-인-더-루프(Hardware-in-the-Loop, HIL)는 실제 컴퓨터, 제어기, 네트워크, 임베디드 장치를 시뮬레이션과 연결한다. 실제 로봇 대신 가상 로봇을 사용하지만 실제 AI 하드웨어와 통신 시스템은 그대로 사용하므로 추론 지연, 스케줄링, 통신 특성을 현실적으로 검증할 수 있다.

특히 엣지 AI(Edge AI) 시스템에서는 발열(Thermal Throttling), 메모리 한계, 네트워크 지연, 타이밍 지터(Timing Jitter)를 실제 운용 전에 확인할 수 있다. 실시간 성능(Real-Time Performance)은 반드시 검증되어야 한다. 평균 추론 속도뿐 아니라 최악의 지연 시간(Worst-Case Latency)도 함께 측정해야 한다. 센서 데이터 누락이나 입력 지연이 발생하는 경우에도 정책은 안정적으로 동작하거나 안전한 백업(Fallback) 모드로 전환되어야 한다. 불확실성 추정(Uncertainty Estimation)은 안전한 Sim-to-Real 이전을 지원한다. 정책 또는 별도의 모델이 현재 상태가 학습 데이터와 얼마나 유사한지를 추정한다.

높은 불확실성은 새로운 적재물, 새로운 지형, 손상된 센서, 드문 장애물, 예상하지 못한 환경을 의미할 수 있다. 이 경우 로봇은 속도를 줄이거나 기존 제어기를 사용하거나 사람의 개입을 요청하거나 안전 정지를 수행해야 한다. 앙상블 모델(Ensemble Model)은 여러 개의 정책을 학습시키고 결과의 차이를 이용하여 불확실성을 추정하는 대표적인 방법이다. 거리 기반(Distance-Based) 방법은 현재 특징이 학습 데이터와 얼마나 다른지를 계산한다. 베이지안(Bayesian) 방법이나 신뢰도 예측 모델도 함께 사용할 수 있다. 불확실성은 완벽한 안전 보장을 제공하지는 않는다. 하지만 보수적인 의사결정과 실시간 모니터링을 위한 매우 중요한 정보가 된다.

섀도우 모드(Shadow Mode)는 Sim-to-Real 이전의 핵심 단계이다. 강화 학습 정책은 실제 센서를 입력받아 행동을 생성하지만 실제 제어는 수행하지 않는다. 기존 제어기가 계속 로봇을 제어하는 동안 엔지니어는 강화 학습 정책과 기존 제어기의 차이를 비교할 수 있다. 섀도우 모드는 실제 센서 노이즈, 시간 지연, 교통 상황, 환경 변화를 위험 없이 검증할 수 있는 매우 안전한 방법이다. 두 정책의 차이는 반드시 분석되어야 한다. 일부는 성능 향상일 수도 있지만 일부는 위험한 행동일 수도 있다. 이러한 사례는 시뮬레이션에서 다시 재현되어 이후 학습과 검증에 활용된다. 섀도우 모드 이후에는 파일럿 배포(Pilot Deployment)를 수행한다.

처음에는 낮은 속도, 제한된 구역, 특정 적재물, 위험이 낮은 작업에서만 정책을 사용한다. 파일럿 단계에서는 원격 감독(Remote Supervisor)이나 안전 운영자(Safety Operator)가 항상 개입할 수 있어야 하며, 모든 로그를 기록해야 한다. 충분한 성능과 안전성이 입증된 이후에만 적용 범위를 점진적으로 확대해야 한다. 점진적 배포(Progressive Rollout)는 한 대의 로봇에서 시작하여 소규모 그룹, 이후 전체 플릿(Fleet)으로 확대하는 방식이 일반적이다. 문제가 발생하면 즉시 이전 정책으로 되돌릴 수 있는 롤백(Rollback) 기능도 반드시 준비되어 있어야 한다.

강화 학습은 비상 정지(Emergency Stop), 안전 스캐너(Safety Scanner), 지오펜스(Geofence), 속도 제한, 인증된 안전 제어기를 절대 대체해서는 안 된다. 안전 실드(Safety Shield)는 강화 학습이 생성한 행동을 실행 전에 검사하여 위험한 명령을 수정하거나 거부한다. 안전 실드는 제동 거리, 충돌 영역, 토크 제한, 관절 제한, 경사 제한, 사람과의 거리, 최고 속도 등을 항상 검사한다. 학습 과정에서도 동일한 안전 실드를 사용하는 것이 바람직하다. 그렇지 않으면 실제 환경에서는 항상 차단되는 행동을 정책이 계속 생성하게 된다. 안전 시스템 개입 횟수는 중요한 운영 지표이다. 개입이 자주 발생한다면 정책이 실제 제약 조건을 제대로 학습하지 못한 것이다.

백업 제어(Fallback Control)도 반드시 준비되어야 한다. 정책이 실패하거나 불확실하거나 입력이 잘못되면 즉시 기존 제어기로 전환해야 한다. 백업 방식으로는 기존 경로 계획기(Classical Planner), PID 제어기, MPC 제어기, 저속 모드, 안전 정지, 원격 제어 등이 사용될 수 있다. 강화 학습과 백업 제어기 사이의 전환은 부드럽게 이루어져야 한다. 갑작스러운 전환은 불연속적인 명령을 생성하여 시스템을 불안정하게 만들 수 있다. 블렌딩(Blending) 기법은 강화 학습의 영향력을 점차 줄이고 기존 제어기의 비중을 증가시키는 방식이다. 상태 기계(State Machine)는 언제 강화 학습을 사용할 수 있고 언제 결정론적 제어를 우선해야 하는지를 정의한다.

실제 환경에서의 미세 조정(Fine-Tuning)은 초기 이전 이후 성능을 향상시킬 수 있지만, 산업용 로봇에서는 무제한 온라인 강화 학습은 거의 허용되지 않는다. 실제 탐험은 충돌, 장비 마모, 과열, 위험한 상황을 만들 수 있으므로 반드시 제한된 방식으로 수행되어야 한다. 오프라인 강화 학습(Offline Reinforcement Learning)은 실제 운행 데이터를 이용하여 새로운 탐험 없이 정책을 개선할 수 있다. 데이터셋에는 정상 운용뿐 아니라 안전 개입, 근접 사고(Near Miss), 어려운 도킹, 휠 슬립, 복구 행동도 포함되어야 한다. 데이터셋의 다양성은 매우 중요하다. 데이터에 존재하지 않는 상태와 행동에 대해서는 정책이 안정적으로 동작하기 어렵다.

보수적인 오프라인 강화 학습은 데이터 분포를 크게 벗어나는 행동을 선택하지 않도록 한다. 미세 조정은 지도 학습(Supervised Learning)을 이용할 수도 있다. 강화 학습 정책이 부족한 상황에서는 기존 제어기나 사람의 조작을 모방하도록 학습할 수 있다. 적은 양의 실제 데이터라도 다양한 상황을 포함한다면 반복적인 정상 데이터보다 훨씬 높은 가치를 가질 수 있다. 능동적 데이터 선택(Active Data Selection)은 불확실성이 높거나 정책 간 차이가 큰 사례를 우선적으로 선택하여 재학습에 사용한다. Sim-to-Real 이전 이후 평가는 반드시 독립적인 성능 지표를 사용해야 한다. 학습 보상만으로는 실제 성능을 판단할 수 없다.

내비게이션에서는 성공률, 충돌률, 근접 사고, 최소 안전 거리, 이동 시간, 경로 길이, 에너지 소비, 개입 횟수, 교착 상태를 평가해야 한다. 제어에서는 추종 오차, 오버슈트(Overshoot), 정착 시간(Settling Time), 저크(Jerk), 토크 사용량, 열 부하(Thermal Load), 안정성, 제약 조건 위반 등을 측정해야 한다. 도킹(Docking)에서는 최종 위치 오차, 정렬 성공률, 접촉력, 재시도 횟수, 충전 연결 성공률 등을 평가해야 한다. 매니퓰레이션에서는 파지 성공률, 배치 정확도, 최대 힘, 물체 손상, 작업 시간, 복구 능력을 평가해야 한다. 평가는 정상 상황뿐 아니라 어려운 환경과 적대적 환경(Adversarial Scenario)에서도 수행되어야 한다.

적재물 변화, 타이어 마모, 낮은 배터리, 센서 오차, 통신 장애, 조명 변화, 비, 먼지, 바닥 변화, 예상하지 못한 장애물도 모두 포함해야 한다. 장시간 운용(Long-Term Operation)도 필수적이다. 작은 오차는 시간이 지나면서 드리프트(Drift), 발열, 배터리 소모 증가로 이어질 수 있다. 정책은 여러 대의 실제 로봇에서도 검증되어야 한다. 동일한 모델이라도 제조 편차 때문에 서로 다른 동작을 보일 수 있다. 플릿 수준(Fleet-Level)의 배포는 단일 로봇에서는 보이지 않는 혼잡(Congestion), 통신 부하, 우선순위 충돌, 공유 자원 문제를 발견할 수 있다. 모든 이전 단계에서 상세한 로깅(Logging)이 필요하다.

관측값, 정책 행동, 실제 실행 명령, 안전 개입, 불확실성, 지연 시간, 시스템 응답을 모두 기록해야 한다. 로그는 실패 분석, 정책 비교, 실제 문제의 시뮬레이션 재현에 매우 중요한 역할을 한다. 정책 버전 관리(Policy Versioning)는 엄격해야 한다. 모든 정책은 고유 식별자, 학습 설정, 시뮬레이터 버전, 랜덤화 범위, 평가 결과, 허용 운용 범위를 가져야 한다. 로봇 하드웨어, 펌웨어(Firmware), 센서, 적재 구조, 네트워크가 변경되면 기존 검증 결과는 무효가 될 수 있다. 하나의 하드웨어에서 검증된 정책을 다른 시스템에서도 그대로 사용할 수 있다고 가정해서는 안 된다. 재보정(Recalibration), 회귀 시험(Regression Test), 재학습이 필요할 수 있다.

시뮬레이터 버전 관리도 중요하다. 물리 엔진, 센서 모델, 충돌 메시(Collision Mesh), 시간 설정, 보상 함수가 변경되면 정책도 달라질 수 있다. 전체 Sim-to-Real 파이프라인은 재현 가능해야 한다. 어떤 방식으로 학습하고 검증했는지를 정확하게 추적할 수 있어야 한다. 실제 환경에서 발생한 실패 사례는 반드시 시뮬레이션으로 재현되어야 한다. 근접 사고, 도킹 실패, 센서 오류, 지형 문제 등을 시뮬레이션에 추가해야 한다. 이러한 사례는 영구적인 회귀 테스트(Regression Test) 시나리오가 되며 이후의 모든 정책은 이를 반드시 통과해야 한다. 이렇게 실제 데이터와 시뮬레이션을 연결하는 지속적인 개선 루프(Continuous Improvement Loop)가 만들어진다.

현장 데이터로 문제를 발견하고, 시뮬레이션에서 재현하고, 정책을 개선하고, 다시 단계적으로 검증하는 구조이다. AMR에서는 Sim-to-Real 이전을 통해 지역 내비게이션(Local Navigation), 도킹, 구동력 제어(Traction Control), 조향 적응(Steering Adaptation), 에너지 최적화(Energy Optimization), 교통 상호작용(Traffic Interaction)을 향상시킬 수 있다. 내비게이션 정책은 현실적인 라이다 노이즈, 사람의 행동, 바닥 마찰, 제어 지연, 지도 불확실성을 반영해야 한다. 도킹 정책은 정확한 기하학(Geometry), 센서 오프셋, 휠 슬립, 충전기 허용 오차, 접촉 모델이 중요하다.

구동력 제어 정책은 적재물 변화, 타이어 마찰, 모터 응답, 경사, 배터리 전압, 노면 상태를 랜덤화하여 학습하는 것이 효과적이다. 플릿 정책은 통신 지연, 교통 혼잡, 작업 요청, 공유 구역, 다른 로봇의 행동을 현실적으로 모델링해야 한다. Sim-to-Real 전략은 정책이 담당하는 권한 수준(Level of Authority)에 따라 달라져야 한다. 고수준 경로 선택은 직접 토크 제어보다 낮은 수준의 물리 정확성으로도 충분할 수 있다. 반대로 힘, 토크, 균형을 직접 제어하는 정책은 훨씬 높은 시뮬레이션 정확성, 안전 보호, 실제 검증이 필요하다. 실제 산업에서는 하이브리드 구조(Hybrid Architecture)가 가장 현실적이다.

시뮬레이션 기반 강화 학습은 적응성을 제공하고, 기존 경로 계획기와 제어기, 안전 시스템은 안정성과 예측 가능성을 유지한다. 성공적인 Sim-to-Real 구조는 인식(Perception), 학습(Learning), 제어(Control), 모니터링(Monitoring), 안전(Safety)의 역할을 명확하게 분리한다. 학습된 정책은 속도, 적재물, 지형, 센서 상태, 불확실성 등 정의된 운용 범위 안에서만 동작해야 한다. 운용 범위를 벗어나면 로봇은 억지로 자율성을 유지하려고 하기보다 안전하게 성능을 낮추고(Graceful Degradation) 백업 시스템으로 전환해야 한다.

따라서 Sim-to-Real 이전은 단순한 하나의 기술이 아니라 보정(Calibration), 랜덤화(Randomization), 적응(Adaptation), 시험(Test), 안전 설계(Safety Design), 단계적 배포(Staged Deployment), 모니터링(Monitoring), 지속적인 개선(Continuous Improvement)을 포함하는 종합적인 엔지니어링 프로세스이다. 시뮬레이션에서 높은 성능을 보이는 정책은 출발점일 뿐이다. 실제 환경에서의 신뢰성은 Sim-to-Real Gap을 얼마나 정확하게 측정하고 관리했는지에 의해 결정된다. 최종 목표는 시뮬레이션을 현실과 완전히 동일하게 만드는 것이 아니다. 그것은 현실적으로 불가능하다.

진정한 목표는 현실과의 차이가 존재하더라도 안정적으로 동작하는 정책을 만드는 것이다. 시뮬레이터가 중요한 물리 특성을 충분히 반영하고, 랜덤화가 현실적인 변화를 포함하며, 인터페이스가 일관되고, 안전 시스템이 정책을 적절히 제한한다면 강화 학습은 실제 로봇으로 성공적으로 이전될 수 있다. 성공적인 Sim-to-Real 이전은 가상 환경에서 얻은 방대한 경험을 실제 산업용 로봇의 신뢰성 있는 행동으로 변환한다. 이를 통해 강화 학습의 장점을 활용하면서도 산업 현장에서 요구되는 안전성(Safety), 예측 가능성(Predictability), 강인성(Robustness)을 동시에 만족하는 로봇 시스템을 구축할 수 있다.

##  

## 09.7 Safe Reinforcement Learning

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

Safe reinforcement learning focuses on learning useful behavior while limiting the probability and severity of harmful actions. In robotics, this means the agent must improve performance without creating unacceptable risks to people, equipment, infrastructure, or the robot itself. Conventional reinforcement learning often assumes that exploration is inexpensive.

The agent can try many actions, fail repeatedly, and gradually discover a better policy. This assumption may be acceptable in games or simulations, but it is dangerous for physical robots operating in real environments. A mobile robot cannot learn collision avoidance by repeatedly striking people or equipment.

A manipulator cannot explore force control by applying arbitrary torque to fragile objects. A legged robot cannot fall without consequences every time it tests a new movement. Safe reinforcement learning therefore modifies the learning process so that safety is treated as a fundamental requirement rather than a secondary reward term.

The objective is not only to maximize return, but to do so while respecting explicit constraints and controlling uncertainty. A central distinction exists between performance objectives and safety requirements. Performance objectives may include speed, energy efficiency, task completion, and throughput.

Safety requirements define conditions that must not be violated, even when doing so could improve the reward. This distinction is important because a single weighted reward may hide critical trade-offs. If safety is represented only by a collision penalty, the agent may still accept a small collision probability when the expected performance benefit is high enough.

In industrial robotics, some risks are non-negotiable. Maximum speed, braking distance, torque, temperature, human clearance, and allowed operating zones may need to remain within strict limits at all times. Safe reinforcement learning often models these requirements as constraints.

The agent maximizes expected reward while keeping expected cost, failure probability, or state violations below defined thresholds. A constrained Markov decision process extends the standard reinforcement learning framework by adding one or more cost functions. Reward represents desired performance, while cost represents risk, resource use, or safety violation.

For an autonomous mobile robot, reward may represent mission completion and travel efficiency. Cost may represent collision risk, human proximity, excessive speed, unstable motion, battery overuse, or entry into a restricted zone. The policy must optimize these competing quantities without violating acceptable safety budgets.

This approach is more transparent than combining all objectives into one scalar reward. However, expected cost alone may not be sufficient. A policy with low average risk may still produce rare catastrophic failures. Industrial safety therefore requires attention to worst-case behavior, tail risk, and failure severity.

Risk-sensitive reinforcement learning considers not only the average return but also its variability or lower-probability outcomes. The policy is trained to avoid behaviors that occasionally produce severe losses even when their average performance is attractive. Conditional value at risk is one method used to emphasize the worst portion of outcomes.

Instead of optimizing only the mean, the agent considers the average loss among the most harmful episodes. This is useful when rare collisions, falls, or control failures are unacceptable. A policy with slightly lower average performance may be preferred if it significantly reduces extreme failure cases. Chance constraints provide another method.

They require the probability of violating a safety condition to remain below a specified limit. For example, the probability of entering a human safety zone, exceeding a joint limit, or losing stability may need to remain below a very small threshold. Estimating these probabilities accurately can be difficult because rare events require large amounts of data.

Simulation, importance sampling, adversarial scenario generation, and statistical confidence bounds can support this evaluation. Safe reinforcement learning can protect safety during both training and deployment. These are related but different problems. Training safety concerns how the agent explores and updates its policy.

Deployment safety concerns how a learned policy behaves after it has been placed in a physical system. A policy may be safe after convergence but unsafe during learning. Random exploration may produce extreme actions long before the policy becomes useful. This is why unrestricted online reinforcement learning is rarely appropriate for industrial robots.

Most exploration should occur in simulation or within tightly controlled physical conditions. Action limits are the simplest form of safe exploration. Torque, velocity, acceleration, steering rate, force, or joint position can be clipped to permitted ranges. Although action clipping prevents extreme commands, it does not guarantee safe behavior.

A sequence of individually valid actions may still lead to collision, instability, or overheating. State constraints are therefore also required. The robot may need to remain outside collision zones, below temperature limits, within stable orientation ranges, and inside approved operating regions. A safety filter evaluates the proposed action before execution.

If the action could cause a constraint violation, it is modified or replaced with a safer alternative. The learning policy remains responsible for the main behavior, but the filter prevents unsafe commands from reaching the physical system. A safety shield is a broader protective mechanism.

It may use geometric rules, predictive models, formal methods, or verified controllers to supervise the learned policy. For a mobile robot, the shield may calculate whether the proposed velocity allows sufficient braking distance. If not, it can reduce speed or command a stop.

For a manipulator, the shield may prevent excessive force, self-collision, joint-limit violation, or entry into a human workspace. For a legged robot, the shield may reject actions that create an unstable support pattern or excessive body tilt. Control barrier functions provide a mathematical framework for safety filtering.

A barrier function defines whether the current state lies inside a safe set. The controller modifies the proposed action so that the system remains within this safe region. The adjustment is often designed to preserve as much of the original RL action as possible. Barrier functions are attractive because they can provide local safety guarantees under known system dynamics.

However, their effectiveness depends on the accuracy of the model and the definition of the safe set. Unmodeled delays, disturbances, or contact effects can reduce the guarantee. Lyapunov-based methods are used to address stability. A Lyapunov function measures whether the system is moving toward a stable condition.

Safe policy updates can be constrained so that the Lyapunov value decreases or remains within an acceptable region. This approach is particularly relevant for balancing, locomotion, trajectory tracking, and other control problems where instability can develop rapidly. Formal safety guarantees for deep reinforcement learning remain difficult.

Neural policies are highly nonlinear and may behave unpredictably outside the training distribution. Therefore, mathematical constraints should be combined with monitoring, fallback control, and conservative deployment. A model predictive safety filter can predict future states over a short horizon.

It evaluates whether the proposed action may lead to collision, constraint violation, or instability. If a risk is detected, a constrained optimizer produces a safer command. This allows the learned policy to operate while a predictive controller enforces physical limits. The quality of this protection depends on the predictive model and time horizon.

Very short horizons may miss delayed hazards, while long horizons increase computational cost. Safe reinforcement learning also uses backup controllers. A verified controller, classical planner, or emergency behavior remains available if the learned policy becomes unreliable. The backup controller may not be optimal, but it should provide predictable and safe behavior.

For an AMR, fallback behavior may include slowing down, stopping, following a classical local planner, returning to a safe location, or requesting remote assistance. For a manipulator, fallback may involve holding position, releasing force, moving to a home pose, or disabling motion. The transition between the learned policy and backup control must be carefully designed.

Abrupt switching can create discontinuities, oscillation, or mechanical stress. Blended control can gradually reduce the influence of the RL policy while increasing the contribution of the verified controller. A supervisory state machine can define when RL control is permitted.

Conditions may include healthy sensors, low uncertainty, acceptable speed, valid localization, and operation inside an approved zone. When any condition fails, the system can enter degraded mode or safe stop. Uncertainty estimation is a major component of safe reinforcement learning. A policy should not behave with high confidence when the current situation is far outside its training experience.

Uncertainty may arise from unfamiliar environments, sensor failure, new payloads, changing friction, unusual human behavior, or model drift. Epistemic uncertainty represents a lack of knowledge caused by limited training data. Aleatoric uncertainty represents inherent randomness or noise in the environment. These two forms of uncertainty have different implications.

Epistemic uncertainty may be reduced through more data, while aleatoric uncertainty may require conservative decision making. Ensemble methods estimate uncertainty by training several models and comparing their predictions. Large disagreement indicates that the current state is not well understood.

Bayesian approximations, confidence networks, latent-distance methods, and out-of-distribution detectors can also be used. Uncertainty estimates should influence behavior. The robot may reduce speed, increase clearance, avoid complex actions, or switch to fallback control when confidence is low.

A safe system should recognize not only dangerous states but also states in which its own predictions are unreliable. Distribution shift is a common source of risk. The environment may change after deployment because of new layouts, lighting, weather, equipment, traffic patterns, or mechanical wear. A policy trained in one distribution may produce unsafe actions in another.

Runtime monitoring is required to detect this shift. Monitoring can compare current observations, action distributions, confidence values, and performance metrics with the training baseline. Sudden changes in sensor statistics, safety interventions, braking frequency, or tracking error may indicate emerging risk. Safe reinforcement learning should also consider reward misspecification.

A policy can behave dangerously while still maximizing the formal reward. Reward hacking occurs when the agent exploits a shortcut or modeling weakness. A robot rewarded for speed may pass too close to people. A robot rewarded for remaining near a target may circle without completing the task.

Safety requirements should therefore be evaluated with metrics that are independent of the training reward. Human oversight can support safe learning. Engineers, operators, or remote supervisors can intervene when the agent enters an unfamiliar or risky situation. Human intervention data can be used to identify unsafe states, train a risk model, or improve the policy.

However, relying on human intervention alone is not sufficient. Reaction time, communication delay, and operator workload may prevent timely action. Human input is most effective when combined with automatic monitoring and safety systems. Learning from human preferences can help represent complex safety and comfort requirements.

Evaluators can compare two behaviors and indicate which one appears safer or more acceptable. A reward model can learn from these preferences. This is useful for social navigation, smooth motion, cooperative behavior, and tasks where safety is difficult to encode numerically. Preference models can also be wrong or inconsistent.

They should support, not replace, formal constraints and direct safety metrics. Imitation learning provides another safe starting point. A policy can first learn from a trusted controller or expert demonstration rather than beginning with random actions. This reduces early exploration risk and gives the agent a reasonable initial behavior.

However, demonstrations may not cover unusual failures or recovery conditions. The policy must still be tested beyond the nominal expert data. Offline reinforcement learning is attractive for safety-critical systems because it trains from existing datasets without direct exploration. Recorded trajectories may include normal operation, human interventions, failures, and recovery behavior.

The main risk is distributional extrapolation. The policy may select actions that are not well represented in the dataset, where value estimates are unreliable. Conservative offline reinforcement learning discourages actions that move far beyond the recorded behavior. Dataset quality is critical.

Safe learning requires not only successful trajectories but also difficult states, near misses, faults, and corrective actions. A dataset containing only ideal operation may teach the policy nothing about safety recovery. Simulation is the primary environment for safe reinforcement learning research and training. It allows dangerous exploration without physical consequences.

The simulator can generate collisions, sensor failures, high-speed instability, actuator faults, and rare environmental events. However, simulation safety does not automatically transfer to reality. The simulator may omit important hazards or underestimate physical uncertainty.

Domain randomization improves safety robustness by varying mass, friction, delay, sensor noise, obstacle behavior, and other conditions. Adversarial training intentionally searches for states that cause failure. The environment or a separate adversary creates difficult disturbances, obstacle motions, or sensor errors.

This approach can reveal vulnerabilities more efficiently than random scenario generation. The adversary must remain realistic. Unrealistic attacks may waste training resources or produce unnecessarily conservative behavior. Curriculum learning can gradually increase safety difficulty.

The agent may begin with open environments and then encounter tighter constraints, moving obstacles, sensor dropout, and stronger disturbances. The policy first learns useful behavior and then develops robustness under increasing risk. Recovery behavior should be trained explicitly. Avoiding all failures is impossible, so the robot must know how to respond when it approaches an unsafe condition.

A navigation policy may need to escape deadlock, back away from an obstacle, or recover after localization error. A control policy may need to stabilize after a push, wheel slip, sudden load change, or partial actuator loss. A manipulator may need to reduce force, release an object, or return to a safe pose after unexpected contact.

Recovery rewards should not encourage intentional entry into dangerous states. Training scenarios should control when and how failures are introduced. Safe exploration can also use reachability analysis. This method estimates the set of states from which the system can remain safe or return to safety. The agent is prevented from entering states outside this recoverable region.

Reachability methods can provide strong guarantees for lower-dimensional systems, but they become computationally difficult for complex robots and large neural policies. Approximate reachability and learned safety critics can extend these ideas to larger systems. A safety critic estimates expected future cost or violation probability. The policy can avoid actions with high predicted risk.

The critic may be trained from simulated failures, real interventions, or labeled unsafe trajectories. Because safety critics can make errors, they should be validated conservatively and combined with independent protective systems. Multi-agent systems create additional safety challenges. Each robot\'s action changes the risk faced by others.

A policy may be individually safe but collectively create congestion, deadlock, or unsafe competition. Safe multi-agent reinforcement learning must address communication, right-of-way, coordinated braking, shared zones, and uncertainty about other agents. Centralized training may use information about all robots, while decentralized execution relies on local observations and communication.

Global safety constraints can include total congestion, minimum inter-robot distance, shared-resource capacity, and emergency access routes. Credit assignment remains difficult because one robot may create risk that appears later in another robot\'s trajectory. Communication failure must also be considered. Robots should remain safe even when messages are delayed, lost, or inconsistent.

Policies should not assume perfect cooperation. Conservative right-of-way rules and local collision avoidance must remain available. Safe reinforcement learning for human-robot interaction requires special care. Human motion is uncertain, and people may not understand the robot\'s intentions.

The robot should maintain comfortable distance, use predictable trajectories, avoid sudden acceleration, and communicate its intent clearly. Social safety includes psychological comfort as well as physical collision avoidance. A technically collision-free path may still be unacceptable if it moves too closely, blocks a person, or behaves unpredictably. Safety evaluation must use diverse metrics.

Average reward and task success are not sufficient. Important metrics include collision rate, near-miss frequency, minimum clearance, intervention count, speed-limit violations, constraint violations, uncertainty events, and fallback activation. For control systems, tracking error, stability margin, overshoot, thermal load, torque limits, and recovery time should also be measured.

For manipulation, contact force, object damage, joint-limit violations, and human-zone intrusion are important. Rare-event metrics require many trials. Confidence intervals and statistical testing should accompany reported safety results. A policy with zero failures in a small test set is not necessarily safe. The test may simply be too limited to expose the weakness.

Scenario coverage should be tracked systematically. Speed, payload, terrain, weather, sensor condition, traffic density, and task type should be varied. Boundary conditions deserve special attention because failures often occur near the edge of the operating range. Adversarial and out-of-distribution testing should supplement nominal evaluation. Long-duration testing is also essential.

Repeated small errors can cause heat, battery degradation, mechanical wear, or gradual drift. Safety cases for learned systems should document the policy, operating limits, training process, validation evidence, runtime safeguards, and fallback behavior. A safety case explains why the system can be trusted within a clearly defined domain. It should not claim universal safety.

Instead, it should state assumptions, known limitations, and conditions that require human intervention. Policy versioning is critical. Every deployed model should have a unique identifier, validated operating range, training configuration, and rollback path. Changes in sensors, firmware, payload, motors, tires, or environment may invalidate earlier safety evidence.

A policy must be revalidated after significant system changes. Deployment should proceed in stages. The first stage is usually simulation and recorded-data evaluation. Software-in-the-loop and hardware-in-the-loop testing then verify timing, interfaces, and safety mechanisms. Shadow mode allows the policy to process real data without controlling the robot.

Pilot deployment begins with low speed, restricted areas, selected missions, and close supervision. Progressive rollout expands the policy to more robots and environments only after meeting predefined criteria. Continuous monitoring remains necessary after full deployment. Safety is not a one-time approval but an ongoing operational process.

All relevant events should be logged, including observations, proposed actions, executed actions, safety overrides, uncertainty, latency, and system response. Logs support incident analysis, drift detection, and future training. Real-world failures and near misses should be reproduced in simulation and added to the regression test suite.

Future policy versions must demonstrate that they handle these cases correctly. Rollback must be immediate when safety metrics deteriorate or unexpected behavior appears. Online policy updates should generally be avoided in industrial robots unless the update mechanism itself has been validated.

A safer approach is to collect field data, retrain offline, validate the new model, and deploy it through a controlled approval process. Safe reinforcement learning does not mean that the learning policy alone guarantees safety. Reliable systems use multiple layers of protection.

These may include mechanical limits, safety-rated sensors, emergency stops, deterministic controllers, software monitors, and operational procedures. The learned policy occupies only one layer within this larger architecture. Defense in depth ensures that one model failure does not directly become a physical accident.

For AMRs, the policy may optimize navigation or control, while certified safety scanners and emergency braking remain independent. For manipulators, RL may improve force or motion planning, while joint limits and human safety zones are enforced by separate systems. For legged robots, the learned policy may control locomotion, while stability monitors and emergency shutdown logic remain active.

The most practical role of safe reinforcement learning is to improve adaptive performance within a verified safety envelope. The policy should know when it is allowed to act, when it should become conservative, and when it must surrender control. Safe reinforcement learning is therefore not a single algorithm.

It is a complete engineering discipline that combines constrained optimization, uncertainty estimation, simulation, formal methods, fallback control, monitoring, validation, and governance. Its success depends on clearly defined hazards, realistic operating limits, diverse data, independent safeguards, and continuous evidence collection.

The final objective is not to eliminate all risk, which is impossible in complex physical environments. The objective is to make risk measurable, bounded, detectable, and manageable while still allowing the robot to learn useful behavior.

When safety is designed into the learning process, deployment architecture, and operational workflow, reinforcement learning can provide adaptation without sacrificing the reliability required for real robotic systems.

안전 강화 학습(Safe Reinforcement Learning)은 유용한 행동을 학습하면서도 해로운 행동의 발생 가능성과 피해 규모를 제한하는 데 초점을 둔다. 로봇 분야에서는 에이전트(Agent)가 사람, 장비, 기반 시설, 그리고 로봇 자체에 허용할 수 없는 위험을 만들지 않으면서 성능을 향상해야 한다는 의미이다. 기존 강화 학습(Reinforcement Learning)은 탐험(Exploration)의 비용이 낮다고 가정하는 경우가 많다. 에이전트는 다양한 행동을 시도하고 반복적으로 실패하면서 더 나은 정책(Policy)을 발견한다. 이러한 가정은 게임이나 시뮬레이션에서는 가능하지만 실제 로봇 환경에서는 매우 위험하다. 이동 로봇은 사람이나 설비에 반복적으로 충돌하면서 충돌 회피를 학습할 수 없다.

매니퓰레이터(Manipulator)는 깨지기 쉬운 물체에 무작위 토크(Torque)를 가하면서 힘 제어를 탐험할 수 없다. 보행 로봇(Legged Robot)도 새로운 동작을 시험할 때마다 넘어져서는 안 된다. 따라서 안전 강화 학습은 안전을 단순한 부가적인 보상 항목이 아니라 학습 과정의 핵심 요구사항으로 다룬다. 목표는 단순히 반환값(Return)을 최대화하는 것이 아니라, 명시적인 제약 조건을 지키고 불확실성을 통제하면서 성능을 향상시키는 것이다. 성능 목표(Performance Objective)와 안전 요구사항(Safety Requirement)은 명확하게 구분되어야 한다. 성능 목표에는 속도, 에너지 효율, 작업 완료, 처리량 등이 포함될 수 있다.

반면 안전 요구사항은 보상이 증가하더라도 절대로 위반해서는 안 되는 조건을 의미한다. 이러한 구분은 안전을 하나의 가중치 기반 보상으로만 표현할 경우 핵심적인 위험 절충 관계(Trade-off)가 가려질 수 있기 때문에 중요하다. 충돌을 단순한 패널티(Penalty)로만 표현하면, 정책은 성능 향상이 충분히 크다고 판단할 경우 작은 충돌 확률을 받아들일 수도 있다. 산업용 로봇에서는 일부 위험 요소가 절대로 타협할 수 없는 조건이다. 최고 속도, 제동 거리, 토크, 온도, 사람과의 안전 거리, 운용 허용 구역 등은 항상 엄격한 범위 안에 유지되어야 한다. 안전 강화 학습은 이러한 조건을 제약 조건(Constraint)으로 모델링하는 경우가 많다.

에이전트는 기대 보상(Expected Reward)을 최대화하면서도 기대 비용(Expected Cost), 고장 확률(Failure Probability), 상태 위반(State Violation)을 정해진 한계 이하로 유지해야 한다. 제약 마르코프 결정 과정(Constrained Markov Decision Process, CMDP)은 기존 강화 학습 구조에 하나 이상의 비용 함수(Cost Function)를 추가한다. 보상은 원하는 성능을 표현하고, 비용은 위험, 자원 사용, 또는 안전 위반을 표현한다. 자율이동로봇(Autonomous Mobile Robot, AMR)의 경우 보상은 임무 완료와 이동 효율을 나타낼 수 있다.

비용은 충돌 위험, 사람과의 근접, 과속, 불안정한 움직임, 과도한 배터리 사용, 제한 구역 진입 등을 나타낼 수 있다. 정책은 이러한 요소들을 최적화하면서 허용된 안전 예산(Safety Budget)을 초과하지 않아야 한다. 이는 모든 요소를 하나의 스칼라 보상으로 결합하는 것보다 훨씬 명확하고 해석 가능하다. 그러나 평균적인 기대 비용만으로는 충분하지 않을 수 있다. 평균 위험은 낮지만 드물게 치명적인 실패를 일으키는 정책은 산업 현장에서 허용할 수 없다. 따라서 최악 조건(Worst-Case), 꼬리 위험(Tail Risk), 실패의 심각도까지 함께 고려해야 한다.

위험 민감 강화 학습(Risk-Sensitive Reinforcement Learning)은 평균 반환값뿐 아니라 결과의 변동성과 낮은 확률로 발생하는 심각한 결과까지 고려한다. 평균 성능은 높지만 가끔 매우 큰 손실을 만드는 행동을 피하도록 학습한다. 조건부 위험 가치(Conditional Value at Risk, CVaR)는 최악의 결과 구간에 더 큰 비중을 주는 대표적인 방법이다. 전체 평균만 최적화하는 대신, 가장 심각한 에피소드(Episode) 집합에서의 평균 손실을 고려한다. 이는 드문 충돌, 전도(Fall), 제어 실패가 허용되지 않는 경우 매우 유용하다. 평균 성능이 약간 낮더라도 극단적인 실패 가능성을 크게 줄이는 정책이 더 우수할 수 있다.

확률 제약(Chance Constraint)은 또 다른 방법이다. 특정 안전 조건을 위반할 확률이 정해진 한계 이하가 되도록 요구한다. 예를 들어 사람의 안전 구역에 진입할 확률, 관절 한계를 초과할 확률, 또는 자세 안정성을 잃을 확률을 매우 낮은 값 이하로 제한할 수 있다. 이러한 확률을 정확하게 추정하는 것은 어렵다. 희귀 사건(Rare Event)을 평가하려면 매우 많은 데이터가 필요하기 때문이다. 시뮬레이션, 중요도 샘플링(Importance Sampling), 적대적 시나리오 생성(Adversarial Scenario Generation), 통계적 신뢰 구간(Confidence Bound)을 활용할 수 있다. 안전 강화 학습은 학습 단계와 배포 단계 모두에서 안전을 고려해야 한다.

이 두 문제는 서로 관련되지만 동일하지는 않다. 학습 안전(Training Safety)은 탐험과 정책 업데이트 과정에서 위험을 어떻게 제한할지를 다룬다. 배포 안전(Deployment Safety)은 학습된 정책이 실제 시스템에서 어떻게 안전하게 동작하는지를 다룬다. 최종적으로 수렴한 정책은 안전하더라도 학습 초기에는 매우 위험할 수 있다. 무작위 탐험은 정책이 충분히 개선되기 전에 극단적인 행동을 생성할 수 있다. 이 때문에 산업용 로봇에서는 제한 없는 온라인 강화 학습(Online Reinforcement Learning)을 거의 사용하지 않는다. 대부분의 탐험은 시뮬레이션이나 매우 엄격하게 통제된 물리 환경에서 수행해야 한다. 행동 제한(Action Limit)은 가장 기본적인 안전 탐험 방법이다.

토크, 속도, 가속도, 조향 속도, 힘, 관절 위치 등을 허용 범위 안으로 제한할 수 있다. 그러나 단순한 행동 클리핑(Action Clipping)만으로는 충분하지 않다. 각각은 허용 범위 안에 있는 행동이라도 연속적으로 실행되면 충돌, 불안정성, 과열을 유발할 수 있다. 따라서 상태 제약(State Constraint)도 함께 필요하다. 로봇은 충돌 위험 구역 밖에 있어야 하고, 온도 제한 이하를 유지하며, 안정적인 자세 범위 안에서 운용되고, 승인된 구역 안에 머물러야 한다. 안전 필터(Safety Filter)는 정책이 제안한 행동을 실행 전에 평가한다. 행동이 제약 조건 위반으로 이어질 가능성이 있으면 더 안전한 행동으로 수정하거나 교체한다.

학습 정책은 여전히 주된 행동을 생성하지만, 필터가 위험한 명령이 실제 시스템에 전달되는 것을 차단한다. 안전 실드(Safety Shield)는 더 넓은 개념의 보호 메커니즘이다. 기하학적 규칙, 예측 모델, 형식 기법(Formal Method), 검증된 제어기를 이용하여 학습 정책을 감시할 수 있다. 이동 로봇에서는 안전 실드가 정책이 제안한 속도로 충분한 제동 거리를 확보할 수 있는지 계산할 수 있다. 위험하다고 판단되면 속도를 낮추거나 정지 명령을 생성한다. 매니퓰레이터에서는 과도한 힘, 자기 충돌(Self-Collision), 관절 한계 초과, 사람 작업 공간 진입을 방지할 수 있다. 보행 로봇에서는 불안정한 지지 상태나 과도한 몸체 기울기를 유발하는 행동을 거부할 수 있다.

제어 장벽 함수(Control Barrier Function)는 안전 필터링을 위한 수학적 프레임워크이다. 장벽 함수는 현재 상태가 안전 집합(Safe Set) 안에 있는지를 나타낸다. 제어기는 시스템이 안전 영역을 벗어나지 않도록 정책이 제안한 행동을 수정한다. 이때 가능한 한 원래 강화 학습 행동을 유지하도록 설계할 수 있다. 제어 장벽 함수는 시스템 동역학을 충분히 알고 있을 경우 국소적인 안전 보장(Local Safety Guarantee)을 제공할 수 있다는 장점이 있다. 그러나 모델 정확도와 안전 집합의 정의에 크게 의존한다. 모델링되지 않은 지연, 외란, 접촉 효과가 존재하면 보장 수준이 약해질 수 있다.

리아프노프 기반 방법(Lyapunov-Based Method)은 안정성(Stability)을 다룬다. 리아프노프 함수(Lyapunov Function)는 시스템이 안정 상태에 가까워지는지 멀어지는지를 측정한다. 정책 업데이트 과정에서 리아프노프 값이 감소하거나 허용 범위 안에 있도록 제약할 수 있다. 이 방법은 균형 유지, 보행, 궤적 추종(Trajectory Tracking)과 같이 불안정성이 빠르게 증가할 수 있는 제어 문제에서 특히 중요하다. 심층 강화 학습(Deep Reinforcement Learning)의 형식적인 안전 보장은 여전히 매우 어렵다. 신경망 정책은 비선형성이 강하고 학습 분포 밖에서는 예측하기 어려운 행동을 보일 수 있다.

따라서 수학적 제약은 모니터링, 백업 제어(Fallback Control), 보수적인 배포와 함께 사용되어야 한다. 모델 예측 안전 필터(Model Predictive Safety Filter)는 짧은 시간 범위에서 미래 상태를 예측한다. 정책 행동이 충돌, 제약 조건 위반, 불안정성으로 이어지는지 평가한다. 위험이 감지되면 제약 최적화기(Constrained Optimizer)가 더 안전한 명령을 생성한다. 이를 통해 학습 정책을 사용하면서도 물리적 제약을 유지할 수 있다. 이러한 보호의 성능은 예측 모델과 예측 시간 범위(Horizon)에 달려 있다. 범위가 너무 짧으면 지연된 위험을 놓칠 수 있고, 너무 길면 계산량이 증가한다. 안전 강화 학습은 백업 제어기도 활용한다.

학습 정책이 불안정하거나 신뢰도가 낮아지면 검증된 제어기, 기존 경로 계획기, 비상 행동이 대신 동작한다. 백업 제어기는 최적의 성능을 제공하지 못하더라도 예측 가능하고 안전해야 한다. AMR의 백업 행동에는 감속, 정지, 기존 지역 경로 계획기 사용, 안전 위치로 복귀, 원격 지원 요청 등이 포함될 수 있다. 매니퓰레이터의 백업 행동에는 현재 자세 유지, 힘 제거, 홈 자세(Home Pose)로 이동, 동작 비활성화 등이 포함될 수 있다. 학습 정책과 백업 제어기 사이의 전환은 매우 신중하게 설계해야 한다. 갑작스러운 전환은 명령 불연속, 진동, 기계적 스트레스를 만들 수 있다.

혼합 제어(Blended Control)는 강화 학습 정책의 영향력을 점진적으로 줄이고 검증된 제어기의 기여도를 높이는 방식이다. 감독 상태 기계(Supervisory State Machine)는 언제 강화 학습 제어를 허용할지를 정의할 수 있다. 정상 센서, 낮은 불확실성, 허용 속도, 정상 위치 추정, 승인 구역 운용 등을 조건으로 사용할 수 있다. 하나라도 조건을 만족하지 않으면 시스템은 성능 저하 모드(Degraded Mode)나 안전 정지(Safe Stop)로 전환할 수 있다. 불확실성 추정(Uncertainty Estimation)은 안전 강화 학습의 핵심 구성 요소이다. 정책은 현재 상황이 학습 경험에서 크게 벗어났을 때 높은 확신을 가져서는 안 된다.

불확실성은 새로운 환경, 센서 고장, 새로운 적재물, 마찰 변화, 예측하기 어려운 사람 행동, 모델 드리프트(Model Drift)에서 발생할 수 있다. 인식론적 불확실성(Epistemic Uncertainty)은 학습 데이터가 부족하여 발생하는 지식의 부족을 의미한다. 우연적 불확실성(Aleatoric Uncertainty)은 환경 자체의 본질적인 무작위성이나 노이즈를 의미한다. 이 두 가지는 서로 다른 의미를 가진다. 인식론적 불확실성은 추가 데이터로 줄일 수 있지만, 우연적 불확실성은 보수적인 의사결정으로 대응해야 할 수 있다. 앙상블 방법(Ensemble Method)은 여러 모델을 학습하고 예측 차이를 비교하여 불확실성을 추정한다.

모델 간 차이가 크면 현재 상태를 충분히 이해하지 못하고 있다는 의미이다. 베이지안 근사(Bayesian Approximation), 신뢰도 네트워크(Confidence Network), 잠재 거리(Latent Distance), 분포 외 탐지기(Out-of-Distribution Detector)도 사용할 수 있다. 불확실성 추정 결과는 행동에 반영되어야 한다. 신뢰도가 낮아지면 로봇은 속도를 줄이고, 안전 거리를 늘리며, 복잡한 행동을 피하고, 백업 제어기로 전환할 수 있다. 안전한 시스템은 위험한 상태뿐 아니라 자신의 예측을 신뢰하기 어려운 상태도 인식해야 한다. 분포 변화(Distribution Shift)는 대표적인 위험 요인이다.

배포 이후 지도, 조명, 날씨, 장비, 교통 패턴, 기계적 마모가 변할 수 있다. 한 분포에서 학습한 정책은 새로운 분포에서 위험한 행동을 생성할 수 있다. 따라서 런타임 모니터링(Runtime Monitoring)이 필요하다. 모니터링은 현재 관측값, 행동 분포, 신뢰도, 성능 지표를 학습 기준선(Baseline)과 비교할 수 있다. 센서 통계, 안전 개입 횟수, 제동 빈도, 추종 오차 등이 갑자기 변하면 새로운 위험이 발생했을 가능성이 있다. 안전 강화 학습은 보상 명세 오류(Reward Misspecification)도 고려해야 한다. 정책은 정의된 보상을 최대화하면서도 실제로는 위험한 행동을 할 수 있다.

보상 해킹(Reward Hacking)은 에이전트가 보상 함수의 허점이나 모델링 오류를 이용하는 현상이다. 속도 보상이 큰 로봇은 사람에게 너무 가까이 지나갈 수 있고, 목표 근접 보상만 있는 로봇은 작업을 끝내지 않고 주변을 맴돌 수 있다. 따라서 안전 요구사항은 학습 보상과 독립적인 평가 지표를 통해 검증해야 한다. 인간 감독(Human Oversight)은 안전 학습을 지원할 수 있다. 엔지니어, 운영자, 원격 감독자가 위험하거나 익숙하지 않은 상황에서 개입할 수 있다. 인간 개입 데이터는 위험 상태를 식별하고, 위험 모델을 학습하며, 정책을 개선하는 데 활용될 수 있다. 그러나 인간 개입만으로 안전을 보장할 수는 없다.

반응 시간, 통신 지연, 운영자 피로 때문에 적절한 시점에 대응하지 못할 수 있다. 인간 입력은 자동 모니터링과 독립 안전 시스템과 결합될 때 가장 효과적이다. 인간 선호 학습(Learning from Human Preferences)은 수치화하기 어려운 안전성과 편안함을 표현하는 데 도움이 된다. 평가자는 두 행동을 비교하여 어느 쪽이 더 안전하거나 자연스러운지 선택할 수 있다. 보상 모델(Reward Model)은 이러한 선호 데이터를 기반으로 학습할 수 있다. 사회적 내비게이션(Social Navigation), 부드러운 움직임, 협력 행동 등에 유용하다. 그러나 선호 모델도 잘못되거나 일관되지 않을 수 있다. 따라서 형식적 제약과 직접적인 안전 지표를 대체해서는 안 된다.

모방 학습(Imitation Learning)은 안전한 초기 정책을 만드는 또 다른 방법이다. 에이전트는 처음부터 무작위 행동을 하지 않고 신뢰할 수 있는 제어기나 전문가의 시연(Demonstration)을 학습한다. 이 방식은 초기 탐험 위험을 줄이고 합리적인 시작 행동을 제공한다. 그러나 전문가 데이터는 드문 고장이나 복구 상황을 충분히 포함하지 않을 수 있다. 따라서 정상 시연만으로는 부족하며 추가적인 안전 테스트가 필요하다. 오프라인 강화 학습(Offline Reinforcement Learning)은 기존 데이터셋으로 학습하기 때문에 안전이 중요한 시스템에 적합하다. 실제 탐험 없이 정책을 개선할 수 있다. 기록된 궤적에는 정상 운용, 사람 개입, 실패, 복구 행동이 포함될 수 있다.

가장 큰 위험은 분포 외 추론(Distributional Extrapolation)이다. 정책이 데이터셋에 거의 없는 행동을 선택하면 가치 추정이 매우 부정확할 수 있다. 보수적 오프라인 강화 학습(Conservative Offline Reinforcement Learning)은 기록된 행동 분포에서 지나치게 멀리 벗어나는 행동을 억제한다. 데이터셋의 품질이 매우 중요하다. 안전 학습에는 성공 궤적뿐 아니라 어려운 상태, 근접 사고(Near Miss), 고장, 보정 행동이 포함되어야 한다. 이상적인 운용 데이터만 포함된 데이터셋은 안전 복구 행동을 가르치지 못한다. 시뮬레이션은 안전 강화 학습 연구와 학습의 주요 환경이다. 실제 피해 없이 위험한 탐험을 수행할 수 있기 때문이다.

시뮬레이터는 충돌, 센서 고장, 고속 불안정, 액추에이터 고장, 드문 환경 이벤트를 생성할 수 있다. 하지만 시뮬레이션에서의 안전성이 자동으로 실제 환경으로 이전되는 것은 아니다. 시뮬레이터는 중요한 위험을 누락하거나 물리적 불확실성을 과소평가할 수 있다. 도메인 랜덤화(Domain Randomization)는 질량, 마찰, 지연, 센서 노이즈, 장애물 행동 등을 변화시켜 안전 강인성을 향상시킨다. 적대적 학습(Adversarial Training)은 의도적으로 실패를 유발하는 상태를 찾는다. 환경이나 별도의 적대 에이전트(Adversary)가 강한 외란, 위험한 장애물 움직임, 센서 오류를 생성한다. 이 방식은 무작위 시나리오보다 정책의 취약점을 더 빠르게 발견할 수 있다.

그러나 적대 조건도 현실적이어야 한다. 비현실적인 공격은 학습 자원을 낭비하고 정책을 지나치게 보수적으로 만들 수 있다. 커리큘럼 학습(Curriculum Learning)은 안전 난이도를 점진적으로 증가시킨다. 처음에는 넓고 단순한 공간에서 시작하고, 이후 좁은 제약, 이동 장애물, 센서 누락, 강한 외란을 추가한다. 정책은 먼저 기본적인 행동을 학습한 뒤 점차 위험 조건에 대한 강인성을 개발한다. 복구 행동(Recovery Behavior)은 명시적으로 학습해야 한다. 모든 실패를 완전히 피할 수는 없으므로 위험 상태에 접근했을 때 어떻게 회복할지를 알아야 한다. 내비게이션 정책은 교착 상태(Deadlock)에서 빠져나오거나, 장애물에서 후퇴하거나, 위치 추정 오류 이후 복구할 수 있어야 한다.

제어 정책은 외부 충격, 휠 슬립, 적재물 급변, 일부 액추에이터 고장 이후 안정성을 회복할 수 있어야 한다. 매니퓰레이터는 예상하지 못한 접촉 이후 힘을 줄이거나, 물체를 놓거나, 안전한 자세로 돌아갈 수 있어야 한다. 복구 보상은 위험한 상태에 의도적으로 진입하도록 만들어서는 안 된다. 실패 상태는 시나리오가 통제된 방식으로 주입해야 한다. 안전 탐험에는 도달 가능성 분석(Reachability Analysis)도 사용할 수 있다. 이는 시스템이 안전을 유지하거나 안전 상태로 복귀할 수 있는 상태 집합을 추정한다. 에이전트는 복구 불가능한 영역으로 진입하지 않도록 제한된다. 도달 가능성 분석은 저차원 시스템에서는 강한 보장을 제공할 수 있지만 복잡한 로봇과 대규모 신경망 정책에서는 계산량이 매우 크다.

근사 도달 가능성(Approximate Reachability)과 학습 기반 안전 크리틱(Safety Critic)은 이러한 방법을 더 큰 시스템에 적용하려는 접근법이다. 안전 크리틱은 미래 비용이나 제약 위반 확률을 추정한다. 정책은 위험이 높다고 평가된 행동을 피할 수 있다. 크리틱은 시뮬레이션 실패, 실제 개입, 위험 궤적 데이터를 이용하여 학습할 수 있다. 그러나 안전 크리틱도 오류를 만들 수 있으므로 보수적으로 검증하고 독립적인 보호 시스템과 함께 사용해야 한다. 다중 에이전트 시스템(Multi-Agent System)은 추가적인 안전 문제를 만든다. 한 로봇의 행동은 다른 로봇의 위험 수준을 변화시킨다. 개별적으로 안전한 정책이라도 전체적으로는 혼잡, 교착, 위험한 경쟁을 만들 수 있다.

안전 다중 에이전트 강화 학습(Safe Multi-Agent Reinforcement Learning)은 통신, 통행 우선권, 협조 제동, 공유 구역, 다른 에이전트의 불확실성을 함께 고려해야 한다. 중앙집중형 학습(Centralized Training)은 모든 로봇의 정보를 사용할 수 있지만 실제 실행은 지역 관측과 통신에 의존하는 분산 실행(Decentralized Execution)으로 수행할 수 있다. 전역 안전 제약에는 전체 혼잡도, 최소 로봇 간 거리, 공유 자원 용량, 비상 통로 유지 등이 포함될 수 있다. 한 로봇이 만든 위험이 나중에 다른 로봇의 궤적에서 나타날 수 있기 때문에 기여도 할당(Credit Assignment)은 여전히 어렵다. 통신 고장도 반드시 고려해야 한다.

메시지가 지연되거나 손실되거나 서로 일치하지 않아도 로봇은 안전을 유지해야 한다. 정책은 완벽한 협력을 가정해서는 안 된다. 보수적인 우선권 규칙과 지역 충돌 회피는 항상 존재해야 한다. 인간-로봇 상호작용(Human-Robot Interaction)에서의 안전 강화 학습은 특별한 주의가 필요하다. 사람의 움직임은 불확실하고, 사람은 로봇의 의도를 항상 이해하지 못한다. 로봇은 편안한 거리를 유지하고, 예측 가능한 궤적을 사용하며, 급가속을 피하고, 자신의 의도를 명확하게 전달해야 한다. 사회적 안전(Social Safety)은 물리적 충돌 회피뿐 아니라 심리적 편안함까지 포함한다. 기술적으로 충돌하지 않는 경로라도 사람에게 지나치게 가까이 접근하거나 길을 막거나 예측하기 어렵게 움직이면 허용하기 어렵다.

안전 평가는 다양한 지표를 사용해야 한다. 평균 보상과 작업 성공률만으로는 충분하지 않다. 충돌률, 근접 사고 빈도, 최소 안전 거리, 개입 횟수, 속도 제한 위반, 제약 위반, 불확실성 발생, 백업 제어 활성화 등을 측정해야 한다. 제어 시스템에서는 추종 오차, 안정 여유(Stability Margin), 오버슈트(Overshoot), 열 부하(Thermal Load), 토크 제한, 복구 시간도 평가해야 한다. 매니퓰레이션에서는 접촉력, 물체 손상, 관절 한계 초과, 사람 구역 침입 등이 중요하다. 희귀 사건 지표를 평가하려면 매우 많은 시험이 필요하다. 안전 결과에는 신뢰 구간과 통계적 검정이 함께 제공되어야 한다. 작은 테스트 세트에서 실패가 한 번도 없었다고 해서 반드시 안전한 것은 아니다.

단지 취약점을 발견할 만큼 시험이 충분하지 않았을 수 있다. 시나리오 커버리지(Scenario Coverage)는 체계적으로 관리해야 한다. 속도, 적재물, 지형, 날씨, 센서 상태, 교통 밀도, 작업 유형을 다양하게 조합해야 한다. 고장은 운용 한계에 가까운 조건에서 자주 발생하므로 경계 조건(Boundary Condition)을 특별히 검증해야 한다. 적대적 테스트와 분포 외 테스트(Out-of-Distribution Testing)는 정상 평가를 보완해야 한다. 장시간 운용 시험도 필수적이다. 반복적인 작은 오차는 발열, 배터리 성능 저하, 기계적 마모, 점진적인 드리프트를 만들 수 있다.

학습 기반 시스템의 안전 사례(Safety Case)는 정책, 운용 한계, 학습 과정, 검증 근거, 런타임 보호, 백업 행동을 문서화해야 한다. 안전 사례는 정의된 운용 영역 안에서 시스템을 신뢰할 수 있는 이유를 설명한다. 보편적인 안전성을 주장해서는 안 된다. 대신 가정, 알려진 한계, 인간 개입이 필요한 조건을 명확하게 기록해야 한다. 정책 버전 관리(Policy Versioning)는 매우 중요하다. 모든 배포 모델은 고유 식별자, 검증된 운용 범위, 학습 설정, 롤백(Rollback) 경로를 가져야 한다. 센서, 펌웨어(Firmware), 적재물, 모터, 타이어, 환경이 변경되면 이전의 안전 검증이 더 이상 유효하지 않을 수 있다. 중요한 시스템 변경 후에는 정책을 반드시 재검증해야 한다.

배포는 단계적으로 진행해야 한다. 첫 단계는 일반적으로 시뮬레이션과 기록 데이터 평가이다. 이후 소프트웨어-인-더-루프(Software-in-the-Loop, SIL)와 하드웨어-인-더-루프(Hardware-in-the-Loop, HIL)를 이용하여 타이밍, 인터페이스, 안전 기능을 검증한다. 섀도우 모드(Shadow Mode)에서는 정책이 실제 데이터를 처리하지만 로봇을 직접 제어하지 않는다. 파일럿 배포(Pilot Deployment)는 낮은 속도, 제한된 구역, 선택된 임무, 강한 감독 아래에서 시작한다. 점진적 배포(Progressive Rollout)는 미리 정의된 기준을 통과한 경우에만 더 많은 로봇과 환경으로 확대한다. 전체 배포 이후에도 지속적인 모니터링이 필요하다.

안전은 한 번의 승인으로 끝나는 것이 아니라 계속 관리해야 하는 운영 과정이다. 관측값, 제안 행동, 실제 실행 행동, 안전 개입, 불확실성, 지연 시간, 시스템 응답을 모두 기록해야 한다. 로그(Log)는 사고 분석, 드리프트 탐지, 향후 학습에 활용된다. 실제 실패와 근접 사고는 시뮬레이션에서 재현하고 회귀 테스트(Regression Test)에 추가해야 한다. 이후의 모든 정책은 이러한 사례를 올바르게 처리하는지 검증해야 한다. 안전 지표가 악화되거나 예상하지 못한 행동이 나타나면 즉시 이전 버전으로 롤백할 수 있어야 한다. 산업용 로봇에서 온라인 정책 업데이트는 업데이트 메커니즘 자체가 충분히 검증되지 않는 한 일반적으로 피해야 한다.

더 안전한 방식은 현장 데이터를 수집하고, 오프라인에서 다시 학습하며, 새 모델을 검증한 뒤 통제된 승인 절차를 통해 배포하는 것이다. 안전 강화 학습은 학습 정책 하나만으로 안전을 보장한다는 의미가 아니다. 신뢰성 있는 시스템은 여러 개의 보호 계층(Protection Layer)을 사용한다. 기계적 제한, 안전 인증 센서, 비상 정지, 결정론적 제어기, 소프트웨어 감시기, 운영 절차 등이 포함될 수 있다. 학습 정책은 이러한 전체 아키텍처 가운데 하나의 계층만 담당한다. 심층 방어(Defense in Depth)는 하나의 모델 실패가 곧바로 물리적 사고로 이어지지 않도록 한다. AMR에서는 정책이 내비게이션이나 제어를 최적화하더라도 인증된 안전 스캐너와 비상 제동은 독립적으로 유지되어야 한다.

매니퓰레이터에서는 강화 학습이 힘 제어나 모션 계획을 개선하더라도 관절 한계와 사람 안전 구역은 별도 시스템에서 강제되어야 한다. 보행 로봇에서는 학습 정책이 이동을 제어하더라도 안정성 감시기와 비상 종료 로직은 계속 동작해야 한다. 안전 강화 학습의 가장 현실적인 역할은 검증된 안전 범위(Safety Envelope) 안에서 적응형 성능을 향상시키는 것이다. 정책은 언제 동작할 수 있는지, 언제 보수적으로 행동해야 하는지, 언제 제어권을 넘겨야 하는지를 알아야 한다. 따라서 안전 강화 학습은 하나의 알고리즘이 아니다.

이는 제약 최적화(Constrained Optimization), 불확실성 추정, 시뮬레이션, 형식 기법, 백업 제어, 모니터링, 검증, 거버넌스(Governance)를 결합하는 종합적인 엔지니어링 분야이다. 성공 여부는 위험 요인의 명확한 정의, 현실적인 운용 한계, 다양한 데이터, 독립적인 보호 장치, 지속적인 근거 수집에 달려 있다. 최종 목표는 모든 위험을 완전히 제거하는 것이 아니다. 복잡한 물리 환경에서는 그것이 불가능하다. 진정한 목표는 위험을 측정 가능하고, 제한 가능하며, 탐지 가능하고, 관리 가능한 상태로 만드는 동시에 로봇이 유용한 행동을 학습하도록 하는 것이다.

안전이 학습 과정, 배포 아키텍처, 운영 워크플로에 처음부터 포함될 때 강화 학습은 실제 로봇 시스템이 요구하는 신뢰성을 해치지 않으면서도 적응 능력을 제공할 수 있다.

##  

## 09.8 RL Limitations in AMR

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

Reinforcement learning offers powerful methods for adaptive navigation and control, but its practical use in autonomous mobile robots remains limited by safety, data, computation, validation, and operational complexity. These limitations become especially important when AMRs operate near people, equipment, and critical infrastructure.

An AMR must perform reliably across long periods rather than only during short demonstrations. A policy that succeeds in most test episodes may still be unsuitable for production if it occasionally causes collisions, deadlocks, unstable motion, or unpredictable responses. One major limitation is sample inefficiency.

Reinforcement learning often requires millions of interactions before a useful policy emerges. Collecting this experience on a physical AMR would consume excessive time, energy, labor, and hardware life. Real-world exploration also creates safety risk. Early policies may command unnecessary rotations, aggressive acceleration, unsafe obstacle approaches, or inefficient routes.

These actions cannot be freely tested in warehouses, hospitals, factories, airports, or public spaces. Simulation reduces this problem but does not eliminate it. A policy can collect large amounts of virtual experience, yet its performance may decline sharply when transferred to a physical robot because the simulated environment differs from reality.

This difference is known as the simulation-to-reality gap. It may arise from incorrect friction, wheel slip, motor response, braking delay, sensor noise, communication latency, floor conditions, or human behavior. AMR navigation is particularly sensitive to small modeling errors. A slight difference in tire friction or actuator delay may change stopping distance and turning behavior.

A policy trained under ideal conditions may therefore produce unsafe motion on worn, dusty, wet, or uneven floors. Sensor models are another source of mismatch. Simulated LiDAR and depth cameras often provide clean measurements, while real sensors contain dropout, reflections, occlusion, motion distortion, calibration error, and asynchronous timestamps.

A policy may appear robust when trained with perfect observations but fail when real sensor data becomes incomplete. Industrial environments contain reflective metal, transparent doors, dark surfaces, dust, vibration, and changing lighting that are difficult to model accurately. Localization errors also create problems.

Reinforcement learning policies frequently assume that robot pose and goal direction are sufficiently accurate. Real AMRs may experience map mismatch, wheel odometry drift, GNSS loss, or temporary scan-matching failure. A small pose error can cause an action to be inappropriate. A turning command that is correct for the estimated state may move the real robot toward an obstacle.

Reinforcement learning does not automatically compensate for incorrect state estimation. Partial observability is another limitation. The robot cannot see behind shelves, walls, vehicles, or people. It may not know whether a hidden pedestrian is approaching or whether another robot will enter a shared corridor.

Memory-based policies can use recent observations, but hidden information remains uncertain. Recurrent networks may improve prediction, yet they can also become difficult to train, validate, and interpret. Human behavior is especially difficult to model. People may hesitate, reverse direction, ignore traffic rules, block routes, or approach the robot unexpectedly.

A policy trained on simple pedestrian models may behave poorly in real social environments. Social navigation requires more than collision avoidance. The AMR must maintain comfortable distance, move predictably, avoid trapping people, and respect local movement conventions. These requirements are difficult to represent through a single reward function.

Reward design is therefore a major limitation. The policy learns what the reward measures, not necessarily what the designer intended. A poorly designed reward may create behavior that appears successful numerically but is operationally unacceptable. For example, rewarding only rapid goal progress may encourage the robot to pass too closely to obstacles.

Rewarding short travel time may encourage aggressive acceleration. Rewarding collision avoidance too strongly may cause the robot to stop excessively. A reward may also create oscillation. If forward progress and obstacle clearance compete, the robot may alternate between movement and avoidance without committing to a stable path.

Reward hacking occurs when the agent exploits a weakness in the reward definition. An AMR may circle near a destination, repeatedly request passage, or remain in a locally rewarding state without completing the mission. It is difficult to guarantee that every possible shortcut has been removed. Complex environments contain interactions that designers did not anticipate during reward construction.

Multi-objective optimization adds further difficulty. AMRs must balance safety, mission time, energy use, battery health, path length, motion comfort, congestion, and equipment wear. Combining these goals through weighted reward terms requires careful tuning. Small weight changes can produce large behavioral differences, making policy development unstable and difficult to reproduce.

A policy optimized for travel time may consume more energy. A policy optimized for energy may move too slowly. A policy optimized for clearance may block traffic by remaining excessively cautious. The correct trade-off may also vary by customer and application.

A hospital AMR, factory transport robot, outdoor patrol robot, and warehouse vehicle have different safety margins and performance priorities. A single policy may therefore not generalize well across products. Retuning rewards and retraining for every robot configuration increases engineering cost. Generalization is one of the most serious limitations.

Policies may memorize patterns from training maps instead of learning transferable navigation principles. An AMR trained in a small collection of corridors may perform well during evaluation on similar layouts but fail in a new facility with different widths, intersections, slopes, doors, or obstacle distributions. Visual and semantic changes can also reduce performance.

New shelves, signs, reflective objects, construction zones, pallets, carts, and temporary barriers may create states outside the training distribution. Outdoor AMRs face even greater variation. Rain, snow, fog, leaves, mud, gravel, shadows, sunlight, and temperature changes affect perception and motion.

Domain randomization helps by varying simulated conditions, but it is difficult to determine the correct range. Too little variation produces fragile policies, while excessive variation makes training slower and may produce overly conservative behavior. A policy trained to tolerate extreme uncertainty may sacrifice efficiency under normal conditions.

This creates a practical trade-off between robustness and performance. Distribution shift continues after deployment. Facility layouts change, tires wear, payloads vary, sensors age, and pedestrian patterns evolve. A policy validated at one time may become less reliable later.

Detecting this degradation is difficult because average mission success may remain high while rare hazardous situations increase. Reinforcement learning policies are also difficult to interpret. Deep neural networks can contain millions of parameters, and their decisions may not have a clear human-readable explanation.

When an AMR turns unexpectedly or stops in an open area, engineers may struggle to determine which sensor feature or learned association caused the action. Value estimates, attention maps, and trajectory analysis can provide partial insight, but they do not fully explain complex policies. Lack of explainability complicates incident analysis, customer acceptance, certification, and maintenance.

Industrial teams often prefer deterministic rules because they can be inspected and tested directly. Validation is another major challenge. Traditional navigation modules can be tested through defined requirements, geometric constraints, and deterministic scenarios. Learned policies may produce different actions across small input changes. The possible state space of a real AMR is enormous.

It includes combinations of maps, speeds, payloads, obstacles, sensor faults, human behavior, communication delay, and battery condition. Testing every combination is impossible. A limited test set cannot prove that the policy will remain safe in all future situations. High average success rates may hide rare but severe failures.

A policy with a 99.99 percent success rate may still create unacceptable incidents when deployed across hundreds of robots operating continuously. Rare-event evaluation requires very large numbers of episodes. Generating and reviewing these scenarios can be expensive even in simulation. Statistical confidence is also difficult to establish.

Zero collisions in a small test set does not prove that the true collision probability is sufficiently low. Adversarial testing can search for failures, but the adversarial scenarios must remain realistic. Unrealistic conditions may provide little practical value, while insufficiently strong tests may miss important weaknesses. Safety certification presents additional difficulties.

Many safety standards were designed around deterministic systems, physical safeguards, and clearly defined failure modes. A neural reinforcement learning policy may not provide a simple proof of behavior. Its internal parameters do not directly correspond to physical safety requirements.

For this reason, RL policies usually cannot replace certified safety scanners, emergency stops, safety controllers, protective fields, or mechanical limits. Independent safety layers remain necessary, but they also reduce the policy\'s authority. The AMR may frequently override RL commands, limiting the practical benefit of the learned behavior.

If safety interventions occur often, the policy has not learned the real operational constraints effectively. If interventions are rare, extensive evidence is still required to justify trust. Runtime monitoring adds computational and architectural complexity.

The system may need uncertainty estimation, out-of-distribution detection, safety filtering, command validation, fallback control, and event logging. Each additional layer introduces interfaces, failure modes, timing requirements, and validation effort. Uncertainty estimation itself is imperfect. A policy may assign high confidence to an unfamiliar state or low confidence to a safe one.

Ensemble models and Bayesian approximations increase computational cost. They also do not provide absolute guarantees that unknown conditions will be detected. Fallback control is essential, but switching between RL and conventional control can be difficult. Sudden changes in command source may cause discontinuity, oscillation, or delayed response.

A state machine or blending mechanism can smooth the transition, but this adds more design logic and test cases. The fallback controller must also remain fully maintained. As a result, using RL may not eliminate the need for the classical navigation stack. This duplication increases software complexity, memory use, maintenance effort, and integration cost.

Real-time computation creates another limitation. AMRs must process sensors, localization, planning, control, communication, and safety functions within strict time limits. Large neural policies may require GPUs or high-performance edge computers. These platforms increase power consumption, heat, weight, cost, and system integration requirements.

Average inference time may appear acceptable, but worst-case latency and timing jitter can still cause unsafe responses. Thermal throttling may slow inference during long operation. Competing workloads such as perception, mapping, video streaming, and fleet communication may further increase delay.

Network-based inference is generally unsuitable for safety-critical low-level control because connectivity may be delayed or unavailable. Edge inference avoids network dependence but requires sufficient onboard computing resources. This creates a trade-off between model complexity and practical deployment cost. Energy consumption is also relevant.

An AMR with powerful GPUs may reduce battery operating time. The energy saved by an optimized RL policy may be smaller than the power consumed by the additional computation. Model compression, quantization, and pruning can reduce cost, but they may alter policy behavior and require complete revalidation. Training cost can also be high.

Large simulation environments, parallel training, hyperparameter searches, and repeated evaluations require substantial GPU or CPU resources. Reinforcement learning is sensitive to random seeds, learning rates, reward scales, network architecture, and environment settings. Two training runs with similar configurations may produce different behaviors.

This reduces reproducibility and makes engineering schedules difficult to predict. Hyperparameter tuning is often expensive because the effect of one parameter may not become visible until many training episodes have been completed. A policy may improve early and later collapse. Another may achieve high reward but poor safety.

Selecting the final checkpoint requires extensive independent evaluation. Data management becomes complex. Teams must track simulator versions, map sets, reward definitions, policy checkpoints, randomization ranges, and evaluation results. A small change in physics, sensor modeling, collision geometry, or time step may change learned behavior significantly.

Without strict version control, it becomes impossible to reproduce the policy deployed on a robot or understand why it behaves differently from another version. Policy updates also create operational risk. A new model may improve one environment while degrading another. Regression testing must therefore include previous failures, edge cases, customer-specific maps, and hardware configurations.

Gradual rollout and rollback mechanisms are necessary, but they increase deployment complexity. Continual online learning is often presented as an advantage of reinforcement learning, yet it is difficult to use safely in industrial AMRs. A policy that updates during operation changes after validation. Its future behavior may no longer match the tested model.

Online updates also reduce reproducibility because two robots may develop different policies from different experiences. Most production systems therefore collect data online but perform learning offline. The new policy is then validated and deployed through a controlled process. This reduces risk but also limits the promise of continuous autonomous improvement.

Offline reinforcement learning avoids active exploration but introduces other problems. The policy depends strongly on the quality and coverage of the historical dataset. Recorded AMR data usually contains many examples of normal operation but few collisions, faults, or recovery events.

A policy trained on this dataset may perform well in routine conditions but fail when it encounters a rare state. Value estimates become unreliable for actions not represented in the data. Conservative methods reduce this problem but may restrict improvement beyond the existing controller. Multi-robot operation introduces additional limitations.

Each robot\'s behavior changes the environment observed by others. A policy trained with a fixed model of other robots may perform poorly when the fleet size, communication pattern, or task distribution changes. Cooperative rewards create credit-assignment problems. It may be difficult to determine which robot caused congestion, delay, or a future deadlock.

Centralized training may use global information unavailable during decentralized execution. Communication failure can then reduce policy performance. Fleet-level policies also increase the state and action spaces dramatically. Training becomes more expensive and validation becomes even more difficult. Policies may learn competitive or unfair behavior if global objectives are poorly specified.

One robot may repeatedly yield while another receives most high-priority tasks. Shared areas, elevators, doors, chargers, and narrow corridors require explicit coordination. Classical reservation and traffic-control systems often provide clearer guarantees. Reinforcement learning may improve these systems, but fully learned coordination can be difficult to explain and certify.

Maintenance personnel may also lack the expertise required to diagnose learned policies. Traditional AMR teams are familiar with maps, planners, controllers, and safety scanners. Reinforcement learning adds neural networks, simulation pipelines, reward engineering, training infrastructure, and model monitoring.

Organizations must maintain specialized skills across robotics, machine learning, safety, data engineering, and DevOps. This increases staffing requirements and dependence on a small number of experts. Vendor and tool dependence can also become a problem. Training may rely on a specific simulator, physics engine, GPU platform, or software framework.

Changes in these tools may require retraining or migration. Long-term support is important because industrial AMRs may remain in service for many years. Customer acceptance is another constraint. Customers generally expect predictable behavior, clear service procedures, and measurable performance guarantees.

A statement that the robot learned its behavior through experience may not reassure operators after an unexpected movement. Customers may request clear explanations of operating limits, failure handling, and responsibility. Liability becomes difficult when a learned policy contributes to an accident.

Engineers must determine whether the cause was training data, reward design, sensor failure, model drift, software integration, or safety-system behavior. Detailed logging is therefore necessary, but storing high-frequency sensor and policy data creates storage, privacy, and analysis challenges.

Privacy concerns may arise when cameras or human-interaction data are recorded for training and incident review. Cybersecurity must also be considered. Policy files, training pipelines, reward definitions, and update mechanisms can become attack surfaces. An attacker who modifies a policy or observation stream may cause unsafe behavior without changing the conventional navigation software.

Model integrity checks, secure boot, signed updates, access control, and anomaly monitoring are required. These protections add further system complexity. Another limitation is the difficulty of defining the appropriate authority for RL. High-level decisions are easier to constrain but may provide limited performance improvement.

Low-level control provides greater adaptation but creates much higher safety, timing, and validation risk. For many AMRs, the most practical role of RL is therefore narrow and bounded. It may select among routes, adjust speed, optimize energy, or provide a small residual correction. Using RL for direct motor control or complete navigation replacement is usually more difficult to justify.

Hybrid architectures are often more realistic. A classical planner provides global routes, a learned policy handles selected local decisions, and a deterministic controller executes motion. An independent safety layer monitors the final command. This design limits the consequences of policy failure. However, hybrid systems require careful arbitration.

The components may disagree, create oscillation, or duplicate functions. Clear responsibility boundaries and update rates are essential. The RL policy should not conflict with traffic rules, mission logic, safety fields, or low-level control. The added complexity must provide measurable value.

If RL improves travel time only slightly while greatly increasing validation and maintenance cost, it may not be commercially justified. A conventional method may offer lower peak performance but higher predictability, easier certification, and faster deployment.

The decision to use reinforcement learning should therefore begin with a clear problem that cannot be solved adequately by traditional methods. Suitable problems may involve complex adaptation, uncertain interactions, or optimization across long-term objectives. Problems with simple dynamics, fixed rules, and well-defined models may be better served by classical planning and control.

A production AMR should not use reinforcement learning merely because it is technically fashionable. A strong engineering process should compare RL with non-learning baselines using safety, efficiency, cost, maintainability, and lifecycle metrics. The baseline should include realistic tuning effort. Reinforcement learning should demonstrate a meaningful advantage under representative conditions.

Even when RL is selected, the policy should operate within a defined operational design domain. This domain specifies allowed maps, payloads, speeds, sensor health, weather, traffic, and hardware configuration. Operation outside this domain should trigger reduced performance, fallback control, or safe stop.

The policy should not attempt to maintain full autonomy when the assumptions supporting its validation are no longer true. Long-term monitoring is necessary because the real environment continues to evolve. Success at deployment does not guarantee future reliability.

Safety intervention rate, confidence, collision warnings, energy consumption, travel time, deadlock frequency, and human complaints should be monitored. Changes in these indicators may reveal performance drift before a serious incident occurs. Field failures and near misses should be reproduced in simulation and added to regression testing.

This creates a continuous improvement loop, but each update requires new training, evaluation, approval, and deployment effort. The lifecycle cost of this loop may be substantial. Reinforcement learning limitations in AMRs are therefore not caused by one weak algorithm. They arise from the interaction of learning, robotics, safety, infrastructure, people, and business requirements.

The technology is strongest when its role is carefully bounded, its benefits are measurable, and its behavior is protected by conventional engineering safeguards. The safest approach is usually to preserve deterministic mission logic, proven navigation components, verified low-level control, and independent safety systems.

Reinforcement learning can then provide adaptation in selected areas where traditional methods struggle. Its output should be monitored, constrained, and replaceable. A fallback path must remain available whenever confidence, sensor quality, or operational conditions become unacceptable. In this role, RL becomes an enhancement rather than a single point of failure.

The final limitation is that learned performance is always conditional. It depends on training coverage, simulator quality, reward alignment, hardware consistency, and operating assumptions. No policy can guarantee reliable behavior in every environment or under every failure. A realistic AMR strategy therefore treats reinforcement learning as one component in a larger autonomous system.

It combines learning with formal requirements, deterministic control, safety engineering, validation, monitoring, and human governance. When these limitations are recognized early, reinforcement learning can be applied selectively and responsibly. When they are ignored, impressive simulation results may create fragile, expensive, and unsafe products.

The practical question is not whether reinforcement learning can navigate or control an AMR. The more important question is whether it can deliver enough verified value to justify its additional risk, complexity, cost, and lifecycle burden.

한글

강화 학습(Reinforcement Learning)은 적응형 내비게이션(Navigation)과 제어(Control)에 강력한 방법을 제공하지만, 자율이동로봇(Autonomous Mobile Robot, AMR)에서 실제로 활용하는 데에는 안전성(Safety), 데이터(Data), 계산(Computation), 검증(Validation), 운용 복잡성(Operational Complexity) 등 다양한 한계가 존재한다. 이러한 한계는 AMR이 사람, 장비, 핵심 인프라 주변에서 동작할수록 더욱 중요해진다. AMR은 단순히 짧은 시연에서 좋은 성능을 보이는 것이 아니라 장기간 안정적으로 동작해야 한다.

대부분의 시험에서는 성공하더라도 간헐적으로 충돌(Collision), 교착 상태(Deadlock), 불안정한 움직임, 예측하기 어려운 행동이 발생한다면 실제 산업 환경에서는 사용할 수 없다. 가장 큰 한계 중 하나는 샘플 비효율성(Sample Inefficiency)이다. 강화 학습은 유용한 정책을 얻기 위해 수백만 번의 상호작용이 필요한 경우가 많다. 이러한 경험을 실제 AMR에서 수집하려면 엄청난 시간, 에너지, 인력, 장비 수명이 소모된다. 실제 환경에서의 탐험(Exploration)은 안전 위험도 함께 만든다. 초기 정책은 불필요한 회전, 과도한 가속, 위험한 장애물 접근, 비효율적인 경로를 생성할 수 있다. 이러한 행동은 창고, 병원, 공장, 공항, 공공장소에서 자유롭게 시험할 수 없다.

시뮬레이션(Simulation)은 이러한 문제를 줄여주지만 완전히 해결하지는 못한다. 정책은 가상 환경에서 방대한 경험을 학습할 수 있지만, 실제 로봇으로 이전되면 성능이 크게 저하될 수 있다. 이러한 차이를 시뮬레이션-현실 간 차이(Simulation-to-Reality Gap, Sim-to-Real Gap)라고 한다. 이는 마찰(Friction), 휠 슬립(Wheel Slip), 모터 응답, 제동 지연, 센서 노이즈, 통신 지연, 바닥 상태, 사람의 행동 차이 등에서 발생한다. AMR 내비게이션은 작은 모델링 오차에도 매우 민감하다. 타이어 마찰이나 액추에이터 지연이 조금만 달라져도 제동 거리와 회전 특성이 변할 수 있다.

이상적인 환경에서 학습한 정책은 마모되거나 먼지가 많은 바닥, 젖은 노면, 울퉁불퉁한 바닥에서는 위험한 움직임을 보일 수 있다. 센서 모델(Sensor Model) 역시 중요한 차이를 만든다. 시뮬레이션의 라이다(LiDAR)와 깊이 카메라(Depth Camera)는 깨끗한 데이터를 제공하지만 실제 센서는 데이터 누락(Dropout), 반사(Reflection), 가림(Occlusion), 움직임 왜곡(Motion Distortion), 보정 오차(Calibration Error), 비동기 타임스탬프를 포함한다. 완벽한 관측값만 사용하여 학습한 정책은 실제 센서 데이터가 불완전해지는 순간 성능이 급격히 저하될 수 있다.

산업 환경에는 금속 반사, 유리문, 어두운 표면, 먼지, 진동, 조명 변화와 같은 요소가 지속적으로 존재한다. 위치 추정(Localization) 오류도 중요한 문제이다. 강화 학습 정책은 로봇의 위치와 목표 방향이 정확하다고 가정하는 경우가 많다. 그러나 실제 AMR에서는 지도 불일치(Map Mismatch), 휠 오도메트리 드리프트(Odometry Drift), GNSS 손실, 스캔 매칭 실패가 발생할 수 있다. 작은 위치 오차도 잘못된 행동을 유발할 수 있다. 추정 위치에서는 올바른 회전 명령이 실제 환경에서는 장애물을 향해 이동하는 결과를 만들 수도 있다. 강화 학습은 상태 추정 오류를 자동으로 보정하지 못한다. 부분 관측 가능성(Partial Observability)도 중요한 한계이다.

로봇은 선반, 벽, 차량, 사람 뒤를 볼 수 없다. 숨겨진 보행자가 접근하는지, 다른 로봇이 좁은 통로로 진입하는지도 알 수 없다. 메모리 기반 정책(Memory-Based Policy)은 최근 관측 정보를 활용할 수 있지만 숨겨진 정보 자체는 여전히 불확실하다. 순환 신경망(Recurrent Network)은 예측을 향상시킬 수 있지만 학습과 검증이 더욱 어려워질 수 있다. 사람의 행동(Human Behavior)은 특히 모델링하기 어렵다. 사람은 갑자기 멈추거나 방향을 바꾸고, 교통 규칙을 무시하거나, 예기치 않게 로봇 앞으로 접근할 수 있다. 단순한 보행자 모델만으로 학습한 정책은 실제 사회적 환경에서 제대로 동작하지 않을 수 있다.

사회적 내비게이션(Social Navigation)은 단순히 충돌만 피하는 것이 아니다. AMR은 적절한 거리 유지, 예측 가능한 움직임, 사람을 가두지 않는 행동, 지역 문화에 맞는 이동 방식을 고려해야 한다. 이러한 요소를 하나의 보상 함수(Reward Function)로 표현하는 것은 매우 어렵다. 보상 설계(Reward Design)는 강화 학습의 대표적인 한계이다. 정책은 설계자가 의도한 행동이 아니라 보상이 정의한 행동을 학습한다. 잘못 설계된 보상은 수치적으로는 성공하지만 실제로는 사용할 수 없는 행동을 만들 수 있다. 예를 들어 목표까지 빠르게 이동하는 보상만 주면 로봇은 장애물에 지나치게 가까이 접근할 수 있다. 이동 시간만 최적화하면 과도하게 가속할 수 있다.

충돌 회피 보상이 너무 크면 조금만 위험해도 계속 멈추는 정책이 될 수 있다. 보상 함수는 진동(Oscillation)도 유발할 수 있다. 전진 보상과 장애물 회피 보상이 경쟁하면 로봇은 앞으로 갔다가 뒤로 물러나는 행동을 반복하며 안정적인 경로를 선택하지 못할 수 있다. 보상 해킹(Reward Hacking)은 정책이 보상의 허점을 이용하는 현상이다. AMR은 목적지 근처를 계속 맴돌거나, 반복적으로 통행을 요청하거나, 실제 임무를 끝내지 않으면서 높은 보상을 받을 수도 있다. 복잡한 환경에서는 설계자가 예상하지 못한 지름길(Shortcut)이 존재하기 때문에 모든 허점을 제거하기는 어렵다. 다목적 최적화(Multi-Objective Optimization)는 또 다른 어려움을 만든다.

AMR은 안전, 작업 시간, 에너지 사용, 배터리 수명, 경로 길이, 승차감, 교통 혼잡, 장비 마모를 동시에 고려해야 한다. 이러한 목표를 가중치 기반 보상으로 결합하려면 매우 정교한 튜닝(Tuning)이 필요하다. 작은 가중치 변화만으로도 정책의 행동이 크게 달라질 수 있다. 이동 시간을 최적화하면 에너지 소비가 증가할 수 있다. 에너지를 최적화하면 이동 속도가 지나치게 느려질 수 있다. 안전 거리를 최적화하면 지나치게 보수적으로 움직여 다른 로봇의 통행을 막을 수도 있다. 또한 고객과 응용 분야에 따라 요구사항도 달라진다. 병원 AMR, 공장 물류 로봇, 야외 순찰 로봇, 창고 운반 차량은 모두 서로 다른 안전 기준과 성능 목표를 가진다.

따라서 하나의 정책이 모든 제품에 일반화(Generalization)되기는 어렵다. 제품마다 보상 함수를 다시 조정하고 재학습해야 하므로 개발 비용이 증가한다. 일반화 성능은 강화 학습의 가장 큰 한계 중 하나이다. 정책은 일반적인 내비게이션 원리를 배우기보다 학습 지도(Map)의 특정 패턴을 암기하는 경우가 많다. 일부 복도 환경에서 학습한 정책은 비슷한 구조에서는 잘 동작하지만 새로운 시설의 통로 폭, 교차로, 경사, 문, 장애물 배치가 달라지면 쉽게 실패할 수 있다. 시각적, 의미적 변화도 성능을 저하시킨다. 새로운 선반, 표지판, 반사 물체, 공사 구역, 팔레트(Pallet), 카트(Cart), 임시 장애물은 모두 학습 분포 밖의 상태를 만든다. 야외 AMR은 훨씬 더 다양한 환경을 경험한다.

비, 눈, 안개, 낙엽, 진흙, 자갈, 그림자, 강한 햇빛, 온도 변화가 인식과 주행 성능에 영향을 준다. 도메인 랜덤화(Domain Randomization)는 다양한 환경을 학습하게 하지만 적절한 변화 범위를 결정하기가 어렵다. 변화가 너무 적으면 정책이 약해지고, 너무 많으면 학습 속도가 느려지고 지나치게 보수적인 정책이 만들어질 수 있다. 극단적인 환경까지 모두 견디도록 학습한 정책은 정상 환경에서도 효율성이 낮아질 수 있다. 결국 강인성(Robustness)과 성능 사이에는 항상 절충 관계가 존재한다. 분포 변화(Distribution Shift)는 배포 이후에도 계속 발생한다. 시설 구조가 바뀌고, 타이어가 마모되고, 적재물이 변하며, 센서가 노화되고, 사람들의 이동 패턴도 달라진다.

초기에는 잘 동작하던 정책도 시간이 지나면 성능이 저하될 수 있다. 이러한 성능 저하는 발견하기 어렵다. 전체 성공률은 높게 유지되더라도 드물게 발생하는 위험 상황은 점차 증가할 수 있기 때문이다. 강화 학습 정책은 해석 가능성(Explainability)이 낮다는 문제도 가진다. 심층 신경망은 수백만 개의 파라미터를 가지며 사람이 이해할 수 있는 형태로 의사결정을 설명하기 어렵다. AMR이 갑자기 방향을 바꾸거나 넓은 공간에서 멈추더라도 어떤 센서 특징이나 내부 표현이 그러한 행동을 만들었는지 분석하기 어렵다. 가치 함수(Value Function), 어텐션 맵(Attention Map), 궤적 분석(Trajectory Analysis)은 일부 정보를 제공하지만 정책 전체를 완전히 설명하지는 못한다.

설명 가능성 부족은 사고 분석, 고객 신뢰, 인증(Certification), 유지보수를 어렵게 만든다. 산업 현장에서는 검증 가능한 결정론적 규칙(Deterministic Rule)이 여전히 선호된다. 검증(Validation)도 매우 어려운 문제이다. 기존 내비게이션 알고리즘은 명확한 요구사항과 기하학적 제약을 기반으로 시험할 수 있지만 학습된 정책은 작은 입력 변화에도 다른 행동을 생성할 수 있다. 실제 AMR의 상태 공간(State Space)은 매우 크다. 지도, 속도, 적재물, 장애물, 센서 고장, 사람 행동, 통신 지연, 배터리 상태를 모두 고려해야 하기 때문이다. 이 모든 조합을 시험하는 것은 현실적으로 불가능하다. 제한된 시험만으로는 미래의 모든 상황에서 정책이 안전하다고 증명할 수 없다.

평균 성공률이 매우 높더라도 드물게 발생하는 심각한 실패는 실제 수백 대의 로봇을 장기간 운용할 경우 큰 문제가 될 수 있다. 희귀 사건(Rare Event)을 평가하려면 매우 많은 시험이 필요하다. 시뮬레이션에서도 이러한 시나리오를 생성하고 분석하는 데 상당한 비용이 든다. 통계적 신뢰성도 확보하기 어렵다. 작은 시험에서 충돌이 한 번도 발생하지 않았다고 해서 실제 충돌 확률이 충분히 낮다고 증명되는 것은 아니다. 적대적 시험(Adversarial Testing)은 실패를 찾는 데 도움이 되지만 현실적인 시나리오를 사용해야 한다. 비현실적인 조건은 실용성이 낮고, 너무 약한 시험은 중요한 문제를 발견하지 못한다. 안전 인증(Safety Certification)도 어려운 과제이다.

대부분의 안전 표준은 결정론적 시스템과 물리적 보호 장치를 기준으로 설계되었다. 심층 강화 학습 정책은 내부 파라미터와 실제 안전 요구사항 사이의 직접적인 대응 관계를 제공하지 않는다. 따라서 RL 정책은 인증된 안전 스캐너(Safety Scanner), 비상 정지(Emergency Stop), 안전 제어기(Safety Controller), 보호 영역(Protective Field), 기계적 제한(Mechanical Limit)을 대체할 수 없다. 독립적인 안전 계층(Independent Safety Layer)은 계속 유지되어야 한다. 그러나 이러한 계층은 RL 정책의 권한을 제한하여 실제 성능 향상 효과를 감소시킬 수도 있다.

안전 개입이 자주 발생한다면 정책은 실제 운용 제약을 제대로 학습하지 못한 것이다. 개입이 거의 없더라도 충분한 검증 근거가 필요하다. 런타임 모니터링(Runtime Monitoring)은 추가적인 계산과 시스템 복잡성을 만든다. 불확실성 추정, 분포 외 탐지, 안전 필터, 명령 검증, 백업 제어, 이벤트 로깅 등이 모두 필요할 수 있다. 이러한 추가 계층은 새로운 인터페이스, 새로운 고장 모드, 새로운 타이밍 요구사항, 추가 검증 작업을 만든다. 불확실성 추정 자체도 완벽하지 않다. 정책은 익숙하지 않은 상태에서도 높은 신뢰도를 보이거나, 반대로 안전한 상태를 위험하다고 판단할 수 있다.

앙상블 모델(Ensemble Model)과 베이지안 근사(Bayesian Approximation)는 계산 비용을 증가시키며, 모든 미지의 상황을 탐지할 수 있다는 보장을 제공하지 않는다. 백업 제어(Fallback Control)는 필수적이지만 RL과 기존 제어기 사이의 전환은 어렵다. 갑작스러운 전환은 명령 불연속, 진동, 응답 지연을 유발할 수 있다. 상태 기계(State Machine)나 혼합 제어(Blending Mechanism)는 이러한 문제를 줄일 수 있지만 시스템 설계와 시험 항목이 더욱 복잡해진다. 또한 백업 제어기 역시 지속적으로 유지관리해야 한다. 결국 RL을 사용해도 기존 내비게이션 스택(Classical Navigation Stack)을 완전히 제거할 수는 없다.

이러한 중복 구조는 소프트웨어 복잡성, 메모리 사용량, 유지보수 비용, 통합 비용을 증가시킨다. 실시간 계산(Real-Time Computation)도 중요한 제약이다. AMR은 센서 처리, 위치 추정, 경로 계획, 제어, 통신, 안전 기능을 엄격한 시간 안에 수행해야 한다. 대형 신경망 정책은 GPU나 고성능 엣지 컴퓨터(Edge Computer)를 필요로 한다. 이는 전력 소비, 발열, 무게, 비용, 시스템 통합 부담을 증가시킨다. 평균 추론 시간(Average Inference Time)은 충분하더라도 최악의 지연 시간(Worst-Case Latency)과 타이밍 지터(Timing Jitter)는 위험한 반응을 만들 수 있다.

장시간 운용 시 발열(Thermal Throttling)로 인해 추론 속도가 감소할 수 있으며, 인식, 지도 생성, 영상 스트리밍, 플릿 통신 등과 경쟁하면서 지연이 증가할 수도 있다. 네트워크 기반 추론(Network-Based Inference)은 통신 지연이나 연결 끊김 때문에 안전이 중요한 저수준 제어에는 적합하지 않다. 엣지 추론(Edge Inference)은 이러한 문제를 줄이지만 충분한 온보드(Onboard) 연산 자원이 필요하다. 결국 모델 크기와 실제 배포 비용 사이의 절충이 필요하다. 에너지 소비(Energy Consumption)도 고려해야 한다. 강력한 GPU를 장착한 AMR은 배터리 운용 시간이 줄어들 수 있다. RL이 절약한 에너지보다 GPU가 소비하는 에너지가 더 클 수도 있다.

모델 압축(Model Compression), 양자화(Quantization), 가지치기(Pruning)는 비용을 줄일 수 있지만 정책 행동을 변화시킬 수 있으므로 다시 전체 검증을 수행해야 한다. 학습 비용(Training Cost)도 매우 높다. 대규모 시뮬레이션, 병렬 학습, 하이퍼파라미터(Hyperparameter) 탐색, 반복 평가에는 많은 GPU와 CPU 자원이 필요하다. 강화 학습은 랜덤 시드(Random Seed), 학습률(Learning Rate), 보상 스케일, 신경망 구조, 환경 설정에 매우 민감하다. 거의 동일한 설정으로 두 번 학습해도 서로 다른 정책이 만들어질 수 있다. 이는 재현성(Reproducibility)을 떨어뜨리고 개발 일정을 예측하기 어렵게 만든다.

하이퍼파라미터 튜닝은 비용이 많이 든다. 하나의 파라미터 영향이 수많은 학습 에피소드 이후에야 나타나는 경우도 많기 때문이다. 정책은 초기에 잘 학습되다가 나중에 성능이 붕괴할 수도 있고, 높은 보상을 얻으면서도 실제 안전성은 낮을 수도 있다. 따라서 최종 모델을 선택하려면 매우 많은 독립 평가가 필요하다. 데이터 관리(Data Management)도 복잡하다. 팀은 시뮬레이터 버전, 지도 세트, 보상 함수, 정책 체크포인트, 랜덤화 범위, 평가 결과를 모두 관리해야 한다. 물리 엔진, 센서 모델, 충돌 모델, 시간 간격(Time Step)이 조금만 바뀌어도 정책 행동이 크게 달라질 수 있다. 엄격한 버전 관리가 없다면 실제 로봇에서 사용 중인 정책을 재현하거나 다른 버전과의 차이를 분석하기 어렵다.

정책 업데이트(Policy Update) 역시 위험을 만든다. 새로운 모델은 어떤 환경에서는 성능을 향상시키지만 다른 환경에서는 오히려 악화시킬 수 있다. 따라서 회귀 시험(Regression Testing)에는 과거 실패 사례, 경계 조건, 고객별 지도, 하드웨어 구성이 모두 포함되어야 한다. 점진적 배포(Gradual Rollout)와 롤백(Rollback) 기능도 필요하지만 배포 절차를 더욱 복잡하게 만든다. 온라인 지속 학습(Continual Online Learning)은 강화 학습의 장점으로 자주 소개되지만 산업용 AMR에서는 안전하게 적용하기 어렵다. 운용 중 정책이 계속 업데이트되면 검증이 끝난 정책과 실제 정책이 달라진다. 미래 행동은 더 이상 시험된 모델과 동일하지 않다.

또한 각 로봇이 서로 다른 경험을 학습하면 서로 다른 정책을 가지게 되어 재현성이 사라진다. 따라서 대부분의 실제 시스템은 온라인으로 데이터를 수집하지만 학습은 오프라인에서 수행한다. 이후 새로운 정책을 검증하고 승인 절차를 거쳐 배포한다. 이는 위험을 줄여주지만 완전한 자율적 지속 학습이라는 장점도 제한하게 된다. 오프라인 강화 학습(Offline Reinforcement Learning)은 적극적인 탐험을 피하지만 다른 문제를 만든다. 정책은 기록된 데이터셋의 품질과 다양성에 크게 의존한다. 기록된 AMR 데이터에는 정상 운용 사례는 많지만 충돌, 고장, 복구 사례는 매우 적다. 이러한 데이터셋으로 학습한 정책은 정상 상황에서는 잘 동작하지만 드문 상황에서는 쉽게 실패할 수 있다.

데이터에 없는 행동에 대해서는 가치 추정(Value Estimation)이 부정확해진다. 보수적인 방법은 이러한 문제를 줄이지만 기존 제어기보다 더 좋은 성능을 내기 어려워질 수도 있다. 다중 로봇(Multi-Robot) 환경은 추가적인 한계를 만든다. 한 로봇의 행동이 다른 로봇의 환경을 변화시키기 때문이다. 다른 로봇의 행동을 고정된 모델로 가정하고 학습한 정책은 플릿 규모(Fleet Size), 통신 구조, 작업 분포가 달라지면 성능이 크게 저하될 수 있다. 협력 보상(Cooperative Reward)은 기여도 할당(Credit Assignment)을 어렵게 만든다. 어느 로봇이 혼잡이나 교착 상태를 만들었는지 판단하기 어렵다.

중앙집중형 학습(Centralized Training)은 전체 정보를 사용하지만 실제 분산 실행에서는 이러한 정보를 사용할 수 없다. 통신 장애도 정책 성능을 떨어뜨릴 수 있다. 플릿 수준 정책은 상태 공간과 행동 공간을 크게 증가시키므로 학습과 검증 모두 훨씬 어려워진다. 전역 목표를 잘못 정의하면 일부 로봇만 계속 양보하거나 특정 로봇에게만 우선순위가 집중되는 불공정한 행동이 나타날 수도 있다. 공유 구역, 엘리베이터, 문, 충전기, 좁은 통로는 명시적인 협조 메커니즘이 필요하다. 기존 예약 기반 시스템이나 교통 제어 시스템은 여전히 명확한 보장을 제공한다. 강화 학습은 이러한 시스템을 개선할 수는 있지만 완전히 학습된 협조 정책은 설명과 인증이 어렵다. 유지보수 인력도 학습 정책을 분석하기 어렵다.

기존 AMR 엔지니어는 지도, 경로 계획기, 제어기, 안전 스캐너에는 익숙하지만 강화 학습은 신경망, 시뮬레이션, 보상 설계, 학습 파이프라인, 모델 모니터링까지 요구한다. 조직은 로봇공학, 머신러닝, 안전공학, 데이터 엔지니어링, DevOps 등 다양한 전문 인력을 유지해야 한다. 이는 인력 비용을 증가시키고 소수 전문가에게 지나치게 의존하게 만든다. 특정 벤더나 도구에 대한 의존성도 문제가 된다. 학습은 특정 시뮬레이터, 물리 엔진, GPU 플랫폼, 소프트웨어 프레임워크에 의존할 수 있다. 이러한 도구가 변경되면 정책을 다시 학습하거나 전체 시스템을 이전해야 할 수도 있다. 산업용 AMR은 수년 동안 운용되므로 장기 지원이 중요하다. 고객 수용성(Customer Acceptance)도 중요한 제약이다.

고객은 예측 가능한 행동, 명확한 서비스 절차, 측정 가능한 성능 보장을 기대한다. "경험을 통해 학습했다"는 설명만으로는 예상하지 못한 움직임이 발생했을 때 고객을 안심시키기 어렵다. 고객은 운용 한계, 고장 처리 방식, 책임 소재에 대한 명확한 설명을 요구한다. 사고 발생 시 RL 정책의 책임을 분석하는 것도 어렵다. 원인이 학습 데이터인지, 보상 설계인지, 센서 고장인지, 모델 드리프트인지, 소프트웨어 통합 문제인지, 안전 시스템인지 구분해야 한다. 이를 위해 상세한 로깅(Logging)이 필요하지만 고주파 센서 데이터와 정책 데이터를 저장하면 저장 공간, 개인정보 보호, 분석 비용이 증가한다.

카메라 데이터나 사람과의 상호작용 데이터를 학습과 사고 분석에 사용할 경우 개인정보 보호 문제도 발생할 수 있다. 사이버 보안(Cybersecurity)도 중요하다. 정책 파일, 학습 파이프라인, 보상 정의, 업데이트 시스템은 모두 공격 대상이 될 수 있다. 공격자가 정책이나 센서 데이터를 조작하면 기존 내비게이션 소프트웨어를 변경하지 않아도 위험한 행동을 만들 수 있다. 모델 무결성 검사(Model Integrity Check), 보안 부팅(Secure Boot), 전자서명 업데이트(Signed Update), 접근 제어(Access Control), 이상 탐지(Anomaly Monitoring)가 필요하다. 그러나 이러한 보호 기능도 시스템 복잡성을 더욱 증가시킨다.

또 다른 한계는 RL의 권한(Level of Authority)을 어디까지 줄 것인가이다. 고수준 의사결정은 제약하기 쉽지만 성능 향상도 제한적이다. 반대로 저수준 제어는 더 큰 적응성을 제공하지만 안전, 실시간성, 검증 부담이 훨씬 커진다. 따라서 대부분의 AMR에서는 RL의 역할을 제한하는 것이 현실적이다. 경로 선택(Route Selection), 속도 조정, 에너지 최적화, 작은 잔차 보정(Residual Correction) 정도가 적절하다. 반대로 모터를 직접 제어하거나 전체 내비게이션을 완전히 대체하는 것은 정당화하기 어렵다. 하이브리드 아키텍처(Hybrid Architecture)가 가장 현실적인 접근이다.

기존 경로 계획기가 전역 경로를 만들고, RL은 일부 지역 의사결정을 담당하며, 결정론적 제어기가 실제 움직임을 수행한다. 독립적인 안전 계층이 최종 명령을 항상 감시한다. 이러한 구조는 정책 실패의 영향을 제한할 수 있다. 그러나 하이브리드 시스템도 구성 요소 간 충돌, 진동, 기능 중복을 만들 수 있다. 구성 요소의 책임 범위와 업데이트 주기는 명확해야 한다. RL 정책은 교통 규칙, 임무 논리, 안전 영역, 저수준 제어와 충돌해서는 안 된다. 추가된 복잡성은 반드시 측정 가능한 가치를 제공해야 한다. RL이 이동 시간을 조금 줄이지만 검증과 유지보수 비용을 크게 증가시킨다면 상업적으로 적절하지 않을 수 있다.

기존 방법은 최고 성능은 낮더라도 더 높은 예측 가능성, 쉬운 인증, 빠른 배포를 제공할 수 있다. 따라서 강화 학습을 사용하는 결정은 기존 방법으로 해결하기 어려운 명확한 문제에서 시작되어야 한다. 복잡한 적응, 불확실한 상호작용, 장기적인 최적화와 같은 문제는 RL이 적합할 수 있다. 반대로 단순한 동역학, 고정된 규칙, 명확한 모델을 가진 문제는 기존 계획 및 제어 방식이 더 적합할 수 있다. 실제 AMR에서는 강화 학습을 단지 최신 기술이라는 이유만으로 적용해서는 안 된다. 좋은 엔지니어링 프로세스는 RL과 기존 방법을 안전성, 효율성, 비용, 유지보수성, 전체 생애주기(Lifecycle) 비용 측면에서 비교해야 한다.

기존 방법의 실제 튜닝 비용까지 포함하여 RL이 충분한 이점을 제공하는지를 검증해야 한다. RL을 사용하더라도 정책은 반드시 운용 설계 영역(Operational Design Domain, ODD) 안에서만 동작해야 한다. 이 영역에는 허용 지도, 적재물, 속도, 센서 상태, 날씨, 교통, 하드웨어 구성이 포함된다. 운용 설계 영역을 벗어나면 성능 저하 모드, 백업 제어, 안전 정지로 전환해야 한다. 정책은 자신의 검증 가정이 더 이상 성립하지 않는 환경에서도 무조건 자율성을 유지하려고 해서는 안 된다. 실제 환경은 계속 변하므로 장기 모니터링(Long-Term Monitoring)이 필요하다. 초기 성공이 미래의 신뢰성을 보장하지는 않는다.

안전 개입 빈도, 신뢰도, 충돌 경고, 에너지 소비, 이동 시간, 교착 상태 발생률, 사람의 불만 등을 지속적으로 모니터링해야 한다. 이러한 지표의 변화는 심각한 사고가 발생하기 전에 성능 저하를 미리 알려줄 수 있다. 실제 현장에서 발생한 실패와 근접 사고는 반드시 시뮬레이션에서 재현하여 회귀 시험에 추가해야 한다. 이를 통해 지속적인 개선 루프(Continuous Improvement Loop)를 만들 수 있지만, 모든 업데이트에는 다시 학습, 평가, 승인, 배포가 필요하다. 이 전체 생애주기 비용은 매우 클 수 있다. 따라서 AMR에서 강화 학습의 한계는 하나의 알고리즘이 부족하기 때문이 아니다. 학습, 로봇공학, 안전, 인프라, 사람, 사업 요구사항이 서로 복합적으로 작용하기 때문에 발생한다.

강화 학습은 역할이 명확히 제한되고, 성능 향상이 측정 가능하며, 기존 엔지니어링 안전 장치로 보호될 때 가장 큰 효과를 발휘한다. 가장 안전한 접근은 결정론적 임무 논리(Mission Logic), 검증된 내비게이션 구성 요소, 신뢰성 있는 저수준 제어기, 독립적인 안전 시스템을 그대로 유지하는 것이다. 강화 학습은 기존 방법이 어려운 일부 영역에서만 적응성을 제공하도록 사용하는 것이 바람직하다. 정책의 출력은 항상 모니터링되고, 제약되며, 언제든지 대체 가능해야 한다. 신뢰도, 센서 상태, 운용 조건이 허용 범위를 벗어나면 즉시 백업 제어기로 전환할 수 있어야 한다.

이러한 구조에서 RL은 단일 실패 지점(Single Point of Failure)이 아니라 기존 시스템을 보완하는 성능 향상 기술이 된다. 마지막 한계는 학습된 성능은 항상 조건부라는 점이다. 이는 학습 데이터 범위, 시뮬레이터 품질, 보상 정렬(Reward Alignment), 하드웨어 일관성, 운용 가정에 의존한다. 어떤 정책도 모든 환경과 모든 고장 상황에서 완전한 신뢰성을 보장할 수는 없다. 따라서 현실적인 AMR 전략은 강화 학습을 전체 자율 시스템의 하나의 구성 요소로 취급해야 한다. 형식적 요구사항(Formal Requirement), 결정론적 제어, 안전공학, 검증, 모니터링, 인간 거버넌스(Human Governance)와 함께 사용하는 것이 바람직하다.

이러한 한계를 초기에 이해하면 강화 학습을 선택적이고 책임감 있게 적용할 수 있다. 반대로 이러한 한계를 무시하면 시뮬레이션에서는 뛰어난 성능을 보이더라도 실제로는 취약하고 비용이 많이 들며 위험한 제품이 만들어질 수 있다. 실제 중요한 질문은 강화 학습이 AMR을 움직일 수 있는가가 아니다. 더 중요한 질문은 강화 학습이 추가되는 위험, 복잡성, 비용, 생애주기 부담을 정당화할 만큼 충분히 검증된 가치를 제공할 수 있는가이다.
