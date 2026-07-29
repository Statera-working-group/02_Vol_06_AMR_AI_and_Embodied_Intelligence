**Volume 06. AMR AI and Embodied Intelligence**


# Chapter 03. Deep Learning for Perception

##  

## 03.1 Deep Learning Fundamentals

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Deep learning is a branch of artificial intelligence that enables computers to learn complex representations directly from data using multi-layer artificial neural networks. Unlike traditional machine learning methods that depend heavily on manually designed features, deep learning automatically discovers hierarchical patterns through optimization. This ability has transformed numerous fields including computer vision, natural language processing, speech recognition, robotics, healthcare, autonomous driving, and scientific computing. In autonomous mobile robots, deep learning serves as the foundation for perception, decision making, navigation, manipulation, and increasingly for embodied intelligence.

The concept of deep learning originates from artificial neural networks inspired by the biological nervous system. Although artificial neurons are greatly simplified compared with biological neurons, they share the fundamental principle of receiving multiple inputs, combining information through weighted connections, and producing outputs after nonlinear activation. By connecting large numbers of these artificial neurons into multiple computational layers, neural networks become capable of approximating highly complex mathematical functions and discovering meaningful patterns hidden within high-dimensional data.

Artificial intelligence encompasses a broad range of computational methods that enable machines to perform tasks normally requiring human intelligence. Machine learning represents a subset of artificial intelligence in which algorithms improve through experience rather than explicit programming. Deep learning is a further specialization of machine learning that employs deep neural network architectures to automatically learn representations from large datasets. This hierarchical relationship explains why deep learning has become one of the dominant technologies driving recent advances in artificial intelligence.

The word "deep" refers to the presence of multiple hidden layers between network inputs and outputs. Early neural networks often contained only one or two hidden layers because limited computational resources and optimization methods made deeper networks difficult to train. Modern deep learning architectures may contain dozens, hundreds, or even thousands of layers, allowing increasingly abstract feature representations to emerge throughout the network hierarchy.

A neural network begins with an input layer that receives numerical representations of data. Images become arrays of pixel values, audio signals become sampled waveforms or spectrograms, sensor measurements become feature vectors, and language becomes numerical embeddings or token representations. The network processes these inputs through multiple hidden layers before producing predictions at the output layer. Every layer gradually transforms information into increasingly meaningful internal representations suitable for the target learning task.

The artificial neuron represents the fundamental computational unit of deep learning. Each neuron receives multiple input values, multiplies them by learnable weights, adds a bias term, and applies a nonlinear activation function. The resulting output becomes input to neurons in subsequent layers. Although mathematically simple, millions or even billions of interconnected neurons collectively learn highly sophisticated representations capable of solving remarkably complex problems.

Weights determine the strength of connections between neurons. During training, optimization algorithms continuously adjust these weights to minimize prediction errors. Initially, weights are typically assigned small random values because identical initialization would prevent neurons from learning distinct representations. Through repeated optimization, weights gradually encode meaningful relationships extracted from training data, effectively storing the learned knowledge of the neural network.

Bias parameters provide additional flexibility by shifting activation thresholds independently of weighted inputs. Without bias terms, neural networks would possess unnecessarily restricted representational capability because every decision boundary would be forced through the coordinate origin. Learnable biases enable neurons to activate under appropriate conditions regardless of input magnitude, improving model expressiveness across diverse learning tasks.

Activation functions introduce nonlinearity into neural networks. Without nonlinear activation, multiple stacked layers would mathematically collapse into a single linear transformation regardless of network depth. Nonlinear functions enable deep networks to approximate arbitrarily complex relationships among inputs and outputs. Consequently, activation functions constitute one of the most important components enabling modern deep learning.

Sigmoid activation historically played a central role in early neural networks because its output resembles a probability between zero and one. However, sigmoid functions suffer from gradient saturation when neuron outputs approach their extreme values, slowing optimization within deep networks. Although sigmoid remains useful for binary classification outputs, hidden layers of modern architectures generally employ more computationally efficient activation functions.

Hyperbolic tangent activation extends sigmoid by producing outputs ranging from negative one to positive one. Zero-centered outputs improve optimization compared with sigmoid under many circumstances. Nevertheless, hyperbolic tangent still experiences gradient saturation during deep optimization, limiting its effectiveness within extremely deep neural networks despite remaining useful for selected recurrent architectures and specialized applications.

Rectified Linear Units revolutionized deep learning by providing simple yet highly effective activation behavior. Rather than saturating for positive inputs, Rectified Linear Units produce outputs equal to the input whenever positive while returning zero otherwise. This behavior significantly reduces gradient vanishing, accelerates optimization, and enables efficient training of substantially deeper neural networks than previously possible.

Numerous Rectified Linear Unit variants have subsequently been developed. Leaky Rectified Linear Units preserve small gradients for negative inputs, reducing inactive neuron problems. Parametric Rectified Linear Units learn negative slopes during optimization. Exponential Linear Units and Gaussian Error Linear Units introduce smoother nonlinear behavior that often improves convergence and predictive performance within modern transformer architectures.

Forward propagation describes the process of computing predictions from input data using current network parameters. Information flows sequentially through every layer, where weighted combinations and nonlinear activations transform representations until final outputs are produced. During inference, only forward propagation is required because network parameters remain fixed. Efficient forward computation therefore directly determines real-time performance within deployed robotic systems.

Learning occurs by comparing predicted outputs against known target values using objective functions known as loss functions. Loss functions quantify prediction errors numerically, providing optimization algorithms with measurable objectives. Smaller losses indicate better agreement between predictions and ground truth. Selecting appropriate loss functions depends upon the learning task, including classification, regression, segmentation, object detection, reinforcement learning, or generative modeling.

Mean Squared Error remains one of the most common loss functions for regression tasks. Prediction errors are squared before averaging, emphasizing larger deviations more strongly than smaller ones. Mean Squared Error encourages accurate numerical estimation but may become sensitive to outliers because large errors contribute disproportionately to overall optimization objectives.

Cross-entropy loss dominates modern classification problems because it directly measures disagreement between predicted probability distributions and target class labels. Lower cross-entropy indicates greater confidence assigned to correct categories. Binary cross-entropy addresses two-class classification, while categorical cross-entropy generalizes naturally to multi-class recognition tasks including object recognition, semantic segmentation, and language modeling.

Optimization requires computing how every network parameter influences prediction errors. Backpropagation efficiently calculates these gradients using the chain rule of differential calculus. Rather than independently differentiating each parameter, gradients propagate backward from output layers toward inputs while reusing intermediate computations. This remarkable algorithm makes large-scale neural network training computationally practical despite millions or billions of adjustable parameters.

Gradient descent represents the fundamental optimization strategy underlying nearly all deep learning. Gradients indicate directions of steepest error increase, allowing optimization to move parameters in opposite directions where prediction errors decrease. Repeated parameter updates gradually minimize loss functions until networks converge toward effective solutions capable of generalizing beyond training examples.

Batch Gradient Descent computes gradients using entire training datasets before every parameter update. Although mathematically stable, processing complete datasets becomes computationally expensive for modern large-scale learning problems. Consequently, deep learning rarely employs full-batch optimization except for relatively small datasets or specialized scientific applications requiring highly accurate gradient estimates.

Stochastic Gradient Descent instead updates parameters after processing individual training examples. Frequent updates introduce optimization noise but significantly reduce memory requirements while enabling continuous learning from streaming data. Mini-batch optimization balances these advantages by computing gradients using small subsets of training data, typically containing several dozen or several hundred examples per optimization step.

Modern optimization algorithms extend Stochastic Gradient Descent through adaptive parameter adjustment. Momentum accelerates optimization by accumulating previous gradient directions, reducing oscillation across steep objective landscapes. RMSProp adaptively scales learning rates according to recent gradient magnitudes. Adam combines momentum with adaptive learning rates, becoming one of the most widely adopted optimization algorithms across contemporary deep learning applications.

Learning rate determines the magnitude of parameter updates during optimization. Excessively large learning rates may cause divergence by overshooting optimal solutions, while excessively small learning rates significantly slow convergence. Selecting appropriate learning rates therefore critically influences optimization success. Learning rate scheduling gradually reduces update magnitude throughout training, enabling rapid initial progress followed by stable convergence toward accurate solutions.

Training data play an equally important role as network architecture. Large, diverse, accurately labeled datasets expose neural networks to broad variations encountered during deployment. Insufficient diversity encourages memorization rather than genuine learning, reducing generalization to previously unseen environments. Consequently, dataset quality often determines practical performance more strongly than modest architectural improvements.

Generalization refers to a network\'s ability to perform accurately on previously unseen examples rather than merely memorizing training data. Successful deep learning discovers underlying patterns applicable across new situations instead of reproducing specific training samples. Autonomous robots particularly require strong generalization because deployment environments inevitably differ from training conditions.

Overfitting occurs when neural networks memorize training examples instead of learning generalizable relationships. Training accuracy becomes extremely high while validation performance stagnates or decreases. Complex architectures, limited datasets, excessive optimization, and insufficient regularization frequently contribute to overfitting. Detecting and preventing overfitting represents one of the central challenges in practical deep learning.

Underfitting represents the opposite situation in which networks remain too simple or insufficiently trained to capture meaningful data patterns. Both training and validation accuracy remain low because model capacity cannot adequately represent task complexity. Increasing architectural capacity, extending training duration, or improving optimization often alleviates underfitting.

Regularization techniques improve generalization by discouraging overly specialized solutions. Weight decay penalizes excessively large parameters, encouraging smoother decision boundaries. Dropout randomly disables subsets of neurons during training, forcing networks to develop redundant distributed representations rather than depending excessively upon individual computational pathways. Batch normalization further stabilizes optimization while providing modest regularization benefits.

Data augmentation artificially expands training datasets through realistic transformations preserving semantic meaning. Image augmentation commonly includes rotation, translation, scaling, flipping, brightness adjustment, color variation, Gaussian noise, blur, cropping, weather simulation, and occlusion synthesis. Exposure to diverse appearances significantly improves robustness against real-world environmental variation encountered during robotic deployment.

Transfer learning dramatically reduces data requirements by initializing neural networks using knowledge previously acquired from large datasets. Rather than training entirely from random initialization, pretrained models provide rich feature representations transferable across related tasks. Fine-tuning adapts these representations toward specialized robotic applications while requiring substantially fewer labeled examples than training from scratch.

Modern deep learning encompasses numerous specialized architectures beyond conventional feedforward networks. Convolutional Neural Networks excel at image understanding through spatial feature extraction. Recurrent Neural Networks process sequential information. Long Short-Term Memory networks improve long-range temporal modeling. Transformers employ self-attention to capture global relationships. Graph Neural Networks operate on relational structures, while diffusion and autoregressive models generate realistic synthetic content.

Deep learning has fundamentally transformed robotic perception. Camera images, depth measurements, point clouds, inertial observations, force sensors, audio signals, and language instructions can all be processed within unified neural architectures. Robots increasingly combine multimodal information to recognize objects, estimate depth, localize themselves, understand human commands, predict environmental changes, and coordinate complex behaviors across diverse operational environments.

The future of deep learning extends beyond isolated prediction tasks toward integrated intelligent systems capable of continual learning, multimodal reasoning, world modeling, embodied interaction, uncertainty estimation, and autonomous adaptation. Foundation models trained across enormous datasets increasingly provide reusable representations applicable to numerous downstream robotic tasks. Combined with edge computing, efficient optimization, and continual learning, these advances are enabling autonomous mobile robots to perceive, understand, and interact with the physical world with unprecedented capability, flexibility, and reliability.

딥러닝(Deep Learning)은 다층 인공신경망(Multi-Layer Artificial Neural Network)을 이용하여 데이터로부터 복잡한 표현(Representation)을 직접 학습하는 인공지능(AI, Artificial Intelligence)의 한 분야이다. 사람이 직접 특징을 설계해야 하는 전통적인 머신러닝(Machine Learning)과 달리, 딥러닝은 최적화(Optimization)를 통해 계층적인 패턴(Hierarchical Pattern)을 자동으로 학습한다. 이러한 능력은 컴퓨터 비전(Computer Vision), 자연어 처리(NLP, Natural Language Processing), 음성 인식(Speech Recognition), 로보틱스(Robotics), 의료(Healthcare), 자율주행(Autonomous Driving), 과학 계산(Scientific Computing) 등 다양한 분야를 혁신하였다. 자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서는 딥러닝이 인식(Perception), 의사결정(Decision Making), 자율주행(Navigation), 물체 조작(Manipulation), 그리고 체화형 인공지능(Embodied Intelligence)의 핵심 기반 기술이 된다.

딥러닝의 개념은 생물학적 신경계(Biological Nervous System)에서 영감을 얻은 인공신경망(Artificial Neural Network)에서 시작되었다. 인공 뉴런(Artificial Neuron)은 실제 생물학적 뉴런보다 매우 단순하지만, 여러 입력을 받아 가중치(Weight)를 이용해 결합하고 비선형 활성화 함수(Activation Function)를 거쳐 출력을 생성한다는 기본 원리는 동일하다. 이러한 뉴런을 다수의 계층(Layer)으로 연결하면 매우 복잡한 수학적 함수를 근사할 수 있으며, 고차원 데이터에 숨겨진 의미 있는 패턴을 학습할 수 있다.

인공지능은 인간의 지능을 필요로 하는 작업을 수행할 수 있도록 하는 다양한 계산 기법을 포함하는 넓은 개념이다. 머신러닝은 명시적인 프로그래밍 대신 경험을 통해 성능을 향상시키는 인공지능의 한 분야이다. 딥러닝은 다시 머신러닝의 하위 분야로, 심층 신경망(Deep Neural Network)을 이용하여 대규모 데이터로부터 특징을 자동으로 학습한다. 이러한 계층적인 관계 때문에 최근 인공지능의 급격한 발전은 대부분 딥러닝 기술에 의해 이루어지고 있다.

\'딥(Deep)\'이라는 용어는 입력(Input)과 출력(Output) 사이에 여러 개의 은닉층(Hidden Layer)이 존재한다는 의미이다. 초기 신경망은 계산 성능과 최적화 기법의 한계 때문에 한두 개의 은닉층만 사용할 수 있었다. 그러나 현대의 딥러닝 모델은 수십, 수백, 심지어 수천 개의 계층을 가지며, 이를 통해 점점 더 추상적인 특징을 학습할 수 있게 되었다.

신경망은 입력층(Input Layer)에서 수치 형태의 데이터를 입력받는다. 이미지는 픽셀(Pixel) 값의 배열로 표현되고, 음성은 파형(Waveform)이나 스펙트로그램(Spectrogram)으로 변환되며, 센서 데이터는 특징 벡터(Feature Vector), 언어는 토큰(Token)이나 임베딩(Embedding)으로 표현된다. 입력 데이터는 여러 개의 은닉층을 거쳐 처리된 후 출력층(Output Layer)에서 최종 예측 결과를 생성한다. 각 계층은 정보를 점점 더 의미 있는 형태로 변환하여 목표 작업을 수행할 수 있도록 한다.

인공 뉴런은 딥러닝의 가장 기본적인 계산 단위이다. 각 뉴런은 여러 입력값을 받아 학습 가능한 가중치를 곱하고 편향(Bias)을 더한 후 활성화 함수를 적용한다. 생성된 출력은 다음 계층의 입력으로 전달된다. 개별 뉴런은 매우 단순하지만 수백만 개에서 수십억 개의 뉴런이 연결되면 매우 복잡한 문제도 해결할 수 있는 강력한 표현 능력을 갖게 된다.

가중치(Weight)는 뉴런 간 연결의 중요도를 나타낸다. 학습 과정에서 최적화 알고리즘은 예측 오차를 줄이기 위해 가중치를 지속적으로 수정한다. 초기에는 모든 가중치를 작은 난수(Random Value)로 설정하는데, 동일한 값으로 초기화하면 모든 뉴런이 같은 역할만 수행하기 때문이다. 반복적인 학습을 통해 가중치는 데이터 속의 의미 있는 관계를 저장하게 되며, 이는 신경망이 학습한 지식(Knowledge)이 된다.

편향(Bias)은 가중치와 독립적으로 뉴런의 활성화 기준을 조절하는 역할을 한다. 편향이 없다면 모든 결정 경계(Decision Boundary)는 원점을 반드시 지나야 하므로 표현 능력이 제한된다. 편향을 함께 학습하면 입력의 크기와 관계없이 적절한 조건에서 뉴런이 활성화될 수 있어 모델의 표현력이 향상된다.

활성화 함수(Activation Function)는 신경망에 비선형성(Nonlinearity)을 부여하는 핵심 요소이다. 활성화 함수가 없다면 여러 계층을 쌓더라도 전체 네트워크는 하나의 선형 변환과 동일해져 복잡한 문제를 해결할 수 없다. 비선형 활성화 함수 덕분에 딥러닝은 매우 복잡한 입력과 출력 사이의 관계를 근사할 수 있다.

시그모이드(Sigmoid) 함수는 초기 신경망에서 가장 널리 사용된 활성화 함수이다. 출력이 0과 1 사이의 확률처럼 표현되기 때문에 이해하기 쉽다. 그러나 출력이 극단적인 값에 가까워질수록 기울기(Gradient)가 거의 사라지는 기울기 소실(Vanishing Gradient) 문제가 발생한다. 따라서 현재는 주로 이진 분류(Binary Classification)의 출력층에서만 사용되며, 은닉층에서는 거의 사용되지 않는다.

하이퍼볼릭 탄젠트(Hyperbolic Tangent, Tanh)는 출력 범위를 -1에서 1까지 확장한 활성화 함수이다. 출력이 0을 중심으로 분포하기 때문에 시그모이드보다 학습이 안정적인 경우가 많다. 그러나 깊은 신경망에서는 여전히 기울기 소실 문제가 발생하기 때문에 최근에는 제한적으로 사용된다.

ReLU(Rectified Linear Unit)는 현대 딥러닝을 크게 발전시킨 활성화 함수이다. 입력이 양수이면 그대로 출력하고 음수이면 0을 출력하는 매우 단순한 구조를 가진다. 양수 영역에서는 기울기가 유지되므로 기울기 소실 문제가 크게 줄어들며, 매우 깊은 신경망도 효율적으로 학습할 수 있게 되었다.

ReLU 이후에는 다양한 변형 함수가 개발되었다. Leaky ReLU는 음수 영역에서도 작은 기울기를 유지하여 죽은 뉴런(Dying Neuron) 문제를 줄인다. PReLU(Parametric ReLU)는 음수 기울기를 학습하며, ELU(Exponential Linear Unit)와 GELU(Gaussian Error Linear Unit)는 더욱 부드러운 비선형성을 제공하여 최신 트랜스포머 모델에서 널리 사용된다.

순전파(Forward Propagation)는 현재의 네트워크 파라미터(Parameter)를 이용하여 입력으로부터 출력을 계산하는 과정이다. 입력 데이터는 각 계층을 순차적으로 통과하면서 가중치와 활성화 함수를 거쳐 점점 더 추상적인 표현으로 변환된다. 실제 추론(Inference) 단계에서는 순전파만 수행되므로, 순전파의 계산 속도는 실시간 로봇 시스템의 성능을 결정하는 중요한 요소이다.

학습은 예측 결과와 실제 정답(Ground Truth)을 비교하는 손실 함수(Loss Function)를 통해 이루어진다. 손실 함수는 예측 오차를 하나의 수치로 표현하여 최적화 알고리즘이 최소화해야 할 목표를 제공한다. 손실 값이 작을수록 예측이 실제 정답에 가깝다는 의미이다. 분류(Classification), 회귀(Regression), 의미론적 분할(Semantic Segmentation), 객체 검출(Object Detection), 강화학습(Reinforcement Learning), 생성 모델(Generative Model) 등 작업의 종류에 따라 적절한 손실 함수가 선택된다.

평균제곱오차(MSE, Mean Squared Error)는 회귀 문제에서 가장 널리 사용되는 손실 함수이다. 예측 오차를 제곱한 후 평균을 계산하므로 큰 오차에 더 큰 패널티를 부여한다. 수치 예측에서는 매우 효과적이지만 이상치(Outlier)에 민감하다는 단점도 가지고 있다.

교차 엔트로피(Cross Entropy)는 현대 분류 문제에서 가장 널리 사용되는 손실 함수이다. 예측한 확률 분포와 실제 정답 분포의 차이를 계산하며, 올바른 클래스에 높은 확률을 부여할수록 손실 값이 작아진다. 이진 분류에는 Binary Cross Entropy가 사용되고, 다중 클래스 분류에는 Categorical Cross Entropy가 사용된다. 객체 인식, 의미론적 분할, 언어 모델(Language Model) 등 다양한 분야에서 핵심적인 역할을 한다.

최적화를 위해서는 각 파라미터가 손실 함수에 얼마나 영향을 주는지를 계산해야 한다. 역전파(Backpropagation)는 미분의 연쇄 법칙(Chain Rule)을 이용하여 이러한 기울기를 효율적으로 계산하는 알고리즘이다. 모든 파라미터를 개별적으로 계산하는 대신 중간 계산 결과를 재사용하기 때문에 수백만 개 이상의 파라미터를 가진 신경망도 현실적인 시간 안에 학습할 수 있다.

경사하강법(Gradient Descent)은 거의 모든 딥러닝 학습의 기본이 되는 최적화 방법이다. 기울기는 손실이 가장 빠르게 증가하는 방향을 나타내므로, 그 반대 방향으로 가중치를 이동시키면 손실이 감소한다. 이러한 과정을 반복하면 신경망은 점차 더 좋은 해를 찾게 된다.

배치 경사하강법(Batch Gradient Descent)은 전체 학습 데이터를 모두 사용하여 한 번의 기울기를 계산한 후 가중치를 갱신한다. 수학적으로는 안정적이지만 대규모 데이터셋에서는 계산량이 매우 크다. 따라서 현대 딥러닝에서는 작은 데이터셋이나 특수한 연구 목적이 아니라면 거의 사용되지 않는다.

확률적 경사하강법(SGD, Stochastic Gradient Descent)은 하나의 학습 샘플마다 가중치를 갱신한다. 계산량은 적지만 기울기에 많은 잡음이 포함된다. 현대 딥러닝은 일반적으로 수십\~수백 개의 샘플을 이용하는 미니배치(Mini-Batch) 학습을 사용하여 계산 효율성과 학습 안정성의 균형을 맞춘다.

현대의 최적화 알고리즘은 SGD를 더욱 발전시킨 형태이다. 모멘텀(Momentum)은 이전 기울기의 방향을 누적하여 진동을 줄이고 학습 속도를 높인다. RMSProp은 최근 기울기의 크기에 따라 학습률(Learning Rate)을 자동으로 조절한다. Adam(Adaptive Moment Estimation)은 모멘텀과 적응형 학습률을 결합하여 현재 가장 널리 사용되는 최적화 알고리즘 가운데 하나가 되었다.

학습률(Learning Rate)은 한 번의 업데이트에서 가중치를 얼마나 크게 수정할지를 결정한다. 학습률이 너무 크면 최적점을 지나쳐 학습이 발산(Divergence)할 수 있고, 너무 작으면 학습 속도가 매우 느려진다. 따라서 적절한 학습률 선택은 매우 중요하다. 학습률 스케줄링(Learning Rate Scheduling)은 학습 초기에 빠르게 학습하고 후반에는 작은 학습률로 안정적으로 수렴하도록 도와준다.

학습 데이터(Training Data)는 네트워크 구조만큼이나 중요하다. 다양하고 정확하게 라벨링된 대규모 데이터셋은 실제 환경에서 발생하는 다양한 상황을 모델이 학습하도록 만든다. 데이터가 부족하거나 다양성이 낮으면 모델은 데이터를 암기(Memorization)하게 되고 일반화 성능이 크게 저하된다. 실제로는 모델 구조보다 데이터 품질이 성능에 더 큰 영향을 미치는 경우도 많다.

일반화(Generalization)는 학습 데이터가 아닌 새로운 데이터에서도 높은 성능을 유지하는 능력이다. 성공적인 딥러닝 모델은 특정 데이터를 암기하는 것이 아니라 새로운 환경에서도 적용 가능한 근본적인 패턴을 학습한다. 자율주행 이동로봇은 학습 환경과 실제 운용 환경이 다르기 때문에 뛰어난 일반화 능력이 필수적이다.

과적합(Overfitting)은 모델이 학습 데이터를 지나치게 암기하는 현상이다. 학습 데이터에서는 매우 높은 정확도를 보이지만 검증 데이터(Validation Data)에서는 성능이 떨어진다. 지나치게 복잡한 모델, 작은 데이터셋, 과도한 학습, 부족한 정규화가 주요 원인이다. 과적합을 방지하는 것은 실제 딥러닝에서 가장 중요한 과제 가운데 하나이다.

과소적합(Underfitting)은 반대로 모델이 너무 단순하거나 충분히 학습되지 않아 데이터의 패턴 자체를 학습하지 못하는 경우이다. 학습 데이터와 검증 데이터 모두에서 성능이 낮게 나타난다. 더 큰 모델을 사용하거나 학습 시간을 늘리거나 최적화 방법을 개선하면 이러한 문제를 해결할 수 있다.

정규화(Regularization)는 일반화 성능을 향상시키는 다양한 기법을 의미한다. 가중치 감쇠(Weight Decay)는 지나치게 큰 가중치를 억제하고, 드롭아웃(Dropout)은 학습 중 일부 뉴런을 무작위로 비활성화하여 특정 뉴런에 과도하게 의존하지 않도록 만든다. 배치 정규화(Batch Normalization)는 학습을 안정화하면서 동시에 일정 수준의 정규화 효과도 제공한다.

데이터 증강(Data Augmentation)은 실제 데이터를 다양한 방식으로 변형하여 학습 데이터를 인위적으로 늘리는 방법이다. 영상에서는 회전(Rotation), 이동(Translation), 확대·축소(Scaling), 좌우 반전(Flipping), 밝기 조정(Brightness Adjustment), 색상 변화(Color Variation), 가우시안 노이즈(Gaussian Noise), 블러(Blur), 자르기(Cropping), 날씨 시뮬레이션(Weather Simulation), 가림(Occlusion) 등을 적용한다. 이러한 다양한 변형은 실제 환경에서의 강인성을 크게 향상시킨다.

전이 학습(Transfer Learning)은 대규모 데이터셋으로 미리 학습된 모델을 새로운 작업에 활용하는 기법이다. 완전히 처음부터 학습하는 대신 사전학습 모델(Pretrained Model)의 풍부한 특징 표현을 이용하면 훨씬 적은 데이터만으로도 높은 성능을 얻을 수 있다. 미세 조정(Fine-Tuning)은 이러한 사전학습 모델을 특정 로봇 응용 분야에 맞게 다시 학습시키는 과정이다.

현대의 딥러닝은 단순한 순방향 신경망을 넘어 다양한 구조로 발전하였다. 합성곱 신경망(CNN, Convolutional Neural Network)은 영상 처리에 뛰어나며, 순환 신경망(RNN, Recurrent Neural Network)은 시계열 데이터를 처리한다. LSTM(Long Short-Term Memory)은 장기 의존성을 학습하고, 트랜스포머(Transformer)는 자기 주의(Self-Attention)를 이용하여 전역적인 관계를 학습한다. 그래프 신경망(GNN, Graph Neural Network)은 그래프 구조를 처리하며, 확산 모델(Diffusion Model)과 자기회귀 모델(Autoregressive Model)은 새로운 데이터를 생성하는 데 활용된다.

딥러닝은 로봇의 인식 기술을 근본적으로 변화시켰다. 카메라 영상, 깊이 데이터, 포인트 클라우드(Point Cloud), IMU, 힘 센서(Force Sensor), 오디오(Audio), 자연어 명령(Language Instruction)을 하나의 신경망 구조에서 함께 처리할 수 있다. 로봇은 이러한 멀티모달 정보(Multimodal Information)를 이용하여 객체를 인식하고, 깊이를 추정하며, 자신의 위치를 계산하고, 사람의 명령을 이해하며, 환경 변화를 예측하고, 복잡한 작업을 수행할 수 있게 되었다.

딥러닝의 미래는 단순한 예측 모델을 넘어 지속 학습(Continual Learning), 멀티모달 추론(Multimodal Reasoning), 월드 모델(World Model), 체화형 상호작용(Embodied Interaction), 불확실성 추정(Uncertainty Estimation), 자율 적응(Autonomous Adaptation)이 가능한 통합 지능 시스템으로 발전하고 있다. 초대규모 데이터셋으로 학습된 파운데이션 모델(Foundation Model)은 다양한 로봇 작업에 재사용 가능한 일반적인 표현을 제공하고 있으며, 엣지 컴퓨팅(Edge Computing), 효율적인 최적화, 지속 학습과 결합되어 자율주행 이동로봇이 실제 물리 세계를 더욱 정확하게 인식하고 이해하며 안전하게 상호작용할 수 있도록 하는 핵심 기반 기술로 자리 잡고 있다.

##  

## 03.2 CNN-Based Perception

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Convolutional Neural Network (CNN) based perception is one of the most influential technologies in modern computer vision and serves as the foundation of visual intelligence for autonomous mobile robots. A CNN enables machines to automatically learn hierarchical visual representations directly from raw image data without requiring manually engineered features. Unlike traditional computer vision algorithms that depend heavily on handcrafted edge detectors, texture descriptors, and geometric rules, CNNs optimize feature extraction through end-to-end learning. This capability has fundamentally transformed robotic perception by enabling reliable object recognition, semantic understanding, depth estimation, localization, inspection, and navigation across highly diverse operating environments.

The development of CNNs was motivated by the limitations of fully connected neural networks when processing images. A typical image contains hundreds of thousands or even millions of pixels. Connecting every pixel directly to every neuron produces an enormous number of parameters, resulting in excessive computational complexity and severe overfitting. CNNs overcome this problem by exploiting the spatial structure of images. Local receptive fields, weight sharing, and hierarchical feature extraction dramatically reduce the number of trainable parameters while preserving the ability to learn highly discriminative visual representations.

The biological inspiration for CNNs originates from studies of the mammalian visual cortex. Neuroscientists discovered that neurons in the visual cortex respond primarily to local visual patterns such as edges, orientations, textures, and shapes rather than processing entire visual scenes simultaneously. These local responses gradually combine to represent increasingly complex visual concepts throughout successive cortical regions. CNNs emulate this hierarchical organization by learning progressively more abstract visual representations from simple image structures to complete semantic objects.

An image presented to a CNN is represented as a multidimensional tensor containing numerical pixel values. Color images usually consist of red, green, and blue channels, while grayscale images contain only one intensity channel. Each pixel represents a numerical measurement rather than symbolic information. The neural network gradually transforms these low-level numerical values into increasingly meaningful internal representations capable of distinguishing objects, environments, and semantic categories relevant to robotic perception.

The convolution operation forms the mathematical core of every CNN. Instead of connecting every neuron to every input pixel, small learnable filters slide across the image while performing weighted summations within local neighborhoods. Each filter detects a particular visual pattern such as horizontal edges, vertical lines, corners, textures, or repeated structures. Because identical filter parameters are shared across all image locations, convolution achieves both computational efficiency and translation invariance while dramatically reducing model complexity.

Convolution kernels typically possess dimensions such as three by three, five by five, or seven by seven pixels. During training, these kernels automatically adapt to detect visual structures useful for the target task. Early layers generally learn simple geometric patterns including edges and gradients, while intermediate layers capture textures, contours, and object parts. Deeper layers gradually recognize complete objects, semantic regions, and complex environmental relationships without requiring explicit feature engineering.

Weight sharing represents one of the defining characteristics of convolutional neural networks. Unlike fully connected networks where every connection possesses an independent parameter, convolution reuses identical filter weights throughout the entire image. This dramatically reduces memory requirements while allowing the same visual pattern to be recognized regardless of its spatial location. Translation invariance becomes especially valuable for autonomous robots because objects rarely appear at fixed image positions during navigation.

Feature maps are generated after convolution filters process input images. Each feature map represents the response of one learned filter across every spatial location. Strong activations indicate regions where particular visual patterns have been detected. Multiple feature maps collectively describe numerous complementary image characteristics, allowing subsequent network layers to integrate simple structures into increasingly sophisticated visual representations.

Activation functions introduce nonlinear behavior following every convolution operation. Rectified Linear Units have become the standard activation function because they significantly improve optimization efficiency and reduce gradient vanishing. Nonlinear activation enables CNNs to represent highly complex visual relationships that cannot be modeled using linear transformations alone. Consequently, stacked convolutional layers become capable of learning remarkably sophisticated perception models suitable for real-world robotic applications.

Pooling layers reduce spatial resolution while preserving the most informative visual features. Max pooling selects the strongest activation within local neighborhoods, whereas average pooling computes local averages. Pooling decreases computational complexity, improves robustness against small image translations, and expands the effective receptive field of subsequent layers. However, excessive pooling may remove fine spatial details important for segmentation, localization, or precise robotic manipulation.

Hierarchical feature learning represents one of the greatest strengths of CNN-based perception. Initial layers primarily recognize edges, gradients, and simple textures. Intermediate layers combine these primitive features into contours, corners, repeated structures, and object components. Deep layers ultimately identify complete semantic concepts such as pedestrians, vehicles, machinery, shelves, doors, or navigation landmarks. This hierarchical organization emerges automatically during optimization without requiring manual feature design.

The receptive field describes the image region influencing a particular neuron within the network. Shallow neurons observe only small local neighborhoods, whereas deeper neurons gradually integrate information from much larger portions of the image. Large receptive fields enable recognition of complete objects and contextual relationships, while small receptive fields preserve precise local details. Effective CNN architectures carefully balance these complementary requirements according to application objectives.

Padding preserves spatial dimensions during convolution by extending image boundaries with additional values. Without padding, repeated convolutions continuously shrink feature maps, eventually eliminating useful spatial information. Zero padding remains the most common approach because it preserves output dimensions while introducing minimal computational overhead. Proper padding also improves boundary recognition for objects appearing near image edges.

Stride determines how far convolution filters move between successive evaluations. Smaller strides preserve higher spatial resolution while increasing computational cost. Larger strides reduce processing requirements by skipping image locations but potentially sacrifice fine visual detail. Appropriate stride selection balances computational efficiency against localization precision according to real-time robotic perception requirements.

Modern CNN architectures frequently employ batch normalization between convolution and activation layers. Batch normalization standardizes intermediate feature distributions, stabilizing optimization while allowing higher learning rates and faster convergence. It additionally provides modest regularization benefits, improving generalization across diverse environmental conditions encountered during robotic deployment.

Residual learning fundamentally changed deep CNN design by introducing shortcut connections that bypass intermediate layers. Instead of learning complete feature transformations directly, residual blocks learn incremental refinements relative to their inputs. This simple architectural innovation greatly alleviates gradient degradation, enabling successful optimization of extremely deep neural networks containing hundreds of convolutional layers.

Residual Networks demonstrated that increasing network depth does not necessarily degrade optimization when appropriate architectural design is employed. Deep residual architectures achieve substantially higher recognition accuracy than earlier CNN models while maintaining stable optimization. Residual learning has subsequently become a foundational design principle adopted across numerous computer vision architectures beyond image classification.

Dense connectivity further extends information flow by connecting each layer directly to all subsequent layers. Rather than transmitting information sequentially through adjacent layers alone, dense architectures encourage feature reuse while improving gradient propagation. These networks often achieve comparable recognition performance using fewer parameters because earlier learned representations remain directly accessible throughout the network hierarchy.

Efficient CNN architectures have become increasingly important for embedded robotic platforms possessing limited computational resources. MobileNet employs depthwise separable convolutions to dramatically reduce computational complexity. ShuffleNet improves information exchange between feature channels. EfficientNet systematically balances network depth, width, and image resolution. These lightweight models enable sophisticated visual perception on mobile robots operating under strict energy and latency constraints.

CNNs have achieved remarkable success in image classification, where the objective is assigning one semantic category to an entire image. Classification networks learn increasingly abstract visual representations capable of distinguishing thousands of object categories. Although classification alone provides limited spatial information, pretrained classification models frequently serve as feature extractors for more advanced robotic perception tasks.

Object detection extends image classification by simultaneously identifying object categories and spatial locations. CNN-based detectors estimate bounding boxes together with class probabilities for every detected object. Two-stage detectors emphasize accuracy through proposal generation followed by classification refinement, while single-stage detectors directly predict objects within one inference pass, providing substantially faster performance suitable for real-time robotic applications.

Semantic segmentation employs CNNs to assign semantic labels to every image pixel rather than recognizing only object locations. Encoder-decoder architectures progressively compress visual information before reconstructing dense pixel-level predictions. Skip connections preserve high-resolution spatial information while integrating deep semantic representations. Semantic segmentation enables robots to distinguish traversable terrain, obstacles, walls, roads, vegetation, and workspaces with remarkable precision.

Instance segmentation further extends semantic segmentation by distinguishing individual object instances belonging to identical semantic categories. Multiple people, vehicles, pallets, or machinery can therefore be identified separately despite sharing common class labels. Instance-level understanding significantly improves manipulation planning, inventory management, collision avoidance, and multi-object interaction within autonomous robotic systems.

CNNs also contribute significantly to monocular depth estimation by learning geometric relationships directly from large annotated datasets. Rather than relying exclusively upon stereo correspondence or active sensors, convolutional architectures infer approximate three-dimensional structure from perspective, shading, texture, occlusion, and semantic context. Learned depth estimation complements traditional geometric approaches while reducing sensor complexity.

Visual localization increasingly relies upon CNN-derived feature representations rather than handcrafted descriptors. Deep features remain substantially more robust against illumination changes, viewpoint variation, seasonal appearance differences, and environmental aging than traditional feature extractors. CNN-based localization therefore improves long-term autonomous navigation across complex industrial, urban, and outdoor environments.

Visual place recognition represents another important CNN application for autonomous robots. Instead of identifying individual objects, the objective becomes recognizing previously visited locations despite substantial environmental variation. Deep feature embeddings encode distinctive environmental signatures allowing robots to recognize familiar places even under different weather conditions, lighting, or seasonal appearance changes.

Transfer learning has become particularly valuable within CNN-based robotic perception. Large-scale image classification datasets enable networks to learn general visual representations transferable across numerous downstream applications. Fine-tuning pretrained CNNs for specialized industrial inspection, warehouse automation, agricultural robotics, medical imaging, or construction monitoring substantially reduces required training data while improving convergence speed.

Data augmentation plays a critical role in developing robust CNN perception systems. Rotation, scaling, cropping, flipping, brightness adjustment, color perturbation, blur, weather simulation, synthetic occlusion, and noise injection expose networks to diverse visual conditions expected during deployment. Proper augmentation significantly improves robustness against real-world environmental variation while reducing overfitting.

CNN performance depends heavily upon high-quality labeled datasets. Object detection requires bounding boxes, semantic segmentation requires pixel-level annotations, instance segmentation requires individual object masks, and depth estimation requires geometric supervision. Producing these annotations demands considerable human effort, motivating increasing interest in synthetic data generation, self-supervised learning, semi-supervised learning, and foundation models capable of learning from limited supervision.

Training CNNs requires substantial computational resources because millions of parameters must be optimized using enormous datasets. Graphics Processing Units accelerate convolution operations through massively parallel numerical computation. Mixed precision training, distributed optimization, gradient accumulation, and efficient memory management enable practical optimization of increasingly sophisticated CNN architectures for large-scale perception tasks.

Real-time inference presents different engineering challenges from training. Autonomous robots must execute CNN models continuously under strict latency constraints while operating with finite computational resources. Model pruning, quantization, knowledge distillation, TensorRT optimization, operator fusion, and hardware-specific acceleration reduce inference latency while preserving recognition accuracy suitable for safety-critical robotic applications.

CNN-based perception has transformed nearly every component of autonomous mobile robotics. Camera images become reliable sources of semantic understanding, enabling robots to recognize people, vehicles, infrastructure, navigation landmarks, inspection targets, and operational hazards. Integrated perception pipelines combine CNNs with depth estimation, object tracking, localization, mapping, sensor fusion, and planning to support increasingly capable autonomous behavior across complex real-world environments.

Despite their remarkable success, CNNs also possess important limitations. They often require large labeled datasets, substantial computational resources, and careful hyperparameter optimization. Generalization may decrease when deployment environments differ significantly from training data, and purely convolutional architectures sometimes struggle to capture long-range spatial relationships compared with attention-based models. These limitations have motivated the integration of CNNs with transformers, multimodal foundation models, and world models.

The future of CNN-based perception lies not in replacing convolution entirely but in combining its exceptional local feature extraction capabilities with complementary architectures capable of reasoning across larger spatial, temporal, and semantic contexts. Hybrid CNN-transformer networks, multimodal perception systems, continual learning, self-supervised representation learning, foundation vision models, and embodied world models are creating increasingly intelligent perception systems. Within autonomous mobile robots, CNNs will remain a fundamental computational building block that transforms raw visual observations into structured environmental understanding, enabling safer navigation, more accurate manipulation, robust inspection, and adaptive interaction with the dynamic physical world.

합성곱 신경망(CNN, Convolutional Neural Network) 기반 인식(CNN-Based Perception)은 현대 컴퓨터 비전(Computer Vision)에서 가장 영향력이 큰 기술 가운데 하나이며, 자율주행 이동로봇(AMR, Autonomous Mobile Robot)의 시각 지능(Visual Intelligence)을 구성하는 핵심 기반 기술이다. CNN은 사람이 직접 특징을 설계하지 않고도 원시 영상 데이터(Raw Image Data)로부터 계층적인 시각 표현(Hierarchical Visual Representation)을 자동으로 학습한다. 전통적인 컴퓨터 비전이 에지 검출기(Edge Detector), 질감 기술자(Texture Descriptor), 기하학적 규칙과 같은 수작업 특징에 크게 의존했던 것과 달리, CNN은 종단간 학습(End-to-End Learning)을 통해 특징 추출을 최적화한다. 이러한 능력은 다양한 환경에서 객체 인식(Object Recognition), 의미 이해(Semantic Understanding), 깊이 추정(Depth Estimation), 위치 추정(Localization), 자동 검사(Inspection), 자율주행(Navigation)을 가능하게 하며 로봇 인식을 근본적으로 변화시켰다.

CNN이 개발된 가장 큰 이유는 완전 연결 신경망(Fully Connected Neural Network)이 영상을 처리할 때 가지는 한계를 해결하기 위해서였다. 하나의 영상은 수십만 개에서 수백만 개의 픽셀을 포함하며, 모든 픽셀을 모든 뉴런과 연결하면 엄청난 수의 파라미터(Parameter)가 필요하다. 이는 계산량 증가와 과적합(Overfitting)을 초래한다. CNN은 영상의 공간적 구조(Spatial Structure)를 적극 활용하여 이러한 문제를 해결한다. 국소 수용 영역(Local Receptive Field), 가중치 공유(Weight Sharing), 계층적 특징 추출(Hierarchical Feature Extraction)을 이용하여 파라미터 수를 크게 줄이면서도 매우 뛰어난 표현 능력을 유지한다.

CNN의 생물학적 영감은 포유류의 시각 피질(Visual Cortex)에 대한 연구에서 비롯되었다. 신경과학 연구에 따르면 시각 피질의 뉴런은 영상 전체를 동시에 처리하는 것이 아니라 에지, 방향, 질감, 형태와 같은 국소적인 시각 패턴에 먼저 반응한다. 이러한 단순한 특징들은 점차 결합되어 복잡한 객체와 장면을 표현하게 된다. CNN 역시 간단한 특징에서 복잡한 의미 정보를 점진적으로 학습하는 계층적 구조를 모방하고 있다.

CNN에 입력되는 영상은 숫자로 구성된 다차원 텐서(Multidimensional Tensor) 형태로 표현된다. 컬러 영상은 일반적으로 빨강(Red), 초록(Green), 파랑(Blue)의 세 개 채널(Channel)을 가지며, 흑백 영상은 하나의 밝기(Intensity) 채널만 포함한다. 각 픽셀은 단순한 숫자일 뿐이지만, 신경망은 이를 점차 의미 있는 특징 표현으로 변환하여 객체와 환경을 이해하게 된다.

합성곱(Convolution)은 CNN의 가장 핵심적인 연산이다. 모든 픽셀을 모든 뉴런과 연결하는 대신, 작은 학습 가능한 필터(Filter)가 영상을 이동하면서 국소 영역(Local Neighborhood)에 대해 가중합을 계산한다. 각각의 필터는 수평 에지, 수직선, 코너, 질감, 반복 패턴과 같은 특정한 시각 특징을 자동으로 학습한다. 동일한 필터를 영상 전체에 반복적으로 적용하기 때문에 계산량이 크게 감소하며, 물체 위치가 변해도 동일한 특징을 인식할 수 있는 이동 불변성(Translation Invariance)을 제공한다.

합성곱 커널(Convolution Kernel)은 일반적으로 3×3, 5×5, 7×7 크기를 가진다. 학습 과정에서 이러한 커널은 목표 작업에 필요한 시각 패턴을 자동으로 학습한다. 초기 계층에서는 에지와 밝기 변화(Gradient)를 학습하고, 중간 계층에서는 질감, 윤곽선, 객체의 부분을 학습하며, 깊은 계층에서는 완전한 객체와 의미 정보를 학습한다. 이 모든 과정은 사람이 직접 특징을 설계하지 않아도 자동으로 이루어진다.

가중치 공유(Weight Sharing)는 CNN을 다른 신경망과 구분하는 가장 중요한 특징 가운데 하나이다. 완전 연결 신경망에서는 모든 연결이 서로 다른 파라미터를 가지지만, CNN에서는 하나의 필터를 영상 전체에서 동일하게 사용한다. 이를 통해 메모리 사용량을 크게 줄일 수 있으며, 객체가 화면 어디에 나타나더라도 동일한 특징을 인식할 수 있다. 이러한 이동 불변성은 자율주행 로봇처럼 객체가 항상 다른 위치에 나타나는 환경에서 매우 중요한 장점이다.

특징 맵(Feature Map)은 합성곱 연산의 결과로 생성되는 출력이다. 하나의 특징 맵은 하나의 필터가 영상 전체에서 얼마나 강하게 반응했는지를 나타낸다. 높은 활성화(Activation)는 해당 위치에서 특정 특징이 존재함을 의미한다. 여러 개의 특징 맵은 서로 다른 시각 정보를 동시에 표현하며, 이후 계층에서는 이를 조합하여 더욱 복잡한 시각 표현을 학습한다.

활성화 함수(Activation Function)는 합성곱 연산 뒤에 적용되어 비선형성(Nonlinearity)을 추가한다. 현재는 ReLU(Rectified Linear Unit)가 가장 널리 사용된다. ReLU는 기울기 소실(Vanishing Gradient)을 줄이고 학습 속도를 크게 향상시킨다. 이러한 비선형성 덕분에 CNN은 매우 복잡한 시각 패턴도 효과적으로 학습할 수 있다.

풀링 계층(Pooling Layer)은 공간 해상도(Spatial Resolution)를 줄이면서 중요한 특징만 유지하는 역할을 한다. 최대 풀링(Max Pooling)은 지역 영역에서 가장 큰 값을 선택하며, 평균 풀링(Average Pooling)은 평균값을 계산한다. 풀링은 계산량을 줄이고 작은 위치 변화에 대한 강인성을 높이며 수용 영역(Receptive Field)을 확대한다. 그러나 지나친 풀링은 세밀한 공간 정보를 잃게 하므로 의미론적 분할(Semantic Segmentation)이나 정밀 조작에서는 신중하게 사용되어야 한다.

계층적 특징 학습(Hierarchical Feature Learning)은 CNN의 가장 큰 장점 가운데 하나이다. 초기 계층은 에지, 밝기 변화, 단순한 질감을 학습한다. 중간 계층은 윤곽선, 코너, 반복 패턴, 객체의 일부를 학습한다. 가장 깊은 계층은 사람(Person), 차량(Vehicle), 기계(Machine), 선반(Shelf), 문(Door), 랜드마크(Landmark)와 같은 완전한 의미 정보를 학습한다. 이러한 계층적 구조는 사람이 직접 설계하지 않아도 학습 과정에서 자연스럽게 형성된다.

수용 영역(Receptive Field)은 하나의 뉴런이 영향을 받는 영상의 범위를 의미한다. 얕은 계층에서는 매우 작은 영역만 관찰하지만, 깊은 계층에서는 영상의 넓은 영역을 동시에 고려할 수 있다. 큰 수용 영역은 객체 전체와 문맥(Context)을 이해하는 데 유리하며, 작은 수용 영역은 세밀한 공간 정보를 유지하는 데 유리하다. 효과적인 CNN은 이러한 두 가지 특성을 균형 있게 조합한다.

패딩(Padding)은 합성곱 연산 시 영상의 가장자리에 추가적인 값을 삽입하여 공간 크기를 유지하는 기법이다. 패딩이 없으면 합성곱을 반복할수록 영상 크기가 점점 줄어들어 중요한 공간 정보가 손실된다. 가장 널리 사용되는 제로 패딩(Zero Padding)은 출력 크기를 유지하면서 계산량 증가를 최소화한다. 또한 영상 가장자리의 객체도 보다 정확하게 인식할 수 있도록 도와준다.

스트라이드(Stride)는 필터가 한 번 이동할 때의 간격을 의미한다. 작은 스트라이드는 높은 해상도를 유지하지만 계산량이 증가한다. 큰 스트라이드는 계산량을 줄이는 대신 세부 정보를 잃을 수 있다. 따라서 스트라이드 선택은 계산 효율성과 위치 정확도 사이의 중요한 균형 요소이다.

현대 CNN은 합성곱과 활성화 함수 사이에 배치 정규화(Batch Normalization)를 자주 사용한다. 배치 정규화는 중간 특징의 분포를 일정하게 유지하여 학습을 안정화하고 더 높은 학습률(Learning Rate)을 사용할 수 있게 한다. 또한 일정 수준의 정규화(Regularization) 효과도 제공하여 일반화 성능을 향상시킨다.

잔차 학습(Residual Learning)은 매우 깊은 CNN을 가능하게 만든 중요한 구조이다. 잔차 블록(Residual Block)은 입력을 출력으로 직접 전달하는 지름길 연결(Shortcut Connection)을 추가한다. 신경망은 전체 변환을 학습하는 대신 입력에 대한 차이(Residual)만 학습하면 된다. 이 단순한 구조는 기울기 감소 문제를 크게 완화하여 수백 개 이상의 계층을 가진 매우 깊은 CNN도 안정적으로 학습할 수 있게 만들었다.

잔차 네트워크(ResNet, Residual Network)는 네트워크 깊이가 증가해도 안정적으로 학습할 수 있음을 보여주었다. 이전 세대 CNN보다 훨씬 깊은 구조에서도 더 높은 정확도를 달성하였으며, 이후 대부분의 컴퓨터 비전 모델에 큰 영향을 미쳤다. 현재의 다양한 CNN 구조 역시 잔차 연결을 기본 설계 요소로 채택하고 있다.

밀집 연결(Dense Connectivity)은 모든 계층을 이후 계층과 직접 연결하는 구조이다. 이전 계층에서 학습된 특징을 반복적으로 재사용할 수 있으며 기울기 전달도 더욱 원활해진다. 따라서 적은 파라미터만으로도 높은 성능을 달성할 수 있으며, 정보 손실도 크게 줄일 수 있다.

경량 CNN(Lightweight CNN)은 연산 자원이 제한된 임베디드 로봇을 위해 개발되었다. MobileNet은 깊이별 분리 합성곱(Depthwise Separable Convolution)을 이용하여 계산량을 크게 줄였고, ShuffleNet은 채널 간 정보 교환(Channel Shuffle)을 효율적으로 수행한다. EfficientNet은 네트워크 깊이, 너비, 입력 해상도를 균형 있게 확장하여 높은 성능과 효율성을 동시에 달성하였다. 이러한 모델들은 배터리와 연산 자원이 제한된 이동로봇에서 매우 중요한 역할을 한다.

CNN은 영상 분류(Image Classification) 분야에서 뛰어난 성과를 거두었다. 영상 전체를 하나의 의미론적 클래스(Semantic Class)로 분류하며 수천 개 이상의 객체를 구분할 수 있다. 비록 공간 정보는 제공하지 않지만, 사전학습(Pretraining)된 분류 모델은 다양한 로봇 인식 작업의 특징 추출기로 널리 활용된다.

객체 검출(Object Detection)은 CNN을 이용하여 객체의 종류뿐 아니라 위치까지 함께 추정한다. 경계 상자(Bounding Box)와 클래스 확률(Class Probability)을 동시에 예측한다. 2단계(Two-Stage) 검출기는 높은 정확도를 제공하며, 1단계(Single-Stage) 검출기는 매우 빠른 속도를 제공하여 실시간 로봇 시스템에서 널리 사용된다.

의미론적 분할(Semantic Segmentation)은 CNN을 이용하여 모든 픽셀을 의미론적 클래스로 분류한다. 인코더-디코더(Encoder-Decoder) 구조는 영상을 압축한 후 다시 복원하며, 스킵 연결(Skip Connection)은 공간 정보를 유지한다. 이를 통해 로봇은 주행 가능한 공간, 벽, 도로, 식생, 장애물을 매우 정밀하게 구분할 수 있다.

인스턴스 분할(Instance Segmentation)은 동일한 클래스에 속하는 객체도 각각 개별적으로 구분한다. 여러 사람, 여러 차량, 여러 팔레트를 각각 독립적으로 인식할 수 있다. 이러한 능력은 물체 조작, 물류 자동화, 충돌 회피, 다중 객체 관리에서 매우 중요하다.

CNN은 단안 깊이 추정(Monocular Depth Estimation)에도 널리 활용된다. 스테레오 비전이나 능동형 센서를 사용하지 않아도 원근(Perspective), 음영(Shading), 질감(Texture), 가림(Occlusion), 의미 정보(Semantic Context)를 학습하여 대략적인 3차원 구조를 추정할 수 있다. 이는 기존 기하학 기반 방법을 보완하면서 센서 구성을 단순화할 수 있다.

비전 기반 위치 추정(Visual Localization)은 기존의 수작업 특징보다 CNN이 학습한 특징 표현을 점점 더 많이 사용하고 있다. 딥러닝 특징은 조명 변화, 시점 변화, 계절 변화, 환경 노후화에도 더욱 강인하여 장기간 자율주행의 위치 추정 정확도를 크게 향상시킨다.

장소 인식(Visual Place Recognition)은 CNN의 또 다른 중요한 응용 분야이다. 개별 객체를 인식하는 것이 아니라 이전에 방문했던 장소를 다시 인식하는 것이 목표이다. 날씨와 조명이 크게 달라져도 딥러닝 특징은 장소의 고유한 특성을 안정적으로 표현할 수 있어 장기 자율주행에서 매우 중요한 역할을 한다.

전이 학습(Transfer Learning)은 CNN 기반 로봇 인식에서 매우 중요한 기술이다. 대규모 이미지 데이터셋으로 학습된 일반적인 특징을 새로운 작업에 그대로 활용할 수 있다. 산업 검사, 물류 자동화, 농업 로봇, 의료 영상, 건설 현장 모니터링과 같은 특수한 응용 분야에서도 적은 데이터만으로 높은 성능을 얻을 수 있다.

데이터 증강(Data Augmentation)은 CNN의 강인성을 높이는 핵심 기법이다. 회전(Rotation), 크기 변경(Scaling), 자르기(Cropping), 좌우 반전(Flipping), 밝기 조절(Brightness Adjustment), 색상 변화(Color Perturbation), 블러(Blur), 날씨 시뮬레이션(Weather Simulation), 가림(Occlusion), 노이즈 추가(Noise Injection)는 실제 환경에서 발생하는 다양한 상황을 학습하도록 도와준다.

CNN의 성능은 고품질 데이터셋에 크게 의존한다. 객체 검출은 경계 상자, 의미론적 분할은 픽셀 수준 라벨, 인스턴스 분할은 객체 마스크(Mask), 깊이 추정은 거리 정보가 필요하다. 이러한 데이터는 제작 비용이 매우 크기 때문에 최근에는 합성 데이터(Synthetic Data), 자기지도 학습(Self-Supervised Learning), 반지도 학습(Semi-Supervised Learning), 파운데이션 모델(Foundation Model)에 대한 연구가 활발히 진행되고 있다.

CNN 학습은 매우 큰 계산 자원을 요구한다. 수백만 개 이상의 파라미터를 대규모 데이터셋으로 반복적으로 최적화해야 하기 때문이다. GPU(Graphics Processing Unit)는 대규모 병렬 연산을 수행하여 합성곱 계산을 크게 가속한다. 혼합 정밀도 학습(Mixed Precision Training), 분산 학습(Distributed Training), 그래디언트 누적(Gradient Accumulation), 메모리 최적화는 대규모 CNN 학습을 가능하게 한다.

실시간 추론(Real-Time Inference)은 학습과는 다른 공학적 과제를 가진다. 자율주행 이동로봇은 제한된 계산 자원에서 CNN을 매우 짧은 시간 안에 반복 실행해야 한다. 모델 가지치기(Model Pruning), 양자화(Quantization), 지식 증류(Knowledge Distillation), TensorRT 최적화, 연산자 융합(Operator Fusion), 하드웨어 가속(Hardware Acceleration)은 추론 시간을 줄이면서도 정확도를 유지하는 핵심 기술이다.

CNN 기반 인식은 자율주행 이동로봇의 거의 모든 인식 기능을 변화시켰다. 카메라 영상은 사람, 차량, 시설, 랜드마크, 검사 대상, 위험 요소를 안정적으로 인식하는 의미 정보로 변환된다. 또한 깊이 추정, 객체 추적(Object Tracking), 위치 추정, 지도 작성(Mapping), 센서 융합(Sensor Fusion), 경로 계획(Path Planning)과 결합되어 더욱 지능적인 자율 행동을 가능하게 한다.

뛰어난 성능에도 불구하고 CNN은 몇 가지 한계를 가진다. 대규모 라벨링 데이터셋이 필요하며, 높은 계산 성능과 세밀한 하이퍼파라미터(Hyperparameter) 조정이 요구된다. 또한 학습 환경과 실제 환경이 크게 달라질 경우 일반화 성능이 저하될 수 있으며, 전역적인 공간 관계(Global Spatial Relationship)를 이해하는 능력은 주의 메커니즘(Attention Mechanism) 기반 모델보다 제한적일 수 있다. 이러한 이유로 최근에는 CNN과 트랜스포머(Transformer), 멀티모달 파운데이션 모델(Multimodal Foundation Model), 월드 모델(World Model)을 결합하는 연구가 활발히 진행되고 있다.

CNN 기반 인식의 미래는 합성곱을 대체하는 것이 아니라, 뛰어난 국소 특징 추출(Local Feature Extraction) 능력을 트랜스포머의 전역 추론(Global Reasoning), 멀티모달 인식(Multimodal Perception), 지속 학습(Continual Learning), 자기지도 표현 학습(Self-Supervised Representation Learning), 파운데이션 비전 모델(Foundation Vision Model), 체화형 월드 모델(Embodied World Model)과 결합하는 방향으로 발전하고 있다. 자율주행 이동로봇에서 CNN은 앞으로도 원시 영상을 구조화된 환경 정보로 변환하는 핵심 계산 모듈로 남아 안전한 자율주행, 정밀한 물체 조작, 신뢰성 높은 자동 검사, 그리고 변화하는 실제 환경과의 지능적인 상호작용을 가능하게 하는 가장 중요한 기반 기술 가운데 하나로 계속 활용될 것이다.

##  

## 03.3 Transformer-Based Perception

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Transformer-based perception is a modern approach to visual intelligence that uses attention mechanisms to model relationships across an entire image, video sequence, or multimodal sensor stream. Unlike conventional convolutional neural networks, which primarily process local neighborhoods, transformers directly learn interactions among distant visual regions. This capability enables autonomous mobile robots to understand global scene structure, object relationships, temporal context, and semantic meaning with greater flexibility.

The transformer architecture was originally developed for natural language processing, where self-attention allowed models to connect words regardless of their distance within a sentence. The same principle can be applied to visual perception by representing an image as a sequence of smaller regions. Each region becomes a token, and the network learns how every token relates to every other token. This transforms visual perception from local filtering into global relational reasoning.

In transformer-based vision, an input image is usually divided into fixed-size patches. Each patch contains a small rectangular region of pixels and is converted into a numerical vector through linear projection. These vectors are called patch embeddings. The resulting sequence resembles a sequence of language tokens, allowing the transformer to process visual information using the same general computational principles applied to text.

Patch size strongly influences model behavior. Smaller patches preserve fine spatial detail and improve recognition of small objects, boundaries, and textures, but they produce longer token sequences and increase computational cost. Larger patches reduce the number of tokens and accelerate inference, but important local information may be lost. Practical robotic systems therefore select patch size according to resolution, latency, and task requirements.

Because self-attention itself does not inherently know where image patches originated, positional information must be added to the patch embeddings. Positional encoding represents the spatial location of each token within the image. Without this information, the transformer would understand which visual patterns are present but not how they are arranged. Spatial position is essential for object localization, segmentation, depth estimation, and navigation.

A classification token is often appended to the patch sequence in vision transformer architectures. This special token gathers information from all image regions through repeated attention operations. After processing, its final representation can be used for image classification or other global prediction tasks. For dense robotic perception, however, individual patch tokens are often retained so that spatially detailed outputs can be reconstructed.

Self-attention is the central mechanism of transformer-based perception. Every token generates three learned representations called query, key, and value. The query represents what a token is searching for, the key represents what information a token contains, and the value stores the content to be aggregated. Similarity between queries and keys determines how strongly tokens influence one another.

Attention weights are calculated by comparing each query with all available keys. These weights are normalized and used to combine the corresponding values. As a result, one image region can directly gather information from any other region, even when they are far apart. A robot observing a person near a forklift can therefore relate the person, vehicle, floor markings, and safety barriers within a unified scene representation.

Multi-head attention extends self-attention by learning several relationship patterns simultaneously. One attention head may focus on object shape, another on spatial proximity, another on texture similarity, and another on semantic context. Combining these heads produces a richer representation than a single attention operation. Multi-head attention is particularly effective in cluttered environments where multiple relationships influence interpretation.

The transformer encoder repeatedly applies multi-head attention, normalization, residual connections, and feedforward neural networks. Each layer refines token representations by integrating increasingly complex contextual information. Shallow layers capture appearance and local structure, while deeper layers describe objects, scene layouts, interactions, and task-relevant meaning. Repetition allows global understanding to emerge progressively.

Residual connections are essential for training deep transformer networks. They allow information and gradients to bypass individual processing blocks, reducing optimization instability. Layer normalization further stabilizes feature distributions and improves convergence. Together, these components enable transformers to scale to large models containing hundreds of millions or billions of parameters.

Feedforward networks operate independently on each token after attention has exchanged information among tokens. These networks apply nonlinear transformations that refine each visual representation. Attention determines which information should be combined, while feedforward layers transform the combined information into more useful task-specific features. Both mechanisms are necessary for effective transformer perception.

Vision Transformers demonstrated that pure attention-based architectures could achieve highly competitive image classification performance. Instead of relying on convolution, they learned visual representations through patch tokenization and global attention. Their success showed that the inductive biases of convolution were helpful but not strictly necessary when sufficient training data and computational resources were available.

Convolutional neural networks assume that nearby pixels are strongly related and reuse the same filters across image locations. These assumptions improve efficiency and data utilization. Transformers use weaker assumptions and learn relationships more freely from data. This flexibility improves global reasoning, but it may require larger datasets and stronger regularization to achieve stable performance.

Hybrid CNN-transformer architectures combine local feature extraction with global attention. Convolutional layers efficiently identify edges, textures, and object parts, while transformer layers model long-range dependencies and semantic relationships. This combination is attractive for autonomous robots because it preserves efficient low-level perception while adding stronger contextual understanding.

Hierarchical vision transformers gradually reduce spatial resolution while increasing feature depth, similar to convolutional networks. Instead of processing one fixed token resolution throughout the model, they merge neighboring tokens at successive stages. This produces multi-scale representations suitable for object detection, semantic segmentation, depth estimation, and other dense prediction tasks.

Window-based attention limits self-attention to local image windows to reduce computational complexity. Global attention over all tokens becomes expensive as image resolution increases because the number of pairwise relationships grows rapidly. Window-based methods calculate attention within smaller regions and periodically shift or connect windows so that information can still propagate across the complete image.

Shifted-window transformers provide an efficient balance between local processing and global communication. Consecutive layers use different window boundaries, allowing tokens previously separated into different windows to interact. This design supports high-resolution perception while maintaining manageable computational cost, making it useful for embedded and real-time robotic applications.

Object detection has been significantly influenced by transformer architectures. Traditional detectors rely on anchors, region proposals, or dense candidate predictions followed by non-maximum suppression. Transformer-based detectors can instead treat object detection as a direct set prediction problem, where a fixed number of learned object queries search the image for relevant objects.

Detection Transformer architectures use object queries that interact with encoded visual tokens through cross-attention. Each query attempts to identify one object and predicts its category and bounding box. A matching algorithm associates predictions with ground-truth objects during training. This end-to-end structure reduces handcrafted components and demonstrates how attention can unify localization and classification.

Object queries can be interpreted as learnable search agents. During training, they develop specialized behaviors for locating meaningful visual entities. Some may focus on large objects, while others become effective at detecting small or partially occluded targets. Because all queries are processed together, the network can reason about multiple objects and reduce duplicate predictions.

Transformer-based semantic segmentation assigns classes to image regions while incorporating global scene context. A local image patch may appear ambiguous when examined alone, but its meaning becomes clearer when related to surrounding regions. A flat gray surface may represent a floor, wall, road, or machine depending on its spatial position and relationship to other objects.

Mask classification approaches treat segmentation as prediction of semantic masks rather than independent classification of every pixel. Learned queries represent objects or regions and generate corresponding mask embeddings. This enables semantic segmentation, instance segmentation, and panoptic segmentation to be handled within similar transformer-based frameworks.

Panoptic segmentation combines semantic understanding of background regions with instance-level separation of individual objects. Floors, walls, roads, and vegetation are labeled as broad semantic areas, while people, vehicles, pallets, or machines are represented as separate instances. Transformer-based models are well suited to this task because they naturally model both regions and object relationships.

Depth estimation also benefits from attention-based global reasoning. Monocular depth is inherently ambiguous because absolute distance cannot be directly measured from a single image. Transformers use long-range context to relate object size, perspective, horizon structure, surface continuity, and semantic identity. These relationships improve relative depth consistency across large scene regions.

Stereo matching can be enhanced using transformers that compare image features across left and right camera views. Attention establishes correspondences between distant candidate regions while considering global geometric context. This approach can improve depth estimation in low-texture areas, repeated patterns, and partially occluded regions where traditional local matching methods often fail.

Video perception extends transformer reasoning across time. Instead of processing every frame independently, video transformers represent spatial patches from multiple frames as spatiotemporal tokens. Attention then models object appearance, movement, interaction, and temporal continuity. This supports action recognition, motion forecasting, object tracking, and dynamic scene understanding.

Temporal attention allows current observations to reference earlier frames. A person briefly hidden behind a shelf can remain represented using information from previous observations. This persistent temporal context improves tracking under occlusion and reduces instability caused by temporary detection failures. For autonomous robots, such consistency is important in crowded and dynamic environments.

Multi-object tracking can be formulated using persistent track queries. Each query represents one tracked object and updates its internal state as new frames arrive. Attention associates track queries with current visual features, enabling the system to maintain identities, estimate trajectories, and recover objects after partial occlusion. This integrates detection and tracking more tightly than separate pipelines.

Transformers are particularly useful for multimodal perception. Camera images, depth maps, LiDAR point clouds, radar measurements, language instructions, and robot state information can all be represented as tokens. Attention enables these heterogeneous data sources to exchange information within a unified model. This supports richer scene understanding than isolated sensor processing.

Camera-LiDAR fusion benefits from attention because visual and geometric data possess different resolutions and coordinate structures. Cross-attention can associate image regions with corresponding 3D points or voxel features. Camera data contribute texture and semantic information, while LiDAR provides accurate distance and geometry. Their combination improves 3D detection and localization.

Bird\'s-eye-view perception transforms observations from multiple cameras into a unified top-down representation. Transformer-based methods use spatial queries to gather relevant image features from different camera views. The resulting bird\'s-eye-view map represents lanes, obstacles, vehicles, free space, and semantic regions within a common coordinate frame suitable for planning.

Multi-camera transformers learn relationships among overlapping and non-overlapping views. They can associate objects observed from different directions and reduce blind spots around the robot. Positional calibration information guides the attention process so that features from separate cameras are correctly projected and fused into a consistent environmental representation.

Language-guided perception is another major advantage of transformer architectures. Because transformers were originally developed for language, visual and textual tokens can be processed within compatible frameworks. A robot can search for an object described by natural language, such as a damaged box, yellow safety cone, open doorway, or person wearing protective equipment.

Open-vocabulary detection and segmentation extend perception beyond fixed training categories. Instead of recognizing only predefined labels, the model compares visual features with text embeddings describing arbitrary concepts. This enables robots to respond more flexibly to new tasks and human instructions without retraining a dedicated detector for every possible object.

Foundation vision models are typically based on large transformer architectures trained using massive and diverse datasets. They learn broadly reusable visual representations that can be adapted to classification, detection, segmentation, depth estimation, retrieval, and robotic control. Fine-tuning or prompt-based adaptation allows one pretrained model to support numerous downstream applications.

Self-supervised learning has become essential for training large transformer perception models. Rather than requiring complete human annotation, models learn by reconstructing masked image regions, predicting relationships between views, or matching different augmentations of the same scene. This reduces labeling cost and enables learning from large quantities of unstructured robotic sensor data.

Masked image modeling hides selected patches and trains the transformer to reconstruct or predict their content. To succeed, the model must understand object structure, surrounding context, and scene semantics. This learning process produces general-purpose representations that transfer effectively to multiple perception tasks after fine-tuning.

Contrastive learning trains representations by bringing related observations closer together while separating unrelated examples. Images of the same place under different lighting conditions may be treated as positive pairs, while unrelated scenes serve as negatives. Such training improves visual place recognition and long-term localization under environmental change.

Transformer models often require substantial computational resources. Full attention across high-resolution token sequences consumes large amounts of memory and processing time. This creates challenges for autonomous mobile robots operating with limited power, thermal capacity, and onboard compute. Efficient attention and model compression are therefore important deployment research areas.

Sparse attention reduces computation by connecting only selected token pairs rather than evaluating every possible relationship. Deformable attention samples a limited number of relevant locations around reference points. Linear attention approximates standard attention using more efficient mathematical formulations. These methods reduce latency while preserving much of the transformer's reasoning capability.

Token pruning removes visual tokens that contribute little to the current task. Background regions, static areas, or low-information patches can be discarded during inference, allowing the network to focus on important objects and navigation regions. Dynamic token selection is especially useful for real-time robotic perception because environmental complexity varies over time.

Knowledge distillation transfers capabilities from a large transformer model into a smaller student network. The student learns not only from ground-truth labels but also from the teacher's output distributions, attention patterns, or intermediate features. Distillation can preserve much of the original accuracy while reducing model size and computational demand.

Quantization reduces numerical precision of model weights and activations. Converting floating-point computation into lower-precision formats such as INT8 decreases memory use and accelerates inference on compatible hardware. Attention operations require careful calibration because numerical errors may affect similarity calculations, but modern deployment frameworks increasingly support efficient transformer quantization.

Real-time transformer deployment also benefits from mixed-precision inference, operator fusion, optimized matrix multiplication, and hardware-specific acceleration. GPUs and neural processing units are well suited to the large parallel matrix operations used by attention. Efficient implementation remains essential because theoretical model quality does not guarantee practical robotic performance.

Transformer-based perception still faces several limitations. Models may require enormous datasets, long training times, and extensive computational resources. Attention maps are not always reliable explanations of model behavior, and global reasoning does not eliminate sensitivity to domain shift, rare conditions, or adversarial visual patterns. Robust field validation remains necessary.

Transformers may also lose fine local detail when patch sizes are too large or token merging is aggressive. Small obstacles, narrow boundaries, distant pedestrians, and tiny inspection defects can be overlooked. Hybrid local-global architectures, high-resolution branches, and multi-scale attention help preserve critical details for safety-sensitive robotic tasks.

Domain adaptation remains important because a transformer trained on urban images may not perform reliably in warehouses, hospitals, construction sites, or agricultural environments. Fine-tuning, synthetic data, continual learning, and test-time adaptation enable models to adjust to changing cameras, lighting, object appearances, and operational conditions.

Uncertainty estimation should accompany transformer predictions in safety-critical systems. A model may produce confident outputs even when observing unfamiliar objects or degraded sensor data. Confidence calibration, ensemble inference, out-of-distribution detection, and probabilistic attention mechanisms help identify situations where autonomous decisions should become more conservative.

In autonomous mobile robots, transformer-based perception is rarely used as an isolated module. It operates within a real-time pipeline containing sensor synchronization, preprocessing, localization, mapping, planning, and control. Attention-based perception converts raw multimodal observations into object, scene, motion, and semantic representations that support safe and intelligent robot behavior.

The future of transformer-based perception will involve tighter integration with world models, embodied intelligence, continual learning, and action generation. Perception models will not merely describe the current frame but maintain persistent representations of objects, spaces, people, and events over time. They will predict future changes and evaluate how robot actions may alter the environment.

Multimodal foundation models will increasingly connect vision, language, audio, geometry, touch, and robot state within unified token-based architectures. A robot will be able to interpret a verbal instruction, identify relevant objects, estimate spatial relationships, predict consequences, and generate an action plan using a shared internal representation.

Transformer-based perception therefore represents more than an alternative feature extractor. It provides a general framework for connecting local observations, global context, temporal history, sensor modalities, semantic knowledge, and task objectives. For autonomous mobile robots, this capability supports more accurate perception, flexible interaction, persistent environmental understanding, and increasingly intelligent operation in complex real-world environments.

트랜스포머 기반 인식(Transformer-Based Perception)은 주의 메커니즘(Attention Mechanism)을 이용하여 영상(Image), 비디오(Video), 멀티모달 센서(Multimodal Sensor) 데이터 전체의 관계를 동시에 학습하는 최신 시각 인식 기술이다. 국소 영역(Local Neighborhood)을 중심으로 특징을 추출하는 합성곱 신경망(CNN, Convolutional Neural Network)과 달리, 트랜스포머는 서로 멀리 떨어진 시각 영역 사이의 관계까지 직접 학습할 수 있다. 이러한 능력은 자율주행 이동로봇(AMR, Autonomous Mobile Robot)이 장면 전체(Scene Structure), 객체 간 관계(Object Relationship), 시간적 문맥(Temporal Context), 의미 정보(Semantic Meaning)를 더욱 유연하게 이해할 수 있도록 한다.

트랜스포머 아키텍처(Transformer Architecture)는 원래 자연어 처리(NLP, Natural Language Processing)를 위해 개발되었다. 자기 주의(Self-Attention)는 문장 안에서 멀리 떨어진 단어들 사이의 관계를 학습할 수 있도록 설계되었다. 동일한 원리를 영상에도 적용할 수 있으며, 영상을 여러 개의 작은 영역으로 나누어 각각을 하나의 토큰(Token)으로 표현한다. 이후 모든 토큰 간의 관계를 학습함으로써 국소적인 필터 기반 처리에서 전역적인 관계 추론(Global Relational Reasoning)으로 발전하였다.

트랜스포머 기반 비전에서는 입력 영상을 일정한 크기의 패치(Patch)로 분할한다. 각 패치는 작은 직사각형 형태의 픽셀 집합이며, 선형 투영(Linear Projection)을 통해 하나의 벡터(Vector)로 변환된다. 이러한 벡터를 패치 임베딩(Patch Embedding)이라고 한다. 결과적으로 영상은 언어 모델의 토큰 시퀀스(Token Sequence)와 유사한 형태로 변환되며, 트랜스포머는 이를 동일한 계산 원리로 처리할 수 있다.

패치 크기(Patch Size)는 모델의 성능과 계산량을 크게 결정한다. 작은 패치는 세밀한 공간 정보를 유지하여 작은 객체, 경계, 질감 인식에 유리하지만 토큰 수가 많아져 계산량이 증가한다. 반대로 큰 패치는 계산 속도를 높이지만 세부 정보가 손실될 수 있다. 실제 로봇 시스템에서는 해상도, 지연 시간(Latency), 응용 목적을 고려하여 적절한 패치 크기를 선택한다.

자기 주의(Self-Attention)는 패치의 위치를 스스로 알 수 없기 때문에 위치 정보(Position Information)를 별도로 추가해야 한다. 이를 위치 인코딩(Positional Encoding)이라고 한다. 위치 정보가 없다면 모델은 어떤 특징이 존재하는지는 알 수 있지만 그것이 어디에 있는지는 이해하지 못한다. 공간 위치는 객체 검출(Object Detection), 의미론적 분할(Semantic Segmentation), 깊이 추정(Depth Estimation), 자율주행(Navigation)에서 매우 중요한 정보이다.

비전 트랜스포머(Vision Transformer)에서는 일반적으로 분류 토큰(Classification Token)을 패치 시퀀스 앞에 추가한다. 이 특별한 토큰은 반복적인 주의 연산을 통해 모든 패치의 정보를 통합한다. 최종적으로 생성된 표현은 영상 분류(Image Classification)와 같은 전역 예측(Global Prediction)에 사용된다. 반면 밀집 예측(Dense Prediction) 작업에서는 개별 패치 토큰을 유지하여 공간 정보를 복원한다.

자기 주의(Self-Attention)는 트랜스포머 기반 인식의 핵심 메커니즘이다. 모든 토큰은 쿼리(Query), 키(Key), 값(Value)의 세 가지 표현으로 변환된다. 쿼리는 어떤 정보를 찾고 있는지를 나타내고, 키는 자신이 가진 정보를 표현하며, 값은 실제 전달할 내용을 저장한다. 쿼리와 키의 유사도를 계산하여 각 토큰이 서로 얼마나 중요한지를 결정한다.

주의 가중치(Attention Weight)는 모든 쿼리와 키를 비교하여 계산된다. 이후 정규화(Normalization)를 거쳐 값(Value)을 가중합하여 새로운 표현을 생성한다. 따라서 하나의 영상 영역은 멀리 떨어진 다른 영역의 정보도 직접 참조할 수 있다. 예를 들어 로봇은 지게차(Forklift) 근처의 작업자, 바닥 표시, 안전 울타리를 하나의 장면으로 통합하여 이해할 수 있다.

멀티헤드 주의(Multi-Head Attention)는 여러 종류의 관계를 동시에 학습하는 구조이다. 하나의 헤드는 객체 형태를 학습하고, 다른 헤드는 공간적 거리, 또 다른 헤드는 질감(Texture), 또 다른 헤드는 의미론적 관계(Semantic Context)를 학습할 수 있다. 여러 헤드의 결과를 결합하면 하나의 주의 연산보다 훨씬 풍부한 표현을 얻을 수 있으며, 복잡한 환경에서 더욱 강력한 성능을 제공한다.

트랜스포머 인코더(Transformer Encoder)는 멀티헤드 주의, 정규화(Normalization), 잔차 연결(Residual Connection), 피드포워드 네트워크(Feedforward Network)를 반복적으로 수행한다. 각 계층은 더욱 복잡한 문맥 정보를 통합하여 토큰 표현을 점진적으로 개선한다. 얕은 계층은 외형과 국소 구조를 표현하고, 깊은 계층은 객체, 장면 구조, 상호작용, 의미 정보를 표현한다.

잔차 연결(Residual Connection)은 깊은 트랜스포머 학습에서 매우 중요하다. 정보와 기울기(Gradient)가 중간 계층을 우회하여 전달될 수 있기 때문에 최적화가 안정적으로 이루어진다. 또한 계층 정규화(Layer Normalization)는 특징 분포를 안정화하여 학습 수렴을 향상시킨다. 이러한 구조 덕분에 수억 개 이상의 파라미터를 가진 초대형 모델도 안정적으로 학습할 수 있다.

피드포워드 네트워크(Feedforward Network)는 주의 연산 이후 각 토큰을 독립적으로 비선형 변환하는 역할을 한다. 자기 주의는 어떤 정보를 통합할지를 결정하고, 피드포워드 네트워크는 통합된 정보를 더욱 의미 있는 특징으로 변환한다. 두 과정은 서로 보완적으로 동작하며 강력한 시각 표현을 생성한다.

비전 트랜스포머(Vision Transformer, ViT)는 순수한 주의 기반 구조만으로도 매우 높은 영상 분류 성능을 달성할 수 있음을 보여주었다. CNN 없이도 패치 토큰과 전역 주의를 이용하여 뛰어난 시각 표현을 학습할 수 있었으며, 충분한 데이터와 계산 자원이 있다면 합성곱이 반드시 필요한 것은 아니라는 사실을 입증하였다.

CNN은 인접한 픽셀들이 서로 강한 관계를 가진다는 가정을 이용하고 동일한 필터를 반복 사용한다. 이러한 구조는 계산 효율성과 데이터 활용성을 높인다. 반면 트랜스포머는 이러한 가정을 최소화하고 데이터 자체로부터 관계를 자유롭게 학습한다. 따라서 전역적인 추론 능력은 뛰어나지만 더 많은 데이터와 계산 자원이 필요하다.

하이브리드 CNN-트랜스포머(Hybrid CNN-Transformer)는 국소 특징 추출과 전역 추론을 결합한 구조이다. CNN은 에지, 질감, 객체의 부분을 효율적으로 추출하고, 트랜스포머는 장거리 관계(Long-Range Dependency)와 의미론적 관계를 모델링한다. 이러한 구조는 효율성과 문맥 이해를 동시에 요구하는 자율주행 이동로봇에 매우 적합하다.

계층형 비전 트랜스포머(Hierarchical Vision Transformer)는 CNN처럼 해상도를 점차 줄이고 특징의 깊이를 증가시키는 구조를 가진다. 인접한 토큰을 단계적으로 병합(Token Merging)하여 다중 스케일(Multi-Scale) 특징을 생성한다. 이러한 특징은 객체 검출, 의미론적 분할, 깊이 추정 등 다양한 밀집 예측 작업에 매우 적합하다.

윈도우 기반 주의(Window-Based Attention)는 계산량을 줄이기 위해 작은 영역 안에서만 자기 주의를 계산하는 방법이다. 모든 토큰 간의 관계를 계산하면 계산량이 매우 커지므로, 국소 윈도우(Local Window) 내부에서만 주의를 수행한다. 이후 윈도우를 이동하거나 연결하여 전체 영상으로 정보가 전달되도록 한다.

이동 윈도우 트랜스포머(Shifted Window Transformer)는 연속된 계층마다 서로 다른 윈도우 경계를 사용한다. 이전 계층에서 서로 다른 윈도우에 속했던 토큰들이 다음 계층에서는 서로 상호작용할 수 있으므로 전체 영상에 대한 정보 전달이 가능하다. 이는 고해상도 영상에서도 계산량을 크게 증가시키지 않으면서 전역 정보를 학습할 수 있게 한다.

객체 검출(Object Detection)은 트랜스포머에 의해 크게 변화하였다. 기존 검출기는 앵커(Anchor), 영역 제안(Region Proposal), 후보 생성 후 비최대 억제(NMS, Non-Maximum Suppression)를 사용하였다. 반면 트랜스포머 기반 검출기는 객체 검출을 집합 예측(Set Prediction) 문제로 정의하여 이러한 수작업 과정을 크게 줄였다.

검출 트랜스포머(DETR, Detection Transformer)는 객체 쿼리(Object Query)를 이용하여 인코더의 시각 특징과 교차 주의(Cross-Attention)를 수행한다. 각 객체 쿼리는 하나의 객체를 찾도록 학습되며, 클래스와 경계 상자를 동시에 예측한다. 학습 과정에서는 매칭 알고리즘(Matching Algorithm)을 이용하여 예측과 실제 객체를 연결한다. 이를 통해 객체 검출을 종단간 학습으로 수행할 수 있다.

객체 쿼리는 학습 가능한 탐색 에이전트(Search Agent)처럼 동작한다. 일부는 큰 객체를 잘 찾도록 학습되고, 일부는 작은 객체나 가려진 객체를 탐색하도록 학습된다. 모든 객체를 동시에 처리하므로 객체 간의 관계도 함께 고려할 수 있으며 중복 검출도 줄일 수 있다.

트랜스포머 기반 의미론적 분할은 영상 전체의 문맥을 고려하여 모든 픽셀을 분류한다. 하나의 작은 패치는 단독으로 보면 의미가 모호할 수 있지만, 주변 영역과의 관계를 함께 고려하면 정확한 의미를 판단할 수 있다. 예를 들어 동일한 회색 표면이라도 주변 환경에 따라 바닥, 벽, 도로, 기계가 될 수 있다.

마스크 분류(Mask Classification)는 픽셀 하나하나를 독립적으로 분류하는 대신 객체나 영역 전체의 마스크(Mask)를 예측하는 방식이다. 학습 가능한 쿼리가 객체 또는 영역을 표현하며 해당 마스크를 생성한다. 이를 통해 의미론적 분할, 인스턴스 분할, 파놉틱 분할(Panoptic Segmentation)을 하나의 통합 구조에서 수행할 수 있다.

파놉틱 분할은 배경의 의미 정보와 개별 객체를 동시에 표현한다. 바닥, 벽, 도로, 식생은 의미 영역으로 표현하고, 사람, 차량, 팔레트, 기계는 각각 독립적인 인스턴스로 표현한다. 트랜스포머는 영역과 객체 간의 관계를 동시에 모델링할 수 있기 때문에 이러한 작업에 매우 적합하다.

깊이 추정(Depth Estimation) 역시 전역 문맥 정보를 활용함으로써 성능이 향상된다. 단안 영상에서는 절대 거리를 직접 측정할 수 없기 때문에 원근(Perspective), 객체 크기, 수평선, 표면 연속성, 의미 정보를 함께 이용해야 한다. 트랜스포머는 이러한 장거리 관계를 효과적으로 학습하여 더 일관된 깊이 지도를 생성한다.

스테레오 매칭(Stereo Matching)은 좌우 카메라 영상의 대응점을 찾는 과정이다. 트랜스포머는 멀리 떨어진 후보 영역 사이의 관계까지 고려하여 대응점을 찾을 수 있다. 따라서 질감이 부족한 영역이나 반복 패턴, 부분 가림 상황에서도 기존 방법보다 더욱 정확한 깊이 추정이 가능하다.

비디오 인식(Video Perception)은 시간 축까지 포함하여 추론을 수행한다. 여러 프레임의 패치를 시공간 토큰(Spatiotemporal Token)으로 표현하고, 주의를 이용하여 움직임, 객체 변화, 상호작용을 학습한다. 이를 통해 행동 인식(Action Recognition), 움직임 예측(Motion Forecasting), 객체 추적, 동적 장면 이해가 가능해진다.

시간적 주의(Temporal Attention)는 현재 프레임이 이전 프레임의 정보를 직접 참조하도록 한다. 선반 뒤에 잠시 가려진 사람도 이전 프레임의 정보를 이용하여 계속 추적할 수 있다. 이러한 시간적 일관성은 복잡한 환경에서 안정적인 객체 추적을 가능하게 한다.

다중 객체 추적(Multi-Object Tracking)은 지속적인 추적 쿼리(Track Query)를 이용하여 구현할 수 있다. 각각의 쿼리는 하나의 객체를 나타내며 새로운 프레임이 들어올 때마다 자신의 상태를 업데이트한다. 이를 통해 객체 ID를 유지하고 이동 경로를 추적하며 부분 가림 이후에도 다시 객체를 인식할 수 있다.

트랜스포머는 멀티모달 인식(Multimodal Perception)에 특히 적합하다. 카메라 영상, 깊이 지도, 라이다 포인트 클라우드(Point Cloud), 레이더(Radar), 언어 명령(Language Instruction), 로봇 상태 정보 모두를 토큰으로 표현할 수 있다. 자기 주의를 이용하면 서로 다른 센서가 하나의 통합된 표현 안에서 정보를 교환할 수 있다.

카메라-라이다 융합(Camera-LiDAR Fusion)은 교차 주의(Cross-Attention)를 이용하여 영상 특징과 3차원 포인트를 연결한다. 카메라는 색상과 의미 정보를 제공하고, 라이다는 정확한 거리와 기하학 정보를 제공한다. 두 정보를 결합하면 3차원 객체 검출과 위치 추정의 정확도가 크게 향상된다.

조감도(BEV, Bird\'s-Eye View) 인식은 여러 대의 카메라 영상을 하나의 위에서 내려다본 지도 형태로 변환한다. 트랜스포머는 공간 쿼리(Spatial Query)를 이용하여 여러 카메라의 특징을 통합한다. 결과적으로 차선, 장애물, 차량, 자유 공간을 하나의 좌표계에서 표현할 수 있어 경로 계획에 매우 유리하다.

멀티카메라 트랜스포머는 서로 다른 카메라 영상 사이의 관계를 학습한다. 서로 다른 방향에서 관측된 동일한 객체를 연결하고 사각지대(Blind Spot)를 줄일 수 있다. 카메라의 위치와 자세 정보는 주의 연산을 올바르게 수행하는 데 중요한 역할을 한다.

언어 기반 인식(Language-Guided Perception)은 트랜스포머의 또 다른 큰 장점이다. 시각 토큰과 언어 토큰을 동일한 구조에서 처리할 수 있기 때문에 "노란 안전 콘", "손상된 상자", "열린 문", "안전모를 쓴 작업자"와 같은 자연어 명령을 이해하고 해당 객체를 찾을 수 있다.

개방형 어휘(Open-Vocabulary) 객체 검출과 분할은 고정된 클래스에 제한되지 않는다. 텍스트 임베딩(Text Embedding)과 영상 특징을 비교하여 새로운 개념도 인식할 수 있다. 따라서 새로운 객체를 추가하기 위해 매번 검출기를 다시 학습할 필요가 없으며, 사람의 다양한 명령에도 유연하게 대응할 수 있다.

파운데이션 비전 모델(Foundation Vision Model)은 대부분 대규모 트랜스포머 구조를 기반으로 한다. 방대한 데이터셋으로 학습된 일반적인 시각 표현은 분류, 객체 검출, 의미론적 분할, 깊이 추정, 검색(Retrieval), 로봇 제어 등 다양한 작업에 재사용될 수 있다. 미세 조정(Fine-Tuning)이나 프롬프트(Prompt)를 이용하여 하나의 모델을 다양한 작업에 활용할 수 있다.

자기지도 학습(Self-Supervised Learning)은 대규모 트랜스포머 학습에서 매우 중요한 기술이다. 사람이 직접 라벨링하지 않아도 가려진 패치를 복원하거나 서로 다른 시점(View)의 관계를 학습하도록 만들어 일반적인 특징 표현을 얻는다. 이를 통해 대량의 로봇 센서 데이터를 효율적으로 활용할 수 있다.

마스크드 이미지 모델링(Masked Image Modeling)은 일부 패치를 가린 후 이를 복원하도록 학습한다. 이를 위해 모델은 객체 구조, 주변 문맥, 장면 의미를 이해해야 한다. 학습된 표현은 다양한 시각 작업으로 매우 효과적으로 전이된다.

대조 학습(Contrastive Learning)은 관련 있는 데이터는 가깝게, 관련 없는 데이터는 멀어지도록 표현을 학습한다. 같은 장소를 다른 조명에서 촬영한 영상은 긍정 쌍(Positive Pair)으로 사용하고, 다른 장소는 부정 쌍(Negative Pair)으로 사용한다. 이러한 학습은 장소 인식과 장기 위치 추정의 강인성을 크게 향상시킨다.

트랜스포머는 일반적으로 매우 큰 계산 자원을 요구한다. 모든 토큰 사이의 주의를 계산하면 메모리 사용량과 계산량이 급격히 증가한다. 따라서 제한된 전력과 연산 자원을 가진 자율주행 이동로봇에서는 효율적인 주의(Efficient Attention) 구조가 매우 중요하다.

희소 주의(Sparse Attention)는 일부 토큰 간의 관계만 계산하여 연산량을 줄인다. 변형 가능 주의(Deformable Attention)는 중요한 위치만 선택하여 계산하고, 선형 주의(Linear Attention)는 보다 효율적인 수학적 계산을 사용한다. 이러한 방법은 계산량을 줄이면서도 대부분의 추론 성능을 유지한다.

토큰 가지치기(Token Pruning)는 현재 작업에 거의 기여하지 않는 토큰을 제거하는 기법이다. 배경이나 변화가 없는 영역은 계산에서 제외하고 중요한 객체와 주행 영역만 집중적으로 처리한다. 환경의 복잡도에 따라 계산량을 동적으로 조절할 수 있어 실시간 로봇 시스템에 매우 유용하다.

지식 증류(Knowledge Distillation)는 큰 트랜스포머 모델의 성능을 작은 학생(Student) 모델에 전달하는 기법이다. 학생 모델은 정답뿐 아니라 교사 모델(Teacher Model)의 출력, 주의 패턴, 중간 특징까지 함께 학습한다. 이를 통해 모델 크기를 크게 줄이면서도 높은 성능을 유지할 수 있다.

양자화(Quantization)는 모델의 가중치와 활성화를 낮은 정밀도로 변환하는 기법이다. FP32를 INT8과 같은 형식으로 변환하면 메모리 사용량과 계산 시간이 크게 감소한다. 주의 연산은 수치 오차에 민감하지만 최근의 배포 프레임워크는 효율적인 트랜스포머 양자화를 지원하고 있다.

실시간 트랜스포머 배포는 혼합 정밀도(Mixed Precision), 연산자 융합(Operator Fusion), 최적화된 행렬 연산(Matrix Multiplication), 하드웨어 가속(Hardware Acceleration)을 적극 활용한다. GPU와 NPU는 대규모 행렬 연산에 매우 적합하며, 실제 로봇 성능을 위해서는 이러한 최적화가 필수적이다.

트랜스포머 기반 인식 역시 몇 가지 한계를 가진다. 매우 큰 데이터셋과 긴 학습 시간이 필요하며, 높은 계산 자원을 요구한다. 또한 주의 맵(Attention Map)이 항상 모델의 실제 판단 근거를 설명하는 것은 아니며, 도메인 변화(Domain Shift), 드문 상황, 적대적 환경(Adversarial Condition)에 대한 완전한 해결책도 아니다. 따라서 실제 현장에서의 충분한 검증은 여전히 필수적이다.

패치 크기가 너무 크거나 토큰 병합(Token Merging)이 과도하면 세밀한 지역 정보를 잃을 수 있다. 작은 장애물, 좁은 경계, 먼 보행자, 작은 검사 결함은 쉽게 놓칠 수 있다. 이를 해결하기 위해 하이브리드 구조, 고해상도 분기(High-Resolution Branch), 다중 스케일 주의(Multi-Scale Attention)가 함께 사용된다.

도메인 적응(Domain Adaptation)은 트랜스포머에서도 매우 중요하다. 도시 환경으로 학습된 모델은 창고, 병원, 건설 현장, 농업 환경에서 성능이 크게 달라질 수 있다. 미세 조정(Fine-Tuning), 합성 데이터(Synthetic Data), 지속 학습(Continual Learning), 테스트 시 적응(Test-Time Adaptation)은 이러한 문제를 해결하기 위한 대표적인 방법이다.

안전이 중요한 시스템에서는 불확실성 추정(Uncertainty Estimation)이 반드시 함께 사용되어야 한다. 모델은 처음 보는 객체나 센서 품질이 낮은 상황에서도 높은 신뢰도로 잘못된 결과를 출력할 수 있다. 신뢰도 보정(Confidence Calibration), 앙상블 추론(Ensemble Inference), 분포 밖 데이터 탐지(OOD Detection), 확률적 주의(Probabilistic Attention)는 이러한 위험을 줄여준다.

자율주행 이동로봇에서 트랜스포머 기반 인식은 독립적으로 사용되지 않는다. 센서 동기화(Sensor Synchronization), 전처리(Preprocessing), 위치 추정(Localization), 지도 작성(Mapping), 경로 계획(Path Planning), 제어(Control)와 함께 하나의 실시간 파이프라인을 구성한다. 트랜스포머는 원시 멀티모달 데이터를 객체, 장면, 움직임, 의미 정보로 변환하여 안전하고 지능적인 자율 행동을 지원한다.

트랜스포머 기반 인식의 미래는 월드 모델(World Model), 체화형 인공지능(Embodied Intelligence), 지속 학습, 행동 생성(Action Generation)과의 통합으로 발전하고 있다. 미래의 인식 시스템은 단순히 현재 영상을 분석하는 것이 아니라 시간에 따라 객체, 공간, 사람, 사건을 지속적으로 기억하고 미래를 예측하며 로봇의 행동이 환경에 미칠 영향을 함께 고려하게 될 것이다.

멀티모달 파운데이션 모델(Multimodal Foundation Model)은 비전, 언어, 오디오, 기하학, 촉각(Touch), 로봇 상태를 하나의 토큰 기반 구조에서 통합하게 된다. 로봇은 자연어 명령을 이해하고, 관련 객체를 찾고, 공간 관계를 계산하며, 행동 결과를 예측하고, 최적의 작업 계획(Action Plan)을 생성할 수 있게 된다.

따라서 트랜스포머 기반 인식은 단순히 새로운 특징 추출기가 아니라 국소 정보(Local Observation), 전역 문맥(Global Context), 시간 정보(Temporal History), 다양한 센서, 의미 지식(Semantic Knowledge), 작업 목표(Task Objective)를 하나의 통합 표현으로 연결하는 일반적인 인식 프레임워크이다. 자율주행 이동로봇에서는 이러한 능력을 통해 더욱 정확한 환경 인식, 유연한 상호작용, 지속적인 환경 이해, 그리고 복잡한 실제 환경에서의 지능적인 자율 운용이 가능해질 것이다.

##  

## 03.4 Detection and Segmentation Models

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Detection and segmentation models enable robots to transform raw visual data into structured information about objects, surfaces, free space, obstacles, and functional regions. These models form a central part of modern robotic perception because they determine what is present in the environment, where it is located, and how precisely it occupies physical space.

Object detection identifies individual objects and represents them using class labels, confidence scores, and bounding boxes. Segmentation provides denser spatial understanding by assigning labels to pixels or separating exact object regions. Detection is generally faster, while segmentation provides more precise geometry for navigation, manipulation, inspection, and safety monitoring.

Image classification represents the simplest visual recognition task because it assigns one label to an entire image. Detection extends this task by locating multiple objects within the image. Semantic segmentation further assigns a category to every pixel, while instance segmentation distinguishes separate objects belonging to the same category.

Panoptic segmentation combines semantic and instance segmentation within a unified scene representation. Background regions such as floors, walls, roads, and vegetation are labeled semantically, while countable objects such as people, vehicles, pallets, and machines are separated individually. This provides comprehensive scene understanding for autonomous systems.

Early object detection relied on handcrafted features such as Haar-like patterns, Histogram of Oriented Gradients, Scale-Invariant Feature Transform, and color or texture descriptors. These features were combined with classifiers such as Support Vector Machines, AdaBoost, or random forests to recognize predefined object categories.

Traditional detection methods performed reasonably well in controlled environments but struggled with large variations in scale, illumination, viewpoint, background clutter, and partial occlusion. Their limited representation capacity motivated the transition toward deep neural networks that could learn visual features directly from training data.

Two-stage object detectors separate candidate generation from object classification. In the first stage, the model identifies image regions likely to contain objects. In the second stage, each proposal is classified and its bounding box is refined. This architecture generally achieves high accuracy but requires more computation.

Region-based Convolutional Neural Networks introduced deep learning into object detection by extracting candidate regions and processing each region using a CNN. Although recognition accuracy improved substantially, repeated feature computation for many proposals made the original R-CNN architecture slow and expensive.

Fast R-CNN improved efficiency by computing shared convolutional feature maps for the entire image. Region proposals were projected onto these shared features, allowing classification and bounding box regression without repeating the convolutional backbone for every candidate region.

Faster R-CNN introduced the Region Proposal Network, which generates candidate boxes directly from learned feature maps. This removed the need for external proposal algorithms and enabled nearly end-to-end training. Faster R-CNN remains widely used when detection precision is more important than maximum inference speed.

Two-stage detectors are often preferred for industrial inspection, small object recognition, medical imaging, and applications requiring accurate localization. Their proposal refinement stages improve box quality, although they may not satisfy strict real-time requirements on low-power robotic hardware.

Single-stage detectors predict classes and bounding boxes directly from dense feature maps without a separate proposal stage. They process the image in one unified forward pass, providing significantly higher speed. This makes them particularly suitable for real-time autonomous mobile robots.

The YOLO family treats object detection as a direct regression problem. A single network predicts object positions, dimensions, classes, and confidence scores simultaneously. YOLO architectures offer an effective balance between accuracy, inference speed, model size, and deployment simplicity.

Successive YOLO generations introduced stronger backbones, multi-scale feature fusion, improved loss functions, anchor-free prediction, attention modules, and more efficient training strategies. These improvements have made YOLO one of the most widely deployed detection families in robotics and industrial automation.

Single Shot Detector predicts objects from multiple feature map resolutions. High-resolution maps support small object detection, while low-resolution maps represent larger objects and broader context. SSD provided an important early example of efficient multi-scale single-stage detection.

RetinaNet introduced focal loss to address the extreme imbalance between background and foreground samples. Easy background examples often dominate training, making small or difficult objects less influential. Focal loss reduces the weight of easy examples and focuses optimization on harder detections.

Anchor-based detectors use predefined reference boxes with different scales and aspect ratios. The network predicts corrections relative to these anchors. Anchors improve training stability but require careful configuration because poorly chosen shapes may reduce accuracy for unusual object geometries.

Anchor-free detectors predict object centers, keypoints, box boundaries, or distances directly. This removes manual anchor design and often simplifies optimization. Modern anchor-free models achieve high accuracy while providing efficient inference and improved flexibility across datasets.

Feature pyramids are essential for detecting objects at different scales. Shallow high-resolution features preserve details needed for small objects, while deeper low-resolution features capture semantic context for larger objects. Feature Pyramid Networks combine these representations through top-down and lateral connections.

Path Aggregation Networks further improve multi-scale fusion by strengthening information flow between low-level spatial features and high-level semantic features. Bidirectional feature pyramids repeatedly exchange information across resolutions, improving detection accuracy without excessive computational growth.

Bounding box regression estimates object location and dimensions. Modern detectors often predict center coordinates, width, height, or distances from reference points. Loss functions must encourage accurate overlap while remaining stable for boxes of different sizes and aspect ratios.

Intersection over Union measures the overlap between predicted and ground-truth bounding boxes. IoU-based losses directly optimize localization quality. Generalized IoU, Distance IoU, and Complete IoU incorporate additional geometric factors such as center distance and aspect ratio.

Classification loss determines whether predicted object categories match ground-truth labels. Cross-entropy remains common, while focal loss is useful when background or easy examples dominate. Label smoothing and class-balanced losses can further improve generalization and reduce overconfidence.

Non-Maximum Suppression removes duplicate predictions describing the same object. The highest-confidence box is retained while heavily overlapping alternatives are removed. Soft-NMS reduces confidence instead of deleting boxes immediately, improving performance when objects appear close together.

Transformer-based detectors reformulate object detection as direct set prediction. Learned object queries attend to global image features and predict a fixed set of objects. DETR demonstrated that anchors, proposal generation, and conventional Non-Maximum Suppression could be reduced or eliminated.

Deformable attention improved transformer detection by focusing computation on a small number of relevant spatial locations. This accelerated convergence and enhanced small object recognition. Hybrid CNN-transformer detectors now combine efficient local feature extraction with global relational reasoning.

Semantic segmentation assigns one semantic class to every pixel. It enables robots to identify traversable floors, roads, walls, vegetation, machinery, people, and other environmental regions. Unlike bounding boxes, semantic masks represent exact occupied areas and boundaries.

Fully Convolutional Networks replaced final dense classification layers with convolutional prediction layers. They generated spatial outputs rather than one image-level label, establishing the basic structure of modern semantic segmentation networks.

Encoder-decoder architectures became widely adopted for dense prediction. The encoder reduces spatial resolution while extracting semantic features. The decoder restores the output resolution and generates pixel-level labels. Skip connections preserve fine boundaries and small structures.

U-Net introduced a symmetric encoder-decoder design with strong skip connections between matching resolution levels. Originally developed for biomedical imaging, it became popular in industrial inspection, agricultural robotics, medical analysis, and robotic perception because it performs well with limited data.

SegNet reuses pooling indices from the encoder during decoder upsampling. This reduces memory requirements and supports accurate spatial reconstruction. Its efficient design made it attractive for embedded systems and early real-time segmentation applications.

DeepLab introduced atrous convolution to enlarge the receptive field without reducing feature map resolution. Atrous Spatial Pyramid Pooling captures information at multiple scales, allowing the model to understand both local boundaries and broad contextual structure.

Pyramid Scene Parsing Network aggregates contextual information from several spatial scales. Global context helps resolve ambiguous regions that may look similar locally. A gray surface may represent a wall, road, floor, or machine depending on its relationship to the surrounding scene.

High-Resolution Networks maintain high-resolution representations throughout the network instead of repeatedly downsampling and restoring them. Parallel multi-resolution branches exchange information continuously, preserving precise spatial details that are important for boundaries and small objects.

Instance segmentation combines object detection with pixel-level masks. Each object receives a category, bounding box, and individual segmentation mask. Mask R-CNN extended Faster R-CNN by adding a parallel mask prediction branch for each detected object.

Mask R-CNN uses Region of Interest alignment to preserve precise correspondence between feature maps and object regions. This improves mask boundaries compared with quantized pooling operations. The architecture remains an important baseline for accurate instance-level perception.

One-stage instance segmentation models generate masks directly without proposal refinement. Prototype-based methods produce shared mask bases and object-specific coefficients. This reduces computation and enables real-time instance segmentation for robotic applications.

Query-based mask models use learned queries to represent objects or semantic regions. The same framework can perform semantic, instance, and panoptic segmentation. Mask classification simplifies dense prediction by treating segmentation as a set of region-level predictions.

Segmentation loss often combines pixel-wise classification with boundary, overlap, or region consistency terms. Cross-entropy handles class prediction, while Dice loss improves overlap for small or imbalanced regions. Focal loss emphasizes difficult pixels, and boundary loss improves edge precision.

Class imbalance is common in robotic datasets. Floors and walls may occupy most pixels, while safety cones, tools, defects, or pedestrians occupy only small regions. Weighted losses, oversampling, targeted cropping, and hard-example mining improve recognition of rare but important classes.

Small object detection and segmentation remain difficult because repeated downsampling removes limited visual evidence. High-resolution inputs, feature pyramids, super-resolution, attention, tiling, and dedicated small-object heads help preserve fine details throughout the network.

Occlusion reduces visible object information and may cause detection or segmentation failures. Temporal tracking, multi-view cameras, depth sensing, transformer attention, and world models help maintain object identity and estimate hidden structure from context.

Boundary quality is especially important for navigation and manipulation. Inaccurate masks may falsely enlarge obstacles, remove free space, or shift grasp locations. Boundary refinement modules, high-resolution features, conditional random fields, and edge-aware losses improve geometric precision.

Detection and segmentation models require extensive labeled data. Detection datasets need object boxes and classes, while segmentation requires pixel-level masks. Annotation cost motivates the use of synthetic data, weak supervision, active learning, semi-supervised learning, and automated labeling tools.

Data augmentation improves generalization by simulating realistic appearance variations. Scaling, cropping, rotation, blur, color change, noise, shadows, rain, fog, occlusion, and copy-paste augmentation expose models to conditions expected during real deployment.

Transfer learning reduces training requirements by adapting pretrained visual backbones to specialized tasks. Models trained on large general datasets already understand edges, textures, shapes, and common objects. Fine-tuning transfers this knowledge to warehouses, hospitals, factories, or outdoor robots.

Open-vocabulary detection connects visual features with language embeddings. Instead of recognizing only fixed training classes, the model can detect objects described through text. This allows a robot to search for a red toolbox, damaged package, open door, or worker without a dedicated class-specific retraining process.

Open-vocabulary segmentation extends language-guided recognition to pixel-level masks. Text prompts define the concepts to be segmented, increasing flexibility in changing operational environments. Foundation vision-language models provide the broad representations required for this capability.

Promptable segmentation models can generate object masks from points, boxes, text, or reference regions. They reduce manual annotation effort and support interactive perception. In robotics, prompts may originate from language commands, object detectors, operator input, or task planners.

Three-dimensional detection estimates object position, dimensions, and orientation in physical space. Camera, LiDAR, radar, and depth data may be fused to generate 3D bounding boxes. This supports collision prediction, manipulation, trajectory forecasting, and spatial planning.

Three-dimensional segmentation labels points, voxels, meshes, or occupancy cells rather than image pixels. Point-based networks, sparse convolutional models, and voxel transformers classify environmental geometry. Semantic 3D maps provide persistent world representations for autonomous robots.

Bird\'s-eye-view perception unifies multi-camera and multi-sensor observations within a top-down coordinate frame. Detection and segmentation can then operate directly in the robot\'s navigation space. This simplifies path planning, free-space estimation, and multi-object reasoning.

Real-time deployment requires careful selection between model accuracy and computational cost. High-resolution segmentation may be accurate but slow, while lightweight detection may be fast but geometrically coarse. The correct architecture depends on robot speed, safety requirements, hardware, and task complexity.

Model pruning removes unimportant parameters or channels. Quantization reduces numerical precision, lowering memory use and accelerating inference. Knowledge distillation transfers behavior from a large teacher model to a smaller student. These methods enable advanced perception on embedded hardware.

TensorRT, mixed-precision inference, operator fusion, and hardware-specific kernels further reduce latency. GPUs, neural processing units, and dedicated accelerators provide parallel computation for convolution and attention. Efficient memory movement is often as important as raw arithmetic performance.

Evaluation must consider more than one accuracy metric. Mean Average Precision measures detection quality, while mean Intersection over Union evaluates semantic segmentation. Average Precision for masks measures instance segmentation. Latency, memory use, energy consumption, robustness, and calibration are equally important.

Field performance can differ greatly from benchmark results. Lighting changes, reflective surfaces, weather, camera contamination, vibration, unseen objects, and domain shift may reduce accuracy. Long-duration field testing is therefore essential before safety-critical deployment.

Uncertainty estimation helps determine when model outputs should not be trusted. Low-confidence detection, ambiguous segmentation, inconsistent temporal predictions, or disagreement across sensors may trigger slower motion, additional sensing, remote review, or safe fallback behavior.

Detection and segmentation should operate as parts of an integrated perception system rather than isolated models. Tracking adds temporal consistency, depth provides geometry, localization connects observations to maps, and sensor fusion improves robustness. Planning then converts perception into safe action.

Future detection and segmentation systems will increasingly combine CNNs, transformers, vision-language models, multimodal sensing, continual learning, and world models. A single adaptable model may detect objects, segment regions, estimate depth, track motion, and interpret natural-language tasks within one unified architecture.

For autonomous mobile robots, these models provide the structured visual understanding required to distinguish objects from background, identify safe space, estimate precise boundaries, and interpret complex scenes. Their continued development will support safer navigation, more accurate manipulation, reliable inspection, and increasingly flexible operation in dynamic real-world environments.

객체 검출 및 분할 모델(Detection and Segmentation Models)은 로봇이 원시 시각 데이터(Raw Visual Data)를 객체, 표면, 자유 공간(Free Space), 장애물, 기능 영역(Functional Region)에 대한 구조화된 정보로 변환할 수 있도록 한다. 이러한 모델은 환경에 무엇이 존재하고, 어디에 위치하며, 실제 공간을 얼마나 정밀하게 점유하는지를 판단하므로 현대 로봇 인식(Robotic Perception)의 핵심을 구성한다.

객체 검출(Object Detection)은 개별 객체를 식별하고 클래스 레이블(Class Label), 신뢰도 점수(Confidence Score), 경계 상자(Bounding Box)를 이용하여 표현한다. 분할(Segmentation)은 픽셀에 레이블을 부여하거나 객체의 정확한 영역을 분리하여 더욱 밀집된 공간 정보를 제공한다. 객체 검출은 일반적으로 빠르며, 분할은 자율주행, 조작, 검사, 안전 감시에 필요한 정밀한 기하학 정보를 제공한다.

영상 분류(Image Classification)는 전체 영상에 하나의 레이블을 부여하는 가장 단순한 시각 인식 작업이다. 객체 검출은 이를 확장하여 영상 안의 여러 객체 위치를 찾는다. 의미론적 분할(Semantic Segmentation)은 모든 픽셀에 클래스를 부여하며, 인스턴스 분할(Instance Segmentation)은 같은 클래스에 속한 개별 객체를 각각 구분한다.

파놉틱 분할(Panoptic Segmentation)은 의미론적 분할과 인스턴스 분할을 하나의 통합된 장면 표현으로 결합한다. 바닥, 벽, 도로, 식생과 같은 배경 영역은 의미론적으로 분류하며, 사람, 차량, 팔레트, 기계와 같이 개수를 셀 수 있는 객체는 각각 독립적으로 분리한다. 이를 통해 자율 시스템은 장면 전체를 종합적으로 이해할 수 있다.

초기의 객체 검출은 Haar 유사 특징(Haar-Like Feature), 방향성 그래디언트 히스토그램(HOG, Histogram of Oriented Gradients), 크기 불변 특징 변환(SIFT, Scale-Invariant Feature Transform), 색상 및 질감 기술자와 같은 수작업 기반 특징(Handcrafted Feature)에 의존하였다. 이러한 특징은 SVM(Support Vector Machine), AdaBoost, 랜덤 포레스트(Random Forest)와 결합되어 미리 정의된 객체를 인식하였다.

전통적인 객체 검출 방법은 제어된 환경에서는 비교적 잘 동작했지만 크기, 조명, 시점, 복잡한 배경, 부분 가림(Occlusion)의 변화에 취약하였다. 이러한 제한된 표현 능력은 학습 데이터로부터 시각 특징을 직접 학습할 수 있는 심층 신경망(Deep Neural Network)으로의 전환을 촉진하였다.

2단계 객체 검출기(Two-Stage Object Detector)는 후보 영역 생성과 객체 분류를 분리한다. 첫 번째 단계에서는 객체가 존재할 가능성이 높은 영상 영역을 찾고, 두 번째 단계에서는 각 후보를 분류하고 경계 상자를 정밀하게 보정한다. 이러한 구조는 일반적으로 높은 정확도를 제공하지만 계산량이 더 많다.

영역 기반 합성곱 신경망(R-CNN, Region-Based Convolutional Neural Network)은 후보 영역을 추출한 후 각 영역을 CNN으로 처리함으로써 객체 검출에 딥러닝을 도입하였다. 인식 정확도는 크게 향상되었지만 수많은 후보에 대해 특징 계산을 반복해야 했기 때문에 초기 R-CNN은 느리고 계산 비용이 매우 높았다.

Fast R-CNN은 전체 영상에 대해 합성곱 특징 맵(Convolutional Feature Map)을 한 번만 계산하여 효율성을 개선하였다. 후보 영역은 공유된 특징 맵에 투영되며, 각 후보마다 백본(Backbone) 계산을 반복하지 않고 분류와 경계 상자 회귀(Bounding Box Regression)를 수행한다.

Faster R-CNN은 학습된 특징 맵으로부터 후보 경계 상자를 직접 생성하는 영역 제안 네트워크(RPN, Region Proposal Network)를 도입하였다. 외부 후보 생성 알고리즘이 필요 없어졌으며 거의 종단간 학습(End-to-End Training)이 가능해졌다. Faster R-CNN은 최대 추론 속도보다 검출 정밀도가 중요한 응용 분야에서 여전히 널리 사용된다.

2단계 검출기는 산업 검사(Industrial Inspection), 작은 객체 인식(Small Object Recognition), 의료 영상(Medical Imaging), 정밀한 위치 추정이 필요한 작업에 자주 사용된다. 후보 영역을 다시 보정하는 과정이 경계 상자의 품질을 높이지만, 저전력 로봇 하드웨어에서는 엄격한 실시간 요구사항을 만족하지 못할 수 있다.

1단계 객체 검출기(Single-Stage Object Detector)는 별도의 후보 영역 생성 과정 없이 밀집 특징 맵(Dense Feature Map)에서 클래스와 경계 상자를 직접 예측한다. 하나의 통합된 순전파(Forward Pass)로 영상을 처리하기 때문에 훨씬 빠르며, 실시간 자율주행 이동로봇에 특히 적합하다.

YOLO(You Only Look Once) 계열은 객체 검출을 직접적인 회귀 문제(Regression Problem)로 처리한다. 하나의 네트워크가 객체 위치, 크기, 클래스, 신뢰도 점수를 동시에 예측한다. YOLO 구조는 정확도, 추론 속도, 모델 크기, 배포 용이성 사이에서 뛰어난 균형을 제공한다.

YOLO의 세대가 발전하면서 더욱 강력한 백본, 다중 스케일 특징 융합(Multi-Scale Feature Fusion), 개선된 손실 함수(Loss Function), 앵커 프리 예측(Anchor-Free Prediction), 주의 모듈(Attention Module), 효율적인 학습 전략이 도입되었다. 이러한 발전으로 YOLO는 로보틱스와 산업 자동화에서 가장 널리 배포되는 객체 검출 모델 계열 중 하나가 되었다.

SSD(Single Shot Detector)는 서로 다른 해상도의 특징 맵에서 객체를 예측한다. 고해상도 특징 맵은 작은 객체 검출을 지원하고, 저해상도 특징 맵은 큰 객체와 넓은 문맥(Context)을 표현한다. SSD는 효율적인 다중 스케일 1단계 객체 검출의 초기 대표 사례를 제공하였다.

RetinaNet은 배경과 전경 샘플 사이의 극심한 불균형 문제를 해결하기 위해 초점 손실(Focal Loss)을 도입하였다. 쉬운 배경 샘플이 학습을 지배하면 작거나 어려운 객체의 영향력이 감소한다. Focal Loss는 쉬운 샘플의 가중치를 낮추고 어려운 객체에 학습을 집중시킨다.

앵커 기반 검출기(Anchor-Based Detector)는 여러 크기와 종횡비를 가진 기준 상자를 미리 정의한다. 네트워크는 이러한 앵커를 기준으로 위치 보정값을 예측한다. 앵커는 학습을 안정화하지만, 형태를 잘못 설정하면 특이한 객체 기하 구조에 대한 정확도가 저하될 수 있어 세밀한 설정이 필요하다.

앵커 프리 검출기(Anchor-Free Detector)는 객체 중심, 키포인트(Keypoint), 경계, 또는 기준점으로부터의 거리를 직접 예측한다. 이를 통해 수작업 앵커 설계를 제거하고 학습을 단순화할 수 있다. 최신 앵커 프리 모델은 높은 정확도와 효율적인 추론, 다양한 데이터셋에 대한 높은 유연성을 제공한다.

특징 피라미드(Feature Pyramid)는 다양한 크기의 객체를 검출하는 데 필수적이다. 얕은 고해상도 특징은 작은 객체에 필요한 세부 정보를 유지하고, 깊은 저해상도 특징은 큰 객체와 의미론적 문맥을 표현한다. 특징 피라미드 네트워크(FPN, Feature Pyramid Network)는 상향 및 측면 연결을 통해 이러한 표현을 결합한다.

경로 집계 네트워크(PAN, Path Aggregation Network)는 저수준 공간 특징과 고수준 의미 특징 사이의 정보 흐름을 강화하여 다중 스케일 융합을 개선한다. 양방향 특징 피라미드(Bidirectional Feature Pyramid)는 여러 해상도 사이에서 정보를 반복적으로 교환하여 과도한 계산 증가 없이 검출 성능을 향상시킨다.

경계 상자 회귀(Bounding Box Regression)는 객체의 위치와 크기를 추정한다. 현대의 검출기는 일반적으로 중심 좌표, 너비, 높이 또는 기준점으로부터 경계까지의 거리를 예측한다. 손실 함수는 서로 다른 크기와 종횡비를 가진 경계 상자에서도 안정적으로 겹침 정확도를 향상시켜야 한다.

교집합 대비 합집합(IoU, Intersection over Union)은 예측 경계 상자와 실제 경계 상자의 겹침 정도를 측정한다. IoU 기반 손실은 위치 추정 품질을 직접 최적화한다. 일반화 IoU(GIoU), 거리 IoU(DIoU), 완전 IoU(CIoU)는 중심 거리와 종횡비와 같은 추가적인 기하학 요소를 포함한다.

분류 손실(Classification Loss)은 예측한 객체 클래스가 실제 레이블과 일치하는지를 판단한다. 교차 엔트로피(Cross-Entropy)가 일반적으로 사용되며, 배경이나 쉬운 샘플이 지나치게 많은 경우 Focal Loss가 유용하다. 레이블 스무딩(Label Smoothing)과 클래스 균형 손실(Class-Balanced Loss)은 일반화 성능을 높이고 과도한 확신을 줄일 수 있다.

비최대 억제(NMS, Non-Maximum Suppression)는 동일한 객체를 나타내는 중복 예측을 제거한다. 가장 높은 신뢰도를 가진 경계 상자는 유지하고, 크게 겹치는 다른 경계 상자는 제거한다. Soft-NMS는 상자를 즉시 삭제하지 않고 신뢰도를 감소시켜 객체들이 가까이 존재하는 환경에서 성능을 향상시킨다.

트랜스포머 기반 검출기(Transformer-Based Detector)는 객체 검출을 직접적인 집합 예측(Set Prediction) 문제로 다시 정의한다. 학습 가능한 객체 쿼리(Object Query)는 전역 영상 특징에 주의를 적용하고 고정된 수의 객체를 예측한다. DETR은 앵커, 후보 생성, 전통적인 NMS를 줄이거나 제거할 수 있음을 보여주었다.

변형 가능 주의(Deformable Attention)는 소수의 중요한 공간 위치에 계산을 집중하여 트랜스포머 검출을 개선하였다. 이를 통해 학습 수렴 속도를 높이고 작은 객체 검출 성능을 향상시켰다. 하이브리드 CNN-트랜스포머 검출기는 효율적인 국소 특징 추출과 전역 관계 추론을 결합한다.

의미론적 분할(Semantic Segmentation)은 모든 픽셀에 하나의 의미 클래스를 부여한다. 로봇은 이를 이용하여 주행 가능한 바닥, 도로, 벽, 식생, 기계, 사람, 기타 환경 영역을 식별할 수 있다. 의미론적 마스크는 경계 상자와 달리 실제 점유 영역과 객체 경계를 정확하게 표현한다.

완전 합성곱 신경망(FCN, Fully Convolutional Network)은 마지막 완전 연결 분류 계층을 합성곱 예측 계층으로 대체하였다. 하나의 영상 수준 레이블 대신 공간적 출력 결과를 생성함으로써 현대 의미론적 분할 네트워크의 기본 구조를 확립하였다.

인코더-디코더(Encoder-Decoder) 구조는 밀집 예측(Dense Prediction) 작업에 널리 사용된다. 인코더는 공간 해상도를 줄이면서 의미론적 특징을 추출하고, 디코더는 출력 해상도를 복원하여 픽셀 단위 레이블을 생성한다. 스킵 연결(Skip Connection)은 세밀한 경계와 작은 구조를 보존한다.

U-Net은 동일한 해상도 단계 사이에 강력한 스킵 연결을 사용하는 대칭형 인코더-디코더 구조를 도입하였다. 원래 의료 영상용으로 개발되었지만, 제한된 데이터로도 높은 성능을 제공하여 산업 검사, 농업 로봇, 의료 분석, 로봇 인식 분야에서 널리 사용되고 있다.

SegNet은 인코더에서 계산한 풀링 인덱스(Pooling Index)를 디코더의 업샘플링 과정에서 재사용한다. 이를 통해 메모리 사용량을 줄이면서도 정확한 공간 복원을 지원한다. 효율적인 구조 덕분에 임베디드 시스템과 초기 실시간 분할 응용에서 높은 활용성을 보였다.

DeepLab은 특징 맵 해상도를 줄이지 않고 수용 영역(Receptive Field)을 확대하기 위해 팽창 합성곱(Atrous Convolution)을 도입하였다. 팽창 공간 피라미드 풀링(ASPP, Atrous Spatial Pyramid Pooling)은 여러 크기의 정보를 동시에 추출하여 국소 경계와 넓은 문맥을 함께 이해할 수 있도록 한다.

피라미드 장면 분석 네트워크(PSPNet, Pyramid Scene Parsing Network)는 여러 공간 크기의 문맥 정보를 집계한다. 전역 문맥(Global Context)은 국소적으로 비슷하게 보이는 모호한 영역을 구분하는 데 도움을 준다. 동일한 회색 표면도 주변 관계에 따라 벽, 도로, 바닥, 기계로 해석될 수 있다.

고해상도 네트워크(HRNet, High-Resolution Network)는 공간 해상도를 반복적으로 낮췄다가 복원하는 대신 네트워크 전체에서 고해상도 표현을 유지한다. 여러 해상도의 병렬 분기(Parallel Branch)가 지속적으로 정보를 교환하여 경계와 작은 객체에 필요한 정밀한 공간 정보를 보존한다.

인스턴스 분할(Instance Segmentation)은 객체 검출과 픽셀 단위 마스크를 결합한다. 각 객체는 클래스, 경계 상자, 개별 분할 마스크를 가진다. Mask R-CNN은 Faster R-CNN에 각 검출 객체의 마스크를 예측하는 병렬 분기(Parallel Branch)를 추가하였다.

Mask R-CNN은 특징 맵과 객체 영역의 정확한 대응 관계를 유지하기 위해 관심 영역 정렬(RoI Align)을 사용한다. 이는 양자화된 풀링 연산보다 마스크 경계를 더 정확하게 복원한다. 이 구조는 정밀한 인스턴스 수준 인식을 위한 중요한 기준 모델로 여전히 사용된다.

1단계 인스턴스 분할 모델(One-Stage Instance Segmentation Model)은 후보 영역 보정 없이 마스크를 직접 생성한다. 프로토타입 기반 방법(Prototype-Based Method)은 공통 마스크 기저와 객체별 계수를 생성한다. 이를 통해 계산량을 줄이고 로봇 응용에 필요한 실시간 인스턴스 분할을 가능하게 한다.

쿼리 기반 마스크 모델(Query-Based Mask Model)은 학습 가능한 쿼리를 이용하여 객체나 의미 영역을 표현한다. 동일한 구조로 의미론적 분할, 인스턴스 분할, 파놉틱 분할을 수행할 수 있다. 마스크 분류(Mask Classification)는 분할을 영역 수준의 집합 예측으로 처리하여 밀집 예측 구조를 단순화한다.

분할 손실(Segmentation Loss)은 일반적으로 픽셀 분류, 경계, 겹침, 영역 일관성 요소를 결합한다. 교차 엔트로피는 클래스 예측을 처리하고, 다이스 손실(Dice Loss)은 작거나 불균형한 영역의 겹침을 개선한다. Focal Loss는 어려운 픽셀에 집중하며, 경계 손실(Boundary Loss)은 에지 정확도를 향상시킨다.

클래스 불균형(Class Imbalance)은 로봇 데이터셋에서 흔히 나타난다. 바닥과 벽은 대부분의 픽셀을 차지하는 반면 안전 콘, 공구, 결함, 보행자는 작은 영역만 차지한다. 가중 손실, 오버샘플링(Oversampling), 표적 크롭(Targeted Cropping), 어려운 샘플 채굴(Hard-Example Mining)은 중요하지만 드문 클래스를 더 잘 인식하도록 한다.

작은 객체 검출 및 분할은 반복적인 다운샘플링으로 제한된 시각 정보가 사라지기 때문에 매우 어렵다. 고해상도 입력, 특징 피라미드, 초해상도(Super-Resolution), 주의 메커니즘, 타일링(Tiling), 작은 객체 전용 헤드가 네트워크 전체에서 세부 정보를 유지하도록 돕는다.

가림(Occlusion)은 관측 가능한 객체 정보를 줄여 검출과 분할 실패를 유발한다. 시간적 추적(Temporal Tracking), 다중 시점 카메라, 깊이 센서, 트랜스포머 주의, 월드 모델(World Model)은 객체의 정체성을 유지하고 문맥을 이용하여 가려진 구조를 추정하도록 돕는다.

경계 품질(Boundary Quality)은 자율주행과 조작에서 특히 중요하다. 부정확한 마스크는 장애물 영역을 과도하게 확대하거나 자유 공간을 제거하고, 파지 위치(Grasp Location)를 잘못 계산할 수 있다. 경계 보정 모듈, 고해상도 특징, 조건부 랜덤 필드(CRF), 에지 인식 손실은 기하학적 정확도를 향상시킨다.

객체 검출과 분할 모델은 대규모 라벨링 데이터를 필요로 한다. 객체 검출 데이터셋은 경계 상자와 클래스가 필요하며, 분할 데이터셋은 픽셀 단위 마스크를 필요로 한다. 높은 주석 비용으로 인해 합성 데이터(Synthetic Data), 약지도 학습(Weak Supervision), 능동 학습(Active Learning), 반지도 학습(Semi-Supervised Learning), 자동 라벨링 도구가 활용되고 있다.

데이터 증강(Data Augmentation)은 실제 배포 환경에서 예상되는 외형 변화를 시뮬레이션하여 일반화 성능을 향상시킨다. 크기 조정, 크롭, 회전, 블러, 색상 변화, 노이즈, 그림자, 비, 안개, 가림, 복사-붙여넣기 증강(Copy-Paste Augmentation) 등이 사용된다.

전이 학습(Transfer Learning)은 사전학습된 시각 백본(Pretrained Visual Backbone)을 특정 작업에 적용하여 학습 요구량을 줄인다. 대규모 일반 데이터셋으로 학습된 모델은 이미 에지, 질감, 형태, 일반 객체를 이해하고 있다. 미세 조정(Fine-Tuning)을 통해 이러한 지식을 창고, 병원, 공장, 야외 로봇 환경에 전이할 수 있다.

개방형 어휘 객체 검출(Open-Vocabulary Detection)은 시각 특징을 언어 임베딩(Language Embedding)과 연결한다. 학습된 고정 클래스만 인식하는 대신 텍스트로 설명된 객체를 검출할 수 있다. 로봇은 전용 클래스 재학습 없이 빨간 공구함, 손상된 포장 상자, 열린 문, 작업자를 찾을 수 있다.

개방형 어휘 분할(Open-Vocabulary Segmentation)은 언어 기반 인식을 픽셀 단위 마스크로 확장한다. 텍스트 프롬프트(Text Prompt)가 분할할 개념을 정의하므로 변화하는 작업 환경에서 높은 유연성을 제공한다. 비전-언어 파운데이션 모델(Vision-Language Foundation Model)은 이러한 기능에 필요한 폭넓은 표현을 제공한다.

프롬프트 기반 분할 모델(Promptable Segmentation Model)은 점, 경계 상자, 텍스트, 기준 영역을 입력으로 받아 객체 마스크를 생성한다. 이는 수작업 라벨링 비용을 줄이고 상호작용형 인식(Interactive Perception)을 지원한다. 로봇에서는 언어 명령, 객체 검출 결과, 운영자 입력, 작업 계획기가 프롬프트를 제공할 수 있다.

3차원 객체 검출(3D Object Detection)은 실제 공간에서 객체의 위치, 크기, 방향을 추정한다. 카메라, 라이다(LiDAR), 레이더(Radar), 깊이 데이터가 융합되어 3차원 경계 상자를 생성할 수 있다. 이러한 정보는 충돌 예측, 로봇 조작, 이동 경로 예측, 공간 계획에 활용된다.

3차원 분할(3D Segmentation)은 영상 픽셀이 아니라 포인트, 복셀(Voxel), 메시(Mesh), 점유 셀(Occupancy Cell)에 레이블을 부여한다. 포인트 기반 신경망, 희소 합성곱 모델(Sparse Convolutional Model), 복셀 트랜스포머(Voxel Transformer)가 환경의 기하 구조를 분류한다. 의미론적 3차원 지도는 로봇의 지속적인 월드 표현을 제공한다.

조감도 인식(BEV Perception, Bird\'s-Eye-View Perception)은 여러 카메라와 센서의 관측 결과를 위에서 내려다보는 공통 좌표계로 통합한다. 이후 객체 검출과 분할을 로봇의 주행 좌표 공간에서 직접 수행할 수 있다. 이는 경로 계획, 자유 공간 추정, 다중 객체 관계 추론을 단순화한다.

실시간 배포에서는 모델 정확도와 계산 비용 사이의 신중한 선택이 필요하다. 고해상도 분할은 정확하지만 느릴 수 있고, 경량 객체 검출은 빠르지만 기하학적 표현이 거칠 수 있다. 적절한 모델은 로봇의 속도, 안전 요구사항, 하드웨어, 작업 복잡도에 따라 결정된다.

모델 가지치기(Model Pruning)는 중요하지 않은 파라미터나 채널을 제거한다. 양자화(Quantization)는 수치 정밀도를 낮춰 메모리 사용량과 추론 시간을 줄인다. 지식 증류(Knowledge Distillation)는 큰 교사 모델의 성능을 작은 학생 모델로 전달한다. 이러한 기법은 임베디드 하드웨어에서도 고급 인식을 가능하게 한다.

TensorRT, 혼합 정밀도 추론(Mixed-Precision Inference), 연산자 융합(Operator Fusion), 하드웨어 전용 커널은 지연 시간을 더욱 줄인다. GPU, 신경망 처리 장치(NPU), 전용 가속기는 합성곱과 주의 연산을 병렬로 처리한다. 실제 시스템에서는 연산 성능만큼 효율적인 메모리 이동도 중요하다.

성능 평가는 하나의 정확도 지표만으로 이루어져서는 안 된다. 평균 정밀도(mAP, Mean Average Precision)는 객체 검출 품질을 평가하고, 평균 교집합 대비 합집합(mIoU, Mean Intersection over Union)은 의미론적 분할을 평가한다. 마스크 평균 정밀도는 인스턴스 분할을 평가한다. 지연 시간, 메모리, 에너지, 강인성, 신뢰도 보정도 함께 평가해야 한다.

현장 성능은 벤치마크 결과와 크게 다를 수 있다. 조명 변화, 반사 표면, 날씨, 렌즈 오염, 진동, 새로운 객체, 도메인 변화(Domain Shift)는 정확도를 저하시킬 수 있다. 따라서 안전이 중요한 실제 배포 이전에는 장시간 현장 검증(Field Testing)이 반드시 필요하다.

불확실성 추정(Uncertainty Estimation)은 모델의 출력을 신뢰해서는 안 되는 상황을 판단하도록 돕는다. 낮은 신뢰도의 객체 검출, 모호한 분할, 시간적으로 일관되지 않은 예측, 센서 간 불일치는 속도 저하, 추가 센싱, 원격 검토, 안전 모드 전환을 유발할 수 있다.

객체 검출과 분할은 독립된 모델이 아니라 통합 인식 시스템(Integrated Perception System)의 일부로 동작해야 한다. 객체 추적은 시간적 일관성을 제공하고, 깊이 정보는 기하학을 제공하며, 위치 추정은 관측 결과를 지도와 연결하고, 센서 융합은 강인성을 향상시킨다. 이후 경로 계획은 이러한 인식 정보를 안전한 행동으로 변환한다.

미래의 객체 검출 및 분할 시스템은 CNN, 트랜스포머, 비전-언어 모델, 멀티모달 센싱, 지속 학습(Continual Learning), 월드 모델을 더욱 긴밀하게 통합할 것이다. 하나의 적응형 모델이 객체 검출, 영역 분할, 깊이 추정, 움직임 추적, 자연어 작업 해석을 통합 구조 안에서 수행할 수 있다.

자율주행 이동로봇에서 이러한 모델은 객체와 배경을 구분하고, 안전한 공간을 식별하며, 정밀한 경계를 계산하고, 복잡한 장면을 해석하는 데 필요한 구조화된 시각 정보를 제공한다. 기술이 발전함에 따라 더욱 안전한 자율주행, 정밀한 물체 조작, 신뢰성 높은 검사, 동적인 실제 환경에서의 유연한 운용이 가능해질 것이다.

##  

## 03.5 3D Perception Models

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Three-dimensional perception models allow autonomous robots to understand the geometry, position, orientation, and spatial relationships of objects in the physical world. Unlike two-dimensional vision, which describes appearance on an image plane, 3D perception estimates where objects and surfaces exist in real space.

This capability is essential for autonomous mobile robots because navigation, obstacle avoidance, manipulation, inspection, mapping, and interaction all depend on accurate spatial understanding. A robot must know not only what an object is, but also how far away it is, how large it is, and whether it blocks a planned path.

Three-dimensional perception models process data from cameras, stereo systems, RGB-D sensors, LiDAR, radar, or combinations of multiple sensors. Each sensor provides a different form of information, and modern models often combine them to create a more complete and reliable representation of the environment.

A monocular camera provides rich color, texture, and semantic information but does not directly measure absolute depth. Stereo cameras estimate depth through disparity, while RGB-D sensors directly provide aligned color and distance information. LiDAR offers highly accurate geometric measurements but contains less visual appearance information.

Radar measures distance and relative velocity and remains reliable under rain, fog, dust, and low-light conditions. However, radar data are generally sparse and lower in spatial resolution than camera or LiDAR data. Sensor fusion is therefore widely used to combine complementary strengths.

Three-dimensional perception can be divided into several major tasks. These include depth estimation, point cloud processing, 3D object detection, 3D semantic segmentation, occupancy prediction, surface reconstruction, pose estimation, scene flow estimation, and semantic mapping.

Depth estimation predicts the distance from the sensor to visible parts of the environment. It may produce a dense depth map aligned with the image or sparse depth values associated with selected features. Reliable depth is fundamental for metric reasoning and safe robotic motion.

Monocular depth estimation uses a single image to predict scene geometry. Because absolute distance cannot be uniquely recovered from one image, the model learns visual cues such as perspective, texture gradient, object size, shading, occlusion, and semantic context.

Deep monocular depth models are trained using ground-truth depth from LiDAR, stereo systems, RGB-D cameras, or synthetic environments. They can generate dense depth maps even when only a standard camera is available, reducing sensor cost and hardware complexity.

The major limitation of monocular depth is scale ambiguity. A model may correctly estimate relative depth while producing inaccurate absolute distance. Wheel odometry, inertial measurements, known object dimensions, or map information can help recover metric scale in robotic applications.

Stereo depth models process left and right camera images captured from slightly different viewpoints. Corresponding points appear at different horizontal positions, and the difference is called disparity. Greater disparity indicates a closer object, while smaller disparity indicates a more distant object.

Traditional stereo methods use hand-designed matching costs and optimization procedures. Deep stereo models learn feature extraction, correspondence matching, cost aggregation, and disparity refinement directly from data, improving performance in low-texture and complex environments.

Stereo models often construct a cost volume that compares candidate correspondences across possible disparity values. Three-dimensional convolution or transformer-based attention is then used to reason over the cost volume and select the most likely depth for each pixel.

Optical geometry remains important even when deep learning is used. Camera calibration, baseline distance, focal length, and image rectification directly affect stereo accuracy. Small calibration errors can produce large depth errors, especially for distant objects.

Depth completion models combine sparse geometric measurements with dense camera images. Sparse LiDAR points provide reliable metric depth, while RGB images supply boundaries, textures, and semantic information. The model predicts a dense depth map that preserves both accuracy and spatial detail.

Point clouds are one of the most common representations of 3D environments. Each point stores spatial coordinates and may also include intensity, color, time, confidence, surface normal, or semantic information. Point clouds directly represent irregular geometry without requiring a regular image grid.

However, point clouds are unordered, sparse, and nonuniform. The distance between neighboring points varies, and sensor density decreases with range. These properties make conventional image-based convolution unsuitable without additional representation changes.

PointNet introduced a direct method for processing unordered point sets. It applies shared neural transformations to individual points and uses symmetric aggregation, such as max pooling, to create representations independent of point ordering.

PointNet is efficient and conceptually simple, but it has limited ability to capture detailed local geometry. PointNet++ improves this by grouping nearby points at multiple spatial scales and learning hierarchical local features.

Point-based models preserve raw geometric precision and avoid voxel quantization. They are useful for object classification, part segmentation, scene segmentation, registration, and point cloud understanding. However, neighbor search and irregular memory access may become computationally expensive.

Voxel-based models divide 3D space into regular volumetric cells called voxels. Points falling inside the same cell are aggregated into a local feature. The resulting voxel grid can be processed using three-dimensional convolutional neural networks.

Regular voxel representations simplify neighborhood operations and are well suited to parallel hardware. However, dense 3D grids consume large amounts of memory because most cells in real environments are empty.

Sparse convolutional networks solve this problem by performing computation only on occupied voxels. They preserve the structured advantages of voxel processing while greatly reducing unnecessary operations in empty space.

Sparse voxel models are widely used for LiDAR segmentation, 3D object detection, occupancy prediction, and large-scale mapping. Their efficiency makes them attractive for real-time autonomous driving and mobile robotic systems.

Pillar-based models simplify 3D processing by dividing the ground plane into vertical columns called pillars. Points within each pillar are encoded into features, producing a two-dimensional feature map that can be processed using efficient 2D convolution.

PointPillars demonstrated that this simplified representation can provide fast 3D object detection with competitive accuracy. Pillar methods are especially suitable for road vehicles and ground robots where vertical structure can be compressed without losing critical information.

Range image models project LiDAR points onto a two-dimensional grid based on azimuth and elevation angles. The result resembles an image in which each pixel stores range, reflectance, or other geometric information.

This projection enables the use of efficient CNN architectures for point cloud segmentation and detection. However, projection may cause information loss, overlapping points, and distortion, particularly near object boundaries.

Bird\'s-eye-view representation projects 3D information onto the ground plane. The resulting top-down map provides a natural coordinate system for robot navigation, lane understanding, free-space estimation, and collision checking.

BEV models combine features from cameras, LiDAR, or radar into a unified spatial representation. Objects are represented according to their physical location rather than their image position, making planning and prediction more direct.

Camera-based BEV models transform image features into a top-down coordinate system using geometry, depth estimation, or learned spatial attention. Multiple cameras can be fused to create nearly complete coverage around the robot.

LiDAR-based BEV models directly encode point cloud geometry into a top-down grid. Camera and LiDAR BEV features can also be fused to combine visual semantics with precise metric structure.

Three-dimensional object detection predicts complete 3D bounding boxes around objects. Each box typically includes center position, length, width, height, orientation, category, and confidence score.

For autonomous robots, 3D detection identifies people, vehicles, forklifts, pallets, machinery, containers, obstacles, and inspection targets in metric space. This allows direct collision analysis and motion planning.

3D detectors may be point-based, voxel-based, pillar-based, BEV-based, or multimodal. Some models generate candidate proposals and refine them, while others directly predict objects in a single stage.

Two-stage 3D detectors generally provide high accuracy. The first stage generates candidate boxes, and the second stage refines object classification, localization, size, and orientation using more detailed local features.

Single-stage 3D detectors predict objects directly from encoded scene features. They are generally faster and easier to deploy in real-time systems, although performance may vary for small or distant objects.

Anchor-based 3D detectors use predefined boxes with common sizes and orientations. The network predicts corrections relative to these anchors. This supports stable learning but may require careful configuration for different object types.

Anchor-free 3D detectors predict object centers, keypoints, or box boundaries directly. They remove manual anchor design and often improve flexibility when object sizes and shapes vary significantly.

Transformer-based 3D detectors use learned queries and attention to identify objects from point, voxel, image, or BEV features. Global reasoning helps model interactions between distant objects and reduces duplicate predictions.

Three-dimensional semantic segmentation assigns a semantic category to every point or voxel. It can label road, floor, wall, vegetation, vehicle, person, shelf, machine, free space, or other environmental classes.

Point-wise segmentation preserves precise geometry, while voxel segmentation enables efficient structured computation. Range image segmentation offers high speed, and multimodal segmentation combines image semantics with 3D geometry.

Instance segmentation extends semantic segmentation by separating individual objects belonging to the same class. Two nearby people or multiple pallets can therefore be represented as distinct instances.

Panoptic 3D segmentation combines semantic regions and individual instances within one representation. Large background structures are labeled semantically, while countable objects are separated individually.

Occupancy models predict whether regions of 3D space are occupied, free, or unknown. Unlike object detection, occupancy prediction does not require every obstacle to belong to a known category.

This is important for safety because unfamiliar debris, irregular structures, and partially visible objects may still block the robot. Occupancy maps provide a direct interface for collision checking and motion planning.

Traditional occupancy grids update cell probabilities using geometric sensor models. Neural occupancy models learn to infer dense 3D structure from cameras, LiDAR, radar, or fused inputs.

Camera-only occupancy networks estimate hidden geometry from multiple views and temporal observations. They can predict occupied space even when direct depth sensing is unavailable, although geometric uncertainty must be carefully managed.

Semantic occupancy adds class information to each occupied cell. The robot can distinguish a static wall from a moving person, vegetation, vehicle, machine, or traversable floor.

Three-dimensional scene completion predicts missing geometry behind occlusions or outside sparse sensor observations. The model uses learned priors and context to estimate the likely structure of partially observed objects and rooms.

Semantic scene completion predicts both missing geometry and semantic labels. This allows a robot to reason about hidden surfaces and objects, supporting more stable mapping and planning.

Surface reconstruction converts depth maps or point clouds into continuous geometric models. Common outputs include meshes, signed distance fields, neural implicit surfaces, and volumetric maps.

Truncated Signed Distance Functions represent the distance from each voxel to the nearest surface. They are widely used in RGB-D mapping because multiple depth frames can be fused into smooth and consistent geometry.

Neural implicit models represent surfaces using learned continuous functions rather than explicit grids. They can produce detailed geometry at arbitrary resolution while using compact model parameters.

Neural radiance fields represent both scene geometry and view-dependent appearance. They are highly effective for photorealistic reconstruction, but traditional implementations are often too computationally expensive for real-time robot deployment.

More efficient radiance field and Gaussian-based methods are improving online mapping performance. These approaches may support high-quality digital twins, remote inspection, simulation, and persistent robot world models.

Six-degree-of-freedom pose estimation predicts object position and orientation. It is essential for robotic grasping, assembly, docking, inspection, and interaction with tools or equipment.

Pose models may use RGB images, depth maps, point clouds, object keypoints, or geometric templates. Accurate pose estimation requires robust correspondence between observed data and known object structure.

Model-based methods rely on CAD geometry or reference models, while category-level methods estimate pose for previously unseen objects within a known category. Category-level generalization is more flexible but generally less precise.

Scene flow estimation predicts the three-dimensional motion of points across time. It extends optical flow from the image plane into physical space and supports dynamic obstacle prediction, tracking, and motion understanding.

Temporal 3D models combine consecutive LiDAR scans, depth frames, or multi-camera observations. They use recurrent networks, temporal convolution, or transformers to model motion consistency and object trajectories.

Multi-sensor fusion improves 3D perception by combining complementary observations. Camera features provide semantic detail, LiDAR supplies accurate geometry, radar measures velocity, and IMU data support motion compensation.

Early fusion combines raw sensor data, feature-level fusion integrates intermediate representations, and decision-level fusion combines final predictions. Feature-level fusion is widely used because it balances flexibility and information preservation.

Cross-attention enables features from one sensor to selectively gather relevant information from another. Camera regions can attend to nearby LiDAR points, while BEV queries can combine image, radar, and geometry features.

Accurate calibration is essential for multimodal fusion. Intrinsic, extrinsic, and temporal calibration errors may misalign objects across sensors and produce incorrect 3D estimates.

Motion compensation is also necessary when sensors capture data at different times. LiDAR scans are accumulated over a period, while cameras capture frames nearly instantaneously. Robot movement can distort the fused scene if timing is ignored.

Training 3D perception models requires large and diverse datasets with accurate geometric annotations. Labels may include 3D boxes, point classes, instance IDs, depth maps, occupancy grids, poses, and motion trajectories.

Creating these annotations is expensive. Automated labeling, simulation, synthetic environments, weak supervision, self-supervised learning, and active learning are increasingly used to reduce cost.

Self-supervised 3D learning can exploit geometric consistency between sensors and time steps. A model may learn depth through image reconstruction, point correspondence, motion consistency, or masked point prediction.

Data augmentation includes point rotation, translation, scaling, random dropout, simulated occlusion, noise, intensity variation, weather effects, and object insertion. Augmentation improves robustness to sensor variation and field conditions.

Domain shift remains a major challenge. Models trained on one LiDAR type, camera configuration, environment, or geographic region may perform poorly when deployed elsewhere.

Domain adaptation, sensor normalization, synthetic-to-real training, fine-tuning, and continual learning help models adjust to new facilities, weather, hardware, and operational conditions.

Small and distant objects are particularly difficult because they contain very few points. Pedestrians, safety cones, cables, tools, and low obstacles may be represented by only a small number of measurements.

High-resolution sensing, temporal accumulation, multi-view fusion, image guidance, and specialized small-object features improve recognition of sparse targets.

Reflective, transparent, dark, or absorbent materials may produce missing or distorted measurements. Rain, fog, dust, snow, and direct sunlight also affect cameras and active depth sensors in different ways.

Robust systems estimate confidence and uncertainty rather than assuming every prediction is correct. Uncertain geometry can be enlarged into safety margins or trigger reduced speed, additional sensing, or operator review.

Real-time deployment requires balancing accuracy, memory use, latency, energy, and thermal limits. Large voxel grids and global attention can become expensive, especially with multiple sensors and high-resolution inputs.

Model pruning, quantization, knowledge distillation, sparse computation, token reduction, mixed precision, and optimized inference engines help reduce deployment cost.

GPUs, NPUs, and dedicated accelerators support the parallel matrix and convolution operations required by 3D models. Efficient memory transfer is often as important as computational throughput.

Evaluation metrics depend on the task. Depth uses absolute and relative error, 3D detection uses average precision and localization accuracy, segmentation uses mean Intersection over Union, and occupancy uses voxel-level IoU.

Practical evaluation must also measure end-to-end latency, robustness, confidence calibration, memory consumption, energy use, and failure behavior under difficult environmental conditions.

Three-dimensional perception models should not operate independently. Their outputs must connect with tracking, localization, mapping, planning, control, and mission management.

Object detection identifies meaningful entities, occupancy predicts collision space, semantic mapping provides persistent environmental knowledge, and scene flow predicts dynamic motion. Together they support safe and intelligent robot behavior.

Future 3D perception will increasingly combine cameras, LiDAR, radar, language, touch, and robot state in unified multimodal models. These systems will reason jointly about geometry, semantics, motion, uncertainty, and task goals.

Foundation models for three-dimensional perception will learn reusable representations from large-scale sensor datasets. They may support detection, segmentation, reconstruction, tracking, localization, and action planning within one adaptable architecture.

World models will maintain persistent three-dimensional representations that continue beyond the current sensor view. Robots will remember objects, predict future changes, and evaluate how planned actions may modify the environment.

For autonomous mobile robots, 3D perception models provide the geometric intelligence required to move safely, interact precisely, inspect reliably, and understand complex spaces. Their continued development will enable more capable, adaptive, and trustworthy robotic systems in real-world environments.

3차원 인식 모델(3D Perception Model)은 자율주행 로봇이 실제 물리 세계에서 객체의 기하학(Geometry), 위치(Position), 방향(Orientation), 그리고 공간적 관계(Spatial Relationship)를 이해할 수 있도록 한다. 2차원 비전(2D Vision)이 영상 평면(Image Plane) 위의 외형만 표현하는 것과 달리, 3차원 인식은 객체와 표면이 실제 공간 어디에 존재하는지를 추정한다.

이러한 능력은 자율주행 이동로봇(AMR, Autonomous Mobile Robot)에 필수적이다. 자율주행(Navigation), 장애물 회피(Obstacle Avoidance), 물체 조작(Manipulation), 자동 검사(Inspection), 지도 작성(Mapping), 환경과의 상호작용(Interaction)은 모두 정확한 공간 이해를 기반으로 이루어진다. 로봇은 객체가 무엇인지뿐 아니라 얼마나 떨어져 있는지, 얼마나 큰지, 이동 경로를 막고 있는지도 함께 이해해야 한다.

3차원 인식 모델은 카메라(Camera), 스테레오 카메라(Stereo Camera), RGB-D 센서(RGB-D Sensor), 라이다(LiDAR), 레이더(Radar), 또는 여러 센서를 조합한 데이터를 처리한다. 각 센서는 서로 다른 형태의 정보를 제공하며, 현대의 모델은 여러 센서를 융합하여 더욱 완전하고 신뢰성 높은 환경 표현(Environment Representation)을 생성한다.

단안 카메라(Monocular Camera)는 풍부한 색상, 질감(Texture), 의미 정보(Semantic Information)를 제공하지만 절대적인 깊이(Depth)는 직접 측정하지 못한다. 스테레오 카메라는 시차(Disparity)를 이용하여 깊이를 계산하며, RGB-D 센서는 색상과 거리 정보를 동시에 제공한다. 라이다는 매우 정확한 기하학 정보를 제공하지만 시각적 외형 정보는 상대적으로 적다.

레이더는 거리와 상대 속도(Relative Velocity)를 측정하며 비, 안개, 먼지, 저조도 환경에서도 안정적으로 동작한다. 그러나 공간 해상도는 카메라나 라이다보다 낮고 데이터도 희소하다. 이러한 이유로 여러 센서를 결합하는 센서 융합(Sensor Fusion)이 널리 사용된다.

3차원 인식은 여러 핵심 작업으로 구성된다. 대표적으로 깊이 추정(Depth Estimation), 포인트 클라우드 처리(Point Cloud Processing), 3차원 객체 검출(3D Object Detection), 3차원 의미론적 분할(3D Semantic Segmentation), 점유 공간 예측(Occupancy Prediction), 표면 복원(Surface Reconstruction), 자세 추정(Pose Estimation), 장면 흐름(Scene Flow) 추정, 의미 지도(Semantic Mapping)가 포함된다.

깊이 추정은 센서에서 환경까지의 거리를 예측하는 과정이다. 영상과 정렬된 밀집 깊이 지도(Dense Depth Map)를 생성하거나 선택된 특징에 대한 희소 깊이 값을 생성할 수 있다. 신뢰성 높은 깊이 정보는 거리 기반 추론과 안전한 로봇 이동의 핵심이다.

단안 깊이 추정(Monocular Depth Estimation)은 하나의 영상만 이용하여 장면의 기하 구조를 예측한다. 하나의 영상만으로는 절대 거리를 정확히 계산할 수 없기 때문에 원근(Perspective), 질감 변화(Texture Gradient), 객체 크기(Object Size), 음영(Shading), 가림(Occlusion), 의미 정보 등을 함께 학습한다.

딥러닝 기반 단안 깊이 모델은 라이다, 스테레오 카메라, RGB-D 센서, 합성 환경(Synthetic Environment)의 깊이 데이터를 이용하여 학습된다. 이를 통해 일반 카메라만으로도 밀집 깊이 지도를 생성할 수 있으며 센서 비용과 하드웨어 복잡도를 줄일 수 있다.

단안 깊이 추정의 가장 큰 한계는 스케일 모호성(Scale Ambiguity)이다. 상대적인 깊이는 정확하게 예측하더라도 절대 거리는 부정확할 수 있다. 실제 로봇에서는 바퀴 오도메트리(Wheel Odometry), IMU(Inertial Measurement Unit), 알려진 객체 크기, 지도 정보를 이용하여 실제 거리 스케일을 복원한다.

스테레오 깊이 모델은 서로 다른 위치에서 촬영된 좌우 카메라 영상을 이용한다. 동일한 점은 두 영상에서 서로 다른 수평 위치에 나타나며 이를 시차(Disparity)라고 한다. 시차가 클수록 가까운 객체이고, 시차가 작을수록 먼 객체이다.

기존의 스테레오 알고리즘은 사람이 설계한 대응 비용(Matching Cost)과 최적화 알고리즘을 사용하였다. 딥러닝 기반 스테레오 모델은 특징 추출, 대응점 탐색, 비용 집계(Cost Aggregation), 시차 보정을 모두 데이터로부터 직접 학습하여 복잡한 환경에서도 높은 성능을 제공한다.

스테레오 모델은 일반적으로 비용 볼륨(Cost Volume)을 구성하여 다양한 시차 후보를 비교한다. 이후 3차원 합성곱(3D Convolution)이나 트랜스포머 기반 주의(Attention)를 이용하여 가장 적절한 깊이를 선택한다.

딥러닝을 사용하더라도 카메라 기하학(Camera Geometry)은 여전히 매우 중요하다. 카메라 보정(Camera Calibration), 기준 거리(Baseline), 초점 거리(Focal Length), 영상 정렬(Rectification)은 깊이 정확도에 직접적인 영향을 미친다. 작은 보정 오차도 먼 거리에서는 큰 깊이 오차를 유발할 수 있다.

깊이 보완(Depth Completion)은 희소한 기하 정보와 밀집 RGB 영상을 결합하는 기술이다. 희소 라이다 포인트는 정확한 거리 정보를 제공하고 RGB 영상은 경계와 질감, 의미 정보를 제공한다. 모델은 이를 이용하여 정확하면서도 세밀한 깊이 지도를 생성한다.

포인트 클라우드(Point Cloud)는 3차원 환경을 표현하는 가장 일반적인 방법 가운데 하나이다. 각 포인트는 공간 좌표뿐 아니라 반사 강도(Intensity), 색상(Color), 시간(Time), 신뢰도(Confidence), 법선 벡터(Normal), 의미 정보를 포함할 수 있다. 포인트 클라우드는 규칙적인 격자 없이 실제 기하 구조를 직접 표현한다.

그러나 포인트 클라우드는 순서가 없고(Unordered), 희소하며(Sparse), 밀도가 일정하지 않다. 거리와 센서 특성에 따라 포인트 간격이 달라지므로 일반적인 영상 기반 합성곱을 직접 적용하기 어렵다.

PointNet은 순서가 없는 포인트 집합을 직접 처리할 수 있는 최초의 대표적인 딥러닝 모델이다. 각 포인트에 동일한 신경망을 적용하고 최대 풀링(Max Pooling)과 같은 대칭 함수(Symmetric Function)를 이용하여 입력 순서와 관계없는 특징 표현을 생성한다.

PointNet은 매우 단순하고 효율적이지만 국소 기하 구조(Local Geometry)를 충분히 표현하지 못하는 한계가 있다. PointNet++은 여러 공간 해상도에서 인접한 포인트를 그룹화하여 계층적인 국소 특징을 학습함으로써 이러한 문제를 개선하였다.

포인트 기반 모델(Point-Based Model)은 원시 기하 정보를 그대로 유지하며 복셀 양자화(Voxel Quantization)가 필요하지 않다. 객체 분류(Object Classification), 부분 분할(Part Segmentation), 장면 분할(Scene Segmentation), 등록(Registration), 포인트 클라우드 이해에 매우 적합하다. 그러나 이웃 탐색과 불규칙한 메모리 접근으로 인해 계산량이 증가할 수 있다.

복셀 기반 모델(Voxel-Based Model)은 3차원 공간을 규칙적인 복셀(Voxel)로 나눈다. 동일한 복셀 안의 포인트는 하나의 특징으로 집계되며, 이후 3차원 합성곱 신경망으로 처리된다.

복셀 표현은 규칙적인 구조를 가지므로 병렬 계산에 적합하며 이웃 연산도 단순하다. 그러나 실제 환경에서는 대부분의 복셀이 비어 있기 때문에 밀집 복셀은 매우 큰 메모리를 필요로 한다.

희소 합성곱 신경망(Sparse Convolutional Network)은 실제 포인트가 존재하는 복셀에서만 계산을 수행한다. 이를 통해 복셀 구조의 장점은 유지하면서 빈 공간에 대한 불필요한 계산을 크게 줄일 수 있다.

희소 복셀 모델은 라이다 분할, 3차원 객체 검출, 점유 공간 예측, 대규모 지도 작성에 널리 활용된다. 높은 효율성 덕분에 자율주행 자동차와 이동로봇에서 매우 중요한 기술로 자리 잡았다.

필러 기반 모델(Pillar-Based Model)은 지면을 수직 기둥(Pillar) 형태로 분할하여 3차원 문제를 단순화한다. 각 필러 안의 포인트를 특징으로 변환하여 2차원 특징 맵을 생성하고 이를 일반적인 2차원 CNN으로 처리한다.

PointPillars는 이러한 단순한 구조만으로도 빠른 3차원 객체 검출과 높은 정확도를 동시에 달성하였다. 수직 방향 정보를 압축해도 충분한 환경에서는 매우 효율적인 방법이다.

거리 영상(Range Image)은 라이다 포인트를 방위각(Azimuth)과 고도각(Elevation)에 따라 2차원 영상으로 투영한 표현이다. 각 픽셀에는 거리, 반사 강도 등의 정보가 저장된다.

거리 영상은 기존 CNN을 그대로 사용할 수 있다는 장점이 있다. 그러나 투영 과정에서 정보 손실이 발생하며 객체 경계에서는 왜곡과 중첩이 발생할 수 있다.

조감도(BEV, Bird\'s-Eye View) 표현은 3차원 정보를 위에서 내려다본 평면으로 투영한다. 이러한 지도는 로봇의 자율주행, 차선 이해, 자유 공간 추정, 충돌 검사를 수행하기에 매우 적합하다.

BEV 모델은 카메라, 라이다, 레이더의 특징을 하나의 공간 표현으로 통합한다. 객체는 영상 좌표가 아니라 실제 공간 위치를 기준으로 표현되므로 계획과 예측이 더욱 직관적이다.

카메라 기반 BEV 모델은 영상 특징을 기하학, 깊이 추정 또는 공간 주의를 이용하여 상단 좌표계로 변환한다. 여러 대의 카메라를 이용하면 로봇 주변을 거의 완전히 표현할 수 있다.

라이다 기반 BEV 모델은 포인트 클라우드의 기하 정보를 직접 상단 격자로 변환한다. 또한 카메라와 라이다 특징을 함께 융합하여 의미 정보와 정밀한 거리 정보를 동시에 활용할 수 있다.

3차원 객체 검출은 객체를 완전한 3차원 경계 상자로 표현한다. 일반적으로 중심 위치, 길이, 너비, 높이, 방향, 클래스, 신뢰도 점수를 함께 예측한다.

자율주행 이동로봇에서는 사람, 차량, 지게차, 팔레트, 기계, 컨테이너, 장애물, 검사 대상을 실제 거리 공간에서 인식한다. 이를 통해 충돌 분석과 경로 계획을 직접 수행할 수 있다.

3차원 객체 검출기는 포인트 기반, 복셀 기반, 필러 기반, BEV 기반, 멀티모달 기반으로 구성될 수 있다. 일부 모델은 후보 영역을 생성하여 보정하고, 다른 모델은 객체를 직접 예측한다.

2단계 3차원 검출기는 일반적으로 높은 정확도를 제공한다. 첫 번째 단계에서 후보 상자를 생성하고, 두 번째 단계에서 위치, 크기, 방향, 클래스를 정밀하게 보정한다.

1단계 3차원 검출기는 장면 특징으로부터 객체를 직접 예측한다. 일반적으로 실시간 시스템에 적합하며 계산량이 적지만 작은 객체나 먼 거리 객체에서는 성능 차이가 발생할 수 있다.

앵커 기반 3차원 검출기는 일반적인 크기와 방향을 가진 기준 상자를 사용한다. 네트워크는 이 기준 상자에 대한 보정값을 예측한다. 학습은 안정적이지만 객체 종류에 따라 세밀한 설정이 필요하다.

앵커 프리 3차원 검출기는 객체 중심, 키포인트, 경계 등을 직접 예측한다. 수작업 앵커 설계가 필요 없으며 다양한 객체 형태에 더욱 유연하게 대응할 수 있다.

트랜스포머 기반 3차원 검출기는 학습 가능한 쿼리(Query)와 주의 메커니즘을 이용하여 포인트, 복셀, 영상, BEV 특징에서 객체를 찾는다. 전역 관계 추론은 멀리 떨어진 객체 간 관계를 이해하고 중복 검출을 줄이는 데 도움이 된다.

3차원 의미론적 분할은 모든 포인트나 복셀에 의미 클래스를 부여한다. 도로, 바닥, 벽, 식생, 차량, 사람, 선반, 기계, 자유 공간 등을 구분할 수 있다.

포인트 기반 분할은 정밀한 기하 정보를 유지하며, 복셀 기반 분할은 계산 효율성이 높다. 거리 영상 기반 분할은 매우 빠르며, 멀티모달 분할은 영상 의미 정보와 3차원 기하 정보를 동시에 활용한다.

인스턴스 분할은 같은 클래스에 속한 객체를 개별적으로 분리한다. 예를 들어 여러 명의 사람이나 여러 개의 팔레트를 각각 독립적인 객체로 표현할 수 있다.

파놉틱 3차원 분할은 의미 영역과 개별 객체를 하나의 통합 표현으로 결합한다. 배경은 의미론적으로 표현하고, 개수를 셀 수 있는 객체는 각각 독립적으로 표현한다.

점유 공간 모델(Occupancy Model)은 공간이 점유(Occupied), 자유(Free), 미확인(Unknown) 상태인지를 예측한다. 객체 검출과 달리 모든 장애물이 반드시 미리 정의된 클래스로 분류될 필요는 없다.

이는 안전 측면에서 매우 중요하다. 처음 보는 장애물이나 불규칙한 구조, 부분적으로만 보이는 물체도 이동을 방해할 수 있기 때문이다. 점유 지도는 충돌 검사와 경로 계획의 핵심 입력으로 사용된다.

기존 점유 격자(Occupancy Grid)는 기하학적 센서 모델을 이용하여 확률을 업데이트하였다. 최근의 신경망 기반 점유 모델은 카메라, 라이다, 레이더 또는 융합 센서를 이용하여 밀집된 3차원 공간 구조를 직접 예측한다.

카메라 전용 점유 네트워크는 여러 시점과 시간 정보를 이용하여 보이지 않는 공간의 구조까지 추정할 수 있다. 그러나 직접적인 깊이 측정이 없기 때문에 불확실성을 함께 고려해야 한다.

의미 점유(Semantic Occupancy)는 각 점유 공간에 클래스 정보를 추가한다. 이를 통해 로봇은 벽, 사람, 차량, 기계, 식생, 주행 가능한 바닥을 서로 구별할 수 있다.

3차원 장면 완성(Scene Completion)은 가려진 영역이나 센서가 관측하지 못한 부분의 기하 구조를 예측한다. 모델은 학습된 사전 지식과 주변 문맥을 이용하여 보이지 않는 구조를 추정한다.

의미 장면 완성(Semantic Scene Completion)은 기하 구조뿐 아니라 의미 클래스도 함께 예측한다. 이를 통해 로봇은 보이지 않는 공간도 보다 안정적으로 지도에 포함시킬 수 있다.

표면 복원(Surface Reconstruction)은 깊이 지도나 포인트 클라우드를 연속적인 기하 구조로 변환하는 기술이다. 일반적으로 메시(Mesh), 부호 거리 함수(Signed Distance Field), 신경 암시적 표면(Neural Implicit Surface), 체적 지도(Volumetric Map)가 생성된다.

절단 부호 거리 함수(TSDF, Truncated Signed Distance Function)는 각 복셀에서 가장 가까운 표면까지의 거리를 표현한다. 여러 RGB-D 프레임을 부드럽고 일관된 기하 구조로 융합하는 데 널리 사용된다.

신경 암시적 모델(Neural Implicit Model)은 명시적인 격자 대신 연속적인 함수로 표면을 표현한다. 적은 파라미터만으로도 매우 높은 해상도의 기하 구조를 생성할 수 있다.

신경 복사장(NeRF, Neural Radiance Field)은 기하 구조와 시점에 따른 외형을 동시에 표현한다. 매우 사실적인 장면 복원이 가능하지만 기존 방식은 실시간 로봇 적용에는 계산량이 매우 크다.

최근에는 더욱 효율적인 복사장과 가우시안 스플래팅(Gaussian Splatting) 기반 기법이 온라인 지도 작성에 활용되고 있다. 이러한 기술은 디지털 트윈(Digital Twin), 원격 검사, 시뮬레이션, 지속적인 월드 모델 구축에 활용될 것으로 기대된다.

6자유도 자세 추정(6-DoF Pose Estimation)은 객체의 위치와 방향을 예측한다. 이는 로봇 파지(Grasping), 조립(Assembly), 도킹(Docking), 검사, 공구 사용에서 핵심적인 역할을 한다.

자세 추정 모델은 RGB 영상, 깊이 지도, 포인트 클라우드, 키포인트, CAD 모델 등을 이용한다. 정확한 자세 추정을 위해서는 관측 데이터와 객체 구조 사이의 정확한 대응이 필요하다.

모델 기반 자세 추정은 CAD 모델과 기준 형상을 이용하며, 카테고리 수준 자세 추정(Category-Level Pose Estimation)은 처음 보는 객체라도 같은 종류라면 자세를 추정할 수 있다. 후자는 유연하지만 일반적으로 정확도는 다소 낮다.

장면 흐름(Scene Flow)은 시간에 따른 3차원 포인트의 움직임을 예측한다. 이는 광학 흐름(Optical Flow)을 실제 공간으로 확장한 개념이며, 동적 장애물 예측과 추적에 활용된다.

시간 기반 3차원 모델은 연속된 라이다 스캔, 깊이 영상, 다중 카메라 데이터를 함께 처리한다. 순환 신경망(RNN), 시간 합성곱(Temporal Convolution), 트랜스포머를 이용하여 객체 이동과 시간적 일관성을 학습한다.

멀티센서 융합은 서로 다른 센서의 장점을 결합한다. 카메라는 의미 정보를 제공하고, 라이다는 정확한 기하 구조를 제공하며, 레이더는 속도를 측정하고, IMU는 움직임 보정을 지원한다.

초기 융합(Early Fusion)은 원시 데이터를 결합하고, 특징 수준 융합(Feature-Level Fusion)은 중간 특징을 통합하며, 결정 수준 융합(Decision-Level Fusion)은 최종 예측 결과를 결합한다. 특징 수준 융합이 가장 널리 사용된다.

교차 주의(Cross-Attention)는 한 센서의 특징이 다른 센서의 중요한 정보를 선택적으로 참조하도록 한다. 카메라는 가까운 라이다 포인트를 참고하고, BEV 쿼리는 영상, 레이더, 기하 정보를 함께 활용할 수 있다.

정확한 센서 보정(Calibration)은 멀티모달 융합에서 매우 중요하다. 내부 파라미터, 외부 파라미터, 시간 동기화 오차는 서로 다른 센서의 객체 위치를 어긋나게 만들어 잘못된 3차원 추정을 유발할 수 있다.

센서마다 데이터 획득 시간이 다르기 때문에 움직임 보정(Motion Compensation)도 필요하다. 라이다는 일정 시간 동안 스캔을 수행하지만 카메라는 거의 순간적으로 촬영한다. 이러한 차이를 보정하지 않으면 융합된 장면이 왜곡될 수 있다.

3차원 인식 모델 학습에는 다양한 환경에서 획득한 대규모 데이터셋과 정확한 기하학적 라벨이 필요하다. 라벨에는 3차원 경계 상자, 포인트 클래스, 인스턴스 ID, 깊이 지도, 점유 지도, 자세 정보, 이동 궤적 등이 포함된다.

이러한 라벨 제작에는 많은 비용이 든다. 자동 라벨링, 시뮬레이션, 합성 환경, 약지도 학습, 자기지도 학습(Self-Supervised Learning), 능동 학습이 비용 절감을 위해 활발히 활용되고 있다.

자기지도 3차원 학습은 센서 간 기하학적 일관성과 시간적 일관성을 이용한다. 영상 복원(Image Reconstruction), 포인트 대응(Point Correspondence), 움직임 일관성(Motion Consistency), 마스크 포인트 예측(Masked Point Prediction)을 통해 지도 없이도 표현을 학습할 수 있다.

데이터 증강(Data Augmentation)은 포인트 회전, 이동, 크기 변경, 랜덤 드롭아웃(Random Dropout), 가림, 노이즈, 반사 강도 변화, 날씨 효과, 객체 삽입 등을 포함한다. 이러한 증강은 다양한 센서 환경과 실제 운용 환경에 대한 강인성을 높여준다.

도메인 변화(Domain Shift)는 여전히 중요한 문제이다. 특정 라이다, 카메라, 환경, 국가에서 학습된 모델은 다른 환경에서는 성능이 크게 저하될 수 있다.

도메인 적응(Domain Adaptation), 센서 정규화(Sensor Normalization), 합성-실제(Synthetic-to-Real) 학습, 미세 조정(Fine-Tuning), 지속 학습(Continual Learning)은 새로운 환경에 모델을 적응시키는 대표적인 방법이다.

작고 먼 객체는 포인트 수가 매우 적기 때문에 특히 인식이 어렵다. 사람, 안전 콘, 케이블, 공구, 낮은 장애물은 극히 적은 측정값만으로 표현되는 경우가 많다.

고해상도 센서, 시간 누적(Temporal Accumulation), 다중 시점 융합, 영상 기반 보조 정보, 작은 객체 전용 특징은 희소한 객체 인식 성능을 향상시킨다.

반사율이 높은 재질, 투명한 재질, 매우 어두운 재질은 측정이 누락되거나 왜곡될 수 있다. 또한 비, 안개, 먼지, 눈, 강한 햇빛은 카메라와 능동형 깊이 센서에 서로 다른 영향을 준다.

강인한 시스템은 모든 예측을 절대적으로 신뢰하지 않고 불확실성과 신뢰도를 함께 추정한다. 불확실성이 높은 경우에는 안전 거리를 확대하거나 속도를 줄이고, 추가 센서를 사용하거나 운영자 확인을 요청할 수 있다.

실시간 배포에서는 정확도, 메모리, 지연 시간, 전력 소비, 발열을 균형 있게 고려해야 한다. 대규모 복셀 지도와 전역 주의는 특히 여러 센서와 고해상도 입력을 사용할 경우 매우 높은 계산량을 요구한다.

모델 가지치기(Model Pruning), 양자화(Quantization), 지식 증류(Knowledge Distillation), 희소 연산(Sparse Computation), 토큰 감소(Token Reduction), 혼합 정밀도(Mixed Precision), 최적화된 추론 엔진은 배포 비용을 크게 줄여준다.

GPU(Graphics Processing Unit), NPU(Neural Processing Unit), 전용 가속기는 3차원 모델의 대규모 행렬 연산과 합성곱 연산을 병렬 처리한다. 실제 시스템에서는 계산 성능뿐 아니라 메모리 전송 효율도 매우 중요하다.

평가 지표는 작업에 따라 다르다. 깊이 추정은 절대 오차와 상대 오차를 사용하고, 3차원 객체 검출은 평균 정밀도와 위치 정확도를 사용하며, 분할은 평균 IoU를 사용하고, 점유 공간은 복셀 수준 IoU를 사용한다.

실제 평가는 정확도뿐 아니라 지연 시간, 강인성, 신뢰도 보정, 메모리 사용량, 에너지 소비, 그리고 어려운 환경에서의 실패 특성까지 함께 평가해야 한다.

3차원 인식 모델은 독립적으로 동작해서는 안 된다. 객체 추적(Object Tracking), 위치 추정(Localization), 지도 작성(Mapping), 경로 계획(Planning), 제어(Control), 임무 관리(Mission Management)와 긴밀하게 연결되어야 한다.

객체 검출은 의미 있는 객체를 찾고, 점유 공간은 충돌 가능 영역을 표현하며, 의미 지도는 지속적인 환경 정보를 제공하고, 장면 흐름은 움직이는 객체를 예측한다. 이들이 함께 동작함으로써 안전하고 지능적인 로봇 행동이 가능해진다.

미래의 3차원 인식은 카메라, 라이다, 레이더, 언어(Language), 촉각(Touch), 로봇 상태 정보를 하나의 멀티모달 모델(Multimodal Model)로 통합하는 방향으로 발전할 것이다. 이러한 시스템은 기하 구조, 의미 정보, 움직임, 불확실성, 작업 목표를 동시에 추론하게 된다.

3차원 인식을 위한 파운데이션 모델(Foundation Model)은 대규모 센서 데이터셋으로부터 재사용 가능한 표현을 학습하게 된다. 하나의 적응형 모델이 객체 검출, 분할, 표면 복원, 추적, 위치 추정, 행동 계획까지 지원할 수 있을 것이다.

월드 모델(World Model)은 현재 센서가 보는 영역을 넘어 지속적인 3차원 환경 표현을 유지하게 된다. 로봇은 이전에 관찰한 객체를 기억하고, 미래의 변화를 예측하며, 자신의 행동이 환경에 미치는 영향을 미리 평가할 수 있게 된다.

자율주행 이동로봇에서 3차원 인식 모델은 안전한 이동, 정밀한 조작, 신뢰성 높은 검사, 복잡한 공간 이해를 가능하게 하는 핵심적인 기하학적 지능(Geometric Intelligence)을 제공한다. 앞으로도 이러한 기술의 발전은 실제 환경에서 더욱 지능적이고 적응력이 뛰어나며 신뢰할 수 있는 자율 로봇 시스템을 구현하는 핵심 기반이 될 것이다.

##  

## 03.6 Model Training Workflow

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

A model training workflow is the complete process used to transform raw data, engineering objectives, and computational resources into a validated machine learning model. It includes problem definition, data preparation, architecture selection, optimization, evaluation, deployment preparation, and continuous improvement.

In robotic perception, training is not simply the act of running an optimization algorithm. The workflow must ensure that the resulting model can operate accurately, efficiently, and safely under real environmental conditions. Every decision made before training influences the final system performance.

The process begins with a clear definition of the target task. A model may classify images, detect objects, segment pixels, estimate depth, predict robot motion, recognize actions, or fuse multimodal sensor data. The task determines the required data, labels, architecture, losses, and evaluation metrics.

Engineering requirements must be converted into measurable model objectives. A safety detector may prioritize recall, while an inspection model may require extremely precise localization. An embedded robot may accept slightly lower accuracy in exchange for lower latency, memory use, and power consumption.

The expected operating environment must also be defined before data collection begins. Indoor warehouses, outdoor construction sites, hospitals, roads, farms, and factories contain very different objects, lighting conditions, backgrounds, and failure modes. Training data must reflect these deployment conditions.

A practical workflow defines the input and output interfaces of the model. Inputs may include RGB images, depth maps, point clouds, radar measurements, robot state, or language instructions. Outputs may include class probabilities, bounding boxes, masks, depth values, poses, or control predictions.

Once the task is defined, data requirements can be estimated. The dataset must cover important object classes, environmental conditions, camera viewpoints, distances, motions, weather, lighting, and rare safety events. Data diversity is often more important than simply increasing the total number of samples.

Data may be collected from real robots, fixed sensors, public datasets, simulation environments, or synthetic generation tools. Combining several sources improves coverage, but differences between domains must be considered carefully. Inconsistent sensors and environments may introduce unwanted distribution shifts.

Real-world data are valuable because they capture actual noise, motion blur, reflections, occlusion, weather, human behavior, and hardware limitations. However, collecting and labeling real data can be expensive, slow, and operationally difficult, especially for rare or dangerous situations.

Simulation provides controlled access to large volumes of data. Object positions, lighting, camera parameters, weather, and sensor noise can be varied systematically. Perfect labels can be generated automatically, reducing annotation cost for detection, segmentation, depth, and pose estimation.

Synthetic data are most effective when they approximate the important characteristics of the target environment. Unrealistic textures, lighting, physics, or object distributions may cause a simulation-to-reality gap. Domain randomization and realistic rendering help reduce this problem.

Raw data must be organized using consistent file structures, naming conventions, metadata, and version control. A well-designed dataset records sensor type, timestamp, location, environmental condition, robot state, and annotation status. This organization supports reproducibility and future debugging.

Data quality inspection should occur before annotation or model training. Corrupted files, duplicated samples, missing frames, incorrect timestamps, extreme compression, sensor failures, and calibration errors can silently damage training. Automated validation tools help detect such issues early.

Duplicate and near-duplicate samples may cause data leakage between training and evaluation sets. Consecutive video frames can appear almost identical, creating misleadingly high validation accuracy. Group-based splitting should keep related sequences within the same dataset partition.

Annotation converts raw data into supervised training targets. Classification requires image labels, detection requires bounding boxes, segmentation requires masks, depth estimation requires distance maps, and 3D perception may require point labels, occupancy grids, poses, or 3D boxes.

Annotation guidelines must clearly define class meanings and boundary rules. Ambiguous categories, inconsistent object inclusion, or different interpretations among annotators create label noise. Written examples and quality checks help maintain consistent labeling across the dataset.

Small objects, partial occlusions, reflections, and uncertain boundaries require special annotation policies. The dataset should indicate whether heavily occluded objects are labeled, ignored, or assigned uncertainty. These choices directly influence model behavior during deployment.

Annotation quality can be improved through multiple review stages. One person may create the label, another may verify it, and automated tools may detect impossible boxes, overlapping masks, missing classes, or inconsistent dimensions. High-quality labels often improve performance more than additional noisy data.

Active learning can reduce annotation cost by selecting the most informative samples for labeling. Instead of labeling random data, the system identifies uncertain, diverse, rare, or representative examples. Human effort is then focused where it produces the greatest model improvement.

Weak supervision uses incomplete or approximate labels instead of fully detailed annotations. Image-level labels may guide localization, rough masks may train segmentation, and heuristic rules may create temporary labels. Although less precise, weak supervision can greatly expand dataset scale.

Semi-supervised learning combines a small labeled dataset with a larger unlabeled collection. A trained model generates pseudo-labels for unlabeled samples, and confident predictions are reused for further training. Careful filtering is necessary to prevent incorrect labels from reinforcing model errors.

The complete dataset is usually divided into training, validation, and test subsets. The training set updates model parameters, the validation set guides model selection, and the test set provides an independent final evaluation. The test set should remain untouched during development.

Splits must represent deployment conditions while preventing leakage. Different locations, recording sessions, robots, weather conditions, or time periods may be separated across subsets. A difficult test set is valuable because it reveals whether the model can generalize beyond familiar data.

Class balance must be examined before training. Common classes may dominate the dataset, while rare but safety-critical objects appear infrequently. A model trained without correction may achieve high average accuracy while failing to detect important rare events.

Oversampling, weighted losses, targeted data collection, synthetic generation, and hard-example mining can reduce class imbalance. However, excessive oversampling may cause memorization. The goal is to increase meaningful diversity rather than simply repeating identical rare examples.

Data preprocessing converts raw inputs into a consistent form required by the model. Images may be resized, normalized, color-converted, undistorted, or cropped. Point clouds may be filtered, voxelized, transformed, or motion-compensated before entering the network.

Preprocessing used during training must match preprocessing used during inference. Differences in image normalization, channel ordering, resizing method, or coordinate transforms may cause severe deployment failures even when the trained model appears correct during evaluation.

Data augmentation increases diversity by applying realistic transformations. Common image augmentations include flipping, rotation, cropping, scaling, blur, noise, color variation, brightness changes, shadows, rain, fog, occlusion, and copy-paste operations.

Three-dimensional augmentation may include point rotation, translation, scaling, random point removal, intensity change, sensor dropout, simulated occlusion, and object insertion. Augmentation should preserve correct labels while reflecting plausible real-world variation.

Excessive augmentation can reduce performance if transformed samples become unrealistic. The augmentation policy should match the robot\'s expected operating conditions. A ground robot may require horizontal rotation and lighting variation but not arbitrary upside-down images.

Model architecture selection depends on the task, data volume, hardware limits, and latency targets. CNNs offer efficient local feature extraction, transformers provide global context, and hybrid architectures combine both properties. Smaller models are often preferable for embedded robots.

Pretrained models provide a strong starting point. Weights learned from large general datasets already encode useful edges, textures, shapes, and semantic concepts. Fine-tuning these models usually requires less data and converges faster than training from random initialization.

Training from scratch may be necessary when sensor inputs differ greatly from standard datasets or when model behavior must be fully controlled. However, it requires more data, longer optimization, careful initialization, and stronger regularization.

The output head must match the target task. Classification heads predict category probabilities, detection heads predict classes and boxes, segmentation heads reconstruct pixel labels, and regression heads estimate continuous values such as depth, pose, or weight.

Loss functions convert prediction errors into numerical training objectives. Cross-entropy is common for classification, focal loss addresses difficult or imbalanced examples, and mean squared error or smooth L1 loss supports regression. Detection and segmentation often combine multiple losses.

Object detection may combine classification loss, bounding box regression loss, objectness loss, and IoU-based localization loss. Segmentation may combine cross-entropy, Dice loss, focal loss, and boundary loss. Each term must be weighted to reflect the task priorities.

Multi-task models require careful loss balancing. A shared model may perform detection, segmentation, depth estimation, and motion prediction simultaneously. If one loss dominates numerically, the network may ignore other tasks even when they are operationally important.

Optimization begins with parameter initialization and selection of an optimizer. Stochastic Gradient Descent, Adam, and AdamW are widely used. The best choice depends on model architecture, dataset size, batch size, and desired convergence behavior.

The learning rate is one of the most influential hyperparameters. A rate that is too large causes unstable updates, while a rate that is too small slows learning or traps the model in poor solutions. Learning-rate warmup often stabilizes the early phase of training.

Learning-rate schedules gradually change the update size during training. Step decay, cosine annealing, polynomial decay, and one-cycle policies are commonly used. Proper scheduling enables rapid early learning followed by stable fine adjustment.

Batch size affects optimization stability, memory use, and training speed. Large batches provide smoother gradients but require more memory and may generalize differently. Small batches introduce more noise and can improve robustness, although training may become unstable.

Gradient accumulation simulates a larger batch by combining gradients over several smaller iterations. This is useful when high-resolution images, 3D data, or large transformer models exceed available GPU memory.

Mixed-precision training uses lower-precision arithmetic for selected operations. FP16 or BF16 reduces memory consumption and accelerates compatible hardware while preserving model quality. Gradient scaling prevents small values from disappearing during reduced-precision computation.

Distributed training divides computation across multiple GPUs or machines. Data parallelism processes different mini-batches on each device, while model parallelism divides large models across devices. Communication overhead must be managed to obtain useful speed improvements.

During every training iteration, the model performs forward propagation, loss computation, backward propagation, and parameter updates. Training logs should record loss values, learning rate, gradient statistics, memory use, speed, and evaluation metrics.

Monitoring training curves helps identify problems early. A loss that does not decrease may indicate incorrect labels, unsuitable learning rates, broken preprocessing, or architectural errors. Sudden divergence may result from unstable gradients or numerical overflow.

Overfitting appears when training performance continues improving while validation performance stagnates or declines. Regularization, stronger augmentation, additional data, reduced model capacity, weight decay, dropout, and early stopping can reduce overfitting.

Underfitting occurs when both training and validation performance remain poor. The model may be too small, training may be too short, learning rates may be inappropriate, or the input data may not contain enough useful information.

Checkpointing saves model states during training. A checkpoint usually includes weights, optimizer state, learning-rate scheduler, epoch number, and random seeds. This allows interrupted training to resume and supports comparison among different development stages.

The best checkpoint should be selected using validation metrics related to the actual application. Lowest training loss is not always the correct criterion. A safety system may choose the checkpoint with the highest pedestrian recall or best calibrated uncertainty.

Hyperparameter optimization explores values such as learning rate, batch size, architecture depth, loss weights, augmentation strength, and regularization. Manual experimentation is common, but grid search, random search, Bayesian optimization, and population-based methods can improve efficiency.

Experiments must be tracked systematically. Every run should record code version, dataset version, configuration, random seed, hardware, metrics, and model artifacts. Without experiment tracking, it becomes difficult to reproduce improvements or understand performance regressions.

Validation should include both aggregate metrics and category-specific analysis. Mean Average Precision, mean Intersection over Union, accuracy, recall, precision, depth error, and pose error summarize performance, but individual class results reveal hidden weaknesses.

Confusion matrices show which classes are frequently mistaken for one another. Precision-recall curves illustrate the tradeoff between missed detections and false alarms. Threshold selection should reflect the operational cost of each error type.

Qualitative evaluation remains essential. Engineers should inspect predictions on representative images, videos, point clouds, and difficult corner cases. Visual review can reveal shifted boxes, broken masks, unstable depth, repeated false positives, or systematic failures not obvious in averages.

Evaluation should include environmental subgroups such as day, night, rain, fog, indoor, outdoor, near, far, crowded, and occluded scenes. A single average metric may hide severe weakness in one important operating condition.

Robustness testing introduces controlled corruption such as blur, noise, compression, brightness change, sensor dropout, and calibration error. These tests estimate how gracefully model performance degrades when field conditions differ from ideal training data.

Out-of-distribution testing evaluates inputs unlike the training set. Unknown objects, unusual environments, damaged sensors, and rare events may produce confident but incorrect predictions. Reliable systems must detect when the model is operating beyond its knowledge.

Confidence calibration measures whether predicted probabilities correspond to actual correctness. A model that reports ninety percent confidence should be correct approximately ninety percent of the time. Calibrated confidence supports safer thresholding and fallback decisions.

A model is not ready for deployment based only on accuracy. Latency, throughput, memory use, power consumption, thermal behavior, and model loading time must be measured on the actual target hardware.

Conversion to deployment formats may include TorchScript, ONNX, TensorRT, OpenVINO, or hardware-specific runtimes. Each conversion must be verified because unsupported operators, numerical differences, or preprocessing changes may alter predictions.

Quantization reduces weight and activation precision to formats such as FP16 or INT8. Post-training quantization is simple but may reduce accuracy. Quantization-aware training simulates low-precision behavior during optimization and usually preserves performance more effectively.

Model pruning removes unimportant weights, channels, blocks, or attention heads. Structured pruning is especially useful because it reduces actual hardware computation. Fine-tuning after pruning allows the remaining network to recover lost accuracy.

Knowledge distillation trains a smaller student model to imitate a larger teacher model. The student learns from labels, teacher probabilities, intermediate features, or attention maps. This often produces an efficient model with much of the teacher\'s capability.

Deployment validation should compare the optimized model against the original training model using identical inputs. Numerical differences, threshold changes, and output formatting must be checked before integration into the robot software stack.

System-level testing evaluates the model inside the complete perception pipeline. Sensor synchronization, preprocessing, tracking, fusion, localization, planning, and control may change how errors affect behavior. A model that performs well alone may still fail when integrated.

Simulation testing allows repeatable evaluation of dangerous or rare scenarios. Pedestrian crossings, sensor failures, blocked paths, sudden lighting changes, and emergency stops can be tested without risking people or hardware.

Field testing exposes the model to real vibration, temperature, network delay, weather, contamination, and unpredictable human behavior. Long-duration trials are necessary because many failures appear only after extended operation.

Failure cases discovered during deployment should be collected systematically. Difficult samples are reviewed, categorized, labeled, and added to the training dataset. This creates a data flywheel in which field experience continuously improves the model.

Continuous learning must be controlled carefully. Automatically updating a deployed safety model without verification may introduce regressions or catastrophic forgetting. New models should pass offline evaluation, simulation, field testing, and approval before release.

Dataset and model versioning are essential for traceability. Engineers should know which data, code, configuration, and hardware produced every deployed model. This information supports audits, rollback, debugging, and safety certification.

A model registry stores approved checkpoints together with metadata, metrics, deployment status, and compatibility information. Production systems should support rapid rollback when a new model behaves unexpectedly.

Monitoring continues after deployment. The robot can record inference latency, confidence distributions, detection frequency, sensor quality, and unusual inputs. Changes in these statistics may indicate domain shift, sensor degradation, or model failure.

Human review remains important for uncertain or high-risk cases. Remote operators may inspect low-confidence events, approve model-generated labels, or intervene when autonomous behavior becomes unsafe. Human feedback can also guide future dataset collection.

The training workflow is therefore an iterative engineering cycle rather than a single linear process. Problem definition guides data collection, data support model training, evaluation reveals weaknesses, and field experience produces new requirements and examples.

A mature workflow balances accuracy, robustness, efficiency, reproducibility, and safety. It treats data quality, validation, deployment optimization, and monitoring as equally important components rather than focusing only on neural network architecture.

For autonomous mobile robots, a disciplined model training workflow converts real-world experience into reliable perception and intelligent behavior. It enables models to learn from data, generalize to new environments, operate within hardware limits, and improve continuously without sacrificing operational safety.

모델 학습 워크플로(Model Training Workflow)는 원시 데이터(Raw Data), 엔지니어링 목표(Engineering Objective), 그리고 계산 자원(Computational Resource)을 검증된 머신러닝 모델(Machine Learning Model)로 변환하는 전체 과정이다. 여기에는 문제 정의(Problem Definition), 데이터 준비(Data Preparation), 모델 구조 선택(Architecture Selection), 최적화(Optimization), 성능 평가(Evaluation), 배포 준비(Deployment Preparation), 지속적인 개선(Continuous Improvement)이 포함된다.

로봇 인식(Robotic Perception)에서 모델 학습은 단순히 최적화 알고리즘을 실행하는 과정이 아니다. 최종 모델이 실제 환경에서 정확하고 효율적이며 안전하게 동작하도록 보장해야 한다. 학습 이전의 모든 결정은 최종 시스템 성능에 직접적인 영향을 미친다.

학습 과정은 먼저 목표 작업(Target Task)을 명확하게 정의하는 것에서 시작된다. 모델은 영상 분류(Image Classification), 객체 검출(Object Detection), 의미론적 분할(Semantic Segmentation), 깊이 추정(Depth Estimation), 로봇 움직임 예측(Motion Prediction), 행동 인식(Action Recognition), 멀티모달 센서 융합(Multimodal Sensor Fusion) 등을 수행할 수 있다. 작업의 종류에 따라 필요한 데이터, 라벨, 모델 구조, 손실 함수, 평가 지표가 결정된다.

엔지니어링 요구사항은 측정 가능한 모델 목표(Model Objective)로 변환되어야 한다. 안전 감지 시스템은 재현율(Recall)을 우선할 수 있으며, 검사 시스템은 매우 높은 위치 정확도를 요구할 수 있다. 임베디드 로봇은 메모리, 지연 시간, 소비 전력을 줄이기 위해 약간의 정확도를 희생하는 것이 더 적합할 수도 있다.

데이터 수집 이전에는 모델이 동작할 실제 운영 환경(Operating Environment)을 명확하게 정의해야 한다. 창고, 건설 현장, 병원, 도로, 농장, 공장은 서로 다른 객체, 조명, 배경, 위험 요소를 가진다. 학습 데이터는 실제 배포 환경을 충분히 반영해야 한다.

실제 워크플로는 모델의 입력(Input)과 출력(Output)을 명확하게 정의한다. 입력은 RGB 영상, 깊이 지도(Depth Map), 포인트 클라우드(Point Cloud), 레이더 데이터, 로봇 상태(Robot State), 자연어 명령(Language Instruction) 등이 될 수 있다. 출력은 클래스 확률(Class Probability), 경계 상자(Bounding Box), 마스크(Mask), 깊이 값, 자세(Pose), 제어 명령(Control Prediction) 등이 될 수 있다.

작업이 정의되면 필요한 데이터의 규모와 종류를 추정할 수 있다. 데이터셋은 주요 객체 클래스, 다양한 환경 조건, 카메라 시점(Viewpoint), 거리, 움직임, 날씨, 조명, 드문 안전 이벤트까지 충분히 포함해야 한다. 단순히 데이터 양을 늘리는 것보다 데이터의 다양성(Data Diversity)이 더욱 중요하다.

데이터는 실제 로봇, 고정형 센서, 공개 데이터셋, 시뮬레이션 환경, 합성 데이터 생성 도구를 통해 수집할 수 있다. 여러 출처를 함께 사용하는 것이 일반적이지만, 센서와 환경 차이로 인한 도메인 차이(Domain Shift)를 반드시 고려해야 한다.

실제 환경 데이터는 센서 노이즈, 모션 블러(Motion Blur), 반사(Reflection), 가림(Occlusion), 날씨, 사람의 행동, 하드웨어 한계까지 그대로 포함하므로 매우 가치가 높다. 그러나 희귀하거나 위험한 상황의 데이터는 수집과 라벨링 비용이 매우 크다.

시뮬레이션(Simulation)은 대량의 데이터를 체계적으로 생성할 수 있는 장점을 가진다. 객체 위치, 조명, 카메라 파라미터, 날씨, 센서 노이즈를 자유롭게 변경할 수 있으며, 완벽한 라벨(Ground Truth)을 자동으로 생성할 수 있다.

합성 데이터(Synthetic Data)는 실제 환경과 충분히 유사할 때 가장 효과적이다. 질감, 조명, 물리 특성, 객체 분포가 현실과 크게 다르면 시뮬레이션-실환경 차이(Sim-to-Real Gap)가 발생한다. 도메인 랜덤화(Domain Randomization)와 사실적인 렌더링(Photorealistic Rendering)은 이러한 문제를 줄이는 데 도움이 된다.

원시 데이터는 일관된 폴더 구조(File Structure), 파일 이름 규칙(Naming Convention), 메타데이터(Metadata), 버전 관리(Version Control)를 이용하여 체계적으로 관리되어야 한다. 데이터셋은 센서 종류, 시간, 위치, 환경 조건, 로봇 상태, 라벨링 상태를 함께 기록하는 것이 바람직하다.

라벨링 이전에는 반드시 데이터 품질 검사를 수행해야 한다. 손상된 파일, 중복 데이터, 누락된 프레임, 잘못된 시간 정보, 과도한 압축, 센서 오류, 보정 오류는 학습 성능을 크게 저하시킬 수 있다. 자동 검증 도구를 이용하면 이러한 문제를 조기에 발견할 수 있다.

중복 데이터와 거의 동일한 데이터는 학습 데이터와 검증 데이터 사이의 데이터 누수(Data Leakage)를 유발할 수 있다. 연속된 비디오 프레임은 거의 동일한 경우가 많으므로 같은 시퀀스는 하나의 데이터 분할(Set)에 포함시키는 것이 바람직하다.

라벨링(Annotation)은 원시 데이터를 지도학습(Supervised Learning)에 사용할 수 있는 목표 데이터로 변환하는 과정이다. 분류는 클래스 라벨, 객체 검출은 경계 상자, 분할은 픽셀 마스크, 깊이 추정은 깊이 지도, 3차원 인식은 포인트 라벨, 점유 지도, 자세, 3차원 경계 상자 등을 필요로 한다.

라벨링 규칙은 클래스의 의미와 객체 경계를 명확하게 정의해야 한다. 애매한 클래스 정의나 작업자마다 다른 기준은 라벨 노이즈(Label Noise)를 발생시킨다. 문서화된 기준과 예제는 일관성을 유지하는 데 매우 중요하다.

작은 객체, 부분적으로 가려진 객체, 반사 물체, 애매한 경계에 대해서는 별도의 라벨링 정책이 필요하다. 심하게 가려진 객체를 라벨링할지, 무시할지, 불확실한 객체로 표시할지를 미리 정의해야 한다. 이러한 결정은 실제 배포 환경에서 모델의 행동에 직접적인 영향을 미친다.

라벨 품질은 여러 단계의 검토 과정을 통해 향상시킬 수 있다. 한 명이 라벨을 생성하고 다른 사람이 검증하며, 자동 도구는 잘못된 경계 상자, 누락된 객체, 중복 마스크, 비정상적인 크기를 검사할 수 있다. 높은 품질의 라벨은 단순히 데이터 양을 늘리는 것보다 더욱 큰 성능 향상을 가져오는 경우가 많다.

능동 학습(Active Learning)은 가장 가치 있는 데이터를 우선적으로 라벨링하여 비용을 줄인다. 무작위 샘플 대신 모델이 불확실하게 예측한 데이터, 희귀 사례, 다양한 사례를 선택하여 사람의 노력을 집중시킨다.

약지도 학습(Weak Supervision)은 완전한 라벨 대신 대략적인 정보를 이용한다. 영상 수준의 라벨로 객체 위치를 추정하거나, 거친 마스크를 이용하여 분할을 학습하고, 규칙 기반 자동 생성 라벨을 활용할 수 있다. 정확도는 다소 낮지만 데이터 규모를 크게 확장할 수 있다.

반지도 학습(Semi-Supervised Learning)은 소량의 라벨 데이터와 대량의 비라벨 데이터를 함께 사용한다. 이미 학습된 모델이 비라벨 데이터에 가상 라벨(Pseudo Label)을 생성하고, 신뢰도가 높은 결과를 다시 학습에 활용한다. 잘못된 라벨이 반복적으로 강화되지 않도록 신중한 필터링이 필요하다.

전체 데이터셋은 일반적으로 학습(Training), 검증(Validation), 테스트(Test) 데이터셋으로 분할된다. 학습 데이터는 모델 파라미터를 업데이트하고, 검증 데이터는 모델 선택에 사용되며, 테스트 데이터는 최종 성능을 독립적으로 평가한다. 테스트 데이터는 개발 과정에서 사용하지 않는 것이 원칙이다.

데이터 분할은 실제 운영 환경을 반영하면서도 데이터 누수를 방지해야 한다. 서로 다른 장소, 날짜, 로봇, 날씨, 시간대가 서로 다른 데이터셋에 포함되도록 하는 것이 일반적이다. 어려운 테스트셋은 모델의 일반화 능력을 평가하는 데 매우 중요하다.

학습 전에 클래스 불균형(Class Imbalance)을 반드시 확인해야 한다. 일반적인 클래스는 매우 많이 존재하지만, 안전과 관련된 희귀 객체는 극히 적을 수 있다. 이를 보정하지 않으면 평균 정확도는 높아도 중요한 객체를 거의 검출하지 못하는 모델이 만들어질 수 있다.

오버샘플링(Oversampling), 가중 손실(Weighted Loss), 추가 데이터 수집, 합성 데이터 생성, 어려운 샘플 학습(Hard Example Mining)은 클래스 불균형을 완화할 수 있다. 그러나 동일한 데이터를 반복 사용하는 것은 과적합(Overfitting)을 유발할 수 있으므로 다양한 데이터를 확보하는 것이 더욱 중요하다.

데이터 전처리(Data Preprocessing)는 원시 데이터를 모델이 사용할 수 있는 형태로 변환하는 과정이다. 영상은 크기 변경, 정규화(Normalization), 색상 변환, 왜곡 보정, 크롭 등을 수행하고, 포인트 클라우드는 필터링, 복셀화(Voxelization), 좌표 변환, 움직임 보정을 수행할 수 있다.

학습 시 사용하는 전처리와 추론(Inference) 시 사용하는 전처리는 반드시 동일해야 한다. 정규화 방식, 채널 순서, 영상 크기 변경 방법, 좌표 변환이 다르면 학습이 정상적으로 이루어졌더라도 실제 배포에서는 심각한 오류가 발생할 수 있다.

데이터 증강(Data Augmentation)은 실제 환경의 다양한 변화를 모방하여 데이터 다양성을 높인다. 영상에서는 좌우 반전, 회전, 크롭, 크기 변경, 블러, 노이즈, 색상 변화, 밝기 변화, 그림자, 비, 안개, 가림, Copy-Paste 등이 널리 사용된다.

3차원 데이터 증강은 포인트 회전, 이동, 크기 변경, 랜덤 포인트 제거, 반사 강도 변화, 센서 드롭아웃, 가림, 객체 삽입 등을 포함한다. 모든 증강은 실제 환경에서 발생 가능한 변화를 반영하면서도 정답 라벨은 유지해야 한다.

과도한 데이터 증강은 오히려 성능을 저하시킬 수 있다. 증강 정책은 로봇의 실제 운영 환경과 일치해야 한다. 예를 들어 지상 이동로봇은 수평 회전과 조명 변화는 필요하지만 영상을 거꾸로 뒤집는 증강은 실제 환경과 맞지 않을 수 있다.

모델 구조(Model Architecture)는 작업 종류, 데이터 규모, 하드웨어 성능, 실시간 요구사항에 따라 선택된다. CNN은 국소 특징 추출에 강하고, 트랜스포머는 전역 문맥 이해에 강하며, 하이브리드 모델은 두 장점을 동시에 활용한다. 임베디드 로봇에서는 작은 모델이 더 적합한 경우가 많다.

사전학습 모델(Pretrained Model)은 매우 강력한 출발점이 된다. 대규모 데이터셋에서 학습된 가중치는 이미 에지, 질감, 형태, 일반 객체를 잘 표현하고 있기 때문에 적은 데이터로도 빠르게 높은 성능을 얻을 수 있다.

센서 종류가 기존 데이터와 크게 다르거나 모델의 동작을 완전히 제어해야 하는 경우에는 처음부터 학습(Training from Scratch)이 필요할 수 있다. 그러나 훨씬 많은 데이터와 긴 학습 시간, 적절한 초기화와 정규화가 요구된다.

출력 헤드(Output Head)는 작업에 맞게 설계되어야 한다. 분류는 클래스 확률을 출력하고, 객체 검출은 클래스와 경계 상자를 출력하며, 분할은 픽셀 단위 마스크를 생성하고, 회귀(Regression)는 깊이, 자세, 무게와 같은 연속값을 예측한다.

손실 함수(Loss Function)는 예측 오차를 학습 목표로 변환한다. 분류에는 Cross Entropy, 어려운 샘플에는 Focal Loss, 회귀에는 Mean Squared Error(MSE)와 Smooth L1 Loss가 널리 사용된다. 객체 검출과 분할은 여러 손실 함수를 함께 사용한다.

객체 검출은 분류 손실, 경계 상자 회귀 손실, 객체 존재(Objectness) 손실, IoU 기반 위치 손실을 함께 사용한다. 분할은 Cross Entropy, Dice Loss, Focal Loss, Boundary Loss 등을 함께 사용하며 각각의 가중치를 적절하게 조정해야 한다.

멀티태스크 모델(Multi-Task Model)은 여러 작업을 동시에 수행하기 때문에 손실 함수 간 균형이 중요하다. 객체 검출, 분할, 깊이 추정, 움직임 예측을 동시에 수행하는 경우 하나의 손실이 지나치게 크면 다른 작업이 제대로 학습되지 않을 수 있다.

최적화(Optimization)는 파라미터 초기화와 옵티마이저(Optimizer) 선택에서 시작된다. SGD(Stochastic Gradient Descent), Adam, AdamW가 대표적으로 사용되며, 모델 구조와 데이터 규모에 따라 적절한 방법을 선택한다.

학습률(Learning Rate)은 가장 중요한 하이퍼파라미터(Hyperparameter) 중 하나이다. 너무 크면 학습이 불안정해지고, 너무 작으면 학습 속도가 매우 느려지거나 나쁜 해에 머물 수 있다. 초기에는 워밍업(Warmup)을 사용하는 경우가 많다.

학습률 스케줄(Learning Rate Schedule)은 학습이 진행됨에 따라 학습률을 점진적으로 변경한다. Step Decay, Cosine Annealing, Polynomial Decay, One-Cycle 정책이 널리 사용되며 빠른 초기 학습과 안정적인 후반 미세 조정을 동시에 가능하게 한다.

배치 크기(Batch Size)는 최적화 안정성, 메모리 사용량, 학습 속도에 영향을 준다. 큰 배치는 안정적인 기울기를 제공하지만 메모리가 많이 필요하고, 작은 배치는 노이즈가 증가하지만 일반화 성능이 향상되는 경우도 있다.

기울기 누적(Gradient Accumulation)은 여러 작은 배치의 기울기를 합쳐 큰 배치처럼 학습하는 방법이다. 고해상도 영상, 3차원 데이터, 대형 트랜스포머 모델에서 GPU 메모리가 부족할 때 유용하게 사용된다.

혼합 정밀도 학습(Mixed Precision Training)은 일부 연산을 FP16 또는 BF16으로 수행하여 메모리 사용량을 줄이고 학습 속도를 높인다. Gradient Scaling을 함께 사용하여 수치적인 안정성을 유지한다.

분산 학습(Distributed Training)은 여러 GPU 또는 여러 컴퓨터에 계산을 분산한다. 데이터 병렬(Data Parallelism)은 서로 다른 배치를 처리하고, 모델 병렬(Model Parallelism)은 하나의 모델을 여러 장치에 나누어 저장한다.

매 반복마다 모델은 순전파(Forward Propagation), 손실 계산(Loss Computation), 역전파(Backward Propagation), 파라미터 업데이트(Parameter Update)를 수행한다. 학습 로그에는 손실, 학습률, 메모리 사용량, 처리 속도, 평가 지표를 함께 기록해야 한다.

학습 곡선(Training Curve)을 지속적으로 모니터링하면 문제를 조기에 발견할 수 있다. 손실이 감소하지 않으면 잘못된 라벨, 부적절한 학습률, 잘못된 전처리, 모델 구조 문제를 의심해야 한다. 갑작스러운 발산(Divergence)은 수치적인 불안정성 때문일 수 있다.

과적합(Overfitting)은 학습 성능은 계속 향상되지만 검증 성능이 더 이상 개선되지 않는 현상이다. 데이터 증강, 정규화(Regularization), Dropout, Weight Decay, Early Stopping 등을 통해 이를 줄일 수 있다.

과소적합(Underfitting)은 학습과 검증 모두 성능이 낮은 상태이다. 모델이 너무 작거나 학습 시간이 부족하거나 학습률이 적절하지 않거나 데이터 자체가 부족할 수 있다.

체크포인트(Checkpoint)는 학습 중간 상태를 저장하는 기능이다. 일반적으로 모델 가중치, 옵티마이저 상태, 학습률 스케줄러, Epoch, 랜덤 시드를 함께 저장하여 중단된 학습을 다시 시작할 수 있다.

최적의 체크포인트는 실제 응용 환경에 적합한 검증 지표를 이용하여 선택해야 한다. 단순히 학습 손실이 가장 낮은 모델이 항상 최선은 아니다. 안전 시스템에서는 보행자 재현율이나 불확실성 추정 성능이 더 중요할 수 있다.

하이퍼파라미터 최적화(Hyperparameter Optimization)는 학습률, 배치 크기, 모델 깊이, 손실 가중치, 데이터 증강 강도, 정규화 등을 탐색한다. Grid Search, Random Search, Bayesian Optimization, Population-Based Search 등이 널리 사용된다.

모든 실험은 체계적으로 관리되어야 한다. 코드 버전, 데이터셋 버전, 설정(Configuration), 랜덤 시드, 하드웨어, 평가 결과를 기록해야 동일한 결과를 재현하거나 성능 저하의 원인을 분석할 수 있다.

검증은 전체 평균 성능뿐 아니라 클래스별 성능도 함께 분석해야 한다. mAP, mIoU, Accuracy, Precision, Recall, 깊이 오차, 자세 오차는 전체 성능을 나타내지만 클래스별 결과는 숨겨진 약점을 발견하는 데 중요하다.

혼동 행렬(Confusion Matrix)은 서로 혼동되는 클래스를 보여준다. Precision-Recall 곡선은 검출 실패와 오검출(False Alarm) 사이의 균형을 보여준다. 임계값(Threshold)은 실제 운영 비용을 고려하여 결정해야 한다.

정성 평가(Qualitative Evaluation)는 여전히 매우 중요하다. 엔지니어는 실제 영상, 비디오, 포인트 클라우드, 어려운 사례를 직접 확인해야 한다. 평균 성능에서는 드러나지 않는 잘못된 경계 상자, 마스크 오류, 깊이 불안정성, 반복적인 오검출을 발견할 수 있다.

평가는 낮과 밤, 비와 안개, 실내와 실외, 가까운 거리와 먼 거리, 혼잡한 환경, 가려진 환경 등 다양한 조건별로 수행되어야 한다. 평균 성능만으로는 특정 환경에서의 심각한 약점을 발견하기 어렵다.

강인성 테스트(Robustness Test)는 블러, 노이즈, 압축, 밝기 변화, 센서 드롭아웃, 보정 오류 등을 인위적으로 추가하여 모델 성능이 어떻게 감소하는지를 평가한다.

분포 밖 데이터(OOD, Out-of-Distribution) 테스트는 학습하지 않은 환경이나 객체를 평가한다. 새로운 환경에서는 모델이 높은 신뢰도로 잘못된 결과를 출력할 수 있으므로 이를 탐지하는 기능이 매우 중요하다.

신뢰도 보정(Confidence Calibration)은 모델이 출력하는 확률이 실제 정확도를 반영하는지를 평가한다. 예를 들어 90%의 신뢰도를 출력했다면 실제로 약 90%의 경우에 맞아야 한다. 이는 안전한 임계값 설정과 예비 동작(Fallback)을 위해 중요하다.

모델은 정확도만 높다고 배포할 수 있는 것이 아니다. 실제 하드웨어에서 지연 시간(Latency), 처리량(Throughput), 메모리 사용량, 소비 전력, 발열, 모델 로딩 시간까지 함께 평가해야 한다.

배포를 위해 모델은 TorchScript, ONNX, TensorRT, OpenVINO와 같은 형식으로 변환될 수 있다. 변환 과정에서 지원되지 않는 연산이나 수치 차이로 인해 결과가 달라질 수 있으므로 반드시 검증해야 한다.

양자화(Quantization)는 FP16이나 INT8과 같은 저정밀 표현으로 모델을 변환한다. 학습 후 양자화(Post-Training Quantization)는 간단하지만 정확도가 감소할 수 있으며, 양자화 인식 학습(QAT, Quantization Aware Training)은 정확도를 더욱 잘 유지한다.

모델 가지치기(Model Pruning)는 중요하지 않은 가중치, 채널, 블록, Attention Head를 제거한다. 구조적 가지치기(Structured Pruning)는 실제 하드웨어 계산량도 함께 줄일 수 있다. 이후 Fine-Tuning을 수행하면 손실된 정확도를 상당 부분 회복할 수 있다.

지식 증류(Knowledge Distillation)는 큰 Teacher 모델의 지식을 작은 Student 모델에 전달하는 방법이다. Student는 정답뿐 아니라 Teacher의 확률 분포, 중간 특징, Attention Map까지 함께 학습하여 높은 성능을 유지하면서도 훨씬 가벼운 모델을 만들 수 있다.

배포 전 검증에서는 최적화된 모델과 원본 모델을 동일한 입력으로 비교해야 한다. 수치적인 차이, 출력 형식, 임계값 변화를 모두 확인한 후 로봇 시스템에 통합해야 한다.

시스템 수준 테스트(System-Level Test)는 모델을 실제 인식 파이프라인 안에서 평가한다. 센서 동기화, 전처리, 객체 추적, 센서 융합, 위치 추정, 경로 계획, 제어 과정에서 모델 오류가 어떻게 영향을 미치는지를 확인해야 한다.

시뮬레이션 테스트는 위험하거나 드문 상황을 반복적으로 평가할 수 있다. 보행자 횡단, 센서 고장, 경로 차단, 급격한 조명 변화, 비상 정지와 같은 상황을 실제 위험 없이 검증할 수 있다.

현장 테스트(Field Test)는 진동, 온도 변화, 네트워크 지연, 날씨, 렌즈 오염, 예측하기 어려운 사람의 행동까지 포함한 실제 환경에서 모델을 평가한다. 많은 문제는 장시간 운용에서만 나타난다.

현장에서 발견된 실패 사례(Failure Case)는 체계적으로 수집되어야 한다. 어려운 데이터를 다시 검토하고 라벨링하여 데이터셋에 추가함으로써 실제 운용 경험이 지속적으로 모델을 개선하는 데이터 플라이휠(Data Flywheel)을 형성한다.

지속 학습(Continual Learning)은 매우 신중하게 수행되어야 한다. 안전과 관련된 모델을 검증 없이 자동 업데이트하면 성능 저하나 망각(Catastrophic Forgetting)이 발생할 수 있다. 새로운 모델은 오프라인 평가, 시뮬레이션, 현장 시험을 모두 통과한 후 배포해야 한다.

데이터셋과 모델 버전 관리(Versioning)는 추적 가능성(Traceability)을 위해 필수적이다. 어떤 데이터, 코드, 설정, 하드웨어가 특정 모델을 생성했는지를 항상 확인할 수 있어야 감사(Audit), 롤백(Rollback), 디버깅, 안전 인증에 활용할 수 있다.

모델 레지스트리(Model Registry)는 승인된 모델과 성능, 메타데이터, 배포 상태, 호환성 정보를 함께 관리한다. 운영 시스템은 문제가 발생할 경우 이전 모델로 즉시 복귀할 수 있어야 한다.

배포 이후에도 지속적인 모니터링(Monitoring)이 필요하다. 로봇은 추론 시간, 신뢰도 분포, 객체 검출 빈도, 센서 품질, 이상 입력을 기록할 수 있다. 이러한 통계 변화는 도메인 변화, 센서 노후화, 모델 이상을 조기에 알려준다.

신뢰도가 낮거나 위험한 상황에서는 사람의 검토(Human Review)가 여전히 중요하다. 원격 운영자는 불확실한 상황을 확인하고, 모델이 생성한 라벨을 승인하거나, 위험 상황에서 직접 개입할 수 있다. 이러한 피드백은 이후 데이터 수집에도 활용된다.

따라서 모델 학습 워크플로는 한 번 수행되는 직선형 과정이 아니라 반복적으로 개선되는 엔지니어링 사이클(Engineering Cycle)이다. 문제 정의는 데이터 수집을 결정하고, 데이터는 모델 학습을 지원하며, 평가는 약점을 발견하고, 실제 운용 경험은 새로운 데이터와 요구사항을 생성한다.

성숙한 모델 학습 워크플로는 정확도뿐 아니라 강인성(Robustness), 효율성(Efficiency), 재현성(Reproducibility), 안전성(Safety)을 동시에 고려한다. 데이터 품질, 검증, 배포 최적화, 지속적인 모니터링은 신경망 구조만큼 중요한 요소이다.

자율주행 이동로봇에서는 체계적인 모델 학습 워크플로를 통해 실제 환경 경험을 신뢰성 높은 인식과 지능적인 행동으로 변환할 수 있다. 이를 통해 모델은 데이터를 지속적으로 학습하고 새로운 환경에 일반화하며, 제한된 하드웨어 자원 안에서도 안전성을 유지하면서 지속적으로 성능을 향상시킬 수 있다.

##  

## 03.7 Edge Inference Optimization

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

Edge inference optimization is the process of adapting trained artificial intelligence models so that they can operate efficiently on robots, embedded computers, mobile processors, and other resource-constrained devices. The objective is to maintain acceptable accuracy while reducing latency, memory use, energy consumption, and thermal load.

In autonomous mobile robots, edge inference allows perception and decision-making to occur directly onboard the platform. Camera images, depth data, LiDAR scans, radar measurements, and robot state information can be processed locally without depending continuously on remote servers or cloud infrastructure.

Local inference reduces communication delay and enables faster responses to obstacles, people, vehicles, and environmental changes. This is especially important for safety-critical functions such as emergency braking, collision avoidance, localization, and real-time path correction.

Edge processing also improves reliability because the robot can continue operating when wireless communication becomes unstable, unavailable, or congested. Warehouses, tunnels, underground facilities, construction sites, and remote outdoor environments frequently contain communication dead zones.

Privacy is another important advantage of edge inference. Camera and sensor data can remain inside the robot instead of being continuously transmitted to external systems. This is valuable in hospitals, factories, offices, homes, and security-sensitive industrial environments.

However, edge devices have strict resource limitations. They usually provide less computational power, memory capacity, storage, energy, and cooling capability than data-center servers. An accurate model trained on large GPUs may therefore be impractical for direct deployment on an embedded platform.

Edge inference optimization begins by defining operational requirements. Engineers must determine the target frame rate, maximum acceptable latency, expected model accuracy, memory budget, power limit, and hardware platform. These requirements guide every subsequent optimization decision.

Latency describes the time required to process one input and produce an output. For robotic perception, end-to-end latency includes sensor capture, preprocessing, model execution, postprocessing, communication, planning, and control. Optimizing only neural inference may not reduce the total reaction time sufficiently.

Throughput represents the number of inputs processed during a given period. A system may achieve high throughput by processing several inputs in parallel while still suffering from high latency for each individual frame. Real-time robotics therefore requires simultaneous consideration of latency and throughput.

Frame rate is closely related to throughput but should be evaluated together with sensor timing. Processing thirty frames per second is useful only when each result corresponds to recent sensor data. A delayed pipeline may produce high frame counts while reacting to outdated observations.

Memory usage includes model weights, intermediate activations, input buffers, output buffers, runtime libraries, and temporary workspace. Large activation maps can consume more memory than model parameters, especially in segmentation, depth estimation, transformers, and three-dimensional perception models.

Energy efficiency directly affects battery-powered robots. Continuous neural inference can consume a substantial portion of total electrical power, reducing mission duration. Efficient models extend operating time and reduce the size and cost of required batteries.

Thermal constraints are equally important. Sustained high computational load generates heat, and embedded systems may reduce clock speed to protect hardware. This thermal throttling can cause inference latency to increase after several minutes even when initial benchmark results appear satisfactory.

Optimization should therefore be performed on the actual target hardware rather than estimated only from desktop GPU performance. The same model may behave very differently on a server GPU, embedded GPU, NPU, CPU, FPGA, or integrated system-on-chip.

Hardware selection strongly influences available optimization strategies. CPUs provide flexibility and support many operators but may be inefficient for large tensor computations. GPUs offer high parallel throughput, while NPUs accelerate selected neural operations with lower power consumption.

Embedded GPUs are commonly used in robotics because they support convolution, attention, matrix multiplication, image processing, and general-purpose parallel computation. They also provide mature software ecosystems for training model conversion and inference acceleration.

Neural processing units are designed specifically for low-power artificial intelligence inference. They can provide excellent energy efficiency, but they may support only selected operator types, tensor shapes, precision formats, and model architectures.

Field-programmable gate arrays allow custom hardware pipelines to be configured for specific models and timing requirements. They offer deterministic behavior and energy efficiency but require specialized development skills and longer optimization cycles.

Model optimization begins with profiling. Profiling identifies which layers, operators, memory transfers, and preprocessing stages consume the most time. Without profiling, engineers may optimize components that contribute little to total latency.

A profiler records execution duration, device utilization, memory allocation, kernel launch overhead, and data transfer behavior. Layer-by-layer analysis often reveals that a small number of operations dominate the total inference time.

Computational complexity is frequently estimated using floating-point operations or multiply-accumulate operations. However, theoretical operation counts do not fully predict real hardware speed because memory access, parallelism, operator support, and kernel efficiency also matter.

Parameter count affects model storage but does not directly determine latency. A model with few parameters may still produce large activation maps or use inefficient operations. Conversely, a larger model with hardware-friendly layers may execute faster.

Arithmetic intensity describes the ratio between computation and memory movement. Operations with high arithmetic intensity efficiently reuse data, while memory-bound operations spend more time moving tensors than performing calculations. Edge optimization must reduce unnecessary memory traffic.

Input resolution is one of the most powerful optimization variables. Reducing image width and height can greatly decrease convolution and attention cost. However, excessive downsampling may remove small objects, narrow boundaries, text, defects, and distant pedestrians.

Resolution should therefore be selected according to the smallest important target in the deployment environment. Dynamic resolution can also be used, allowing the system to process lower resolution during normal operation and higher resolution when uncertainty increases.

Region-of-interest processing reduces computation by analyzing only relevant parts of the sensor input. A robot may ignore the sky, its own chassis, static borders, or areas outside the planned route. Dynamic cropping can focus on previously detected or predicted object locations.

Frame skipping is another simple strategy. Not every model must run on every sensor frame. Object detection may operate at a lower frequency while lightweight tracking estimates object positions between detections.

Asynchronous pipelines allow different perception modules to run at different rates. Obstacle detection, semantic segmentation, mapping, and visual place recognition may have different timing requirements. Decoupling them prevents slower modules from blocking safety-critical functions.

Model architecture selection has a greater impact than many post-training optimizations. Lightweight networks are designed from the beginning to minimize computation and memory. MobileNet, EfficientNet, ShuffleNet, and similar architectures use efficient convolutional structures.

Depthwise separable convolution divides standard convolution into depthwise spatial filtering and pointwise channel mixing. This substantially reduces operations and parameters while preserving useful feature extraction capability.

Grouped convolution processes channel subsets independently, reducing computational cost. Channel shuffle or other mixing operations are often introduced so that information can still move across groups.

Bottleneck blocks reduce channel dimensions before expensive spatial operations and restore them afterward. This limits the amount of computation performed in the most costly layers.

Inverted residual blocks expand low-dimensional features temporarily, apply efficient depthwise convolution, and project them back to a compact representation. This design is widely used in mobile vision networks.

Efficient transformer architectures reduce the cost of self-attention. Standard attention becomes expensive when token count increases because every token may interact with every other token.

Window attention limits interactions to local regions. Shifted windows allow information to propagate across neighboring regions while avoiding the full cost of global attention.

Sparse attention connects only selected token pairs. Deformable attention samples a small number of relevant positions, and linear attention uses alternative formulations to reduce scaling complexity.

Token pruning removes unimportant image patches or feature tokens during inference. Background regions and low-information areas can be discarded so that later layers focus computation on relevant objects and navigation regions.

Early-exit networks allow simple inputs to terminate processing before reaching the deepest layers. Difficult cases continue through the complete model. This adaptive computation reduces average latency while preserving capacity for complex scenes.

Dynamic neural networks change their computational path according to the input. They may activate fewer channels, blocks, tokens, or experts when the scene is simple and allocate additional resources when uncertainty or environmental complexity increases.

Model pruning removes unnecessary parameters or structures from a trained network. Unstructured pruning sets individual weights to zero, while structured pruning removes complete channels, filters, blocks, or attention heads.

Unstructured pruning can produce highly sparse models but may not improve real hardware latency unless the inference engine supports sparse computation. Storage size may decrease without a corresponding speed improvement.

Structured pruning is generally more practical for edge deployment because it changes tensor dimensions and reduces dense computation. Removing complete channels or blocks can directly decrease latency on standard accelerators.

Pruning criteria may be based on weight magnitude, activation importance, gradient sensitivity, or learned sparsity. After pruning, the model is typically fine-tuned to recover lost accuracy.

Iterative pruning gradually removes small portions of the network and retrains after each step. This is usually more stable than removing a large fraction of the model at once.

Quantization reduces the numerical precision used for weights and activations. Training commonly uses FP32, while edge inference may use FP16, BF16, INT8, or lower-precision formats.

FP16 reduces memory use and often accelerates inference on modern GPUs while causing minimal accuracy loss. It is one of the simplest optimization methods for deployment.

INT8 quantization can provide larger reductions in memory and computation. It requires scale factors and zero points that map floating-point values into integer ranges.

Post-training quantization converts a trained model without full retraining. A calibration dataset is used to measure activation ranges. This method is fast but may reduce accuracy for models sensitive to numerical precision.

Quantization-aware training simulates low-precision behavior during training. The network learns weights that remain robust after conversion, generally preserving accuracy better than post-training quantization.

Calibration data should represent actual deployment inputs. If calibration includes only bright indoor images, quantized activations may behave poorly at night or under different sensors.

Per-channel quantization assigns different scaling parameters to separate channels, improving accuracy compared with one shared scale. Per-tensor quantization is simpler but may be less precise.

Mixed-precision inference uses different numerical formats for different operators. Sensitive layers may remain in FP16 or FP32, while robust layers operate in INT8. This balances speed and accuracy.

Very low precision, such as INT4 or binary weights, can further reduce cost but often requires specialized hardware and careful retraining. These methods are most suitable when extreme efficiency is required.

Knowledge distillation transfers information from a large teacher model to a smaller student model. The student learns from ground-truth labels and from the teacher\'s predictions or internal representations.

Soft probability distributions contain information about relationships among classes. A student may learn that two object categories are visually similar even when only one is the correct label.

Feature distillation aligns intermediate feature maps between teacher and student. Attention distillation transfers important spatial or token relationships. These methods often improve small models beyond ordinary supervised training.

Self-distillation uses deeper layers or previous checkpoints of the same model as teaching signals. It can improve compact networks without maintaining a separate teacher during deployment.

Low-rank factorization approximates large weight matrices using smaller matrices. This is useful for fully connected layers, attention projections, and selected convolutional kernels.

Matrix decomposition reduces parameter count and computation when weight structures contain redundancy. The decomposed model usually requires fine-tuning to recover accuracy.

Operator fusion combines several consecutive operations into one optimized kernel. Convolution, normalization, activation, and elementwise operations can often be fused to reduce memory access and kernel launch overhead.

Batch normalization can frequently be folded into convolution weights during inference. This removes a separate runtime operation without changing the model output.

Activation fusion incorporates functions such as ReLU directly into preceding kernels. Residual addition and quantization conversion may also be fused when supported by the runtime.

Constant folding evaluates static computations during model conversion rather than at runtime. Unused branches and redundant tensor transformations can be removed through graph optimization.

Memory layout affects operator performance. Tensor formats such as channel-first or channel-last may produce different speeds depending on hardware and runtime. Unnecessary layout conversions should be avoided.

Preprocessing can become a major bottleneck if image resizing, color conversion, normalization, and tensor copying are performed inefficiently on the CPU. These operations should be profiled together with neural inference.

GPU-based preprocessing allows image operations to occur on the same device as inference. This reduces CPU load and avoids repeated transfers between system memory and device memory.

Zero-copy pipelines allow multiple modules to reference the same memory buffer without duplicating data. This is especially valuable for high-resolution cameras, multiple sensors, and video streams.

Pinned memory can accelerate transfers between CPU and GPU. However, excessive pinned allocation may reduce system performance, so buffers should be reused efficiently.

Memory pools preallocate reusable workspaces and reduce repeated allocation overhead. Dynamic memory allocation during every frame can introduce latency variation and fragmentation.

Batching improves throughput by processing several inputs together. However, it also increases latency because the system may wait for a batch to fill. Safety-critical robotic perception usually uses small batches or batch size one.

Micro-batching may be useful when several cameras produce synchronized frames. Multiple views can be processed together if the resulting latency remains acceptable.

Pipeline parallelism overlaps sensor capture, preprocessing, inference, postprocessing, and planning. While one frame is being processed by the model, another frame may be captured or decoded.

Multiple execution streams allow independent GPU tasks to run concurrently. Careful synchronization is required to prevent race conditions and excessive resource contention.

Postprocessing should also be optimized. Non-Maximum Suppression, mask resizing, point cloud filtering, coordinate transformation, and tracking can consume substantial time after neural inference.

GPU-accelerated Non-Maximum Suppression reduces detection postprocessing latency. Limiting the number of candidate boxes before suppression can further reduce cost.

Segmentation outputs may be generated at lower resolution and upsampled only when required. Navigation systems may consume compact class maps instead of full-resolution visualization masks.

Three-dimensional models often require voxelization, pillarization, neighbor search, or coordinate sorting. Efficient kernels and sparse data structures are essential for real-time point cloud inference.

Sensor synchronization and calibration transforms should be implemented with minimal copying. Repeated conversion among coordinate systems can become costly in multi-camera and LiDAR fusion pipelines.

Inference runtimes convert trained models into optimized execution graphs. ONNX provides a common interchange format, while TensorRT, OpenVINO, ONNX Runtime, and vendor-specific SDKs optimize execution for target hardware.

Model export must preserve operator behavior, preprocessing, output order, and dynamic dimensions. Unsupported layers may require replacement, decomposition, or custom plugins.

TensorRT selects optimized kernels, fuses compatible operators, and supports FP16 and INT8 execution on NVIDIA hardware. Engine building may explore several tactics before selecting the fastest implementation.

OpenVINO optimizes models for Intel CPUs, integrated GPUs, and accelerators. ONNX Runtime supports multiple execution providers and allows one model format to target different hardware environments.

Vendor-specific NPU compilers may require fixed shapes, supported operators, and calibrated quantization. Model design should consider these restrictions early rather than only after training is complete.

Custom operators can support specialized layers not provided by standard runtimes. However, they increase maintenance cost and may reduce portability across hardware platforms.

Static input shapes usually allow stronger optimization than fully dynamic shapes. When possible, deployment should use a small set of predefined resolutions instead of arbitrary dimensions.

Dynamic shapes provide flexibility but can increase engine complexity and reduce kernel optimization. Separate engines may be built for common operating modes.

Hardware-aware neural architecture search automatically explores model designs under measured latency, memory, or energy constraints. This produces architectures optimized for a specific target device rather than theoretical operation count alone.

Latency lookup tables can estimate the cost of candidate layers on actual hardware. Search algorithms then select combinations that satisfy the deployment budget.

Benchmarking must include warmup because initial runs may contain model loading, memory allocation, kernel compilation, or cache initialization. Stable measurements should be collected after the system reaches normal operating conditions.

Average latency alone is insufficient. Median, high-percentile, minimum, and maximum latency reveal timing variation. A robotic system may fail when occasional inference spikes exceed safety deadlines.

Performance should be measured under sustained operation to capture thermal throttling and competition with other processes. Short benchmarks may overestimate real field performance.

CPU, GPU, memory, storage, network, and sensor processes share platform resources. Benchmarking should therefore occur while the complete robot software stack is running.

Power consumption should be measured during representative workloads. Maximum-performance modes may achieve low latency while reducing battery life and increasing heat beyond acceptable levels.

Dynamic voltage and frequency scaling changes processor speed according to workload and temperature. Fixed performance modes improve timing consistency but may consume more energy.

Task prioritization ensures that critical functions retain computational resources. Emergency obstacle detection should not be delayed by mapping, logging, visualization, or nonessential analytics.

Real-time operating system features, thread affinity, and process priorities can reduce timing jitter. Assigning critical threads to dedicated processor cores may improve consistency.

Scheduling policies may run lightweight safety models continuously while executing heavier semantic models at lower rates. This layered approach combines fast reaction with rich environmental understanding.

Fallback models provide continued operation when the primary model becomes overloaded or hardware resources decrease. The robot may switch to a smaller network, lower resolution, or reduced task set.

Adaptive quality control changes model settings according to robot speed, battery state, temperature, scene complexity, and confidence. A stationary robot may use a slower high-accuracy model, while a moving robot prioritizes low latency.

Uncertainty can guide computation. High-confidence scenes may use lightweight processing, while uncertain observations trigger additional views, higher resolution, or a larger model.

Caching can reuse features when parts of the environment remain unchanged. Static background representations may not need to be recomputed for every frame, although dynamic regions must still be updated.

Temporal feature reuse transfers intermediate representations across video frames. This reduces repeated computation but requires motion compensation and mechanisms to avoid accumulating stale information.

Tracking reduces the need to detect every object from the beginning in every frame. A detector may run periodically while a lightweight tracker updates positions at higher frequency.

Multi-model systems should avoid redundant backbones. Shared feature extraction can support detection, segmentation, depth estimation, and tracking through separate output heads.

Multi-task learning reduces repeated computation, but task interference must be controlled. Shared layers may improve efficiency while reducing accuracy if unrelated tasks compete for representation capacity.

Deployment accuracy must be evaluated after every optimization stage. Pruning, quantization, conversion, and operator fusion may each introduce small changes that accumulate into significant behavior differences.

Layer-wise comparison helps locate where optimized outputs diverge from the original model. This is particularly useful when diagnosing quantization errors or unsupported operator replacements.

Evaluation should include not only benchmark datasets but also deployment-specific corner cases. Small objects, night scenes, sensor noise, reflective surfaces, and rare safety events may be more sensitive to optimization.

Safety thresholds may need recalibration after model conversion. Confidence distributions can shift under quantization even when overall accuracy remains similar.

Robustness should be tested under processor overload, high temperature, memory pressure, dropped frames, and sensor interruptions. The optimized system must fail safely rather than producing uncontrolled delays.

Monitoring continues after deployment. The robot can record inference latency, hardware utilization, temperature, power use, memory consumption, confidence statistics, and dropped frames.

Changes in runtime behavior may indicate thermal degradation, software conflicts, sensor resolution changes, or model input drift. Automatic alerts can identify these issues before they cause operational failures.

Edge inference optimization is therefore a system-level engineering discipline rather than a single compression technique. Model architecture, hardware, runtime, memory management, scheduling, sensor processing, and control timing must be optimized together.

The best model is not always the one with the highest offline accuracy. The most useful model is the one that satisfies safety, latency, energy, robustness, and hardware constraints while preserving sufficient perception quality.

For autonomous mobile robots, effective edge inference optimization enables advanced artificial intelligence to operate continuously inside the machine. It provides fast response, communication independence, longer battery life, predictable timing, and reliable perception in complex real-world environments.

엣지 추론 최적화(Edge Inference Optimization)는 학습된 인공지능(AI, Artificial Intelligence) 모델을 로봇, 임베디드 컴퓨터(Embedded Computer), 모바일 프로세서(Mobile Processor)와 같은 자원이 제한된 장치에서 효율적으로 실행할 수 있도록 최적화하는 과정이다. 목표는 허용 가능한 정확도를 유지하면서 지연 시간(Latency), 메모리 사용량(Memory Usage), 에너지 소비(Energy Consumption), 발열(Thermal Load)을 최소화하는 것이다.

자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서는 엣지 추론을 통해 인식(Perception)과 의사결정(Decision Making)을 로봇 내부에서 직접 수행할 수 있다. 카메라 영상, 깊이 데이터(Depth Data), 라이다(LiDAR) 스캔, 레이더(Radar) 측정값, 로봇 상태 정보를 클라우드 서버에 지속적으로 의존하지 않고 로컬에서 처리할 수 있다.

로컬 추론(Local Inference)은 통신 지연을 줄이고 장애물, 사람, 차량, 환경 변화에 더욱 빠르게 대응할 수 있도록 한다. 이는 비상 제동(Emergency Braking), 충돌 회피(Collision Avoidance), 위치 추정(Localization), 실시간 경로 수정(Path Correction)과 같은 안전 필수 기능에서 매우 중요하다.

엣지 처리(Edge Processing)는 무선 통신이 불안정하거나 끊기더라도 로봇이 계속 동작할 수 있도록 신뢰성을 향상시킨다. 창고, 터널, 지하시설, 건설 현장, 원격 야외 환경은 통신 음영 지역(Dead Zone)이 자주 발생한다.

프라이버시(Privacy) 역시 중요한 장점이다. 카메라 영상과 센서 데이터는 외부 서버로 지속적으로 전송되지 않고 로봇 내부에 유지될 수 있다. 이는 병원, 공장, 사무실, 가정, 보안이 중요한 산업 환경에서 매우 유용하다.

그러나 엣지 장치는 데이터센터 서버보다 연산 성능, 메모리 용량, 저장 공간, 전력, 냉각 능력이 제한적이다. 따라서 대형 GPU에서 학습된 고성능 모델이라도 임베디드 시스템에서는 그대로 실행하기 어려운 경우가 많다.

엣지 추론 최적화는 먼저 운영 요구사항(Operation Requirement)을 정의하는 것에서 시작한다. 목표 프레임 속도(Frame Rate), 허용 가능한 최대 지연 시간, 목표 정확도, 메모리 예산(Memory Budget), 소비 전력 한계, 목표 하드웨어를 먼저 결정해야 한다. 이후의 모든 최적화는 이러한 요구사항을 기준으로 수행된다.

지연 시간(Latency)은 하나의 입력을 처리하여 결과를 출력하기까지 걸리는 시간을 의미한다. 로봇에서는 센서 획득, 전처리(Preprocessing), 신경망 실행, 후처리(Postprocessing), 통신, 경로 계획(Planning), 제어(Control)까지 모두 포함한 종단 간 지연 시간(End-to-End Latency)을 고려해야 한다.

처리량(Throughput)은 일정 시간 동안 처리할 수 있는 입력의 개수를 의미한다. 높은 처리량을 달성하더라도 각 프레임의 지연 시간이 길다면 실시간 로봇에는 적합하지 않을 수 있다. 따라서 처리량과 지연 시간은 함께 평가해야 한다.

프레임 속도(Frame Rate)는 처리량과 밀접한 관계가 있지만 센서의 시간 정보까지 함께 고려해야 한다. 초당 30프레임을 처리하더라도 결과가 오래된 영상이라면 실제 환경 변화에 적절하게 대응할 수 없다.

메모리 사용량은 모델 가중치(Model Weight), 중간 활성화(Activation), 입력 버퍼(Input Buffer), 출력 버퍼(Output Buffer), 실행 라이브러리(Runtime Library), 임시 작업 공간(Workspace)을 모두 포함한다. 특히 분할(Segmentation), 깊이 추정, 트랜스포머(Transformer), 3차원 인식 모델은 중간 활성화 메모리가 매우 커질 수 있다.

에너지 효율(Energy Efficiency)은 배터리 기반 로봇에서 매우 중요하다. 지속적인 인공지능 추론은 전체 소비 전력의 상당 부분을 차지할 수 있으며, 효율적인 모델은 배터리 사용 시간을 늘리고 배터리 크기와 비용도 줄여준다.

발열(Thermal Constraint) 역시 중요한 요소이다. 높은 계산 부하는 많은 열을 발생시키며, 임베디드 시스템은 하드웨어를 보호하기 위해 클럭 속도를 낮추는 열 스로틀링(Thermal Throttling)을 수행할 수 있다. 따라서 초기 벤치마크는 우수하더라도 장시간 운용 시 지연 시간이 크게 증가할 수 있다.

이 때문에 최적화는 데스크톱 GPU 성능이 아니라 실제 목표 하드웨어(Target Hardware)에서 수행해야 한다. 동일한 모델도 서버 GPU, 임베디드 GPU, NPU(Neural Processing Unit), CPU, FPGA, SoC(System-on-Chip)에서 매우 다른 성능을 보일 수 있다.

하드웨어 선택은 적용 가능한 최적화 방법을 크게 결정한다. CPU는 다양한 연산을 지원하지만 대규모 텐서(Tensor) 연산에는 비효율적일 수 있다. GPU는 높은 병렬성을 제공하며, NPU는 낮은 전력으로 신경망 연산을 가속한다.

임베디드 GPU는 합성곱(Convolution), 어텐션(Attention), 행렬 곱(Matrix Multiplication), 영상 처리(Image Processing)를 효율적으로 수행할 수 있어 로봇 분야에서 널리 사용된다. 또한 학습, 모델 변환, 추론 가속을 위한 성숙한 소프트웨어 생태계를 제공한다.

NPU는 저전력 인공지능 추론을 위해 설계된 전용 프로세서이다. 에너지 효율은 매우 뛰어나지만 지원 가능한 연산자(Operator), 텐서 형태, 정밀도, 모델 구조가 제한될 수 있다.

FPGA(Field Programmable Gate Array)는 특정 모델과 시간 요구사항에 맞게 하드웨어를 직접 구성할 수 있다. 높은 에너지 효율과 결정론적(Deterministic) 동작을 제공하지만 개발 난이도가 높고 최적화 시간이 오래 걸린다.

모델 최적화는 프로파일링(Profiling)부터 시작한다. 프로파일링은 어떤 계층(Layer), 연산자, 메모리 전송, 전처리 단계가 가장 많은 시간을 소비하는지를 분석한다. 이를 수행하지 않으면 실제 병목(Bottleneck)이 아닌 부분을 최적화할 위험이 있다.

프로파일러(Profiler)는 실행 시간, 장치 사용률(Device Utilization), 메모리 사용량, 커널 실행(Kernel Launch), 데이터 전송 시간을 기록한다. 일반적으로 전체 실행 시간의 대부분은 소수의 연산에서 발생한다.

계산 복잡도는 FLOPs(Floating Point Operations)나 MAC(Multiply-Accumulate) 연산 수로 표현되는 경우가 많다. 그러나 실제 성능은 메모리 접근, 병렬 처리, 연산자 지원 여부, 커널 최적화에 크게 영향을 받는다.

모델 파라미터(Parameter) 수는 저장 공간에는 영향을 주지만 지연 시간을 직접 결정하지는 않는다. 파라미터가 적어도 중간 활성화가 크거나 비효율적인 연산을 사용하면 실행 속도가 느릴 수 있다.

산술 집약도(Arithmetic Intensity)는 계산량과 메모리 이동량의 비율을 의미한다. 메모리 이동보다 계산이 많은 연산은 효율적이며, 메모리 중심 연산은 계산보다 데이터 이동에 더 많은 시간이 소요된다. 엣지 최적화에서는 불필요한 메모리 이동을 줄이는 것이 중요하다.

입력 해상도(Input Resolution)는 가장 효과적인 최적화 요소 가운데 하나이다. 영상 크기를 줄이면 합성곱과 어텐션 연산량이 크게 감소한다. 그러나 지나친 축소는 작은 객체, 문자, 결함, 먼 거리 보행자를 인식하지 못하게 만들 수 있다.

따라서 입력 해상도는 실제 환경에서 반드시 검출해야 하는 가장 작은 객체를 기준으로 결정해야 한다. 또한 상황에 따라 해상도를 동적으로 변경(Dynamic Resolution)하는 방법도 사용할 수 있다.

관심 영역(ROI, Region of Interest) 기반 처리는 계산량을 크게 줄일 수 있다. 하늘, 로봇 자신의 차체, 고정된 화면 영역, 주행 경로 밖의 영역을 제외하고 중요한 부분만 분석할 수 있다.

프레임 건너뛰기(Frame Skipping)는 모든 센서 프레임마다 모든 모델을 실행하지 않는 방법이다. 객체 검출은 낮은 주기로 수행하고, 그 사이에는 가벼운 객체 추적(Object Tracking)으로 위치를 업데이트할 수 있다.

비동기 파이프라인(Asynchronous Pipeline)은 서로 다른 인식 모듈을 서로 다른 주기로 실행한다. 장애물 검출, 의미 분할, 지도 작성, 장소 인식은 요구되는 속도가 다르므로 이를 분리하면 느린 모듈이 안전 기능을 방해하지 않는다.

모델 구조 선택(Model Architecture Selection)은 많은 후처리 최적화보다 훨씬 큰 영향을 준다. MobileNet, EfficientNet, ShuffleNet과 같은 경량 네트워크는 처음부터 계산량과 메모리 사용을 최소화하도록 설계되어 있다.

깊이별 분리 합성곱(Depthwise Separable Convolution)은 일반 합성곱을 공간 필터링과 채널 혼합으로 분리하여 연산량과 파라미터 수를 크게 줄인다.

그룹 합성곱(Grouped Convolution)은 채널을 여러 그룹으로 나누어 독립적으로 계산한다. 이후 Channel Shuffle과 같은 기법을 사용하여 그룹 간 정보 교환을 수행한다.

병목 블록(Bottleneck Block)은 고비용 공간 연산 전에 채널 수를 줄이고 이후 다시 복원한다. 이를 통해 계산량을 크게 줄일 수 있다.

역잔차 블록(Inverted Residual Block)은 저차원 특징을 일시적으로 확장한 후 효율적인 Depthwise Convolution을 수행하고 다시 압축한다. 이는 모바일 비전 네트워크에서 널리 사용된다.

효율적인 트랜스포머(Efficient Transformer)는 Self-Attention의 계산량을 줄이기 위해 다양한 구조를 사용한다. 일반적인 Self-Attention은 토큰(Token) 수가 증가할수록 계산량이 급격히 증가한다.

윈도우 어텐션(Window Attention)은 지역 영역 안에서만 Attention을 수행한다. Shifted Window를 함께 사용하면 전체 계산량을 크게 증가시키지 않으면서 영역 간 정보 전달이 가능하다.

희소 어텐션(Sparse Attention)은 일부 토큰만 연결하고, Deformable Attention은 중요한 위치만 선택적으로 참조하며, Linear Attention은 계산 복잡도를 줄이는 새로운 수식을 사용한다.

토큰 가지치기(Token Pruning)는 중요하지 않은 영상 패치(Patch)나 토큰을 제거한다. 배경 영역은 제거하고 중요한 객체와 주행 영역에만 계산을 집중할 수 있다.

조기 종료(Early Exit) 네트워크는 쉬운 입력에서는 중간 계층에서 추론을 종료하고, 어려운 입력만 마지막 계층까지 계산한다. 이를 통해 평균 지연 시간을 줄이면서 복잡한 장면에서는 충분한 성능을 유지한다.

동적 신경망(Dynamic Neural Network)은 입력에 따라 활성화되는 채널, 블록, 토큰, 전문가(Expert)를 변경한다. 단순한 장면에서는 적은 계산을 수행하고 복잡한 장면에서는 더 많은 계산을 수행한다.

모델 가지치기(Model Pruning)는 불필요한 파라미터와 구조를 제거하는 기술이다. 비구조적 가지치기(Unstructured Pruning)는 개별 가중치를 제거하고, 구조적 가지치기(Structured Pruning)는 채널, 필터, 블록, Attention Head 전체를 제거한다.

비구조적 가지치기는 높은 희소성(Sparsity)을 얻을 수 있지만, 하드웨어가 희소 연산을 지원하지 않으면 실제 속도 향상은 거의 없다.

구조적 가지치기는 텐서 크기를 줄이므로 대부분의 하드웨어에서 실제 계산량과 지연 시간을 감소시킨다. 따라서 엣지 환경에서는 구조적 가지치기가 더욱 실용적이다.

가지치기 기준은 가중치 크기(Weight Magnitude), 활성화 중요도, 기울기 민감도(Gradient Sensitivity), 학습된 희소성 등을 사용할 수 있다. 이후 Fine-Tuning을 수행하여 손실된 정확도를 회복한다.

반복 가지치기(Iterative Pruning)는 한 번에 많은 구조를 제거하지 않고 조금씩 제거한 후 재학습을 반복한다. 일반적으로 더 안정적인 성능을 얻을 수 있다.

양자화(Quantization)는 가중치와 활성화 값을 낮은 정밀도로 표현하는 방법이다. 학습은 일반적으로 FP32를 사용하지만, 추론에서는 FP16, BF16, INT8, 또는 그 이하의 정밀도를 사용할 수 있다.

FP16은 메모리 사용량을 줄이고 최신 GPU에서 추론 속도를 높이며 정확도 손실도 거의 없다. 가장 간단하면서 효과적인 최적화 방법 중 하나이다.

INT8 양자화는 메모리와 계산량을 더욱 크게 줄일 수 있다. 이를 위해 Scale과 Zero Point를 이용하여 실수값을 정수 범위로 변환한다.

학습 후 양자화(Post-Training Quantization)는 재학습 없이 모델을 변환한다. 보정 데이터셋(Calibration Dataset)을 이용하여 활성화 범위를 측정한다. 간단하지만 정밀도에 민감한 모델은 정확도가 감소할 수 있다.

양자화 인식 학습(QAT, Quantization Aware Training)은 학습 중부터 저정밀 연산을 모사한다. 따라서 변환 이후에도 정확도가 더욱 잘 유지된다.

보정 데이터는 실제 운영 환경을 대표해야 한다. 밝은 실내 영상만으로 보정하면 야간이나 다른 센서 환경에서는 양자화 성능이 크게 저하될 수 있다.

채널별 양자화(Per-Channel Quantization)는 채널마다 다른 스케일을 사용하여 정확도를 높인다. 반면 텐서별 양자화(Per-Tensor Quantization)는 단순하지만 정확도가 다소 낮을 수 있다.

혼합 정밀도 추론(Mixed-Precision Inference)은 계층마다 서로 다른 정밀도를 사용한다. 중요한 계층은 FP16이나 FP32를 유지하고, 나머지는 INT8을 사용하여 정확도와 속도를 동시에 확보한다.

INT4나 이진(Binary) 가중치와 같은 초저정밀 방식은 더욱 높은 효율을 제공하지만 전용 하드웨어와 추가적인 재학습이 필요하다.

지식 증류(Knowledge Distillation)는 큰 Teacher 모델의 지식을 작은 Student 모델에 전달한다. Student는 정답뿐 아니라 Teacher의 출력과 내부 표현까지 함께 학습한다.

Soft Probability는 클래스 간의 관계를 포함한다. Student는 정답뿐 아니라 서로 비슷한 클래스 관계까지 학습하여 일반화 능력을 향상시킬 수 있다.

특징 증류(Feature Distillation)는 중간 특징 맵을 맞추고, Attention Distillation은 중요한 공간 또는 토큰 관계를 전달한다. 이러한 방법은 작은 모델의 성능을 크게 향상시킨다.

자기 증류(Self-Distillation)는 동일한 모델의 이전 버전이나 깊은 계층을 Teacher로 활용한다. 별도의 Teacher 모델 없이도 성능을 향상시킬 수 있다.

저랭크 분해(Low-Rank Factorization)는 큰 행렬을 여러 개의 작은 행렬로 분해하여 계산량을 줄인다. 완전 연결 계층(Fully Connected Layer), Attention Projection, 일부 합성곱 계층에서 많이 사용된다.

행렬 분해(Matrix Decomposition)는 중복된 가중치 구조를 이용하여 계산량과 파라미터 수를 줄인다. 이후 Fine-Tuning을 수행하여 성능을 회복한다.

연산자 융합(Operator Fusion)은 여러 연속된 연산을 하나의 최적화된 커널(Kernel)로 결합한다. 합성곱, 정규화(Normalization), 활성화 함수(Activation), Elementwise 연산을 하나로 통합할 수 있다.

Batch Normalization은 추론 시 합성곱 가중치에 미리 통합(Folding)할 수 있다. 별도의 연산 없이 동일한 결과를 얻을 수 있다.

ReLU와 같은 활성화 함수도 이전 연산에 함께 포함시킬 수 있다. Residual Addition이나 양자화 변환도 런타임이 지원하면 함께 융합할 수 있다.

상수 접기(Constant Folding)는 변환 과정에서 미리 계산 가능한 연산을 제거한다. 사용되지 않는 그래프와 불필요한 텐서 변환도 함께 제거할 수 있다.

메모리 레이아웃(Memory Layout)은 연산 성능에 큰 영향을 준다. Channel First와 Channel Last는 하드웨어에 따라 서로 다른 속도를 보일 수 있으므로 불필요한 변환을 최소화해야 한다.

전처리도 병목이 될 수 있다. 영상 크기 변경, 색상 변환, 정규화, 텐서 복사를 CPU에서 비효율적으로 수행하면 신경망보다 전처리가 더 많은 시간을 사용할 수도 있다.

GPU 기반 전처리(GPU Preprocessing)는 영상 처리와 추론을 같은 장치에서 수행하여 CPU 부하와 메모리 복사를 줄여준다.

Zero-Copy Pipeline은 여러 모듈이 동일한 메모리 버퍼를 공유하도록 하여 데이터 복사를 제거한다. 특히 고해상도 카메라와 다중 센서 환경에서 매우 효과적이다.

Pinned Memory는 CPU와 GPU 사이의 데이터 전송 속도를 향상시킨다. 그러나 과도하게 사용하면 전체 시스템 성능이 저하될 수 있으므로 버퍼를 효율적으로 재사용해야 한다.

메모리 풀(Memory Pool)은 반복적인 메모리 할당을 방지하기 위해 작업 공간을 미리 확보해 둔다. 프레임마다 메모리를 새로 할당하면 지연 시간 변동과 메모리 단편화(Fragmentation)가 발생할 수 있다.

배치 처리(Batching)는 여러 입력을 동시에 처리하여 처리량을 향상시킨다. 그러나 배치가 채워질 때까지 기다려야 하므로 지연 시간이 증가한다. 안전이 중요한 로봇은 일반적으로 Batch Size 1 또는 매우 작은 배치를 사용한다.

마이크로 배치(Micro-Batching)는 여러 카메라가 동시에 영상을 생성하는 경우 유용하다. 허용 가능한 지연 시간 안에서 여러 시점을 함께 처리할 수 있다.

파이프라인 병렬화(Pipeline Parallelism)는 센서 획득, 전처리, 추론, 후처리, 계획을 동시에 수행한다. 하나의 프레임이 추론되는 동안 다음 프레임은 이미 획득될 수 있다.

다중 실행 스트림(Multiple Execution Stream)은 GPU에서 여러 작업을 동시에 수행하도록 한다. 그러나 자원 경쟁과 동기화 문제를 신중하게 관리해야 한다.

후처리(Postprocessing)도 최적화 대상이다. NMS(Non-Maximum Suppression), 마스크 크기 변경, 포인트 클라우드 필터링, 좌표 변환, 객체 추적 역시 많은 시간을 사용할 수 있다.

GPU 기반 NMS는 후처리 시간을 크게 줄여준다. 또한 NMS 이전에 후보 객체 수를 줄이면 계산량을 더욱 감소시킬 수 있다.

분할 결과는 낮은 해상도로 생성한 후 필요한 경우에만 업샘플링(Upsampling)할 수 있다. 자율주행은 전체 해상도의 마스크보다 축소된 클래스 맵만으로도 충분한 경우가 많다.

3차원 모델은 복셀화(Voxelization), 필러화(Pillarization), 이웃 탐색(Neighbor Search), 좌표 정렬(Coordinate Sorting)이 필요하다. 희소 자료구조(Sparse Data Structure)와 효율적인 커널이 실시간 성능에 필수적이다.

센서 동기화와 좌표 변환도 불필요한 메모리 복사를 최소화해야 한다. 다중 카메라와 라이다 융합에서는 반복적인 좌표 변환이 병목이 될 수 있다.

추론 런타임(Inference Runtime)은 학습된 모델을 최적화된 실행 그래프로 변환한다. ONNX는 공통 교환 형식이며 TensorRT, OpenVINO, ONNX Runtime은 각각 목표 하드웨어에 맞게 실행을 최적화한다.

모델 변환 과정에서는 연산자 동작, 전처리, 출력 순서, 동적 크기를 정확하게 유지해야 한다. 지원되지 않는 연산은 대체하거나 사용자 정의 플러그인(Custom Plugin)으로 구현해야 한다.

TensorRT는 NVIDIA GPU에서 최적화된 커널을 선택하고 연산자 융합, FP16, INT8 실행을 지원한다. 엔진 생성 과정에서 다양한 최적화 방법을 시험한 후 가장 빠른 방식을 선택한다.

OpenVINO는 Intel CPU와 GPU에 최적화되어 있으며, ONNX Runtime은 다양한 실행 백엔드(Execution Provider)를 지원하여 여러 하드웨어에서 동일한 모델을 사용할 수 있다.

NPU 전용 컴파일러는 고정된 입력 크기, 지원 가능한 연산자, 양자화 조건 등을 요구하는 경우가 많다. 따라서 모델 설계 단계부터 이러한 제약을 고려해야 한다.

사용자 정의 연산자(Custom Operator)는 표준 런타임에서 지원하지 않는 기능을 구현할 수 있지만 유지보수 비용이 증가하고 이식성(Portability)이 떨어질 수 있다.

고정 입력 크기(Static Shape)는 동적 입력(Dynamic Shape)보다 더욱 강력한 최적화를 가능하게 한다. 가능한 경우 제한된 해상도를 사용하는 것이 유리하다.

동적 입력은 유연성을 제공하지만 실행 엔진이 복잡해지고 최적화 수준이 낮아질 수 있다. 일반적으로 자주 사용하는 해상도별로 별도의 엔진을 생성한다.

하드웨어 인식 신경망 구조 탐색(Hardware-Aware NAS)은 실제 하드웨어의 지연 시간, 메모리, 전력 소비를 고려하여 최적의 모델 구조를 자동으로 탐색한다.

지연 시간 조회표(Latency Lookup Table)는 실제 하드웨어에서 각 계층의 실행 시간을 미리 측정하여 탐색 과정에서 활용한다.

벤치마크(Benchmark)는 반드시 워밍업(Warmup) 이후에 수행해야 한다. 초기 실행에는 모델 로딩, 메모리 할당, 커널 생성, 캐시 초기화가 포함될 수 있기 때문이다.

평균 지연 시간만으로는 충분하지 않다. 중앙값(Median), 최대값(Maximum), 최소값(Minimum), 상위 백분위(Percentile)를 함께 확인해야 간헐적인 지연 스파이크를 발견할 수 있다.

벤치마크는 장시간 실행 상태에서 수행해야 한다. 열 스로틀링과 다른 프로세스의 영향은 짧은 테스트에서는 나타나지 않을 수 있다.

CPU, GPU, 메모리, 저장장치, 네트워크, 센서 프로세스는 모두 같은 시스템 자원을 공유한다. 따라서 실제 로봇 소프트웨어 전체가 실행되는 상태에서 성능을 측정해야 한다.

소비 전력도 실제 운용 환경에서 측정해야 한다. 최고 성능 모드는 매우 빠르지만 배터리 사용 시간을 크게 줄이고 발열을 증가시킬 수 있다.

DVFS(Dynamic Voltage and Frequency Scaling)는 부하와 온도에 따라 클럭 속도를 자동으로 변경한다. 고정 성능 모드는 지연 시간을 일정하게 유지하지만 소비 전력은 증가한다.

작업 우선순위(Task Prioritization)는 중요한 기능이 항상 충분한 계산 자원을 확보하도록 한다. 비상 장애물 검출은 지도 작성, 시각화, 로그 기록보다 우선되어야 한다.

실시간 운영체제(RTOS, Real-Time Operating System), 스레드 우선순위(Thread Priority), CPU Affinity는 실행 시간 변동(Jitter)을 줄여준다. 중요한 스레드를 특정 CPU 코어에 고정하는 방법도 자주 사용된다.

경량 안전 모델은 높은 주기로 실행하고, 복잡한 의미 인식 모델은 낮은 주기로 실행하는 계층형 스케줄링(Hierarchical Scheduling)이 자주 사용된다.

대체 모델(Fallback Model)은 주 모델이 과부하 상태일 때 사용된다. 작은 모델, 낮은 해상도, 일부 기능만 수행하는 모드로 전환하여 안전성을 유지할 수 있다.

적응형 품질 제어(Adaptive Quality Control)는 로봇 속도, 배터리 상태, 온도, 장면 복잡도, 신뢰도에 따라 모델 설정을 변경한다. 정지 상태에서는 높은 정확도 모델을 사용하고, 고속 이동 중에는 저지연 모델을 사용할 수 있다.

불확실성(Uncertainty) 역시 계산량 제어에 활용될 수 있다. 신뢰도가 높은 장면은 간단한 모델을 사용하고, 신뢰도가 낮은 경우에는 고해상도 입력이나 대형 모델을 사용한다.

캐싱(Caching)은 변화하지 않는 환경 정보를 재사용한다. 정적인 배경은 매 프레임 다시 계산할 필요가 없으며, 변화하는 영역만 업데이트하면 된다.

시간적 특징 재사용(Temporal Feature Reuse)은 이전 프레임의 특징을 다음 프레임에서 재사용하여 계산량을 줄인다. 그러나 움직임 보정과 오래된 정보 제거가 반드시 필요하다.

객체 추적(Object Tracking)은 모든 프레임에서 객체 검출을 다시 수행할 필요를 줄여준다. 검출은 일정 주기로만 수행하고 그 사이에는 추적기가 객체 위치를 업데이트한다.

멀티모델 시스템은 공통 백본(Shared Backbone)을 사용하여 객체 검출, 분할, 깊이 추정, 추적을 동시에 수행할 수 있다. 이를 통해 중복 계산을 크게 줄일 수 있다.

멀티태스크 학습(Multi-Task Learning)은 계산량을 줄일 수 있지만 서로 다른 작업이 하나의 표현을 공유하면서 성능이 감소하는 간섭(Task Interference)이 발생할 수 있다.

배포 정확도는 모든 최적화 단계 이후 다시 평가해야 한다. 가지치기, 양자화, 모델 변환, 연산자 융합은 각각 작은 차이를 만들지만 누적되면 실제 동작에 큰 영향을 줄 수 있다.

계층별 비교(Layer-wise Comparison)는 원본 모델과 최적화 모델의 출력이 처음 달라지는 위치를 찾아내는 데 유용하다. 이는 양자화 오류나 연산자 교체 문제를 분석할 때 특히 중요하다.

평가는 공개 벤치마크뿐 아니라 실제 배포 환경의 어려운 사례도 반드시 포함해야 한다. 작은 객체, 야간 환경, 센서 노이즈, 반사 표면, 드문 안전 이벤트는 최적화에 더욱 민감하다.

모델 변환 이후에는 신뢰도 분포가 달라질 수 있으므로 안전 임계값도 다시 보정해야 한다. 전체 정확도는 비슷하더라도 Confidence Calibration은 달라질 수 있다.

강인성은 CPU 과부하, 고온, 메모리 부족, 프레임 손실, 센서 장애에서도 평가해야 한다. 최적화된 시스템은 이러한 상황에서도 안전하게 동작하거나 안전하게 실패(Fail Safe)해야 한다.

배포 이후에도 지속적인 모니터링(Monitoring)이 필요하다. 로봇은 추론 시간, 하드웨어 사용률, 온도, 소비 전력, 메모리 사용량, 신뢰도, 프레임 손실을 지속적으로 기록할 수 있다.

이러한 실행 정보의 변화는 열 문제, 소프트웨어 충돌, 센서 변경, 입력 데이터 변화 등을 조기에 발견하는 데 도움이 된다. 자동 경고 시스템은 실제 장애가 발생하기 전에 문제를 알려줄 수 있다.

엣지 추론 최적화는 단순한 모델 압축 기술이 아니라 전체 시스템 수준(System-Level)의 엔지니어링 분야이다. 모델 구조, 하드웨어, 런타임(Runtime), 메모리 관리, 작업 스케줄링, 센서 처리, 제어 타이밍을 함께 최적화해야 한다.

가장 좋은 모델은 오프라인 정확도가 가장 높은 모델이 아니다. 실제 하드웨어에서 안전성, 지연 시간, 소비 전력, 강인성, 메모리 제약을 만족하면서도 충분한 인식 성능을 유지하는 모델이 가장 우수한 모델이다.

자율주행 이동로봇에서 효과적인 엣지 추론 최적화는 고성능 인공지능을 로봇 내부에서 지속적으로 실행할 수 있도록 한다. 이를 통해 빠른 응답 속도, 통신 독립성, 긴 배터리 사용 시간, 예측 가능한 실행 시간, 복잡한 실제 환경에서의 신뢰성 높은 인식을 동시에 달성할 수 있다.

##  

## 03.8 Perception Model Validation

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

Perception model validation is the systematic process of determining whether a trained model is accurate, reliable, efficient, and safe enough for deployment in a real robotic system. It verifies not only average benchmark performance but also behavior under difficult, uncertain, and unexpected operating conditions.

For autonomous mobile robots, validation is essential because perception outputs directly influence navigation, obstacle avoidance, localization, manipulation, inspection, and mission execution. A model that performs well in laboratory tests may still fail when exposed to vibration, weather, lighting changes, occlusion, or unfamiliar objects.

Validation begins by confirming that the model requirements are clearly defined. Engineers must determine the expected accuracy, recall, precision, latency, memory use, power consumption, robustness, and safety behavior. These requirements should be measurable and connected to the intended robotic task.

A pedestrian detector may require very high recall because missing a person creates a severe safety risk. An inspection model may prioritize precise localization and low false-positive rates. A navigation segmentation model may focus on stable free-space boundaries rather than exact classification of every background object.

The validation plan should identify the model inputs and outputs. Inputs may include RGB images, depth maps, LiDAR point clouds, radar measurements, thermal images, audio, or fused sensor features. Outputs may include classes, bounding boxes, masks, depth, poses, tracks, occupancy grids, or confidence scores.

The first stage of validation checks the integrity of the evaluation dataset. Corrupted files, incorrect labels, duplicated samples, missing sensor data, or inconsistent calibration may produce misleading results. Dataset quality must be verified before model metrics can be trusted.

The evaluation dataset should represent the target deployment environment. It must include expected objects, camera viewpoints, distances, lighting, weather, surfaces, motion patterns, and operational scenarios. A model cannot be validated reliably using data unrelated to its intended environment.

Validation data should be independent from the training data. If near-duplicate images, adjacent video frames, or recordings from the same sequence appear in both sets, the reported performance may be unrealistically high. Group-based splitting reduces this type of leakage.

A dedicated test set should remain untouched during model development. The validation set may be used for model selection and threshold tuning, while the test set should provide the final unbiased estimate of performance after design decisions are complete.

The dataset should also contain difficult examples. Small objects, partial occlusion, motion blur, unusual viewpoints, reflective materials, transparent barriers, crowded scenes, and low-contrast targets often reveal weaknesses that average samples do not show.

Rare safety-critical events deserve special attention. Fallen people, sudden pedestrian entry, low obstacles, emergency vehicles, fire, smoke, damaged barriers, or unexpected machinery may appear infrequently but have a large operational impact.

Scenario-based validation groups data according to meaningful operating conditions. Day and night, indoor and outdoor, near and far distance, dry and wet surfaces, static and moving robot states, and clear and obstructed scenes should be evaluated separately.

Aggregate performance may hide severe weakness in one subgroup. A detector with high overall accuracy may fail almost completely at night or in rain. Subgroup analysis reveals whether the model is dependable across the complete operational design domain.

Classification models are commonly evaluated using accuracy, precision, recall, F1 score, confusion matrices, and class-specific error rates. Accuracy alone is insufficient when the dataset is imbalanced or when different error types have different consequences.

Precision measures how many positive predictions are correct. High precision is important when false alarms are costly, such as unnecessary emergency stops, incorrect inspection failures, or repeated operator alerts.

Recall measures how many real positive cases are successfully detected. High recall is crucial in safety applications because missed pedestrians, obstacles, defects, or hazards may produce dangerous outcomes.

The F1 score combines precision and recall into one value. It is useful when both false positives and false negatives matter, but it still does not express the exact operational cost of each error type.

A confusion matrix shows which classes are frequently mistaken for one another. It may reveal that pallets are confused with boxes, workers with mannequins, or wet surfaces with obstacles. Such patterns guide data collection and model improvement.

Object detection is usually evaluated using Intersection over Union, Average Precision, and mean Average Precision. Intersection over Union measures the overlap between a predicted bounding box and its corresponding ground-truth box.

A detection is considered correct when its overlap exceeds a selected threshold and the predicted class is correct. Higher thresholds require more accurate localization, while lower thresholds emphasize basic object discovery.

Average Precision summarizes the precision-recall curve for one class. Mean Average Precision combines results across multiple classes and often across several overlap thresholds.

Metrics should also be reported by object size and distance. Small or distant objects usually receive fewer pixels or LiDAR points and are more difficult to detect. Separate evaluation prevents large nearby objects from dominating the result.

False-positive analysis should identify repeated background patterns that trigger incorrect detections. Shadows, reflections, signs, machine parts, floor markings, or vegetation may be mistaken for target objects.

False-negative analysis should focus on objects missed under difficult conditions. Common causes include occlusion, low resolution, blur, poor lighting, unusual pose, class imbalance, or inaccurate labels.

Semantic segmentation models are commonly evaluated using pixel accuracy, class accuracy, Intersection over Union, mean Intersection over Union, Dice score, and boundary metrics.

Pixel accuracy can be misleading when large background classes dominate the image. A model may classify most floor pixels correctly while completely missing small but important objects.

Mean Intersection over Union gives equal importance to each semantic class and is therefore more informative for imbalanced datasets. However, it does not directly measure the quality of thin structures or boundaries.

Boundary F1 score evaluates how accurately predicted edges align with ground-truth boundaries. This is especially important for navigation because shifted obstacle boundaries may reduce free space or create unsafe paths.

Instance segmentation combines detection and mask evaluation. Models are assessed using mask Average Precision, object recall, class accuracy, and instance separation quality.

Closely spaced objects may be merged into one mask, while one object may be divided into several fragments. These errors should be analyzed separately because they affect manipulation, counting, and tracking.

Panoptic segmentation is commonly evaluated using Panoptic Quality, which combines recognition quality and segmentation quality. It measures both whether the correct instances are found and how accurately their masks are represented.

Depth estimation requires metrics such as absolute error, relative error, root mean squared error, and threshold accuracy. Evaluation should consider both near and far ranges because depth uncertainty often increases with distance.

A model may produce visually smooth depth maps while containing large metric errors. For robotic navigation and manipulation, absolute distance accuracy is more important than appearance alone.

Depth validation should also examine discontinuities around object boundaries. Blurred depth edges may cause obstacles to appear larger or smaller than they really are, affecting path planning and grasping.

Three-dimensional object detection is evaluated using 3D overlap, bird\'s-eye-view overlap, center distance, orientation error, and class-specific Average Precision.

A prediction may appear correct in the camera image but contain a large depth or orientation error in physical space. Therefore, 2D visualization alone is insufficient for validating 3D models.

Point cloud segmentation uses point-level accuracy and mean Intersection over Union. Performance should be analyzed across range, point density, elevation, object size, and sensor coverage.

Occupancy prediction is evaluated by comparing occupied, free, and unknown cells. Voxel-level Intersection over Union, precision, recall, and free-space error provide useful measures.

For navigation, false-free predictions are particularly dangerous. If an occupied region is predicted as free, the robot may attempt to drive through an obstacle. Validation should therefore report asymmetric safety-related errors.

Pose estimation may be evaluated using translation error, rotation error, keypoint distance, and average distance between transformed model points. The appropriate metric depends on object symmetry and task tolerance.

Tracking validation considers identity consistency over time. Metrics may include identity switches, track fragmentation, missed tracks, false tracks, trajectory error, and association accuracy.

A tracker can maintain high detection accuracy while frequently changing object IDs. Such behavior is problematic for motion prediction, human monitoring, and long-term interaction.

Temporal stability should be evaluated even for models that are not explicitly trackers. Frame-to-frame fluctuations in detection boxes, masks, depth, or confidence may create unstable planning and control behavior.

Prediction consistency can be measured across consecutive frames. A static object should not repeatedly appear and disappear or change class without a meaningful reason.

Confidence scores must also be validated. A well-calibrated model should assign high confidence to predictions that are usually correct and low confidence to uncertain or difficult cases.

Calibration metrics include Expected Calibration Error, reliability diagrams, negative log-likelihood, and Brier score. These tools measure whether predicted probabilities reflect actual correctness.

An overconfident model is dangerous because it may produce incorrect outputs without signaling uncertainty. An underconfident model may generate too many unnecessary fallback actions or operator alerts.

Threshold selection should be based on operational consequences rather than default values. The optimal confidence threshold may differ by class, environment, robot speed, or safety mode.

For safety-critical classes, lower thresholds may improve recall, while secondary classes may use higher thresholds to reduce false alarms. Class-specific threshold tuning is often more effective than one global threshold.

Robustness validation measures performance under controlled input degradation. Images may be modified with blur, noise, compression, brightness change, contrast loss, color shift, rain, fog, snow, or partial occlusion.

Sensor-specific corruption should also be tested. LiDAR may experience missing points, motion distortion, reflective dropout, or reduced range. Radar may contain ghost targets, multipath reflections, or sparse returns.

Robustness testing should evaluate gradual degradation rather than only one severe corruption level. This reveals how quickly performance declines as environmental quality worsens.

A reliable model should degrade gracefully. Small changes in lighting or noise should not produce sudden catastrophic changes in output.

Out-of-distribution validation tests data that differ from the training distribution. New object types, unfamiliar facilities, different countries, new camera hardware, or unusual weather may all create distribution shift.

The objective is not always to classify unknown inputs correctly. It may be more important for the model to recognize that the input is unfamiliar and reduce confidence.

Out-of-distribution detection can use confidence thresholds, feature distances, energy scores, ensembles, or dedicated uncertainty models. These methods must themselves be validated because they may also fail.

Open-set validation includes known and unknown classes in the evaluation. The model should correctly recognize known objects while avoiding confident misclassification of unfamiliar ones.

Adversarial and naturally confusing conditions should be tested. Repetitive patterns, camouflage, strong reflections, unusual shadows, damaged signs, and unexpected object arrangements may exploit model weaknesses.

Although deliberate adversarial attacks may be rare in many robot applications, naturally occurring adversarial examples are common in complex environments.

Domain shift validation compares performance across facilities, cameras, seasons, weather, or geographic regions. A model trained in one warehouse may behave differently in another warehouse with different shelves, floors, and lighting.

Cross-domain evaluation helps determine whether fine-tuning or domain adaptation is required. It also reveals which visual or geometric properties the model relies on most strongly.

Simulation can support validation by generating rare, dangerous, or precisely controlled scenarios. Sensor failures, pedestrian crossings, falling objects, blocked routes, or extreme lighting can be repeated consistently.

However, simulation results should not replace real-world validation. The physical world contains noise, hardware interactions, and human behavior that may not be represented accurately in a simulator.

Hardware-in-the-loop testing connects the real perception hardware and software to a simulated environment. This verifies model execution timing, interfaces, and system behavior without exposing a physical robot to all risks.

Software-in-the-loop testing evaluates the perception and decision software in a virtual environment. It is useful for rapid regression testing and large scenario coverage.

Model validation must include inference performance on the actual target device. Desktop GPU benchmarks do not reliably predict performance on embedded GPUs, CPUs, NPUs, or edge computers.

Latency should be measured from input availability to output completion. Average latency, median latency, maximum latency, and high-percentile latency should all be recorded.

Occasional latency spikes may violate safety deadlines even when average performance is acceptable. Real-time systems therefore require analysis of timing variation and worst-case behavior.

Throughput and frame rate should be measured together with pipeline freshness. Processing many frames is not useful when outputs are delayed or queued behind old data.

Memory usage should include model weights, activations, buffers, runtime workspace, and neighboring software processes. Out-of-memory conditions may appear only when the full robot stack is operating.

Power and temperature should be measured during sustained inference. Short tests may hide thermal throttling that occurs after several minutes of continuous operation.

Validation should be repeated under different performance modes, clock settings, battery states, and environmental temperatures. Field conditions may reduce hardware capability compared with laboratory measurements.

Optimized deployment models must be compared with their original training versions. Quantization, pruning, model conversion, operator replacement, or runtime optimization may alter outputs.

Layer-level comparison can identify where divergence begins. This is useful when an INT8 model loses accuracy or when exported ONNX and TensorRT models produce different results.

Post-training quantization should be validated using representative calibration data. Poor calibration may distort activation ranges and reduce performance under conditions not included in the calibration set.

Pruned models should be tested for class-specific degradation. Removing channels may affect rare or small objects more strongly than common large objects.

Knowledge-distilled models should be evaluated independently rather than assumed to inherit the teacher\'s reliability. A student may reproduce average accuracy while losing robustness or calibration.

System-level validation connects the model to preprocessing, tracking, fusion, mapping, planning, and control. Many failures arise from interactions among modules rather than from the neural network alone.

A correct detector may still produce unsafe behavior if coordinate transforms are wrong, timestamps are misaligned, or tracking introduces delayed positions.

Sensor synchronization must be validated with moving objects. Small timestamp errors can cause camera, LiDAR, radar, and odometry measurements to describe different physical states.

Calibration validation should confirm intrinsic, extrinsic, and temporal alignment. Small geometric errors may produce large fusion errors at long distances.

End-to-end scenario testing evaluates whether the robot behaves correctly, not merely whether the perception metric is high. The system should detect hazards, slow down, stop, replan, or request assistance appropriately.

Failure injection deliberately introduces sensor loss, delayed frames, corrupted data, overheating, memory pressure, or communication failure. The system should respond safely rather than continuing with invalid inputs.

Fallback behavior must be validated. The robot may switch to a secondary sensor, lower speed, simplified model, remote control, or safe stop when perception quality decreases.

Human-machine interaction should also be tested. Operators must understand alerts, confidence indicators, and failure messages. Ambiguous interfaces can convert a manageable model failure into an operational problem.

Long-duration field testing is essential because some failures appear only after hours or days. Lens contamination, calibration drift, temperature changes, memory leaks, and environmental changes accumulate over time.

Field trials should cover different seasons, times of day, traffic levels, and operational workloads. A short demonstration cannot represent the complete deployment environment.

Failure cases discovered during testing should be stored with sensor data, model outputs, environmental context, and system state. This creates a structured failure database for future improvement.

Each failure should be categorized by source. Possible categories include data limitation, label error, model weakness, calibration issue, synchronization issue, hardware overload, sensor failure, or software integration error.

Root-cause analysis prevents repeated trial-and-error changes. Retraining the model will not solve a failure caused by incorrect coordinate transformation or delayed timestamps.

Regression testing ensures that improvements do not break previously working behavior. Every new model should be evaluated on a fixed suite of representative and safety-critical scenarios.

The regression suite should include common cases, difficult cases, and known historical failures. New failure examples should be added continuously.

Model comparison should use consistent datasets, thresholds, preprocessing, and hardware settings. Otherwise, apparent improvement may result from changed evaluation conditions rather than a better model.

Statistical significance should be considered when performance differences are small. Results may vary due to random initialization, data sampling, or limited test size.

Confidence intervals and repeated runs provide a more reliable comparison than one metric value. This is especially important for rare-event evaluation where sample counts are small.

Safety validation may require hazard analysis and traceability. Each perception requirement should connect to a test, metric, result, and acceptance criterion.

Acceptance criteria should be defined before final evaluation. Changing criteria after observing results may produce biased decisions and hide important weaknesses.

A model may be accepted only when it satisfies all critical conditions rather than one average score. Required conditions may include minimum recall, maximum latency, acceptable calibration, and safe fallback behavior.

Documentation is a central part of validation. The dataset version, model version, code version, hardware, runtime, thresholds, metrics, and known limitations should all be recorded.

A model card can summarize intended use, training data, evaluation results, operating limits, ethical considerations, and known failure modes. This supports responsible deployment and maintenance.

Validation reports should clearly separate measured facts from assumptions. They should explain what was tested, what was not tested, and where uncertainty remains.

Model validation continues after deployment. Runtime monitoring can track confidence distributions, detection frequency, latency, temperature, dropped frames, and sensor health.

Changes in these statistics may indicate domain drift, sensor degradation, environmental change, or software conflicts. Automatic alerts support early intervention.

Field data can be sampled for periodic review. Low-confidence events, unexpected detections, and operator interventions are especially valuable for identifying emerging failure patterns.

Continuous validation does not mean automatic uncontrolled retraining. Updated models should still pass offline evaluation, simulation, regression testing, field validation, and approval before release.

Model and dataset versioning enable rollback when a new release performs poorly. Every deployed model should be traceable to its training data, configuration, and validation evidence.

A model registry can store approved models, metrics, hardware compatibility, deployment history, and status. This supports controlled release management across multiple robots.

Perception model validation is therefore a lifecycle process rather than a one-time benchmark. It begins during requirement definition and continues through training, optimization, deployment, monitoring, and future model updates.

A strong validation strategy combines quantitative metrics, qualitative review, subgroup analysis, robustness testing, system integration, long-duration trials, and safe fallback verification.

For autonomous mobile robots, rigorous perception validation converts model performance into operational confidence. It ensures that perception is not only accurate in ideal datasets but also dependable, timely, and safe in the diverse conditions of the real physical world.

인식 모델 검증(Perception Model Validation)은 학습된 모델이 실제 로봇 시스템에 배포될 만큼 정확하고, 신뢰할 수 있으며, 효율적이고, 안전한지를 체계적으로 판단하는 과정이다. 이는 평균적인 벤치마크 성능뿐 아니라 어렵고 불확실하며 예상하지 못한 운용 조건에서의 행동까지 검증한다.

자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서 검증은 매우 중요하다. 인식 결과가 자율주행(Navigation), 장애물 회피(Obstacle Avoidance), 위치 추정(Localization), 물체 조작(Manipulation), 자동 검사(Inspection), 임무 실행(Mission Execution)에 직접적인 영향을 미치기 때문이다. 실험실에서 높은 성능을 보인 모델도 진동, 날씨, 조명 변화, 가림(Occlusion), 처음 보는 객체에 노출되면 실패할 수 있다.

검증은 먼저 모델 요구사항(Model Requirement)이 명확하게 정의되어 있는지를 확인하는 것에서 시작된다. 엔지니어는 목표 정확도, 재현율(Recall), 정밀도(Precision), 지연 시간(Latency), 메모리 사용량, 소비 전력, 강인성(Robustness), 안전 동작(Safety Behavior)을 결정해야 한다. 이러한 요구사항은 측정 가능해야 하며 실제 로봇 작업과 직접 연결되어야 한다.

보행자 검출기(Pedestrian Detector)는 사람을 놓치는 것이 심각한 안전 위험을 만들기 때문에 매우 높은 재현율이 필요할 수 있다. 검사 모델은 정밀한 위치 추정과 낮은 거짓 양성(False Positive)을 우선할 수 있다. 주행용 분할 모델은 모든 배경 객체의 완벽한 분류보다 자유 공간(Free Space) 경계의 안정성을 더 중요하게 평가할 수 있다.

검증 계획(Validation Plan)은 모델의 입력과 출력을 명확하게 정의해야 한다. 입력은 RGB 영상, 깊이 지도(Depth Map), 라이다 포인트 클라우드(LiDAR Point Cloud), 레이더 측정값, 열화상(Thermal Image), 오디오(Audio), 융합 센서 특징(Fused Sensor Feature) 등이 될 수 있다. 출력은 클래스, 경계 상자(Bounding Box), 마스크(Mask), 깊이, 자세(Pose), 추적 결과(Track), 점유 격자(Occupancy Grid), 신뢰도 점수(Confidence Score) 등이 될 수 있다.

검증의 첫 번째 단계는 평가 데이터셋(Evaluation Dataset)의 무결성을 확인하는 것이다. 손상된 파일, 잘못된 라벨, 중복 샘플, 누락된 센서 데이터, 일관되지 않은 보정 정보는 잘못된 결과를 만들 수 있다. 데이터셋 품질이 검증되지 않으면 모델 성능 지표도 신뢰할 수 없다.

평가 데이터셋은 실제 배포 환경을 충분히 대표해야 한다. 예상되는 객체, 카메라 시점(Viewpoint), 거리, 조명, 날씨, 표면, 움직임 패턴, 운용 시나리오를 포함해야 한다. 실제 환경과 관련이 없는 데이터만으로는 모델을 신뢰성 있게 검증할 수 없다.

검증 데이터는 학습 데이터와 독립적이어야 한다. 거의 동일한 영상, 인접한 비디오 프레임, 같은 시퀀스에서 얻은 데이터가 학습과 검증 데이터에 동시에 포함되면 성능이 비현실적으로 높게 나타날 수 있다. 그룹 기반 분할(Group-Based Split)은 이러한 데이터 누수(Data Leakage)를 줄여준다.

전용 테스트셋(Test Set)은 모델 개발 과정에서 사용하지 않고 최종 평가까지 유지하는 것이 바람직하다. 검증셋(Validation Set)은 모델 선택과 임계값 조정에 사용할 수 있지만, 테스트셋은 모든 설계 결정이 끝난 뒤 편향 없는 최종 성능을 제공해야 한다.

데이터셋에는 어려운 사례(Difficult Example)도 포함되어야 한다. 작은 객체, 부분 가림, 모션 블러(Motion Blur), 특이한 시점, 반사 물질, 투명 장벽, 혼잡한 장면, 낮은 대비 객체는 일반적인 데이터에서 드러나지 않는 약점을 보여준다.

희귀하지만 안전과 관련된 사건(Rare Safety-Critical Event)은 별도로 검증해야 한다. 쓰러진 사람, 갑작스러운 보행자 진입, 낮은 장애물, 긴급 차량, 화재, 연기, 파손된 장벽, 예상하지 못한 기계는 빈도는 낮지만 운용에 미치는 영향이 매우 크다.

시나리오 기반 검증(Scenario-Based Validation)은 의미 있는 운용 조건에 따라 데이터를 구분한다. 주간과 야간, 실내와 실외, 가까운 거리와 먼 거리, 건조한 표면과 젖은 표면, 정지 상태와 이동 상태, 가림이 없는 장면과 가려진 장면을 별도로 평가해야 한다.

전체 평균 성능은 특정 하위 조건에서의 심각한 약점을 감출 수 있다. 전체 정확도가 높은 검출기도 야간이나 비가 오는 상황에서는 거의 동작하지 않을 수 있다. 하위 그룹 분석(Subgroup Analysis)은 모델이 전체 운용 설계 영역(Operational Design Domain)에서 신뢰할 수 있는지를 보여준다.

분류 모델(Classification Model)은 일반적으로 정확도(Accuracy), 정밀도, 재현율, F1 점수(F1 Score), 혼동 행렬(Confusion Matrix), 클래스별 오류율로 평가한다. 데이터가 불균형하거나 오류 종류마다 영향이 다를 경우 정확도만으로는 충분하지 않다.

정밀도는 모델이 양성으로 예측한 결과 가운데 실제로 올바른 비율을 의미한다. 불필요한 비상 정지, 잘못된 검사 불량 판정, 반복적인 운영자 경보와 같이 거짓 경보가 비용을 발생시키는 경우 높은 정밀도가 중요하다.

재현율은 실제 양성 사례 가운데 모델이 성공적으로 검출한 비율을 의미한다. 보행자, 장애물, 결함, 위험 상황을 놓치면 안전 문제가 발생할 수 있으므로 안전 응용에서는 높은 재현율이 매우 중요하다.

F1 점수는 정밀도와 재현율을 하나의 값으로 결합한다. 거짓 양성과 거짓 음성(False Negative)이 모두 중요한 경우 유용하지만, 각각의 오류가 실제 운용에 미치는 비용을 직접 표현하지는 못한다.

혼동 행렬은 어떤 클래스들이 서로 자주 잘못 분류되는지를 보여준다. 예를 들어 팔레트(Pallet)와 박스(Box), 작업자와 마네킹(Mannequin), 젖은 바닥과 장애물이 혼동될 수 있다. 이러한 패턴은 추가 데이터 수집과 모델 개선 방향을 제시한다.

객체 검출(Object Detection)은 일반적으로 교집합 대비 합집합(IoU, Intersection over Union), 평균 정밀도(AP, Average Precision), 평균 평균 정밀도(mAP, Mean Average Precision)를 사용하여 평가한다. IoU는 예측 경계 상자와 실제 경계 상자의 겹침 정도를 측정한다.

예측 클래스가 올바르고 IoU가 선택된 임계값을 초과하면 올바른 검출로 판단한다. 높은 IoU 임계값은 더 정확한 위치 추정을 요구하고, 낮은 임계값은 객체 존재 여부 자체를 더욱 중요하게 평가한다.

평균 정밀도는 하나의 클래스에 대한 정밀도-재현율 곡선(Precision-Recall Curve)을 요약한다. mAP는 여러 클래스와 여러 IoU 임계값에 대한 결과를 종합한다.

객체 크기와 거리별 성능도 별도로 보고해야 한다. 작거나 먼 객체는 영상 픽셀 수나 라이다 포인트 수가 적어 검출이 더 어렵다. 이를 분리하지 않으면 가까운 대형 객체가 전체 결과를 지나치게 높게 만들 수 있다.

거짓 양성 분석(False-Positive Analysis)은 반복적으로 잘못 검출되는 배경 패턴을 찾아야 한다. 그림자, 반사, 표지판, 기계 부품, 바닥 표시, 식생 등이 목표 객체로 잘못 인식될 수 있다.

거짓 음성 분석(False-Negative Analysis)은 어려운 환경에서 놓친 객체를 중심으로 수행해야 한다. 일반적인 원인에는 가림, 낮은 해상도, 블러, 부족한 조명, 특이한 자세, 클래스 불균형, 잘못된 라벨이 포함된다.

의미론적 분할(Semantic Segmentation)은 픽셀 정확도(Pixel Accuracy), 클래스 정확도(Class Accuracy), IoU, 평균 IoU(mIoU), 다이스 점수(Dice Score), 경계 지표(Boundary Metric)를 사용하여 평가한다.

픽셀 정확도는 큰 배경 클래스가 영상 대부분을 차지하는 경우 잘못된 인상을 줄 수 있다. 예를 들어 바닥은 대부분 정확히 분류하면서도 작은 안전 객체를 완전히 놓칠 수 있다.

평균 IoU는 각 클래스를 동일하게 고려하므로 불균형한 데이터셋에서 더욱 유용하다. 그러나 얇은 구조나 경계의 품질을 직접적으로 충분히 나타내지는 못한다.

경계 F1 점수(Boundary F1 Score)는 예측 경계가 실제 경계와 얼마나 정확하게 일치하는지를 평가한다. 이는 장애물 경계가 이동하면 자유 공간이 감소하거나 위험한 경로가 생성될 수 있는 주행 시스템에서 특히 중요하다.

인스턴스 분할(Instance Segmentation)은 객체 검출과 마스크 평가를 함께 수행한다. 마스크 평균 정밀도(Mask AP), 객체 재현율, 클래스 정확도, 인스턴스 분리 품질을 평가할 수 있다.

서로 가까운 객체가 하나의 마스크로 합쳐지거나, 하나의 객체가 여러 조각으로 나뉠 수 있다. 이러한 오류는 물체 조작, 개수 계산, 객체 추적에 서로 다른 영향을 미치므로 구분해서 분석해야 한다.

파놉틱 분할(Panoptic Segmentation)은 일반적으로 파놉틱 품질(PQ, Panoptic Quality)을 사용하여 평가한다. 이는 올바른 객체를 찾았는지와 마스크가 얼마나 정확한지를 동시에 측정한다.

깊이 추정(Depth Estimation)은 절대 오차(Absolute Error), 상대 오차(Relative Error), 평균 제곱근 오차(RMSE, Root Mean Squared Error), 임계값 정확도(Threshold Accuracy) 등을 사용하여 평가한다. 깊이 불확실성은 거리에 따라 증가할 수 있으므로 가까운 영역과 먼 영역을 분리해서 분석해야 한다.

모델이 시각적으로 부드러운 깊이 지도를 생성하더라도 실제 거리 오차는 클 수 있다. 자율주행과 물체 조작에서는 외형보다 절대적인 거리 정확도가 더욱 중요하다.

깊이 검증에서는 객체 경계 주변의 불연속성도 확인해야 한다. 깊이 경계가 흐려지면 장애물이 실제보다 크거나 작게 보일 수 있어 경로 계획과 파지(Grasping)에 영향을 준다.

3차원 객체 검출(3D Object Detection)은 3차원 IoU, 조감도(BEV, Bird\'s-Eye View) IoU, 중심 거리, 방향 오차(Orientation Error), 클래스별 AP로 평가할 수 있다.

예측이 카메라 영상에서는 정확해 보여도 실제 공간에서는 깊이 또는 방향 오차가 클 수 있다. 따라서 2차원 시각화만으로는 3차원 모델을 충분히 검증할 수 없다.

포인트 클라우드 분할(Point Cloud Segmentation)은 포인트 수준 정확도와 평균 IoU를 사용한다. 거리, 포인트 밀도, 높이, 객체 크기, 센서 커버리지에 따른 성능도 함께 분석해야 한다.

점유 공간 예측(Occupancy Prediction)은 점유, 자유, 미확인 셀을 실제 값과 비교하여 평가한다. 복셀 수준 IoU, 정밀도, 재현율, 자유 공간 오류(Free-Space Error)를 사용할 수 있다.

주행에서는 점유된 공간을 자유 공간으로 잘못 예측하는 거짓 자유(False-Free) 오류가 특히 위험하다. 로봇이 실제 장애물로 이동할 수 있기 때문에 비대칭적인 안전 오류를 별도로 보고해야 한다.

자세 추정(Pose Estimation)은 위치 이동 오차(Translation Error), 회전 오차(Rotation Error), 키포인트 거리(Keypoint Distance), 변환된 모델 포인트 사이의 평균 거리로 평가할 수 있다. 객체의 대칭성과 작업 허용 오차에 따라 적절한 지표를 선택해야 한다.

객체 추적(Tracking) 검증은 시간에 따른 ID 일관성을 평가한다. ID 전환(Identity Switch), 추적 단절(Track Fragmentation), 누락된 추적, 거짓 추적, 궤적 오차(Trajectory Error), 연관 정확도(Association Accuracy) 등이 사용된다.

검출 정확도가 높더라도 객체 ID가 반복적으로 변경되면 움직임 예측, 사람 모니터링, 장기 상호작용에 문제가 발생할 수 있다.

시간적 안정성(Temporal Stability)은 명시적인 추적 모델이 아니더라도 평가해야 한다. 프레임마다 경계 상자, 마스크, 깊이, 신뢰도가 크게 흔들리면 경로 계획과 제어도 불안정해질 수 있다.

연속된 프레임 사이의 예측 일관성을 측정할 수 있다. 정적인 객체가 이유 없이 반복적으로 나타났다 사라지거나 클래스가 변경되어서는 안 된다.

신뢰도 점수도 반드시 검증해야 한다. 잘 보정된 모델은 대부분 정확한 예측에 높은 신뢰도를 부여하고, 어렵거나 불확실한 사례에는 낮은 신뢰도를 부여해야 한다.

신뢰도 보정 지표에는 기대 보정 오차(ECE, Expected Calibration Error), 신뢰도 다이어그램(Reliability Diagram), 음의 로그 가능도(Negative Log-Likelihood), 브라이어 점수(Brier Score)가 포함된다. 이러한 도구는 예측 확률이 실제 정확도를 얼마나 잘 반영하는지를 측정한다.

과도하게 확신하는 모델(Overconfident Model)은 잘못된 결과를 출력하면서도 불확실성을 알리지 않기 때문에 위험하다. 반대로 지나치게 낮은 신뢰도를 출력하면 불필요한 예비 동작이나 운영자 경보가 반복될 수 있다.

임계값 선택(Threshold Selection)은 기본값이 아니라 실제 운용 결과를 기준으로 수행해야 한다. 최적 신뢰도 임계값은 클래스, 환경, 로봇 속도, 안전 모드에 따라 달라질 수 있다.

안전이 중요한 클래스는 낮은 임계값을 사용하여 재현율을 높이고, 부가적인 클래스는 높은 임계값으로 거짓 경보를 줄일 수 있다. 클래스별 임계값 조정이 하나의 전역 임계값보다 효과적인 경우가 많다.

강인성 검증(Robustness Validation)은 의도적으로 입력 품질을 저하시켜 성능 변화를 측정한다. 영상에 블러, 노이즈, 압축, 밝기 변화, 대비 저하, 색상 변화, 비, 안개, 눈, 부분 가림을 적용할 수 있다.

센서별 손상 조건도 검증해야 한다. 라이다는 포인트 누락, 움직임 왜곡, 반사 물질의 측정 누락, 거리 감소를 경험할 수 있다. 레이더는 유령 객체(Ghost Target), 다중 경로 반사(Multipath Reflection), 희소한 측정값을 생성할 수 있다.

강인성 테스트는 하나의 심각한 손상 수준뿐 아니라 여러 단계의 점진적인 손상을 포함해야 한다. 이를 통해 환경 품질이 낮아질 때 성능이 얼마나 빠르게 감소하는지를 알 수 있다.

신뢰성 높은 모델은 점진적으로 성능이 저하되어야 한다. 작은 조명 변화나 약한 노이즈가 갑작스러운 치명적 출력 변화로 이어져서는 안 된다.

분포 밖 데이터(OOD, Out-of-Distribution) 검증은 학습 분포와 다른 데이터를 평가한다. 새로운 객체 종류, 처음 보는 시설, 다른 국가, 새로운 카메라 하드웨어, 특이한 날씨가 모두 분포 변화(Domain Shift)를 만들 수 있다.

목표는 항상 알 수 없는 입력을 올바르게 분류하는 것이 아니다. 모델이 해당 입력이 익숙하지 않다는 사실을 인식하고 신뢰도를 낮추는 것이 더욱 중요할 수 있다.

OOD 탐지는 신뢰도 임계값, 특징 거리(Feature Distance), 에너지 점수(Energy Score), 앙상블(Ensemble), 전용 불확실성 모델을 사용할 수 있다. 이러한 탐지 방법 역시 자체 검증이 필요하다.

개방형 집합 검증(Open-Set Validation)은 알려진 클래스와 알려지지 않은 클래스를 함께 포함한다. 모델은 알려진 객체를 올바르게 인식하면서도 새로운 객체를 높은 신뢰도로 잘못 분류하지 않아야 한다.

적대적이거나 자연적으로 혼란을 주는 조건도 평가해야 한다. 반복 패턴, 위장(Camouflage), 강한 반사, 특이한 그림자, 손상된 표지판, 예상하지 못한 객체 배치는 모델의 약점을 드러낼 수 있다.

의도적인 적대적 공격(Adversarial Attack)은 일부 로봇 환경에서 드물 수 있지만, 자연적으로 발생하는 적대적 사례는 복잡한 환경에서 흔하게 나타난다.

도메인 변화 검증은 시설, 카메라, 계절, 날씨, 지역에 따른 성능 차이를 비교한다. 하나의 창고에서 학습된 모델은 선반, 바닥, 조명이 다른 창고에서 전혀 다르게 동작할 수 있다.

교차 도메인 평가(Cross-Domain Evaluation)는 추가 미세 조정(Fine-Tuning)이나 도메인 적응(Domain Adaptation)이 필요한지를 판단하게 해준다. 또한 모델이 어떤 시각적 또는 기하학적 특징에 지나치게 의존하는지도 보여준다.

시뮬레이션은 희귀하고 위험하며 정밀하게 제어된 시나리오를 생성하여 검증에 활용할 수 있다. 센서 고장, 보행자 횡단, 낙하 물체, 경로 차단, 극단적인 조명 조건을 반복적으로 재현할 수 있다.

그러나 시뮬레이션 결과가 실제 환경 검증을 대체해서는 안 된다. 실제 세계에는 시뮬레이터가 완전히 표현하지 못하는 센서 노이즈, 하드웨어 상호작용, 인간 행동이 존재한다.

하드웨어 인더루프 테스트(HIL, Hardware-in-the-Loop)는 실제 인식 하드웨어와 소프트웨어를 시뮬레이션 환경에 연결한다. 이를 통해 실제 로봇에 모든 위험을 노출하지 않고도 실행 시간, 인터페이스, 시스템 동작을 검증할 수 있다.

소프트웨어 인더루프 테스트(SIL, Software-in-the-Loop)는 가상 환경에서 인식과 의사결정 소프트웨어를 평가한다. 빠른 회귀 테스트(Regression Test)와 대규모 시나리오 평가에 유용하다.

모델 검증은 반드시 실제 목표 장치(Target Device)에서 추론 성능을 측정해야 한다. 데스크톱 GPU 성능은 임베디드 GPU, CPU, NPU, 엣지 컴퓨터의 성능을 정확히 예측하지 못한다.

지연 시간은 입력 데이터가 준비된 시점부터 출력이 완료될 때까지 측정해야 한다. 평균, 중앙값, 최대값, 상위 백분위 지연 시간을 모두 기록해야 한다.

간헐적인 지연 시간 급증은 평균 성능이 충분하더라도 안전 제한 시간을 초과할 수 있다. 실시간 시스템에서는 타이밍 편차와 최악 조건(Worst Case)을 반드시 분석해야 한다.

처리량과 프레임 속도는 파이프라인의 최신성(Freshness)과 함께 측정해야 한다. 많은 프레임을 처리하더라도 오래된 데이터가 큐에 쌓이면 실시간 대응에는 도움이 되지 않는다.

메모리 사용량은 모델 가중치, 중간 활성화, 버퍼, 런타임 작업 공간, 주변 소프트웨어 프로세스를 모두 포함해야 한다. 전체 로봇 소프트웨어가 동시에 실행될 때만 메모리 부족 문제가 나타날 수 있다.

소비 전력과 온도는 지속적인 추론 부하에서 측정해야 한다. 짧은 테스트는 몇 분 뒤 발생하는 열 스로틀링(Thermal Throttling)을 감출 수 있다.

검증은 여러 성능 모드, 클럭 설정, 배터리 상태, 외부 온도에서 반복되어야 한다. 실제 현장에서는 실험실보다 하드웨어 성능이 낮아질 수 있다.

최적화된 배포 모델은 원본 학습 모델과 비교해야 한다. 양자화(Quantization), 가지치기(Pruning), 모델 변환, 연산자 교체, 런타임 최적화가 출력에 영향을 줄 수 있다.

계층별 비교(Layer-Level Comparison)는 출력 차이가 어디에서 시작되는지를 찾는 데 유용하다. INT8 모델의 정확도가 감소하거나 ONNX와 TensorRT 결과가 다를 때 특히 효과적이다.

학습 후 양자화(Post-Training Quantization)는 실제 배포 환경을 대표하는 보정 데이터(Calibration Data)를 사용하여 검증해야 한다. 잘못된 보정은 활성화 범위를 왜곡하고 특정 환경에서 성능을 감소시킬 수 있다.

가지치기된 모델은 클래스별 성능 감소를 확인해야 한다. 일부 채널 제거는 일반적인 대형 객체보다 희귀하거나 작은 객체에 더 큰 영향을 줄 수 있다.

지식 증류(Knowledge Distillation) 모델은 Teacher 모델의 신뢰성을 그대로 물려받는다고 가정해서는 안 된다. Student 모델은 평균 정확도를 유지하면서도 강인성이나 신뢰도 보정 성능을 잃을 수 있다.

시스템 수준 검증(System-Level Validation)은 모델을 전처리, 객체 추적, 센서 융합, 지도 작성, 경로 계획, 제어와 연결하여 평가한다. 실제 실패는 신경망 자체보다 모듈 간 상호작용에서 발생하는 경우가 많다.

검출 결과가 올바르더라도 좌표 변환이 잘못되거나, 타임스탬프가 어긋나거나, 추적 결과가 지연되면 위험한 행동이 발생할 수 있다.

센서 동기화는 움직이는 객체를 이용하여 검증해야 한다. 작은 시간 오차만으로도 카메라, 라이다, 레이더, 오도메트리가 서로 다른 물리 상태를 나타낼 수 있다.

보정 검증(Calibration Validation)은 내부 파라미터(Intrinsic Parameter), 외부 파라미터(Extrinsic Parameter), 시간 정렬(Temporal Alignment)을 모두 확인해야 한다. 작은 기하학적 오차도 먼 거리에서는 큰 융합 오류를 만들 수 있다.

종단간 시나리오 테스트(End-to-End Scenario Test)는 단순히 인식 지표가 높은지가 아니라 로봇이 올바르게 행동하는지를 평가한다. 시스템은 위험을 검출하고, 속도를 줄이고, 정지하고, 우회하거나, 운영자 지원을 요청해야 한다.

고장 주입(Failure Injection)은 센서 손실, 지연 프레임, 손상된 데이터, 과열, 메모리 압박, 통신 장애를 의도적으로 발생시킨다. 시스템은 잘못된 입력으로 계속 동작하지 않고 안전하게 대응해야 한다.

대체 동작(Fallback Behavior)도 반드시 검증해야 한다. 인식 품질이 저하되면 보조 센서, 저속 모드, 경량 모델, 원격 제어, 안전 정지로 전환할 수 있어야 한다.

사람-기계 상호작용(Human-Machine Interaction)도 평가해야 한다. 운영자는 경보, 신뢰도 표시, 오류 메시지를 정확히 이해해야 한다. 모호한 사용자 인터페이스는 관리 가능한 모델 실패를 실제 운용 사고로 확대할 수 있다.

장시간 현장 테스트(Long-Duration Field Test)는 필수적이다. 렌즈 오염, 보정 변화, 온도 상승, 메모리 누수, 환경 변화는 수 시간 또는 수일이 지난 뒤에만 나타날 수 있다.

현장 시험은 계절, 시간대, 작업량, 교통량, 환경 조건을 폭넓게 포함해야 한다. 짧은 데모만으로는 실제 배포 환경 전체를 대표할 수 없다.

시험 중 발견된 실패 사례는 센서 데이터, 모델 출력, 환경 정보, 시스템 상태와 함께 저장해야 한다. 이를 통해 향후 개선을 위한 체계적인 실패 데이터베이스(Failure Database)를 구축할 수 있다.

각 실패는 원인별로 분류해야 한다. 데이터 부족, 라벨 오류, 모델 한계, 보정 문제, 동기화 문제, 하드웨어 과부하, 센서 고장, 소프트웨어 통합 오류 등이 가능하다.

근본 원인 분석(Root-Cause Analysis)은 반복적인 시행착오를 줄여준다. 좌표 변환 오류나 타임스탬프 지연으로 발생한 문제는 모델을 다시 학습하는 것만으로 해결되지 않는다.

회귀 테스트(Regression Testing)는 새로운 개선이 기존의 정상 기능을 손상시키지 않는지를 확인한다. 모든 새 모델은 고정된 대표 시나리오와 안전 시나리오 집합을 통과해야 한다.

회귀 테스트 세트에는 일반적인 사례, 어려운 사례, 과거에 발생했던 실패 사례가 모두 포함되어야 한다. 새로운 실패 사례도 지속적으로 추가해야 한다.

모델 비교는 동일한 데이터셋, 임계값, 전처리, 하드웨어 조건에서 수행해야 한다. 그렇지 않으면 실제 모델 개선이 아니라 평가 조건 변화 때문에 성능이 좋아 보일 수 있다.

성능 차이가 작은 경우 통계적 유의성(Statistical Significance)을 고려해야 한다. 무작위 초기화, 데이터 샘플링, 작은 테스트 규모 때문에 결과가 달라질 수 있다.

신뢰 구간(Confidence Interval)과 반복 실험은 하나의 수치보다 더 신뢰성 높은 비교를 제공한다. 희귀 사건처럼 샘플 수가 적은 평가에서는 특히 중요하다.

안전 검증(Safety Validation)은 위험 분석(Hazard Analysis)과 추적 가능성(Traceability)을 요구할 수 있다. 각 인식 요구사항은 테스트, 지표, 결과, 합격 기준과 연결되어야 한다.

합격 기준(Acceptance Criteria)은 최종 평가 이전에 정의해야 한다. 결과를 본 뒤 기준을 변경하면 편향된 결정을 내리거나 중요한 약점을 감출 수 있다.

모델은 하나의 평균 점수가 아니라 모든 핵심 조건을 만족할 때 승인되어야 한다. 최소 재현율, 최대 지연 시간, 허용 가능한 신뢰도 보정, 안전한 대체 동작이 모두 요구될 수 있다.

문서화(Documentation)는 검증의 핵심 요소이다. 데이터셋 버전, 모델 버전, 코드 버전, 하드웨어, 런타임, 임계값, 지표, 알려진 한계를 모두 기록해야 한다.

모델 카드(Model Card)는 의도된 사용 목적, 학습 데이터, 평가 결과, 운용 범위, 윤리적 고려사항, 알려진 실패 모드를 정리할 수 있다. 이는 책임 있는 배포와 유지보수를 지원한다.

검증 보고서는 측정된 사실과 가정을 명확하게 구분해야 한다. 무엇을 시험했고, 무엇을 시험하지 않았으며, 어떤 불확실성이 남아 있는지를 설명해야 한다.

모델 검증은 배포 이후에도 계속된다. 런타임 모니터링(Runtime Monitoring)은 신뢰도 분포, 검출 빈도, 지연 시간, 온도, 프레임 누락, 센서 상태를 추적할 수 있다.

이러한 통계의 변화는 도메인 변화, 센서 노후화, 환경 변화, 소프트웨어 충돌을 나타낼 수 있다. 자동 경보는 문제를 조기에 발견하도록 도와준다.

현장 데이터는 주기적으로 샘플링하여 검토할 수 있다. 낮은 신뢰도 이벤트, 예상하지 못한 검출, 운영자 개입 사례는 새로운 실패 패턴을 찾는 데 특히 유용하다.

지속 검증(Continuous Validation)은 통제되지 않은 자동 재학습을 의미하지 않는다. 업데이트된 모델도 오프라인 평가, 시뮬레이션, 회귀 테스트, 현장 검증, 승인 절차를 통과한 뒤 배포되어야 한다.

모델과 데이터셋 버전 관리는 새 모델이 예상보다 낮은 성능을 보일 때 롤백(Rollback)을 가능하게 한다. 배포된 모든 모델은 학습 데이터, 설정, 검증 결과까지 추적할 수 있어야 한다.

모델 레지스트리(Model Registry)는 승인된 모델, 성능 지표, 하드웨어 호환성, 배포 이력, 현재 상태를 저장할 수 있다. 이는 여러 로봇에 대한 통제된 배포 관리를 지원한다.

따라서 인식 모델 검증은 한 번 수행하는 벤치마크가 아니라 모델 전체 수명주기(Lifecycle)에 걸쳐 지속되는 과정이다. 요구사항 정의에서 시작하여 학습, 최적화, 배포, 모니터링, 향후 업데이트까지 이어진다.

강력한 검증 전략은 정량적 지표, 정성적 검토, 하위 그룹 분석, 강인성 테스트, 시스템 통합 검증, 장시간 현장 시험, 안전 대체 동작 검증을 함께 포함한다.

자율주행 이동로봇에서 엄격한 인식 모델 검증은 단순한 성능 수치를 실제 운용 신뢰성으로 전환한다. 이를 통해 모델은 이상적인 데이터셋뿐 아니라 다양한 실제 물리 환경에서도 정확하고, 신속하며, 신뢰성 있고, 안전하게 동작할 수 있다.
