**Volume 06. AMR AI and Embodied Intelligence**

# Chapter 02. Computer Vision for Robotics

## 02.1 Computer Vision Basics

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

컴퓨터 비전(Computer Vision)은 컴퓨터와 로봇이 시각 데이터(Visual Data)로부터 정보를 획득하고 해석하며 이해할 수 있도록 하는 과학 및 공학 분야이다. 단순히 영상을 변환하거나 향상시키는 영상 처리(Image Processing)와 달리, 컴퓨터 비전은 객체(Object), 장면(Scene), 사건(Event), 공간적 관계(Spatial Relationship)에 대한 의미 있는 정보를 추론하는 것을 목표로 한다. 자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서는 컴퓨터 비전이 주변 환경을 인식하고, 장애물을 탐지하며, 주행 가능한 공간을 판단하고, 사람과 사물을 식별하며, 변화하는 환경에 대한 이해를 지속적으로 갱신하는 핵심 센서 기술 중 하나로 사용된다.

인간의 시각은 수백만 년에 걸친 생물학적 진화를 통해 거의 즉각적으로 환경을 이해할 수 있도록 발전하였다. 인간의 시각 시스템은 색(Color), 깊이(Depth), 움직임(Motion), 형태(Shape), 질감(Texture), 그리고 상황(Context)을 통합하여 하나의 일관된 환경 이해를 형성한다. 컴퓨터 비전은 이러한 능력을 수학적 모델(Mathematical Model), 알고리즘(Algorithm), 그리고 인공지능(AI, Artificial Intelligence)을 이용하여 구현하려는 기술이다. 현대의 비전 시스템은 특정 작업에서는 뛰어난 성능을 달성하였지만, 조명 변화, 가림(Occlusion), 악천후, 센서 노이즈(Sensor Noise), 그리고 학습하지 않은 새로운 환경에서는 여전히 어려움을 겪는다.

컴퓨터 비전 시스템은 영상 획득(Image Acquisition)으로부터 시작된다. 카메라는 입사되는 빛을 이미지 센서(Image Sensor)의 각 센서 요소(Sensor Element)에서 측정하여 디지털 신호로 변환한다. 각 센서 요소는 하나의 픽셀(Pixel)에 해당하며 영상의 최소 단위를 나타낸다. 수백만 개의 픽셀이 2차원 격자로 배열되면서 하나의 디지털 영상이 형성되고, 각 픽셀은 밝기(Brightness) 또는 색(Color) 정보를 저장한다. 일반적으로 영상의 해상도(Resolution)가 높을수록 더욱 많은 시각 정보를 제공하지만, 계산량과 메모리 사용량, 처리 지연 시간 역시 증가하게 된다.

디지털 영상은 사람이 직접 보는 화면이 아니라 숫자로 표현된 데이터이다. 흑백 영상(Grayscale Image)은 일반적으로 각 픽셀마다 0부터 255까지의 하나의 밝기 값을 저장한다. 컬러 영상(Color Image)은 보통 RGB(Red, Green, Blue) 색상 모델을 사용하며, 하나의 픽셀이 빨강(Red), 초록(Green), 파랑(Blue)의 세 개 채널(Channel)을 각각 가진다. 이 세 가지 색을 조합하여 다양한 색상이 표현된다. 또한 HSV(Hue, Saturation, Value), LAB, YCbCr과 같은 다른 색 공간(Color Space)은 밝기와 색상 정보를 분리하여 다양한 컴퓨터 비전 알고리즘을 보다 안정적으로 수행하도록 돕는다.

시각 인식의 품질은 단순히 해상도만으로 결정되지 않는다. 렌즈(Lens)의 품질, 초점 거리(Focal Length), 조리개(Aperture), 노출 시간(Exposure Time), 동적 범위(Dynamic Range), 센서 감도(Sensor Sensitivity), 광학 왜곡(Optical Distortion) 등 다양한 카메라 특성이 최종 영상 품질을 결정한다. 영상 획득 과정에서 손실된 정보는 이후의 알고리즘으로 복원하기 어렵기 때문에, 적절한 카메라 하드웨어를 선택하는 것은 우수한 인식 알고리즘을 개발하는 것만큼 중요하다.

조명(Illumination)은 컴퓨터 비전 성능에 매우 큰 영향을 미친다. 동일한 물체라도 조명이 달라지면 전혀 다른 모습으로 보일 수 있다. 그림자(Shadow), 반사(Reflection), 눈부심(Glare), 저조도(Low-Light) 환경은 객체 인식(Object Recognition)의 정확도를 크게 저하시킨다. 산업용 로봇에서는 이러한 문제를 줄이기 위해 일정한 조명 시스템(Control Lighting), 적외선(IR, Infrared) 조명, 편광 필터(Polarized Filter), 고동적 범위(HDR, High Dynamic Range) 카메라 등을 사용하여 보다 안정적인 입력 영상을 확보한다.

카메라 기하학(Camera Geometry)은 3차원 공간이 2차원 영상으로 투영(Project)되는 과정을 설명하는 수학적 기반이다. 원근 투영(Perspective Projection)에 의해 가까운 물체는 크게 보이고 먼 물체는 작게 보이며, 평행한 직선은 소실점(Vanishing Point)을 향해 모이는 것처럼 나타난다. 이러한 기하학적 특성은 수학적으로 모델링할 수 있으며, 이를 통해 로봇은 물체의 위치(Position), 거리(Distance), 자세(Pose)를 비교적 정확하게 추정할 수 있다.

카메라 보정(Camera Calibration)은 내부 파라미터(Intrinsic Parameter)와 외부 파라미터(Extrinsic Parameter)를 계산하는 과정이다. 내부 파라미터는 초점 거리(Focal Length), 주점(Principal Point), 렌즈 왜곡(Lens Distortion)과 같은 카메라 자체의 특성을 의미한다. 외부 파라미터는 월드 좌표계(World Coordinate System)에서 카메라의 위치와 방향을 나타낸다. 정확한 카메라 보정은 위치 추정(Localization), 객체 조작(Object Manipulation), 비전 기반 내비게이션(Visual Navigation), 다중 카메라 센서 융합(Multi-Camera Sensor Fusion)과 같은 로봇 응용에서 필수적이다.

컴퓨터 비전은 고수준의 인식 작업을 수행하기 전에 영상 전처리(Image Preprocessing)를 수행한다. 영상 전처리는 노이즈를 줄이고 영상 품질을 향상시키는 과정이다. 대표적인 기법으로는 밝기 조정(Brightness Adjustment), 대비 향상(Contrast Enhancement), 히스토그램 평활화(Histogram Equalization), 가우시안 필터(Gaussian Filter), 미디언 필터(Median Filter), 에지 강화(Edge Enhancement), 영상 정규화(Image Normalization) 등이 있다. 이러한 과정은 이후의 인식 알고리즘이 보다 안정적으로 동작하도록 입력 데이터를 개선한다.

에지(Edge)는 영상에서 가장 중요한 특징(Feature) 중 하나이다. 에지는 픽셀 밝기가 급격하게 변화하는 영역으로, 일반적으로 물체의 경계를 의미한다. Sobel, Prewitt, Laplacian, Canny와 같은 고전적인 에지 검출(Edge Detection) 알고리즘은 영상의 밝기 기울기(Gradient)를 계산하여 이러한 경계를 찾는다. 최근에는 딥러닝(Deep Learning)이 널리 사용되면서 수작업 기반 특징 추출의 비중은 줄어들었지만, 에지 정보는 산업 검사와 위치 추정 등 다양한 분야에서 여전히 중요한 역할을 한다.

특징 추출(Feature Extraction)은 원시 픽셀 데이터를 보다 의미 있는 표현으로 변환하는 과정이다. 수백만 개의 픽셀을 그대로 처리하는 대신, 코너(Corner), 블롭(Blob), 윤곽선(Contour), 질감(Texture)과 같은 중요한 구조를 추출한다. Harris Corner, SIFT, SURF, ORB, FAST와 같은 고전적인 특징 기술자(Feature Descriptor)는 객체 매칭(Object Matching), 영상 정합(Image Registration), 비전 기반 위치 추정(Visual Localization), 그리고 동시적 위치 추정 및 지도 작성(SLAM, Simultaneous Localization and Mapping)에 널리 활용된다. 계산 효율성과 해석 가능성이 중요한 환경에서는 이러한 기법이 여전히 높은 가치를 가진다.

움직임(Motion)은 또 하나의 중요한 시각 정보이다. 연속적으로 촬영된 영상(Frame Sequence)을 분석하면 물체의 이동, 카메라의 움직임, 그리고 환경의 변화를 추정할 수 있다. 광류(Optical Flow)는 연속된 프레임 사이에서 픽셀의 이동을 계산하는 기술로, 장애물 회피(Obstacle Avoidance), 객체 추적(Object Tracking), 자기 위치 이동(Ego Motion) 추정, 자율주행 내비게이션 등에 활용된다. 움직임 분석을 통해 로봇은 정적인 배경과 움직이는 물체를 구분하고 미래의 이동 경로를 예측할 수 있다.

깊이 인식(Depth Perception)은 2차원 영상을 3차원 공간 이해로 확장하는 핵심 기술이다. 인간은 양안 시차(Binocular Vision), 움직임(Motion), 원근(Perspective), 경험(Prior Knowledge)을 이용하여 깊이를 자연스럽게 인식한다. 로봇은 스테레오 카메라(Stereo Camera), 구조광(Structured Light), 비행시간(ToF, Time-of-Flight) 카메라, RGB-D 카메라, 라이다(LiDAR)를 이용하여 깊이를 측정한다. 이러한 깊이 정보는 거리 측정, 장애물 탐지, 3차원 환경 복원, 안전한 경로 계획에 필수적이다.

스테레오 비전(Stereo Vision)은 일정한 간격(Baseline)으로 배치된 두 대의 카메라에서 촬영된 영상을 비교하여 깊이를 계산한다. 동일한 물체가 두 영상에서 나타나는 위치 차이를 시차(Disparity)라고 하며, 시차가 클수록 물체는 카메라에 가깝다. 정확한 스테레오 비전을 위해서는 카메라 보정(Camera Calibration), 영상 정렬(Image Rectification), 그리고 대응점 탐색(Correspondence Matching)이 필요하다. 계산량은 많지만 별도의 능동 조명 없이도 밀집된(Dense) 3차원 정보를 생성할 수 있다.

객체 인식(Object Recognition)은 컴퓨터 비전의 가장 중요한 목표 가운데 하나이다. 객체 인식은 영상 속 물체의 종류(Category)와 개별 객체를 식별하는 과정이다. 전통적인 시스템은 특징 추출과 SVM(Support Vector Machine), 랜덤 포레스트(Random Forest)와 같은 통계적 분류기를 사용하였다. 현대의 시스템은 주로 합성곱 신경망(CNN, Convolutional Neural Network)과 비전 트랜스포머(Vision Transformer)를 이용하여 대규모 데이터로부터 계층적인 특징을 자동으로 학습한다.

영상 분류(Image Classification), 객체 검출(Object Detection), 의미론적 분할(Semantic Segmentation), 인스턴스 분할(Instance Segmentation)은 점차 높은 수준의 장면 이해를 제공한다. 영상 분류는 전체 영상의 종류를 예측한다. 객체 검출은 객체의 종류와 위치를 함께 추정한다. 의미론적 분할은 모든 픽셀에 의미 정보를 부여하며, 인스턴스 분할은 동일한 종류의 객체까지 각각 구분한다. 이러한 기술들은 자율주행 로봇이 주변 환경을 종합적으로 이해하는 기반이 된다.

강인한(Robust) 컴퓨터 비전 시스템은 불완전한 관측과 다양한 불확실성을 극복해야 한다. 센서 노이즈(Sensor Noise), 모션 블러(Motion Blur), 부분 가림(Partial Occlusion), 악천후, 다양한 시점(Viewpoint), 그리고 환경 변화는 모두 인식 정확도를 저하시킨다. 따라서 현대의 로봇은 카메라만 사용하는 것이 아니라 비전(Vision), 라이다(LiDAR), 레이더(Radar), 관성측정장치(IMU, Inertial Measurement Unit), 초음파 센서(Ultrasonic Sensor), 위성항법장치(GNSS)를 함께 사용하는 센서 융합(Sensor Fusion)을 적용하여 안정성과 신뢰성을 높인다.

딥러닝(Deep Learning)은 지난 10여 년 동안 컴퓨터 비전 분야를 근본적으로 변화시켰다. 과거처럼 사람이 특징을 직접 설계하는 대신, 신경망(Neural Network)이 대규모 학습 데이터를 통해 계층적인 특징 표현을 자동으로 학습한다. 합성곱 신경망(CNN)은 객체 인식의 성능을 크게 향상시켰으며, 최근에는 비전 트랜스포머(Vision Transformer)가 다양한 시각 인식 작업에서 뛰어난 성능을 보여주고 있다. 그러나 이러한 성능은 고품질 데이터셋(Data Set), 적절한 학습 과정, 효율적인 추론 최적화(Inference Optimization), 그리고 충분한 검증(Validation)이 함께 이루어질 때 비로소 실제 환경에서 안정적으로 활용될 수 있다.

자율주행 이동로봇(AMR)에서 컴퓨터 비전은 하나의 독립적인 알고리즘이 아니라 연속적으로 동작하는 인식 파이프라인(Perception Pipeline)의 핵심 요소이다. 카메라에서 획득된 영상은 전처리되고, 분석되며, 해석된 후 다른 센서의 정보와 통합된다. 이렇게 생성된 환경 이해는 위치 추정(Localization), 지도 작성(Mapping), 장애물 회피(Obstacle Avoidance), 경로 계획(Path Planning), 사람과의 상호작용(Human-Robot Interaction), 안전 모니터링(Safety Monitoring), 그리고 임무 수행(Mission Execution)을 지원한다. 앞으로 파운데이션 모델(Foundation Model), 멀티모달 인공지능(Multimodal AI), 그리고 체화형 인공지능(Embodied Intelligence)이 더욱 발전함에 따라, 컴퓨터 비전은 지능형 로봇이 실제 세계를 이해하고 안전하게 상호작용하기 위한 가장 핵심적인 기반 기술로 계속 발전할 것이다.

## 02.2 Image Preprocessing

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

영상 전처리(Image Preprocessing)는 모든 컴퓨터 비전(Computer Vision) 시스템의 기초를 이루는 단계이며, 입력 영상의 품질은 이후 수행되는 인식 알고리즘의 신뢰성에 직접적인 영향을 미친다. 실제 환경에서 동작하는 카메라는 센서 노이즈(Sensor Noise), 조명 변화(Illumination Change), 모션 블러(Motion Blur), 렌즈 왜곡(Lens Distortion), 기상 조건(Weather Effect), 그리고 다양한 센서 아티팩트(Sensor Artifact)를 포함한 영상을 획득한다. 영상 전처리의 목적은 이러한 불필요한 변화를 줄이면서 객체 검출(Object Detection), 분할(Segmentation), 위치 추정(Localization), 로봇 의사결정(Robot Decision Making)에 필요한 시각 정보를 최대한 유지하는 것이다. 영상 전처리는 새로운 지능을 추가하는 과정이 아니라, 이후의 인식 알고리즘이 보다 안정적이고 정확하게 동작할 수 있도록 데이터를 준비하는 과정이다.

자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서는 환경이 지속적으로 변화하기 때문에 영상 전처리의 중요성이 더욱 커진다. 로봇은 창고(Warehouse), 병원(Hospital), 공장(Factory), 건설 현장(Construction Site), 야외 도로(Outdoor Road) 등 다양한 환경을 이동하며 서로 다른 조명, 움직이는 그림자, 반사면, 먼지, 비, 안개, 그리고 진동을 경험한다. 카메라에서 직접 획득한 원본 영상(Raw Image)은 이러한 영향으로 인해 다양한 결함을 포함하게 되며, 이는 객체 인식 정확도를 크게 저하시킨다. 효과적인 영상 전처리는 이러한 변화를 최소화한 후 계산량이 큰 인식 알고리즘으로 영상을 전달한다.

영상 전처리 파이프라인(Preprocessing Pipeline)은 일반적으로 영상 획득 직후부터 시작된다. 카메라 영상은 메모리로 전송되고, 시간 정보(Time Stamp)가 동기화되며, 처리하기 적합한 표준 형식(Standard Format)으로 변환된다. 응용 분야에 따라 영상 크기 조정(Image Resizing), 자르기(Cropping), 색 공간 변환(Color Space Conversion), 정규화(Normalization), 기하학적 보정(Geometric Correction), 필터링(Filtering), 영상 향상(Image Enhancement) 등의 작업이 수행된 후 특징 추출(Feature Extraction)이나 딥러닝 추론(Deep Learning Inference) 단계로 전달된다. 학습 데이터와 실제 운용 데이터 사이의 일관성을 유지하기 위해서는 동일한 전처리 과정이 반드시 유지되어야 한다.

영상 크기 조정(Image Resizing)은 가장 단순하면서도 가장 자주 사용되는 전처리 과정이다. 대부분의 컴퓨터 비전 모델은 입력 영상의 크기가 고정되어 있으므로 다양한 해상도의 영상을 일정한 크기로 변환해야 한다. 높은 해상도의 영상은 계산량을 줄이기 위해 축소되며, 작은 영상은 모델 입력 크기에 맞추기 위해 확대된다. 그러나 지나친 크기 변경은 중요한 세부 정보를 잃게 하거나 보간(Interpolation) 과정에서 새로운 왜곡을 발생시킬 수 있다. 따라서 영상 해상도는 계산 효율성과 인식 성능을 함께 고려하여 결정해야 한다.

크롭(Cropping)은 영상에서 불필요한 영역을 제거하고 관심 영역(ROI, Region of Interest)에만 계산 자원을 집중시키는 과정이다. 로봇은 전체 영상을 분석하기보다 주행 차선, 선반, 컨베이어 벨트, 보행 구역, 작업 공간과 같이 중요한 영역만을 선택하여 처리하는 경우가 많다. 이러한 관심 영역 선택은 계산량을 줄일 뿐 아니라 배경에 존재하는 불필요한 정보를 제거하여 인식 알고리즘의 안정성을 높여준다.

영상 정규화(Image Normalization)는 픽셀 값을 일정한 범위의 수치로 변환하는 과정이다. 딥러닝 모델은 원시 픽셀 값을 그대로 사용하는 것보다 일정한 분포를 갖는 입력 데이터에서 더욱 안정적인 성능을 보인다. 일반적으로 픽셀 값을 0에서 1 사이로 변환하거나, 평균을 0으로 맞추고 표준편차(Standard Deviation)로 나누는 표준화(Standardization)를 수행한다. 이러한 과정은 학습 과정의 안정성을 높이며 다양한 하드웨어 환경에서도 일관된 추론 성능을 제공한다.

색 공간 변환(Color Space Conversion)은 특정 컴퓨터 비전 작업을 보다 쉽게 수행할 수 있도록 영상을 다른 색 표현 방식으로 변환하는 과정이다. RGB는 가장 일반적인 색 공간이지만, 밝기와 색상 정보를 분리하는 HSV, 사람의 시각 특성을 반영하는 LAB, 밝기와 색차를 분리하는 YCbCr 등이 자주 사용된다. 적절한 색 공간을 선택하면 객체 분할, 객체 인식, 결함 검출, 조명 변화에 대한 강인성을 향상시킬 수 있다.

밝기 조정(Brightness Adjustment)은 환경 조명의 변화로 발생하는 전체적인 밝기 차이를 보정하는 과정이다. 조명이 부족하면 객체의 세부 정보가 사라지고, 반대로 지나치게 밝으면 센서가 포화되어 경계 정보가 손실될 수 있다. 밝기 보정은 영상의 전체적인 명암 분포를 조정하여 보다 균형 잡힌 영상을 생성한다. 야외 환경에서는 태양광의 변화가 지속적으로 발생하기 때문에 적응형 밝기 조정(Adaptive Brightness Adjustment)이 자주 활용된다.

대비 향상(Contrast Enhancement)은 밝은 영역과 어두운 영역의 차이를 확대하여 객체를 보다 쉽게 구분하도록 만드는 과정이다. 안개(Fog), 연무(Haze), 흐린 날씨, 조명이 부족한 실내에서는 영상의 대비가 낮아지는 경우가 많다. 히스토그램 스트레칭(Histogram Stretching), 적응형 대비 향상(Adaptive Contrast Enhancement), 국부 대비 향상(Local Contrast Enhancement)은 객체의 경계와 세부 구조를 더욱 선명하게 만들어 이후의 에지 검출과 특징 추출 성능을 향상시킨다.

히스토그램 평활화(Histogram Equalization)는 영상의 밝기 분포를 전체 밝기 범위에 걸쳐 보다 균일하게 재배치하는 기법이다. 특정 밝기 구간에 집중되어 있던 픽셀들을 전체 범위로 분산시켜 전체적인 대비를 증가시킨다. 적응형 히스토그램 평활화(AHE, Adaptive Histogram Equalization)와 CLAHE(Contrast Limited Adaptive Histogram Equalization)는 국부적인 영상 품질을 향상시키면서 균일한 영역에서 노이즈가 과도하게 증폭되는 현상을 방지한다.

노이즈 제거(Noise Reduction)는 영상 전처리의 가장 중요한 목적 가운데 하나이다. 이미지 센서는 저조도 환경, 높은 감도(Gain), 높은 온도, 긴 노출 시간 등에서 다양한 전기적 노이즈를 발생시킨다. 이러한 노이즈는 에지, 질감, 세부 구조를 손상시키며 이후의 인식 알고리즘 성능을 저하시킨다. 적절한 노이즈 제거는 중요한 구조를 유지하면서 인식 성능을 향상시킨다.

가우시안 필터(Gaussian Filter)는 주변 픽셀들의 가중 평균을 이용하여 고주파 노이즈를 제거하는 대표적인 필터이다. 가까운 픽셀일수록 더 큰 가중치를 부여하는 가우시안 분포(Gaussian Distribution)를 사용하여 영상을 부드럽게 만든다. 특히 에지 검출 이전 단계에서 자주 사용되며, 노이즈로 인해 발생하는 잘못된 에지를 줄이는 효과가 있다. 그러나 지나친 평활화는 객체 경계를 흐리게 만들어 중요한 세부 정보를 손실시킬 수 있다.

미디언 필터(Median Filter)는 평균값 대신 주변 픽셀의 중앙값(Median)을 사용하여 노이즈를 제거하는 비선형 필터(Nonlinear Filter)이다. 소금-후추 노이즈(Salt-and-Pepper Noise)와 같은 돌발성 노이즈를 제거하는 데 매우 효과적이며, 에지를 비교적 잘 유지하는 장점이 있다. 산업용 검사 시스템에서는 센서 결함으로 인해 발생하는 이상 픽셀 제거에 자주 활용된다.

양방향 필터(Bilateral Filter)는 공간적인 거리와 밝기 차이를 동시에 고려하여 영상을 평활화하는 필터이다. 밝기가 비슷한 픽셀끼리만 강하게 평균화하므로 균일한 영역은 부드럽게 만들면서도 객체의 경계는 선명하게 유지할 수 있다. 이러한 특성 덕분에 깊이 추정, 객체 분할, 표면 검사와 같은 다양한 응용 분야에서 널리 사용된다.

샤프닝(Sharpening)은 에지와 질감과 같은 고주파 성분을 강조하여 영상의 세부 정보를 더욱 선명하게 만드는 과정이다. 언샤프 마스킹(Unsharp Masking)이나 라플라시안(Laplacian) 기반의 방법이 대표적으로 사용된다. 그러나 과도한 샤프닝은 노이즈까지 함께 증폭시켜 오히려 인식 알고리즘의 성능을 저하시킬 수 있으므로 적절한 수준으로 적용해야 한다.

영상 임계값 처리(Image Thresholding)는 회색조 영상을 흑백(Binary Image)으로 변환하는 기법이다. 전체 영상에 하나의 임계값을 적용하는 전역 임계값(Global Thresholding)과 주변 영역의 밝기에 따라 임계값을 계산하는 적응형 임계값(Adaptive Thresholding)이 대표적이다. 이진 영상(Binary Image)은 부품 개수 계산, 문서 분석, 형상 측정, 결함 검출과 같은 산업용 비전 시스템에서 매우 널리 활용된다.

형태학 연산(Morphological Operation)은 구조 요소(Structuring Element)를 이용하여 이진 영상의 구조를 변경하는 영상 처리 기법이다. 침식(Erosion)은 작은 물체를 제거하거나 서로 붙어 있는 객체를 분리한다. 팽창(Dilation)은 객체를 확장하여 작은 틈을 메운다. 열기(Opening)는 침식 후 팽창을 수행하여 노이즈를 제거하며, 닫기(Closing)는 팽창 후 침식을 수행하여 작은 구멍을 메우고 분리된 객체를 연결한다. 이러한 연산은 분할 결과를 후처리(Post Processing)하는 과정에서 매우 중요한 역할을 한다.

에지 강화(Edge Enhancement)는 객체 경계에서 발생하는 밝기 변화를 더욱 강조하는 과정이다. 그래디언트(Gradient) 기반 연산자는 밝기 변화가 큰 영역을 강조하고 균일한 영역은 상대적으로 억제한다. 이러한 에지 정보는 윤곽선 추출(Contour Extraction), 형상 분석(Shape Analysis), 특징 추출, 위치 추정 등에 중요한 역할을 하며, 특히 질감이 적고 형태가 명확한 객체를 인식할 때 매우 효과적이다.

렌즈 왜곡 보정(Lens Distortion Correction)은 카메라 렌즈에서 발생하는 비선형 왜곡을 제거하는 과정이다. 광각(Wide-Angle) 렌즈나 어안(Fisheye) 렌즈는 직선이 휘어 보이는 배럴 왜곡(Barrel Distortion)이나 핀쿠션 왜곡(Pincushion Distortion)을 발생시킨다. 카메라 보정(Camera Calibration)을 통해 이러한 왜곡 계수를 계산하고 이를 이용하여 영상을 보정한다. 왜곡 제거는 정밀 측정, 스테레오 비전, 동시적 위치 추정 및 지도 작성(SLAM), 자율주행에서 매우 중요하다.

원근 변환(Perspective Transformation)은 카메라 시점을 기하학적으로 변경하는 영상 변환 기법이다. 전방 카메라 영상을 위에서 내려다보는 버드아이뷰(Bird\'s-Eye View)로 변환하면 차선 검출, 장애물 위치 추정, 경로 계획이 훨씬 단순해진다. 또한 비스듬한 시점에서 촬영한 영상을 정면 영상으로 변환하여 정확한 거리 및 크기 측정을 수행할 수도 있다. 이러한 기법은 자율주행과 산업 자동화에서 널리 활용된다.

영상 정합(Image Registration)은 서로 다른 시점이나 시간, 또는 서로 다른 센서에서 획득한 영상을 동일한 좌표계로 정렬하는 과정이다. 대응되는 특징점이나 밝기 분포를 이용하여 기하학적 변환을 계산한다. 다중 카메라 시스템, 파노라마 생성(Panorama Generation), 의료 영상(Medical Imaging), 지도 업데이트(Map Updating) 등은 모두 정확한 영상 정합 기술에 의존한다.

영상 증강(Image Augmentation)은 실제 운용 단계가 아니라 딥러닝 학습 과정에서 매우 중요한 역할을 한다. 회전(Rotation), 이동(Translation), 확대·축소(Scaling), 좌우 반전(Flipping), 색상 변화(Color Jitter), 밝기 변화(Brightness Adjustment), 가우시안 노이즈(Gaussian Noise), 블러(Blur), 랜덤 크롭(Random Cropping) 등을 적용하여 하나의 영상을 다양한 형태로 변형함으로써 학습 데이터를 증가시킨다. 이러한 증강 기법은 신경망이 실제 환경과 유사한 다양한 상황을 학습하도록 하여 일반화 성능(Generalization Performance)을 향상시킨다.

최근의 컴퓨터 비전 시스템은 영상 전처리 기능 일부를 신경망 내부에 통합하는 방향으로 발전하고 있다. 학습 가능한 정규화 계층(Learned Normalization Layer), 미분 가능한 필터(Differentiable Filtering), 적응형 향상 모듈(Adaptive Enhancement Module), 트랜스포머(Transformer) 기반 전처리 기술은 수작업 기반 영상 처리의 비중을 줄이고 있다. 그럼에도 불구하고 고전적인 영상 전처리 기법은 계산량이 적고 해석이 쉬우며 산업 현장에서 여전히 매우 높은 활용 가치를 가진다.

실시간 로봇 시스템(Real-Time Robotic System)은 영상 전처리에도 엄격한 계산 시간 제약을 가진다. 모든 전처리 과정은 인식과 경로 계획 이전에 수행되므로 전체 시스템 지연 시간(Latency)에 직접 영향을 준다. 따라서 GPU(Graphics Processing Unit), 벡터 명령어(Vectorized Instruction), 디지털 신호 처리기(DSP, Digital Signal Processor), 영상 처리 전용 프로세서(IPU, Image Processing Unit) 등을 이용하여 하드웨어 가속(Hardware Acceleration)을 수행한다. 영상 전처리의 목표는 단순히 사람이 보기 좋은 영상을 만드는 것이 아니라, 실시간 조건을 만족하면서 이후 인식 알고리즘의 정확도를 최대화하는 것이다.

영상 전처리는 독립적인 단계로 평가되어서는 안 되며 전체 인식 파이프라인(Perception Pipeline)의 일부로 검증되어야 한다. 사람이 보기에는 더 좋아진 영상이라도 객체 검출이나 위치 추정 성능을 반드시 향상시키는 것은 아니다. 따라서 모든 전처리 알고리즘은 객체 검출 정확도(Detection Precision), 분할 품질(Segmentation Quality), 위치 추정 정확도(Localization Accuracy), 주행 성공률(Navigation Success Rate), 추론 시간(Inference Latency), 시스템 강인성(System Robustness)과 같은 실제 응용 성능 지표를 이용하여 평가되어야 한다.

자율주행 이동로봇이 점점 더 다양한 환경에서 운용됨에 따라 영상 전처리는 컴퓨터 비전 시스템에서 없어서는 안 될 핵심 구성 요소로 자리 잡고 있다. 영상 전처리는 불완전한 물리적 센서와 지능형 인식 알고리즘 사이를 연결하는 다리 역할을 하며, 원시 카메라 영상을 안정적이고 일관된 시각 정보로 변환한다. 딥러닝이 시각 인식의 많은 부분을 자동화하였지만, 견고한 영상 전처리는 여전히 인식 신뢰성, 계산 효율성, 그리고 운용 안전성을 향상시키는 핵심 기술이며, 현대 로봇 비전 시스템의 중요한 기반으로 계속 활용될 것이다.

## 02.3 Feature Extraction

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

특징 추출(Feature Extraction)은 원시 영상 데이터(Raw Image Data)로부터 인식(Recognition), 위치 추정(Localization), 추적(Tracking), 그리고 의사결정(Decision Making)에 활용할 수 있는 의미 있는 패턴(Pattern), 구조(Structure), 특성(Characteristic)을 찾아내는 과정이다. 컴퓨터 비전 시스템은 수백만 개의 픽셀 값을 그대로 처리하는 대신, 시각 정보를 특징(Feature)이라 불리는 간결하고 정보량이 높은 표현으로 변환한다. 이러한 특징은 객체, 장면 또는 영상 영역의 중요한 속성을 표현하면서도 불필요한 정보를 제거한다. 특징 추출은 저수준 영상 처리(Low-Level Image Processing)와 고수준 장면 이해(High-Level Visual Understanding)를 연결하는 핵심 단계이며, 로봇 인식(Robotic Perception)의 가장 중요한 구성 요소 가운데 하나이다.

자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서 특징 추출은 시점(Viewpoint), 조명(Illumination), 크기(Scale), 부분 가림(Partial Occlusion)이 변화하더라도 안정적인 시각 랜드마크(Visual Landmark)를 인식할 수 있도록 한다. 창고, 공장, 병원, 야외 환경을 이동하는 로봇은 지속적으로 변화하는 장면을 관찰한다. 원시 픽셀 값은 프레임마다 크게 달라질 수 있지만, 잘 설계된 특징은 비교적 안정적으로 유지되므로 로봇은 이전에 방문한 장소를 인식하고, 객체를 식별하며, 자신의 움직임을 추정하고, 일관된 환경 지도를 구축할 수 있다.

특징 추출의 가장 중요한 목적은 영상을 적은 수의 정보량이 높은 기술자(Descriptor)로 표현하는 것이다. 모든 픽셀을 저장하는 대신, 알고리즘은 코너(Corner), 에지(Edge), 질감(Texture), 블롭(Blob), 또는 독특한 패턴(Distinctive Pattern)과 같은 중요한 구조를 선택한다. 이러한 특징은 인식에 필요한 정보를 유지하면서 계산량을 크게 줄여준다. 또한 간결한 특징 표현은 매칭(Matching) 속도를 향상시키고 임베디드 컴퓨팅 환경에서도 실시간 로봇 동작을 가능하게 한다.

효과적인 시각 특징은 여러 가지 중요한 특성을 가져야 한다. 동일한 실제 위치가 서로 다른 촬영 조건에서도 동일한 특징으로 검출되는 반복성(Repeatability)이 있어야 하며, 서로 다른 객체나 장소를 구분할 수 있는 구별성(Distinctiveness)을 가져야 한다. 또한 조명 변화, 시점 변화, 영상 노이즈, 크기 변화, 부분 가림에 강인해야 한다. 마지막으로 특징 추출은 자율주행 로봇의 실시간 처리 요구사항을 만족할 수 있도록 계산 효율성(Computational Efficiency)을 가져야 한다.

특징 추출 기법은 크게 수작업 기반 특징(Handcrafted Feature)과 학습 기반 특징(Learned Feature)으로 구분할 수 있다. 수작업 기반 특징은 영상 기울기(Image Gradient), 밝기 분포(Intensity Distribution), 기하학적 구조(Geometric Structure), 질감 통계(Texture Statistics) 등을 이용하여 사람이 직접 설계한다. 반면 학습 기반 특징은 딥러닝(Deep Learning)이 대규모 데이터셋을 학습하면서 자동으로 특징을 발견한다. 최근에는 딥러닝이 주류가 되었지만, 수작업 기반 특징은 해석 가능성, 계산 효율성, 그리고 산업 현장에서의 검증된 신뢰성 덕분에 여전히 널리 활용된다.

에지(Edge)는 가장 기본적인 시각 특징 가운데 하나이다. 에지는 영상 밝기가 급격하게 변화하는 영역으로, 일반적으로 서로 다른 객체나 표면의 경계를 나타낸다. 에지 정보는 밝기 변화에는 비교적 강인하면서도 중요한 기하학적 구조를 제공한다. Sobel, Prewitt, Scharr, Canny와 같은 그래디언트(Gradient) 기반 연산자는 공간 미분(Spatial Derivative)을 계산하여 이러한 밝기 변화를 검출한다. 생성된 에지 맵(Edge Map)은 윤곽선 추출(Contour Extraction), 객체 분할(Object Segmentation), 기하학적 매칭(Geometric Matching)의 기반이 된다.

코너(Corner)는 단순한 에지보다 훨씬 풍부한 시각 정보를 제공한다. 코너는 두 개 이상의 에지가 만나는 지점으로, 여러 방향에서 동시에 밝기 변화가 발생하는 영역이다. 길게 이어지는 직선 에지는 어느 위치나 비슷하게 보일 수 있지만, 코너는 매우 독특한 구조를 가지므로 서로 다른 영상에서도 안정적으로 대응점을 찾을 수 있다. 이러한 이유로 코너 검출(Corner Detection)은 비전 기반 위치 추정과 동시적 위치 추정 및 지도 작성(SLAM, Simultaneous Localization and Mapping)의 핵심 기술이 된다.

해리스 코너 검출기(Harris Corner Detector)는 가장 영향력 있는 코너 검출 알고리즘 가운데 하나이다. 국부적인 영상 기울기를 분석하여 여러 방향에서 밝기 변화가 큰 위치를 코너로 판단한다. 해리스 코너는 회전(Rotation)에 대해 비교적 강인하며 반복성이 높고 계산량도 적다. 최근에는 크기 변화에 더욱 강한 알고리즘들이 등장하였지만, 해리스 검출기는 교육과 산업 분야 모두에서 중요한 기준 알고리즘으로 사용된다.

시-토마시 코너 검출기(Shi-Tomasi Corner Detector)는 해리스 알고리즘을 개선한 방법으로, 국부 기울기 공분산 행렬(Local Gradient Covariance Matrix)의 최소 고유값(Minimum Eigenvalue)을 이용하여 코너를 선택한다. 이러한 방식은 특징 추적(Feature Tracking)에 더욱 안정적인 코너를 제공한다. 따라서 시-토마시 검출기는 비주얼 오도메트리(Visual Odometry)와 광류(Optical Flow) 추정에서 매우 널리 활용된다.

FAST(Features from Accelerated Segment Test)는 실시간 환경을 위해 개발된 매우 빠른 코너 검출 알고리즘이다. 영상 기울기를 계산하지 않고 원형 주변 픽셀들의 밝기를 비교하여 코너 여부를 판단한다. 계산 과정이 매우 단순하기 때문에 제한된 연산 성능을 가진 임베디드 로봇 시스템에서도 매우 빠르게 실행될 수 있다.

블롭 검출(Blob Detection)은 주변 영역과 밝기 또는 질감이 크게 다른 영역을 찾는 기법이다. 코너가 하나의 점(Point)을 표현하는 반면, 블롭은 상대적으로 넓은 균일한 영역을 나타내며 실제 객체나 표면의 특징적인 부분을 표현하는 경우가 많다. 블롭은 객체 인식, 객체 추적, 장면 분석에서 중요한 시각 랜드마크 역할을 수행하며, 코너가 부족한 환경에서도 효과적으로 활용된다.

라플라시안 오브 가우시안(LoG, Laplacian of Gaussian)과 차분 가우시안(DoG, Difference of Gaussian)은 대표적인 블롭 검출 기법이다. 이들은 다양한 공간 해상도(Spatial Scale)에서 2차 미분(Second-Order Derivative)을 분석하여 블롭을 검출한다. 다중 스케일(Multi-Scale) 블롭 검출은 카메라와의 거리가 다른 객체도 안정적으로 인식할 수 있도록 해준다.

SIFT(Scale-Invariant Feature Transform)는 다중 스케일 특징 검출과 강력한 특징 기술자를 결합하여 컴퓨터 비전 분야에 큰 발전을 가져온 알고리즘이다. SIFT는 다양한 해상도에서 안정적인 키포인트(Keypoint)를 찾고, 주변 그래디언트 방향 히스토그램(Gradient Orientation Histogram)을 이용하여 특징 기술자를 생성한다. 이러한 기술자는 크기 변화, 회전, 적당한 시점 변화, 조명 변화에 매우 강인하다. SIFT는 초기 객체 인식, 파노라마 생성(Panorama Stitching), 비전 기반 위치 추정의 핵심 기술이었다.

SURF(Speeded-Up Robust Features)는 SIFT와 유사한 기능을 제공하면서 계산량을 크게 줄이기 위해 개발되었다. 적분 영상(Integral Image)과 박스 필터(Box Filter)를 이용하여 가우시안 필터를 근사함으로써 더욱 빠른 계산이 가능하다. 과거에는 특허(Patent) 문제로 활용이 제한되었지만, SURF는 강인성과 계산 효율성의 균형이 얼마나 중요한지를 보여준 대표적인 알고리즘이다.

ORB(Oriented FAST and Rotated BRIEF)는 FAST 코너 검출기와 BRIEF(Binary Robust Independent Elementary Features) 특징 기술자를 결합한 알고리즘이다. 회전 불변성(Rotation Invariance)을 제공하면서도 SIFT나 SURF보다 훨씬 적은 계산량으로 동작한다. ORB 기술자는 부동소수점 벡터 대신 이진 문자열(Binary String)을 사용하므로 해밍 거리(Hamming Distance)를 이용하여 매우 빠른 특징 매칭이 가능하다. 현재 ORB는 임베디드 로봇과 모바일 컴퓨팅에서 가장 널리 사용되는 수작업 기반 특징 추출 알고리즘 가운데 하나이다.

BRIEF(Binary Robust Independent Elementary Features)는 국부 영상 패치(Local Image Patch) 내의 밝기 비교만을 이용하는 이진 특징 기술자이다. 단독으로는 회전에 강하지 않지만 계산량이 매우 적으며, 이후 등장한 다양한 이진 특징 기술자의 기반이 되었다. 이진 특징은 메모리 사용량을 크게 줄이고 대규모 영상 데이터베이스에서도 매우 빠른 특징 매칭을 가능하게 하였다.

특징 기술자(Feature Descriptor)는 검출된 키포인트 주변의 시각적 정보를 수치 벡터로 표현한다. 키포인트 검출기는 어디에 중요한 특징이 존재하는지를 찾고, 특징 기술자는 그 주변의 시각적 특성을 압축된 형태로 저장한다. 우수한 기술자는 영상의 회전, 밝기 변화, 크기 변화, 시점 변화가 발생하더라도 동일한 위치를 안정적으로 대응시킬 수 있다. 따라서 특징 기술자의 품질은 객체 인식과 위치 추정의 신뢰성을 결정하는 핵심 요소이다.

특징 매칭(Feature Matching)은 서로 다른 영상에서 추출된 특징 기술자들 사이의 대응 관계를 찾는 과정이다. 서로 유사한 기술자는 동일한 실제 객체나 환경 랜드마크에서 생성되었을 가능성이 높다. 부동소수점 기술자는 유클리드 거리(Euclidean Distance), 이진 기술자는 해밍 거리(Hamming Distance)를 이용하여 유사도를 계산한다. 이후 최근접 이웃 탐색(Nearest Neighbor Search)과 기하학적 일관성 검증(Geometric Consistency Verification)을 수행하여 잘못된 대응점을 제거한다.

이상치 제거(Outlier Rejection)는 특징 매칭 과정에서 매우 중요한 단계이다. 실제 환경에서는 잘못된 대응점(False Match)이 항상 존재하기 때문이다. RANSAC(Random Sample Consensus)은 여러 번 무작위 샘플을 선택하여 가장 많은 일치점(Inlier)을 설명하는 기하학적 변환을 찾는다. 이를 통해 잘못된 대응점을 제거하고 비주얼 오도메트리, 영상 정합(Image Registration), SLAM의 안정성을 크게 향상시킨다.

질감 특징(Texture Feature)은 표면에 반복적으로 나타나는 밝기 패턴을 표현한다. 통계 기반 질감 기술자는 인접 픽셀 간의 공간적 관계를 분석하여 콘크리트, 잔디, 목재, 천, 금속과 같은 재질(Material)을 구분할 수 있다. GLCM(Gray-Level Co-occurrence Matrix), LBP(Local Binary Pattern), 가보 필터(Gabor Filter)는 산업 검사, 지형 분류(Terrain Classification), 결함 검출에서 널리 활용된다.

형상 특징(Shape Feature)은 질감이나 색상과 무관하게 객체의 기하학적 구조를 표현한다. 윤곽선(Contour), 볼록 껍질(Convex Hull), 후 모멘트(Hu Moment), 푸리에 기술자(Fourier Descriptor), 곡률(Curvature) 분석 등이 대표적인 방법이다. 조명 변화로 인해 외형이 달라져도 기하학적 구조는 유지되는 경우가 많기 때문에, 형상 특징은 로봇 조작(Robot Manipulation), 부품 검사(Component Inspection), 산업용 계측에서 매우 중요하다.

색상 특징(Color Feature)은 회색조 영상에서는 얻을 수 없는 추가적인 정보를 제공한다. 색상 히스토그램(Color Histogram)은 전체적인 색 분포를 표현하며, 국부 색상 기술자는 특정 영역의 색 정보를 기술한다. 색상 특징은 조명 변화에는 민감하지만 기하학적 특징이나 질감 특징과 결합하면 객체 인식 성능을 크게 향상시킬 수 있다. 농업용 로봇, 식품 검사 시스템, 서비스 로봇에서는 색상 정보가 매우 중요한 역할을 한다.

특징 피라미드(Feature Pyramid)는 다양한 해상도에서 동시에 특징을 추출하는 구조이다. 동일한 객체가 서로 다른 거리에서 관찰되더라도 안정적으로 검출할 수 있도록 지원한다. 이러한 다중 스케일 표현(Multi-Scale Representation)은 고전적인 특징 추출 알고리즘뿐 아니라 현대의 딥러닝 네트워크에서도 매우 중요한 개념으로 사용된다.

딥러닝은 특징 추출 방식을 근본적으로 변화시켰다. 사람이 직접 에지, 코너, 질감 특징을 설계하는 대신, 합성곱 신경망(CNN, Convolutional Neural Network)은 학습 과정에서 계층적인 특징을 자동으로 학습한다. 초기 계층은 에지와 질감을, 중간 계층은 객체의 부분 구조를, 깊은 계층은 의미론적 개념(Semantic Concept)을 표현하는 특징을 학습한다.

합성곱 신경망은 반복적인 합성곱(Convolution), 비선형 활성화(Nonlinear Activation), 풀링(Pooling)을 통해 특징을 추출한다. 합성곱 필터는 학습 과정에서 자동으로 최적화되어 중요한 시각 패턴을 검출한다. 풀링은 수용 영역(Receptive Field)을 점차 확대하면서 위치 변화에 대한 강인성을 높인다. 이렇게 생성된 계층적 특징 맵(Feature Map)은 많은 컴퓨터 비전 문제에서 수작업 기반 특징보다 뛰어난 성능을 제공한다.

특징 시각화(Feature Visualization)는 딥러닝이 실제로 어떤 특징을 학습했는지를 이해하기 위한 기술이다. 활성화 맵(Activation Map), 살리언시 맵(Saliency Map), Grad-CAM, 특징 역변환(Feature Inversion) 등의 기법은 신경망이 어떤 영역에 주목하여 판단을 수행하는지를 보여준다. 학습 기반 특징은 수작업 기반 특징보다 해석이 어렵지만, 이러한 시각화 기법은 안전이 중요한 로봇 시스템에서 모델의 투명성과 오류 분석을 지원한다.

비전 트랜스포머(Vision Transformer)는 합성곱 대신 자기 주의(Self-Attention)를 이용하여 영상 패치(Image Patch) 간의 관계를 학습하는 새로운 특징 추출 방식이다. 자기 주의 메커니즘은 영상 전체에 걸친 장거리 의존성(Long-Range Dependency)을 효과적으로 학습할 수 있다. 따라서 복잡한 환경에서 객체 간의 관계까지 고려한 전역적인 장면 이해(Global Scene Understanding)에 뛰어난 성능을 제공한다.

현대의 로봇 인식 시스템은 하나의 특징만 사용하는 경우가 거의 없다. 대신 여러 종류의 특징을 서로 결합하여 다양한 환경 변화에 더욱 강인한 인식 시스템을 구축한다. 고전적인 기하학적 특징은 정밀한 위치 추정을 지원하고, 딥러닝 기반 의미론적 특징은 안정적인 객체 인식을 제공한다. 여기에 깊이 정보(Depth Information), 움직임 정보(Motion Cue), 색상 정보(Color Distribution), 그리고 다양한 센서 정보를 함께 융합하여 주행, 조작, 검사, 자율 의사결정을 위한 종합적인 환경 표현을 생성한다.

추출된 특징의 품질은 이후 수행되는 모든 인식 알고리즘의 성능을 직접 결정한다. 특징 표현이 부정확하면 아무리 뛰어난 상위 수준의 알고리즘을 사용하더라도 위치 추정, 지도 작성, 객체 추적, 객체 인식은 모두 불안정해질 수밖에 없다. 따라서 특징 추출은 컴퓨터 비전의 가장 핵심적인 기술 가운데 하나이며, 현대 자율주행 이동로봇이 주변 세계를 이해하기 위한 정보량이 높고 효율적인 표현을 제공하는 가장 중요한 기반 기술이다.

## 02.4 Object Detection for AMR

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

객체 검출(Object Detection)은 자율주행 이동로봇(AMR, Autonomous Mobile Robot)의 가장 핵심적인 인식(Perception) 기능 가운데 하나이다. 객체 검출은 주변 환경에 존재하는 객체를 식별하고 그 위치를 추정할 수 있도록 한다. 전체 영상에 하나의 클래스(Class)만 예측하는 영상 분류(Image Classification)와 달리, 객체 검출은 어떤 객체가 존재하는지와 동시에 어디에 존재하는지를 함께 추정한다. 일반적으로 출력 결과는 객체 종류(Category), 신뢰도(Confidence Score), 그리고 객체의 위치를 나타내는 경계 상자(Bounding Box)로 구성된다. 이러한 정보는 자율주행, 장애물 회피, 물체 조작, 안전 감시, 자율 의사결정의 기반이 된다.

자율주행 이동로봇은 다양한 객체가 지속적으로 생성되고 이동하는 동적인 환경(Dynamic Environment)에서 동작한다. 창고에는 선반(Shelf), 팔레트(Pallet), 지게차(Forklift), 작업자(Worker), 물류 박스(Package)가 존재하며, 병원에는 환자(Patient), 의료 카트(Medical Cart), 휠체어(Wheelchair), 의료 장비(Medical Equipment)가 있다. 야외 로봇은 차량(Vehicle), 보행자(Pedestrian), 자전거(Bicycle), 교통 표지판(Traffic Sign), 공사 장벽(Construction Barrier), 동물(Animal)을 지속적으로 관찰한다. 신뢰성 높은 객체 검출은 주행 가능한 공간과 위험 요소를 구분하고, 주변 환경에 대한 이해를 지속적으로 갱신하도록 한다.

객체 검출은 의미론적 분할(Semantic Segmentation)이나 인스턴스 분할(Instance Segmentation)과는 근본적으로 다르다. 의미론적 분할은 모든 픽셀을 미리 정의된 클래스에 할당하지만 동일한 객체를 개별적으로 구분하지는 않는다. 인스턴스 분할은 같은 클래스에 속한 여러 객체를 각각 분리한다. 객체 검출은 이 두 기술의 중간 수준에 위치하며, 경계 상자(Bounding Box)를 이용하여 객체의 위치를 추정하면서도 비교적 낮은 계산량을 유지한다. 이러한 이유로 객체 검출은 실시간 로봇 시스템에서 가장 널리 사용되는 인식 기술 가운데 하나가 되었다.

객체 검출기의 성능은 위치 추정(Localization Accuracy)과 분류 정확도(Classification Accuracy)에 의해 결정된다. 위치 추정은 예측한 경계 상자가 실제 객체와 얼마나 정확하게 일치하는지를 의미하며, 분류 정확도는 객체의 종류를 올바르게 식별했는지를 의미한다. 우수한 객체 검출기는 이 두 가지를 동시에 만족하면서도 높은 처리 속도를 유지해야 한다. 로봇 응용에서는 일반적으로 초당 20\~30 프레임(Frame Per Second) 이상의 실시간 처리 성능이 요구된다.

초기의 객체 검출 시스템은 수작업 기반 특징(Handcrafted Feature)과 통계적 분류기(Statistical Classifier)에 크게 의존하였다. HOG(Histogram of Oriented Gradients)는 국부적인 에지 분포를 표현하였고, Haar-like Feature는 직사각형 영역의 밝기 차이를 이용하였다. 이러한 특징들은 SVM(Support Vector Machine)이나 AdaBoost와 같은 분류기와 결합되어 보행자, 얼굴, 차량 등의 객체를 인식하였다. 그러나 이러한 방법은 외형 변화가 크거나 배경이 복잡한 환경에서는 성능이 크게 저하되는 한계를 가졌다.

Viola-Jones 객체 검출기(Viola-Jones Detector)는 실제 환경에서 사용 가능한 최초의 실시간 객체 검출 시스템 가운데 하나였다. Haar-like Feature와 계단식 분류기(Cascade Classifier)를 이용하여 가능성이 낮은 영역을 빠르게 제거하고 점진적으로 정교한 분류를 수행하였다. 현재는 대부분 딥러닝 기반 방법으로 대체되었지만, 계산 효율성과 정확도의 균형이 중요하다는 사실을 보여준 대표적인 시스템이다.

슬라이딩 윈도우(Sliding Window) 방식은 딥러닝 이전 시대의 대표적인 객체 검출 구조였다. 고정된 크기의 윈도우(Window)를 다양한 위치와 크기로 이동시키면서 모든 영역을 개별적으로 분류하였다. 개념은 단순하지만 계산량이 매우 많았으며, 동일한 객체에 대해 여러 개의 중복 검출이 발생하는 문제가 있었다. 이러한 이유로 실시간 로봇 시스템에서는 활용에 많은 제약이 있었다.

영역 제안(Region Proposal) 방식은 먼저 객체가 존재할 가능성이 높은 후보 영역을 찾은 후 해당 영역만 분류하여 계산량을 크게 줄였다. Selective Search와 같은 알고리즘은 색상, 질감, 기하학적 구조를 이용하여 객체 후보 영역을 생성하고, 이후 신경망이 해당 영역만 분류하였다. 이 방식은 슬라이딩 윈도우보다 훨씬 효율적인 객체 검출을 가능하게 하였다.

딥러닝(Deep Learning)의 등장으로 객체 검출 기술은 근본적으로 변화하였다. 사람이 직접 특징을 설계하는 대신, 합성곱 신경망(CNN, Convolutional Neural Network)이 대규모 데이터셋으로부터 계층적인 시각 특징을 자동으로 학습하였다. 이러한 특징은 시점 변화, 조명 변화, 크기 변화, 부분 가림, 복잡한 배경 등에 훨씬 강인한 성능을 보였으며, 거의 모든 객체 검출 벤치마크(Benchmark)에서 기존 방법을 능가하였다.

R-CNN(Region-based Convolutional Neural Network)은 딥러닝 기반 객체 검출의 초기 성공 사례였다. 기존 영역 제안 알고리즘을 이용하여 후보 영역을 생성한 뒤, 각각을 CNN으로 분류하였다. 정확도는 크게 향상되었지만, 모든 후보 영역에 대해 CNN을 반복 수행해야 하므로 계산량이 매우 컸다.

Fast R-CNN은 전체 영상에 대해 단 한 번만 합성곱 특징 맵(Feature Map)을 계산하고, 모든 후보 영역이 이를 공유하도록 개선하였다. 이를 통해 특징 추출을 반복하지 않아도 되었으며, 계산 속도를 크게 향상시키면서도 높은 정확도를 유지하였다. 이는 특징 공유(Feature Sharing)의 중요성을 보여준 대표적인 구조이다.

Faster R-CNN은 영역 제안 네트워크(RPN, Region Proposal Network)를 도입하여 후보 영역 생성까지 신경망 내부에서 수행하도록 만들었다. 외부 영역 제안 알고리즘이 필요 없어졌으며, 전체 시스템이 종단간 학습(End-to-End Learning)이 가능해졌다. Faster R-CNN은 매우 높은 검출 정확도가 필요한 응용 분야에서 지금도 널리 활용되고 있다.

단일 단계 검출기(Single-Stage Detector)는 영역 제안 과정을 제거하여 더욱 빠른 실시간 처리를 목표로 한다. 객체 후보 생성과 분류를 하나의 네트워크에서 동시에 수행하므로 계산량이 크게 감소한다. 초기에는 정확도가 다소 낮았지만, 최근의 다양한 구조 개선을 통해 정확도와 속도를 모두 만족하는 수준으로 발전하였다.

YOLO(You Only Look Once)는 객체 검출을 하나의 회귀 문제(Regression Problem)로 정의한 대표적인 실시간 객체 검출 알고리즘이다. 하나의 신경망이 객체의 위치, 크기, 신뢰도, 클래스를 동시에 예측한다. 전체 영상을 단 한 번만 처리하기 때문에 매우 높은 추론 속도를 제공하며, 우수한 정확도까지 함께 달성하였다. 이러한 특성 덕분에 YOLO는 자율주행 이동로봇에서 가장 널리 사용되는 객체 검출 프레임워크가 되었다.

YOLO는 세대를 거치면서 지속적으로 발전하였다. 더욱 강력한 백본 네트워크(Backbone Network), 특징 피라미드(Feature Pyramid), 앵커 최적화(Anchor Optimization), 주의 메커니즘(Attention Mechanism), 개선된 손실 함수(Loss Function), 효율적인 학습 전략 등이 적용되면서 정확도와 속도가 모두 향상되었다. YOLOv8, YOLOv9, YOLOv10 이후의 최신 버전들은 임베디드 로봇, 산업 자동화, 자율주행 분야에서 뛰어난 성능을 보여주고 있다.

SSD(Single Shot Detector)는 또 다른 대표적인 단일 단계 객체 검출기이다. 여러 해상도의 특징 맵을 동시에 활용하여 작은 객체와 큰 객체를 함께 검출한다. 다중 스케일(Multi-Scale) 특징을 이용하기 때문에 다양한 크기의 객체를 효과적으로 인식할 수 있으며, 비교적 낮은 계산량으로 동작하여 경량 로봇 시스템에서도 활용된다.

RetinaNet은 전경(Foreground)과 배경(Background)의 데이터 불균형 문제를 해결하기 위해 초점 손실(Focal Loss)을 도입하였다. 대부분의 영상에서 배경이 객체보다 훨씬 많기 때문에 일반적인 손실 함수는 쉬운 배경 샘플에 과도하게 영향을 받는다. Focal Loss는 쉬운 샘플의 영향을 줄이고 어려운 객체에 더 많은 가중치를 부여하여 어려운 객체에 대한 검출 성능을 크게 향상시켰다.

앵커 박스(Anchor Box)는 다양한 크기와 종횡비(Aspect Ratio)를 가진 기준 경계 상자를 미리 정의하여 객체를 검출하는 방식이다. 신경망은 임의의 경계 상자를 직접 예측하는 대신 기준 앵커에 대한 위치 보정값(Offset)을 학습한다. 적절한 앵커 설계는 학습을 안정화하지만 수작업으로 조정해야 하는 단점이 있다. 최근에는 객체 중심과 크기를 직접 예측하는 앵커 프리(Anchor-Free) 방식이 점차 증가하고 있다.

객체 검출 성능은 IoU(Intersection over Union)를 이용하여 평가하는 것이 일반적이다. IoU는 예측한 경계 상자와 실제 경계 상자가 얼마나 겹치는지를 나타내는 지표이다. 겹치는 영역을 전체 합집합 영역으로 나누어 계산하며 값이 클수록 위치 추정이 정확하다는 의미이다. 일반적으로 IoU가 50% 또는 75% 이상이면 올바른 검출로 판단한다.

mAP(Mean Average Precision)는 객체 검출의 대표적인 성능 평가 지표이다. 정밀도(Precision)는 검출된 객체 가운데 실제 객체의 비율이며, 재현율(Recall)은 실제 객체 가운데 검출된 비율이다. Average Precision은 다양한 신뢰도 임계값에서의 정밀도를 종합한 값이며, Mean Average Precision은 이를 모든 객체 클래스에 대해 평균한 값이다. mAP가 높을수록 전체적인 객체 검출 성능이 우수함을 의미한다.

비최대 억제(NMS, Non-Maximum Suppression)는 하나의 객체에 대해 여러 개의 중복된 경계 상자가 생성되는 문제를 해결하는 후처리(Post Processing) 기법이다. 가장 높은 신뢰도를 가진 경계 상자만 남기고, 일정 수준 이상 겹치는 다른 경계 상자는 제거한다. 이를 통해 최종 검출 결과를 깔끔하게 정리하여 로봇의 의사결정 과정에 활용할 수 있다.

작은 객체(Small Object) 검출은 로봇 비전에서 가장 어려운 문제 가운데 하나이다. 멀리 있는 사람, 안전 콘(Safety Cone), 공구(Tool), 전기 부품(Electrical Component), 검사 대상은 영상에서 몇 개의 픽셀만 차지하는 경우가 많다. 특징 피라미드(Feature Pyramid), 초해상도(Super Resolution), 주의 메커니즘, 고해상도 백본 네트워크 등이 이러한 문제를 해결하기 위해 사용된다.

부분 가림(Occlusion)은 또 다른 중요한 문제이다. 객체가 선반, 장비, 차량, 식물, 또는 다른 사람에 의해 일부 가려질 수 있다. 사람은 문맥(Context)과 경험(Prior Knowledge)을 이용하여 쉽게 인식하지만, 컴퓨터 비전 시스템은 시각 정보가 부족하면 성능이 크게 저하된다. 데이터 증강(Data Augmentation), 트랜스포머(Transformer), 다중 시점(Multi-View) 센서 융합이 이러한 문제를 완화한다.

조명 변화(Illumination Change)는 객체의 외형을 크게 변화시킨다. 야외 로봇은 강한 햇빛, 그림자, 비, 안개, 눈, 야간 환경을 모두 경험하며, 실내에서도 인공 조명, 반사, 눈부심이 발생한다. 따라서 객체 검출기는 다양한 조명 환경으로 충분히 학습되어야 하며, 적응형 전처리(Adaptive Preprocessing)와 노출 제어(Exposure Control)가 함께 사용된다.

실시간 처리(Real-Time Operation)는 자율주행 이동로봇에서 매우 중요한 요구사항이다. 객체 검출은 위치 추정(Localization), 지도 작성(Mapping), 경로 계획(Path Planning), 장애물 회피(Obstacle Avoidance), 통신, 시스템 모니터링과 동시에 수행되어야 한다. 따라서 경량 네트워크(Lightweight Network), 모델 가지치기(Model Pruning), 양자화(Quantization), TensorRT 최적화, GPU 가속, AI 전용 가속기 등이 실시간 성능 확보를 위해 사용된다.

객체 추적(Object Tracking)은 객체 검출을 시간적으로 확장한 기술이다. 여러 프레임(Frame)에 걸쳐 동일한 객체에 지속적인 식별 번호(ID)를 부여하여 이동 경로를 추적한다. 이를 통해 로봇은 객체의 이동 경로를 예측하고 미래의 위치를 추정하며 복잡한 환경에서도 안정적인 상황 인식을 수행할 수 있다.

객체 검출은 깊이 센서(Depth Sensor)와 함께 사용되는 경우가 점점 증가하고 있다. RGB 카메라는 외형 정보를 제공하고, 스테레오 비전(Stereo Vision), RGB-D 카메라, 구조광(Structured Light), ToF(Time-of-Flight) 카메라, 라이다(LiDAR)는 거리 정보를 제공한다. 외형 정보와 깊이 정보를 함께 활용하면 위치 추정, 장애물 분류, 로봇 조작, 안전한 자율주행의 정확도를 크게 향상시킬 수 있다.

최근의 비전 파운데이션 모델(Vision Foundation Model)은 폐쇄형 객체 인식(Closed-Set Recognition)을 넘어 개방형 객체 검출(Open-Vocabulary Detection)을 가능하게 하고 있다. 기존 객체 검출기는 학습한 클래스만 인식할 수 있었지만, 개방형 객체 검출은 자연어(Language)로 설명된 새로운 객체까지 인식할 수 있다. 이러한 기술은 서비스 로봇, 물류 자동화, 인간-로봇 협업(Human-Robot Collaboration)의 유연성을 크게 향상시킨다.

자율주행 이동로봇에서 객체 검출은 단순한 인식 알고리즘이 아니라 지속적으로 동작하는 인식 모듈(Perception Module)이다. 카메라 영상은 매 프레임마다 객체를 검출하고, 객체는 시간에 따라 추적되며, 깊이 정보를 이용하여 실제 위치가 계산된다. 이후 라이다, 레이더(Radar), IMU(Inertial Measurement Unit) 등의 센서 정보와 융합되어 최종적인 환경 표현(Environment Representation)이 생성된다. 이러한 정보는 자율주행, 장애물 회피, 로봇 조작, 안전 감시, 사람과의 상호작용, 자동 검사, 임무 수행의 핵심 기반이 된다.

로봇 시스템이 점점 더 지능화됨에 따라 객체 검출은 단순한 2차원 인식을 넘어 종합적인 3차원 장면 이해(3D Scene Understanding)로 발전하고 있다. 미래의 객체 검출 시스템은 멀티모달 인식(Multimodal Perception), 파운데이션 모델(Foundation Model), 체화형 인공지능(Embodied Intelligence), 지속 학습(Continual Learning), 불확실성 추정(Uncertainty Estimation), 월드 모델(World Model)을 하나의 통합 인식 구조로 결합하게 될 것이다. 이러한 발전을 통해 자율주행 이동로봇은 더욱 복잡한 환경을 이해하고, 객체 간의 의미적 관계를 파악하며, 미래 상황을 예측하고, 다양한 실제 환경에서 사람과 안전하게 협력할 수 있게 될 것이다.

## 02.5 Semantic Segmentation

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

의미론적 분할(Semantic Segmentation)은 영상의 모든 개별 픽셀(Pixel)에 의미론적 클래스(Semantic Category)를 할당하는 컴퓨터 비전(Computer Vision) 기술이다. 전체 영상에 하나의 클래스만 예측하는 영상 분류(Image Classification)나, 경계 상자(Bounding Box)를 이용하여 객체를 검출하는 객체 검출(Object Detection)과 달리, 의미론적 분할은 픽셀 단위(Pixel-Level)로 장면을 이해한다. 모든 픽셀은 도로(Road), 벽(Wall), 바닥(Floor), 사람(Person), 차량(Vehicle), 식생(Vegetation), 선반(Shelf), 기계(Machine), 장애물(Obstacle)과 같은 미리 정의된 클래스에 할당된다. 이러한 세밀한 표현은 자율주행 이동로봇이 객체 수준의 인식보다 훨씬 정밀하게 주변 환경을 이해하도록 해준다.

자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서 의미론적 분할은 작업 환경에 대한 상세한 이해를 제공한다. 창고(Warehouse), 병원(Hospital), 공장(Factory), 공항(Airport), 쇼핑몰(Shopping Center), 야외 도로(Outdoor Road)를 이동하는 로봇은 주행 가능한 영역과 장애물을 구분하는 동시에 구조물과 움직이는 객체를 인식해야 한다. 단순히 사람을 하나의 경계 상자로 검출하는 것이 아니라, 사람을 구성하는 정확한 픽셀을 식별함으로써 더욱 정밀한 주행, 충돌 회피, 공간 추론이 가능해진다.

장면 이해(Scene Understanding)는 의미론적 분할의 가장 중요한 목표 가운데 하나이다. 로봇은 개별 객체뿐 아니라 환경을 구성하는 여러 영역 간의 관계도 이해해야 한다. 바닥(Floor)은 복도(Corridor)와 연결되고, 벽(Wall)은 공간의 경계를 형성하며, 문(Door)은 이동 가능한 통로를 제공한다. 선반(Shelf)은 물품을 보관하고 작업 공간(Workstation)은 특정 기능을 수행하는 영역을 정의한다. 픽셀 단위의 분류는 원시 카메라 영상을 구조화된 의미 지도(Semantic Map)로 변환하여 자율주행, 위치 추정(Localization), 물체 조작(Manipulation), 지능형 의사결정을 지원한다.

의미론적 분할은 영상 분류(Image Classification), 객체 검출(Object Detection), 인스턴스 분할(Instance Segmentation)과는 명확하게 구분된다. 영상 분류는 전체 영상에 하나의 클래스를 부여한다. 객체 검출은 객체의 종류와 경계 상자를 예측한다. 의미론적 분할은 모든 픽셀을 분류하지만 동일한 클래스에 속하는 여러 객체를 하나의 영역으로 취급한다. 반면 인스턴스 분할은 동일한 클래스에 속하는 객체들도 각각 개별적으로 분리한다. 이 네 가지 인식 기술은 점점 더 풍부한 장면 이해 수준을 제공하는 단계적인 관계를 가진다.

의미론적 분할 시스템의 출력은 일반적으로 분할 마스크(Segmentation Mask)로 표현된다. 마스크의 각 픽셀에는 미리 정의된 의미론적 클래스 번호가 저장된다. 사람이 쉽게 결과를 이해할 수 있도록 클래스마다 서로 다른 색상을 부여하여 시각화하는 경우가 많다. 그러나 실제 내부 표현은 단순한 색상이 아니라 숫자로 이루어진 레이블 맵(Label Map)이며, 이는 로봇의 경로 계획(Path Planning)과 제어(Control) 알고리즘에서 직접 활용된다.

픽셀 단위 인식(Pixel-Level Perception)은 자율주행의 안전성을 크게 향상시킨다. 객체 검출에서 사용하는 경계 상자는 실제 객체 외에도 상당한 배경 영역을 포함하는 경우가 많다. 예를 들어 사람의 경계 상자는 사람 주변의 빈 공간까지 포함할 수 있다. 의미론적 분할은 실제 객체가 차지하는 픽셀만을 정확하게 식별하므로 장애물의 형태, 주행 가능한 공간, 안전한 이동 경로를 훨씬 정확하게 계산할 수 있다.

의미론적 분할은 자유 공간 추정(Free-Space Estimation)에도 중요한 역할을 한다. 모든 장애물을 개별적으로 검출하는 대신, 로봇은 주행 가능한 바닥 영역을 직접 분할할 수 있다. 바닥(Floor), 도로(Road), 보도(Sidewalk), 복도(Corridor)로 분류된 픽셀은 이동 가능한 영역을 의미하며, 벽(Wall), 차량(Vehicle), 기계(Machine), 가구(Furniture), 식생(Vegetation)은 이동이 불가능한 영역으로 분류된다. 이러한 자유 공간 분할은 복잡한 카메라 영상을 단순한 주행 가능 지도(Traversability Map)로 변환하여 경로 계획을 크게 단순화한다.

딥러닝 이전의 영상 분할(Image Segmentation)은 대부분 수작업 기반 알고리즘에 의존하였다. 임계값 처리(Thresholding)는 밝기 값을 기준으로 전경과 배경을 분리하였고, 영역 성장(Region Growing)은 인접 픽셀의 유사성을 이용하여 영역을 확장하였다. 워터셰드(Watershed)는 밝기 값을 지형으로 해석하여 영역을 분리하였으며, 그래프 컷(Graph Cut)은 에너지 최소화(Energy Minimization)를 통해 영상을 분할하였다. 이러한 방법은 특정 환경에서는 유용하지만 조명 변화, 복잡한 질감, 다양한 배경에서는 한계를 가진다.

완전 합성곱 신경망(FCN, Fully Convolutional Network)의 등장은 의미론적 분할을 근본적으로 변화시켰다. 기존 CNN이 영상 전체를 하나의 클래스로 분류하였다면, FCN은 완전 연결층(Fully Connected Layer)을 합성곱 계층으로 대체하여 모든 픽셀에 대한 분류를 수행하였다. 이를 통해 공간적인 구조를 유지하면서 종단간 학습(End-to-End Learning)이 가능해졌으며, 의미론적 분할의 성능이 크게 향상되었다.

FCN은 의미론적 분할을 위해 설계된 최초의 성공적인 딥러닝 구조 가운데 하나이다. 기존 CNN은 반복적인 풀링(Pooling)으로 영상 해상도를 지속적으로 감소시킨 후 분류를 수행하였다. FCN은 마지막 분류 계층 대신 학습 가능한 업샘플링(Upsampling)을 사용하여 원래 해상도로 복원하면서 픽셀 단위 예측을 수행하였다. 이 구조는 이후 대부분의 의미론적 분할 네트워크의 기반이 되었다.

인코더-디코더(Encoder-Decoder) 구조는 가장 영향력 있는 의미론적 분할 아키텍처 가운데 하나이다. 인코더는 점차 추상적인 의미 정보를 추출하면서 공간 해상도를 감소시키고, 디코더는 업샘플링을 통해 해상도를 다시 복원한다. 스킵 연결(Skip Connection)은 인코더의 고해상도 정보를 디코더로 직접 전달하여 객체의 경계를 유지하면서도 풍부한 의미 정보를 제공한다. 이러한 구조는 인식 성능과 위치 정확도의 균형을 효과적으로 달성한다.

U-Net은 가장 널리 알려진 인코더-디코더 기반 의미론적 분할 네트워크이다. 원래 의료 영상 분석(Medical Image Analysis)을 위해 개발되었지만, 강력한 스킵 연결을 통해 높은 해상도의 공간 정보를 유지할 수 있다. 비교적 적은 학습 데이터만으로도 우수한 성능을 보여 산업 검사, 농업용 로봇, 의료 영상, 자율주행 이동로봇 등 다양한 분야에서 활용되고 있다.

SegNet은 인코더에서 계산된 풀링 인덱스(Pooling Index)를 디코더에서 재사용하는 효율적인 구조를 제안하였다. 복잡한 역합성곱(Deconvolution) 대신 저장된 풀링 위치를 이용하여 해상도를 복원함으로써 메모리 사용량을 줄이면서도 정확한 객체 경계를 유지할 수 있다. 이러한 특성 때문에 SegNet은 연산 자원이 제한된 임베디드 로봇 플랫폼에서 높은 활용성을 가진다.

DeepLab은 팽창 합성곱(Atrous Convolution 또는 Dilated Convolution)을 도입하여 의미론적 분할 성능을 크게 향상시켰다. 팽창 합성곱은 파라미터 수를 증가시키지 않으면서도 수용 영역(Receptive Field)을 확대할 수 있다. 이를 통해 넓은 문맥(Context) 정보를 활용하면서도 세밀한 공간 정보를 유지할 수 있다. 이후 버전에서는 다중 스케일 특징 추출(Multi-Scale Feature Extraction)과 조건부 랜덤 필드(CRF, Conditional Random Field)를 결합하여 최고 수준의 성능을 달성하였다.

피라미드 장면 분석(Pyramid Scene Parsing) 구조는 다양한 공간 해상도의 정보를 동시에 활용하여 의미론적 분할 성능을 향상시킨다. 작은 영역은 세부적인 외형 정보를 제공하고, 넓은 영역은 전체적인 문맥 정보를 제공한다. 피라미드 풀링(Pyramid Pooling)은 다양한 수용 영역에서 의미 정보를 추출하여 통합함으로써 큰 구조물과 작은 객체를 동시에 효과적으로 인식할 수 있도록 한다.

최근에는 트랜스포머(Transformer) 기반 의미론적 분할 모델이 등장하였다. CNN이 주로 국부적인 공간 관계를 학습하는 반면, 트랜스포머는 자기 주의(Self-Attention)를 이용하여 영상 전체의 관계를 동시에 학습한다. 이러한 전역 문맥(Global Context) 분석은 큰 구조물, 부분적으로 가려진 객체, 주변 문맥이 중요한 복잡한 환경에서 더욱 뛰어난 성능을 제공한다.

의미론적 분할은 픽셀 단위의 정답 데이터(Pixel-Level Annotation)를 필요로 하기 때문에 매우 많은 학습 데이터를 요구한다. 객체 검출이 경계 상자만 표시하면 되는 것과 달리, 의미론적 분할은 모든 픽셀에 의미론적 클래스를 지정해야 한다. 이러한 작업은 매우 많은 시간과 비용이 필요하며, 고품질 데이터셋은 딥러닝 기반 의미론적 분할 시스템의 성능을 결정하는 중요한 요소가 된다.

Cityscapes, ADE20K, COCO Stuff, Mapillary Vistas와 같은 공개 데이터셋은 의미론적 분할 연구를 크게 발전시켰다. Cityscapes는 자율주행 도시 환경을, ADE20K는 다양한 실내외 환경을, COCO Stuff는 객체뿐 아니라 배경 클래스까지 포함하는 의미 정보를 제공한다. Mapillary Vistas는 다양한 날씨와 조명 조건을 포함한 실제 도로 환경을 제공하여 강인한 의미론적 분할 모델 개발을 지원한다.

데이터 증강(Data Augmentation)은 의미론적 분할에서도 매우 중요하다. 랜덤 크롭(Random Crop), 좌우 반전(Horizontal Flip), 크기 변경(Scaling), 회전(Rotation), 밝기 조정(Brightness Adjustment), 색상 변화(Color Jitter), 가우시안 노이즈(Gaussian Noise), 블러(Blur), 날씨 시뮬레이션(Weather Simulation) 등을 이용하여 다양한 환경을 학습시킴으로써 실제 환경에서의 일반화 성능(Generalization)을 향상시킨다.

의미론적 분할의 성능은 일반적으로 IoU(Intersection over Union)를 이용하여 평가한다. IoU는 예측된 분할 영역과 실제 분할 영역의 겹침 정도를 측정하는 지표이다. Mean IoU는 모든 클래스에 대한 IoU를 평균하여 전체 성능을 나타낸다. 픽셀 정확도(Pixel Accuracy)는 올바르게 분류된 픽셀의 비율을 의미하지만, 배경이 많은 경우 실제 성능보다 높게 평가될 수 있다는 한계를 가진다.

객체 경계(Boundary Accuracy)의 정확성도 매우 중요한 평가 요소이다. 두 개의 분할 결과가 동일한 픽셀 정확도를 가지더라도 객체의 경계를 얼마나 정확하게 표현하는지는 크게 다를 수 있다. 정확한 경계는 물체 조작, 장애물 회피, 치수 측정, 자유 공간 추정의 정확도를 높여준다. 최근 연구에서는 전체 정확도뿐 아니라 경계 보존 능력도 중요한 성능 지표로 평가하고 있다.

실시간 처리(Real-Time Performance)는 로봇용 의미론적 분할에서 가장 어려운 기술적 과제 가운데 하나이다. 고해상도 영상은 수백만 개의 픽셀을 포함하며 모든 픽셀을 개별적으로 분류해야 하기 때문에 객체 검출보다 계산량이 훨씬 많다. 이를 해결하기 위해 경량 백본 네트워크(Lightweight Backbone), 효율적인 디코더, 모델 가지치기(Model Pruning), 양자화(Quantization), TensorRT 최적화, GPU 가속, AI 전용 프로세서 등이 활용된다.

작은 객체(Small Object)의 의미론적 분할은 매우 어려운 문제이다. 안전 콘(Safety Cone), 전기 커넥터(Electrical Connector), 검사 결함(Inspection Defect), 멀리 있는 보행자, 작은 공구는 영상에서 차지하는 면적이 매우 작아 반복적인 다운샘플링(Downsampling) 과정에서 쉽게 사라질 수 있다. 다중 스케일 특징 융합(Multi-Scale Feature Fusion), 주의 메커니즘(Attention Mechanism), 고해상도 특징 맵, 경계 인식 손실 함수(Boundary-Aware Loss)가 이러한 문제를 해결하는 데 활용된다.

부분 가림(Occlusion)은 의미론적 분할에서도 중요한 문제이다. 객체의 일부가 주변 구조물에 의해 가려질 경우 사람은 문맥과 경험을 이용하여 전체 객체를 쉽게 추론할 수 있지만, 컴퓨터 비전 시스템은 제한된 시각 정보만으로는 정확한 분할이 어려울 수 있다. 이를 해결하기 위해 주의 메커니즘, 트랜스포머 구조, 멀티모달 센서 융합(Multimodal Sensor Fusion)이 적극적으로 연구되고 있다.

조명 변화(Illumination Variation)는 의미론적 분할의 정확도에 큰 영향을 미친다. 야외 로봇은 강한 햇빛, 그림자, 비, 안개, 눈, 야간 환경을 모두 경험하며, 실내 로봇 역시 다양한 조명과 반사 환경에서 동작한다. 따라서 강인한 의미론적 분할을 위해서는 다양한 환경을 포함하는 데이터셋과 적응형 영상 전처리(Image Preprocessing), 자동 노출 제어(Auto Exposure Control)가 함께 활용된다.

깊이 정보(Depth Information)는 의미론적 분할 성능을 크게 향상시킨다. RGB 영상은 외형 정보를 제공하고, 스테레오 비전(Stereo Vision), RGB-D 카메라, 구조광(Structured Light), ToF(Time-of-Flight) 카메라, 라이다(LiDAR)는 거리 정보를 제공한다. 의미 정보와 기하학적 정보를 함께 융합하면 환경 이해, 장애물 위치 추정, 표면 분류, 물체 조작 계획의 정확도를 크게 향상시킬 수 있다. 이러한 멀티모달 센서 융합은 로봇 인식의 중요한 연구 분야가 되고 있다.

의미론적 분할은 동시적 위치 추정 및 지도 작성(SLAM, Simultaneous Localization and Mapping)과도 자연스럽게 결합된다. 의미 정보를 이용하면 사람이나 차량과 같은 동적 객체를 제거하고 벽, 바닥, 기둥과 같은 안정적인 구조물만을 지도 작성에 활용할 수 있다. 의미 지도(Semantic Map)는 장기 위치 추정(Long-Term Localization), 객체 기반 자율주행, 작업 계획(Task Planning), 사람과의 자연스러운 상호작용을 가능하게 한다.

최근의 비전 파운데이션 모델(Vision Foundation Model)은 의미론적 분할을 고정된 클래스에서 개방형(Open-Vocabulary) 분할로 확장하고 있다. 기존의 의미론적 분할은 학습된 클래스만 인식할 수 있었지만, 자연어와 결합된 개방형 분할은 새로운 객체를 텍스트 설명만으로도 분할할 수 있다. 이러한 기술은 서비스 로봇, 산업 자동화, 물류 시스템, 인간-로봇 협업에서 매우 높은 유연성을 제공한다.

의미론적 분할은 월드 모델(World Model)과 체화형 인공지능(Embodied Intelligence)과도 긴밀하게 결합되고 있다. 미래의 로봇은 개별 영상을 독립적으로 해석하는 것이 아니라 시간적으로 지속되는 의미 정보를 유지하게 된다. 객체, 바닥, 방, 기능 영역은 카메라 시야에서 사라진 이후에도 내부적으로 지속적으로 유지되며, 이러한 지속적인 의미 기억(Persistent Semantic Memory)은 장기 자율주행(Long-Term Autonomy), 작업 추론(Task Reasoning), 복잡한 환경에서의 지능적인 상호작용을 가능하게 한다.

자율주행 이동로봇에서 의미론적 분할은 원시 카메라 영상을 구조화된 의미 정보로 변환하는 지속적인 인식 모듈(Perception Module)로 동작한다. 이러한 의미 정보는 위치 추정(Localization), 자유 공간 추정(Free-Space Estimation), 장애물 회피(Obstacle Avoidance), 물체 조작(Manipulation), 자동 검사(Inspection), 사람과의 상호작용(Human Interaction), 임무 수행(Mission Execution)을 지원한다. 앞으로 멀티모달 인식(Multimodal Perception), 트랜스포머(Transformer), 파운데이션 모델(Foundation Model), 지속 학습(Continual Learning)이 더욱 발전함에 따라 의미론적 분할은 로봇이 복잡한 실제 환경을 이해하고 안전하게 동작하기 위한 가장 핵심적인 기반 기술 가운데 하나로 계속 발전해 나갈 것이다.

## 02.6 Depth and 3D Vision

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

깊이 인식(Depth Perception)은 자율주행 이동로봇(AMR, Autonomous Mobile Robot)이 3차원(Three-Dimensional) 물리 세계를 이해하고 상호작용하기 위해 반드시 필요한 핵심 기능 가운데 하나이다. 일반적인 카메라는 환경을 2차원 영상으로만 촬영하지만, 로봇은 안전한 주행과 정확한 물체 조작, 그리고 지능적인 의사결정을 위해 주변 객체의 거리(Distance), 방향(Orientation), 크기(Size), 공간적 관계(Spatial Relationship)를 추정해야 한다. 깊이 및 3차원 비전(Depth and 3D Vision)은 이러한 기하학적 정보를 제공하여 평면 영상을 실제 환경을 측정할 수 있는 공간 정보로 변환한다.

인간은 다양한 시각 단서를 이용하여 자연스럽게 깊이를 인식한다. 좌우 눈의 양안 시차(Binocular Disparity)는 입체 시각(Stereoscopic Vision)을 제공하며, 움직임(Motion), 원근(Perspective), 그림자(Shadow), 질감 기울기(Texture Gradient), 객체 크기(Object Size), 그리고 경험(Prior Experience) 역시 공간 구조를 이해하는 데 중요한 역할을 한다. 로봇 비전 시스템은 카메라, 능동형 깊이 센서(Active Depth Sensor), 기하학적 모델링(Geometric Modeling), 그리고 머신러닝(Machine Learning)을 이용하여 이러한 능력을 구현한다. 또한 로봇은 카메라뿐 아니라 라이다(LiDAR), 관성측정장치(IMU, Inertial Measurement Unit), 레이더(Radar), 위성항법시스템(GNSS)까지 함께 활용하여 더욱 정확한 3차원 월드 모델(World Model)을 구축할 수 있다.

3차원 인식은 단순히 거리만 측정하는 것이 아니다. 완전한 공간 이해를 위해서는 객체의 위치(Position), 자세(Pose), 형상(Shape), 표면 구조(Surface Geometry), 자유 공간(Free Space), 주행 가능 지형(Traversable Terrain), 그리고 환경 구조(Environment Structure)까지 추정해야 한다. 이러한 정보는 위치 추정(Localization), 동시적 위치 추정 및 지도 작성(SLAM, Simultaneous Localization and Mapping), 장애물 회피(Obstacle Avoidance), 물체 조작(Manipulation), 자동 검사(Inspection), 경로 계획(Path Planning), 자율주행(Navigation)을 지원한다. 신뢰성 있는 깊이 정보가 없다면 로봇은 장애물이 얼마나 가까운지, 물체를 잡을 수 있는지, 안전하게 통과할 수 있는 공간이 존재하는지를 정확하게 판단할 수 없다.

깊이 추정(Depth Estimation)은 크게 수동형(Passive) 방식과 능동형(Active) 방식으로 구분할 수 있다. 수동형 방식은 외부로 빛을 투사하지 않고 일반 카메라만 이용하여 깊이를 추정한다. 스테레오 비전(Stereo Vision), 단안 깊이 추정(Monocular Depth Estimation), 움직임 기반 구조 복원(Structure from Motion)이 대표적인 예이다. 반면 능동형 방식은 적외선(Infrared), 구조광(Structured Light), 레이저(Laser), 전자기파(Electromagnetic Wave) 등을 환경으로 직접 투사하여 깊이를 측정한다. 구조광 카메라(Structured Light Camera), ToF(Time-of-Flight) 센서, RGB-D 카메라, 라이다는 대표적인 능동형 깊이 센서이다.

스테레오 비전(Stereo Vision)은 가장 널리 연구된 수동형 깊이 추정 기술 가운데 하나이다. 일정한 간격(Baseline)으로 배치된 두 대의 카메라가 동일한 장면을 서로 다른 시점에서 동시에 촬영한다. 가까운 물체일수록 두 영상에서 서로 다른 위치에 나타나는 시차(Disparity)가 크게 발생한다. 알려진 카메라 간 거리와 초점 거리(Focal Length)를 이용하여 삼각측량(Triangulation)을 수행하면 실제 거리를 계산할 수 있다. 시차가 클수록 물체는 가까우며, 시차가 작을수록 물체는 멀리 위치한다.

정확한 스테레오 비전을 위해서는 카메라 보정(Camera Calibration)이 필수적이다. 내부 파라미터(Intrinsic Parameter)는 초점 거리, 주점(Principal Point), 렌즈 왜곡(Lens Distortion)을 정의하며, 외부 파라미터(Extrinsic Parameter)는 두 카메라 사이의 상대적인 위치와 방향을 나타낸다. 이러한 보정을 수행하면 에피폴라 선(Epipolar Line)이 수평으로 정렬되도록 영상 보정(Image Rectification)을 수행할 수 있으며, 대응점 탐색(Correspondence Matching)의 계산량을 크게 줄일 수 있다.

스테레오 대응점 탐색(Stereo Correspondence)은 스테레오 비전에서 가장 계산량이 많은 과정 가운데 하나이다. 알고리즘은 왼쪽 영상의 각 픽셀과 동일한 실제 위치를 오른쪽 영상에서 찾아야 한다. 밝기(Intensity), 질감(Texture), 그래디언트(Gradient), 또는 딥러닝 기반 특징 표현을 이용하여 대응점을 찾는다. 모든 픽셀에 대해 깊이를 계산하는 방식은 밀집 스테레오(Dense Stereo)라 하며, 일부 특징점만 계산하는 방식은 희소 스테레오(Sparse Stereo)라고 한다. 대응점의 정확도는 최종 깊이 추정 성능을 직접 결정한다.

시차 맵(Disparity Map)은 스테레오 비전의 중간 결과물이다. 각 픽셀에는 대응점 사이의 시차 값이 저장된다. 일반적으로 밝은 영역은 시차가 큰 가까운 물체를 의미하고, 어두운 영역은 시차가 작은 먼 구조물을 의미한다. 시차 맵은 카메라 기하학(Camera Geometry)을 이용하여 실제 거리 정보를 가지는 깊이 맵(Depth Map)으로 변환된다.

깊이 맵(Depth Map)은 카메라와 각 픽셀 사이의 실제 거리를 표현한 영상이다. 카메라 배치에 의존하는 시차 맵과 달리, 깊이 맵은 미터(Meter) 또는 밀리미터(Millimeter) 단위의 실제 거리를 저장한다. 이를 이용하여 로봇은 장애물까지의 거리 측정, 객체 크기 추정, 자유 공간 계산, 표면 복원(Surface Reconstruction), 물체 조작 계획을 수행할 수 있다. 현대의 로봇 시스템은 RGB 영상과 깊이 맵을 동시에 처리하여 더욱 풍부한 환경 이해를 수행한다.

단안 깊이 추정(Monocular Depth Estimation)은 하나의 카메라 영상만으로 3차원 구조를 추정하는 기술이다. 스테레오 비전과 달리 기하학적 시차를 직접 계산할 수 없으므로 원근, 음영(Shading), 질감 기울기, 객체 크기, 가림(Occlusion), 의미 정보(Semantic Context)와 같은 시각적 단서를 이용한다. 최근에는 대규모 데이터셋으로 학습한 딥러닝 모델이 단일 카메라만으로도 상당히 정확한 깊이 예측을 수행할 수 있게 되었다.

그러나 단안 깊이 추정은 본질적으로 스케일 모호성(Scale Ambiguity)을 가진다. 하나의 영상만으로는 실제 절대 거리를 정확하게 결정할 수 없다. 동일한 영상은 크기가 다른 실제 환경에서도 생성될 수 있기 때문이다. 따라서 실제 로봇에서는 IMU, 바퀴 오도메트리(Wheel Odometry), 알려진 객체 크기, 환경에 대한 사전 정보 등을 함께 이용하여 실제 거리 스케일(Metric Scale)을 복원한다.

움직임 기반 구조 복원(SfM, Structure from Motion)은 이동하는 카메라로 촬영한 연속 영상을 이용하여 3차원 환경을 재구성하는 기술이다. 여러 대의 카메라를 사용하는 대신 하나의 이동 카메라만 이용하여 카메라의 움직임과 환경 구조를 동시에 추정한다. 특징 추출(Feature Extraction), 특징 매칭(Feature Matching), 기하학적 최적화(Geometric Optimization), 번들 조정(Bundle Adjustment)을 수행하여 희소한 3차원 포인트 클라우드(Point Cloud)를 생성한다. SfM은 비전 기반 SLAM의 중요한 기반 기술이다.

비주얼 오도메트리(Visual Odometry)는 연속된 영상만을 이용하여 로봇의 이동량을 계산하는 기술이다. 전체 3차원 환경을 복원하는 대신 카메라의 상대적인 이동(Translation)과 회전(Rotation)을 추정하는 데 집중한다. 특징 추적(Feature Tracking), 에피폴라 기하학(Epipolar Geometry), 최적화 기법을 이용하여 이동 경로를 계산한다. GPS 신호가 없는 실내, 터널, 숲, 도심에서도 자율주행을 가능하게 하는 핵심 기술이다.

동시적 위치 추정 및 지도 작성(SLAM)은 깊이 추정과 위치 추정을 동시에 수행하는 기술이다. 로봇은 미지의 환경을 이동하면서 자신의 위치를 추정하는 동시에 일관성 있는 3차원 지도를 생성한다. 특징 기반 방식(Feature-Based Method)은 희소한 랜드마크를 이용하고, 밀집 방식(Dense Method)은 표면과 점유 공간을 상세하게 복원한다. 의미 지도(Semantic Map)는 기하학적 구조뿐 아니라 객체의 의미 정보까지 함께 저장하여 더욱 지능적인 환경 표현을 제공한다.

구조광 센서(Structured Light Sensor)는 적외선 패턴을 환경으로 투사하여 깊이를 측정한다. 카메라는 물체에 의해 변형된 패턴을 관찰하고, 기준 패턴과 비교하여 깊이를 계산한다. 구조광은 짧은 거리에서 매우 높은 정확도를 제공하며 가시광 조명의 영향을 비교적 적게 받는다. 따라서 실내 서비스 로봇, 산업 검사, 로봇 조작 분야에서 널리 활용된다.

ToF(Time-of-Flight) 카메라는 빛이 이동하는 시간을 직접 측정하여 거리를 계산한다. 적외선 광원을 방출한 후 물체에서 반사되어 돌아오는 시간을 측정하면 빛의 속도를 이용하여 거리를 계산할 수 있다. 현대의 ToF 센서는 영상 프레임 속도로 밀집된 깊이 영상을 생성할 수 있으며, 소형화가 가능하여 임베디드 로봇 시스템에 적합하다.

RGB-D 카메라(RGB-D Camera)는 일반 RGB 영상과 깊이 영상을 동시에 획득하는 센서이다. 하나의 프레임에서 컬러 정보와 깊이 정보가 픽셀 단위로 정렬되어 제공된다. 이러한 멀티모달 정보는 의미론적 인식과 기하학적 인식을 동시에 수행할 수 있도록 해준다. RGB-D 센서는 서비스 로봇, 물류 자동화, 연구용 플랫폼, 물체 조작 분야에서 표준적인 센서로 자리 잡고 있다.

라이다(LiDAR)는 레이저를 이용하여 거리를 측정하는 센서이다. 회전형(Mechanical) 라이다는 레이저를 회전시키며 주변 환경을 스캔하여 수백만 개의 3차원 포인트를 생성한다. 최근에는 기계적 회전이 없는 솔리드 스테이트(Solid-State) 라이다가 등장하여 크기와 무게, 유지보수 부담을 줄이고 있다. 라이다는 자율주행 자동차, 야외 로봇, 대규모 환경 지도 작성에서 가장 정확하고 신뢰성 높은 깊이 센서 가운데 하나이다.

포인트 클라우드(Point Cloud)는 3차원 환경을 표현하는 가장 대표적인 방식이다. 각 포인트는 공간 좌표뿐 아니라 밝기(Intensity), 색상(Color), 법선 벡터(Surface Normal), 의미 정보(Semantic Label) 등을 함께 저장할 수 있다. 규칙적인 영상 격자와 달리 포인트 클라우드는 실제 3차원 구조를 자연스럽게 표현할 수 있으며, 정합(Registration), 필터링(Filtering), 분할(Segmentation), 표면 복원에 활용된다.

표면 복원(Surface Reconstruction)은 포인트 클라우드를 연속적인 3차원 표면으로 변환하는 과정이다. 인접한 포인트를 연결하여 다각형 메시(Polygon Mesh)를 생성하면 충돌 검사(Collision Checking), 치수 측정(Dimensional Measurement), 시뮬레이션(Simulation), 시각화(Visualization), 로봇 조작 계획에 활용할 수 있다. 체적 복원(Volumetric Reconstruction)은 점유 공간과 자유 공간까지 함께 추정하여 자율 탐사와 경로 계획을 지원한다.

점유 격자 지도(Occupancy Grid)는 또 다른 대표적인 3차원 환경 표현 방법이다. 공간을 작은 복셀(Voxel) 단위로 나누고 각 복셀에 점유(Occupied), 자유(Free), 미확인(Unknown)의 확률을 저장한다. 이러한 지도는 장애물 회피, 탐사 계획, 센서 융합, 장기 환경 모델링에 널리 활용된다. 옥트리(Octree)는 환경 복잡도에 따라 복셀 크기를 조절하여 메모리 사용량을 크게 줄일 수 있다.

센서 융합(Sensor Fusion)은 서로 다른 센서의 장점을 결합하여 깊이 추정의 신뢰성을 향상시킨다. 카메라는 풍부한 색상과 의미 정보를 제공하지만 조명 변화에 취약하다. 라이다는 매우 정확한 거리 정보를 제공하지만 외형 정보가 부족하다. 레이더는 악천후에서도 안정적으로 동작하지만 해상도가 낮다. IMU는 움직임 정보를 제공하며 GNSS는 야외 절대 위치를 제공한다. 이러한 센서를 함께 융합하면 단일 센서보다 훨씬 강인한 3차원 인식이 가능하다.

딥러닝(Deep Learning)은 3차원 비전에도 큰 변화를 가져왔다. 신경망은 단안 깊이 추정, 스테레오 대응점 보정, 희소 포인트 클라우드 보완(Point Cloud Completion), 표면 복원, 3차원 객체 분류, 의미론적 장면 이해를 수행할 수 있다. PointNet, PointNet++, 희소 합성곱 네트워크(Sparse Convolution Network), 복셀 트랜스포머(Voxel Transformer), 그래프 신경망(Graph Neural Network)은 3차원 데이터를 직접 처리하는 대표적인 모델이다.

3차원 객체 검출(3D Object Detection)은 2차원 경계 상자가 아니라 실제 공간상의 3차원 경계 상자를 추정한다. 3차원 경계 상자는 객체의 위치, 크기, 방향까지 포함한다. 이를 통해 로봇은 객체의 이동 경로를 예측하고 충돌 위험을 평가하며, 물체 조작 계획과 공간 구조 이해를 훨씬 정확하게 수행할 수 있다.

실시간 처리(Real-Time Processing)는 3차원 비전에서도 매우 중요한 요구사항이다. 깊이 추정, 포인트 클라우드 처리, 센서 융합, 위치 추정, 지도 작성, 경로 계획은 모두 제한된 연산 자원을 공유한다. GPU(Graphics Processing Unit) 가속, AI 전용 프로세서, 최적화된 수치 계산 알고리즘, 경량 신경망 구조를 이용하여 복잡한 3차원 인식 파이프라인을 실시간으로 실행할 수 있도록 한다.

깊이 센서는 실제 환경에서 다양한 어려움에 직면한다. 반사율이 높은 표면, 투명한 물체, 질감이 부족한 영역, 안개, 비, 먼지, 강한 햇빛, 센서 노이즈, 모션 블러(Motion Blur), 움직이는 객체, 다중 반사(Multipath Reflection)는 깊이 측정의 정확도를 크게 저하시킨다. 따라서 실제 로봇 시스템은 불확실성 추정(Uncertainty Estimation), 센서 중복(Redundancy), 적응형 필터링(Adaptive Filtering), 신뢰도 모델링(Confidence Modeling), 멀티모달 센서 융합을 이용하여 안정적인 동작을 유지한다.

미래의 3차원 비전 시스템은 파운데이션 비전 모델(Foundation Vision Model), 멀티모달 학습(Multimodal Learning), 월드 모델(World Model), 체화형 인공지능(Embodied Intelligence)을 하나의 통합 인식 구조로 결합하게 될 것이다. 기하학, 의미 정보, 움직임, 상호작용을 각각 독립적으로 처리하는 것이 아니라 지속적으로 변화하는 하나의 3차원 세계 모델을 구축하게 된다. 이러한 통합 모델은 자율주행 이동로봇이 복잡한 환경을 이해하고, 미래 상황을 예측하며, 사람과 자연스럽게 협력하고, 더욱 안전하고 신뢰성 높은 지능형 작업을 수행할 수 있도록 하는 핵심 기반 기술이 될 것이다.

## 02.7 Real-Time Vision Pipeline

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

실시간 비전 파이프라인(Real-Time Vision Pipeline)은 원시 센서 데이터(Raw Sensor Data)를 엄격한 시간 제약(Time Constraint) 안에서 실행 가능한 정보(Actionable Information)로 지속적으로 변환하는 인식(Perception), 연산(Computation), 의사결정(Decision Making) 단계들의 통합 처리 구조이다. 정확도만을 우선하는 오프라인 컴퓨터 비전(Offline Computer Vision)과 달리, 실시간 로봇 비전은 자율주행, 장애물 회피, 물체 조작, 자율 의사결정을 즉시 수행할 수 있을 만큼 빠르게 동작해야 한다. 따라서 파이프라인의 모든 단계는 정확도, 지연 시간(Latency), 계산 효율성(Computational Efficiency), 시스템 신뢰성(System Reliability)의 균형을 고려하여 최적화되어야 한다.

자율주행 이동로봇(AMR, Autonomous Mobile Robot)은 카메라(Camera), 깊이 센서(Depth Sensor), 라이다(LiDAR), 레이더(Radar), 관성측정장치(IMU, Inertial Measurement Unit) 등 다양한 센서로부터 방대한 데이터를 지속적으로 수집한다. 이러한 데이터는 동기화(Synchronization), 처리(Processing), 해석(Interpretation), 환경 이해(Environment Understanding)를 거쳐 제어 명령(Control Command)으로 변환된다. 전체 인식 파이프라인은 일반적으로 초당 30\~100프레임 이상의 속도로 반복 수행되며, 처리 시간이 지연되면 주행 정확도와 안전성이 크게 저하될 수 있다.

실시간 비전 파이프라인은 일반적으로 여러 개의 상호 연결된 처리 모듈(Processing Module)로 구성된다. 센서 획득(Sensor Acquisition)은 다양한 센서의 데이터를 수집하고, 전처리(Preprocessing)는 영상 품질을 향상시키며 센서 잡음을 제거한다. 특징 추출(Feature Extraction)은 중요한 시각 정보를 추출하고, 고수준 인식(High-Level Perception)은 객체 검출(Object Detection), 의미론적 분할(Semantic Segmentation), 깊이 추정(Depth Estimation), 객체 추적(Tracking), 장면 이해(Scene Understanding)를 수행한다. 이후 센서 융합(Sensor Fusion), 위치 추정(Localization), 지도 작성(Mapping)을 거쳐 최종적으로 경로 계획(Path Planning)과 제어(Control)가 수행된다.

센서 획득(Sensor Acquisition)은 전체 파이프라인의 시작 단계이다. 카메라는 컬러 영상을 촬영하고, 깊이 센서는 거리 정보를 제공하며, 라이다는 3차원 포인트 클라우드(Point Cloud)를 생성하고, 레이더는 악천후에서도 움직이는 물체를 탐지하며, IMU는 로봇의 움직임을 측정한다. 각각의 센서는 서로 다른 주기(Frequency), 해상도(Resolution), 통신 인터페이스(Communication Interface), 지연 시간 특성을 가진다. 효율적인 데이터 획득 시스템은 프레임 손실 없이 모든 데이터를 안정적으로 수집해야 한다.

시간 동기화(Time Synchronization)는 여러 센서를 동시에 사용하는 시스템에서 매우 중요하다. 카메라 영상, 깊이 데이터, IMU 정보, 라이다 스캔이 동일한 시점의 환경을 나타내야 센서 융합이 정확하게 수행될 수 있다. 하드웨어 트리거(Hardware Trigger), 정밀 시계 동기화(Precision Clock Synchronization), 타임스탬프 보정(Timestamp Correction), 보간(Interpolation) 기법 등을 이용하여 서로 다른 센서의 데이터를 동일한 시간축으로 정렬한다. 정확한 시간 동기화는 위치 추정, 객체 추적, 3차원 재구성의 정확도를 크게 향상시킨다.

카메라 보정(Camera Calibration)은 신뢰성 있는 인식을 위한 필수 과정이다. 내부 파라미터(Intrinsic Parameter)는 초점 거리(Focal Length), 주점(Principal Point), 렌즈 왜곡(Lens Distortion)을 정의하며, 외부 파라미터(Extrinsic Parameter)는 여러 센서 사이의 상대적인 위치와 방향을 나타낸다. 이러한 보정 정보는 영상 보정(Image Rectification), 좌표 변환(Coordinate Transformation), 센서 융합의 정확도를 결정한다. 보정 오차는 전체 인식 파이프라인에 영향을 미치므로 장기간 운용 시에는 주기적인 재보정(Recalibration)이 필요하다.

영상 전처리(Image Preprocessing)는 고수준 인식 이전에 영상 품질을 향상시키는 과정이다. 원시 영상에는 센서 노이즈(Sensor Noise), 모션 블러(Motion Blur), 노출 변화(Exposure Variation), 렌즈 왜곡, 압축 오류(Compression Artifact) 등이 포함될 수 있다. 노이즈 제거, 히스토그램 평활화(Histogram Equalization), 화이트 밸런스(White Balance), 감마 보정(Gamma Correction), 왜곡 보정(Distortion Correction), 영상 정규화(Image Normalization)는 계산량을 크게 증가시키지 않으면서도 이후 인식 성능을 크게 향상시킨다.

영상 크기 조정(Image Resizing)은 전처리 과정에서 자주 수행된다. 대부분의 딥러닝 모델은 고정된 입력 크기를 요구하기 때문이다. 높은 해상도의 영상은 더 많은 정보를 제공하지만 계산량이 크게 증가한다. 반대로 지나치게 작은 영상은 멀리 있는 사람이나 작은 장애물, 검사 대상과 같은 중요한 정보를 잃을 수 있다. 따라서 영상 해상도는 정확도와 실시간 처리 성능 사이에서 적절한 균형을 찾아야 한다.

관심 영역 선택(ROI, Region of Interest Selection)은 계산 효율성을 높이는 중요한 기법이다. 전체 영상을 모두 처리하는 대신 주행과 관련 없는 하늘(Sky), 로봇의 몸체(Robot Body), 사용자 인터페이스 영역 등을 제외하고 중요한 부분만 분석한다. 이전 프레임의 검출 결과나 현재 주행 상황을 이용하여 동적으로 관심 영역을 선택하면 계산량을 더욱 줄일 수 있다.

특징 추출(Feature Extraction)은 원시 픽셀을 인식 가능한 특징 표현으로 변환하는 과정이다. 전통적인 방법은 에지(Edge), 코너(Corner), 질감(Texture), 기하학적 구조를 수작업 기반 알고리즘으로 추출하였다. 현대의 실시간 파이프라인은 합성곱 신경망(CNN, Convolutional Neural Network)이나 트랜스포머(Transformer)를 이용하여 계층적인 특징을 자동으로 학습한다. 이러한 특징은 객체 검출, 의미론적 분할, 깊이 추정, 장면 이해의 기반이 된다.

객체 검출(Object Detection)은 환경에 존재하는 중요한 객체를 인식하는 과정이다. 사람(Pedestrian), 지게차(Forklift), 선반(Shelf), 팔레트(Pallet), 차량(Vehicle), 기계(Machine), 안전 콘(Safety Cone), 검사 대상(Inspection Target), 움직이는 장애물 등을 경계 상자(Bounding Box), 클래스(Class), 신뢰도(Confidence Score)와 함께 추정한다. 현대의 실시간 로봇 시스템에서는 정확도와 속도의 균형이 뛰어난 YOLO 계열의 검출기가 가장 널리 사용된다.

의미론적 분할(Semantic Segmentation)은 객체 검출을 보완하여 모든 픽셀을 의미론적 클래스로 분류한다. 객체 위치뿐 아니라 바닥(Floor), 벽(Wall), 도로(Road), 식생(Vegetation), 기계(Machine), 주행 가능 공간(Traversable Space) 등을 정확하게 구분한다. 이러한 픽셀 수준의 인식은 자유 공간 추정(Free-Space Estimation), 장애물 경계 계산, 물체 조작 계획, 자율주행 안전성을 크게 향상시킨다. 객체 검출과 의미론적 분할을 함께 사용하면 더욱 풍부한 환경 이해가 가능해진다.

깊이 추정(Depth Estimation)은 2차원 영상을 실제 3차원 공간 정보로 확장한다. 스테레오 비전(Stereo Vision), RGB-D 카메라, ToF(Time-of-Flight) 센서, 구조광(Structured Light), 단안 깊이 추정(Monocular Depth Estimation), 라이다는 모두 객체와 환경의 거리 정보를 제공한다. 깊이 정보는 장애물 크기 추정, 표면 복원(Surface Reconstruction), 주행 가능 영역 분석, 물체 조작 계획에 필수적이다.

객체 추적(Object Tracking)은 연속된 영상에서 동일한 객체를 지속적으로 추적하는 기능이다. 각 프레임을 독립적으로 처리하는 대신 동일한 객체에 일정한 식별 번호(ID)를 부여하여 시간적으로 연결한다. 이동 경로(Trajectory), 속도(Velocity), 미래 위치를 예측할 수 있으며, 일시적인 검출 실패가 발생해도 안정적인 상황 인식(Situational Awareness)을 유지할 수 있다.

다중 객체 추적(Multi-Object Tracking)은 여러 객체를 동시에 추적하는 기술이다. 데이터 연관(Data Association)은 새로운 검출 결과가 이전 프레임의 어떤 객체와 동일한지를 판단하며, 운동 예측(Motion Prediction)은 다음 위치를 추정한다. 칼만 필터(Kalman Filter), 헝가리안 알고리즘(Hungarian Algorithm), ByteTrack, DeepSORT, 트랜스포머 기반 추적기는 현재 가장 널리 사용되는 기술이다.

센서 융합(Sensor Fusion)은 서로 다른 센서의 장점을 결합하는 과정이다. 카메라는 풍부한 외형 정보를 제공하고, 라이다는 정확한 거리 정보를 제공하며, 레이더는 악천후에서도 안정적으로 동작한다. IMU는 움직임을 측정하고 바퀴 오도메트리(Wheel Odometry)는 이동 거리를 제공한다. 이러한 정보를 통합하면 단일 센서보다 훨씬 강인한 환경 인식이 가능하다.

센서 융합은 여러 단계에서 수행될 수 있다. 초기 융합(Early Fusion)은 원시 데이터를 직접 결합하고, 특징 수준 융합(Feature-Level Fusion)은 신경망 내부의 특징을 통합하며, 결정 수준 융합(Decision-Level Fusion)은 각각의 인식 결과를 확률적으로 결합한다. 어떤 방식을 선택할지는 센서 특성, 계산 자원, 통신 대역폭, 응용 분야에 따라 달라진다.

위치 추정(Localization)은 로봇이 현재 환경에서 자신의 위치를 지속적으로 계산하는 과정이다. 비주얼 오도메트리(Visual Odometry)는 카메라만 이용하여 이동량을 계산하며, SLAM은 센서 데이터를 이용하여 지도 작성과 위치 추정을 동시에 수행한다. 의미 랜드마크(Semantic Landmark), 기하학적 특징, IMU, 바퀴 인코더, GNSS는 장기간 운용 시 위치 정확도를 향상시키는 중요한 정보가 된다.

환경 지도 작성(Environmental Mapping)은 누적된 센서 데이터를 지속적인 공간 정보로 변환하는 과정이다. 점유 격자 지도(Occupancy Grid)는 자유 공간과 장애물을 표현하고, 포인트 클라우드는 3차원 구조를 표현하며, 메시(Mesh)는 연속적인 표면을 생성한다. 의미 지도(Semantic Map)는 객체 종류와 위치를 함께 저장하여 자율주행, 검사, 디지털 트윈(Digital Twin), 장기 자율 운용을 지원한다.

장면 이해(Scene Understanding)는 단순한 객체 인식을 넘어 객체들 사이의 관계를 이해하는 과정이다. 로봇은 작업 공간, 통로, 위험 구역, 상호작용 가능한 객체를 구분하고 상황(Context)을 함께 이해해야 한다. 예를 들어 사람과 지게차가 가까이 있는 상황은 보호 울타리 뒤에 사람이 있는 상황과 전혀 다른 안전 의미를 가진다. 이러한 문맥(Context) 이해는 고도화된 자율주행에서 매우 중요하다.

의사결정(Decision Making)은 환경 이해 결과를 실제 행동으로 변환하는 단계이다. 경로 계획(Path Planning)은 안전한 이동 경로를 계산하고, 장애물 회피는 즉각적인 회피 동작을 생성하며, 물체 조작 계획은 집기(Grasp) 경로를 계산한다. 검사 시스템은 검사 순서를 계획하고, 임무 관리자(Mission Manager)는 전체 작업을 조정한다. 모든 의사결정은 앞선 인식 결과를 기반으로 수행된다.

실시간 스케줄링(Real-Time Scheduling)은 모든 인식 모듈이 제한된 시간 안에 완료되도록 관리하는 기술이다. 장애물 검출, 긴급 제동(Emergency Braking), 위치 추정은 지도 작성이나 장기 의미 분석보다 훨씬 높은 우선순위를 가진다. 현대의 로봇 소프트웨어 프레임워크는 중요한 작업이 항상 정해진 시간 안에 수행되도록 결정론적 스케줄링(Deterministic Scheduling)을 사용한다.

파이프라인 지연 시간(Pipeline Latency)은 센서가 데이터를 획득한 순간부터 로봇이 실제 행동을 수행하기까지 걸리는 전체 시간을 의미한다. 센서 획득, 전처리, 신경망 추론, 센서 융합, 경로 계획, 제어 등 모든 단계가 지연 시간을 증가시킨다. 지연 시간이 길어질수록 로봇은 오래된 정보를 이용하여 판단하게 되므로 특히 고속 주행에서는 매우 위험해질 수 있다. 따라서 전체 지연 시간을 최소화하는 것이 핵심 목표이다.

파이프라인 처리량(Pipeline Throughput)은 초당 처리 가능한 프레임 수를 의미한다. 높은 처리량은 더욱 부드러운 환경 인식을 가능하게 하지만, 처리량만 높고 지연 시간이 길다면 실시간 시스템으로는 적합하지 않다. 따라서 실시간 로봇 시스템은 처리량과 지연 시간을 동시에 최적화해야 한다.

병렬 처리(Parallel Processing)는 계산 효율성을 크게 향상시키는 핵심 기술이다. 멀티코어 CPU, GPU(Graphics Processing Unit), NPU(Neural Processing Unit), AI 가속기 등을 이용하여 여러 작업을 동시에 수행한다. 하나의 프레임이 전처리되는 동안 다른 프레임은 객체 검출이나 추적을 수행하는 방식으로 하드웨어 자원을 최대한 활용하여 전체 지연 시간을 줄인다.

GPU는 현재 딥러닝 기반 실시간 비전의 핵심 연산 장치이다. 수천 개의 병렬 코어를 이용하여 합성곱 신경망, 트랜스포머, 행렬 연산을 매우 빠르게 수행한다. TensorRT 최적화, 혼합 정밀도(Mixed Precision), 모델 양자화(Model Quantization), 연산자 융합(Operator Fusion)은 실행 속도를 더욱 향상시키면서 메모리 사용량과 전력 소비를 줄인다.

엣지 AI(Edge AI)는 클라우드가 아닌 로봇 내부에서 직접 인식을 수행하는 방식이다. 로컬 추론(Local Inference)은 네트워크 지연을 제거하고 통신이 불가능한 환경에서도 자율주행을 가능하게 한다. 또한 개인정보 보호와 시스템 신뢰성도 향상된다. 최신 자율주행 이동로봇은 고성능 GPU와 AI 프로세서를 탑재하여 대부분의 인식 기능을 자체적으로 수행한다.

자원 최적화(Resource Optimization)는 실제 로봇에서 매우 중요하다. 로봇은 계산 성능, 메모리, 배터리, 발열 모두 제한되어 있기 때문이다. 경량 신경망(Lightweight Network), 효율적인 백본 구조, 구조적 가지치기(Structured Pruning), 지식 증류(Knowledge Distillation), 동적 추론(Dynamic Inference), 적응형 해상도 처리(Hardware-Aware Optimization)는 이러한 제약 속에서도 실시간 성능을 유지하도록 도와준다.

파이프라인의 강인성(Robustness)은 계산 속도뿐 아니라 시스템의 안정성까지 포함한다. 실제 환경에서는 센서 고장, 통신 장애, 조명 변화, 악천후, 움직이는 장애물, 부분 가림, 보정 오차, 하드웨어 노후화가 발생할 수 있다. 오류 검출(Fault Detection), 불확실성 추정(Uncertainty Estimation), 신뢰도 모델링(Confidence Modeling), 센서 중복(Redundant Sensing), 적응형 파라미터 조정(Adaptive Parameter Adjustment)은 이러한 상황에서도 시스템이 안전하게 동작하도록 한다.

소프트웨어 아키텍처(Software Architecture)는 전체 파이프라인의 유지보수성과 확장성을 크게 좌우한다. 센서 획득, 전처리, 추론, 센서 융합, 위치 추정, 지도 작성, 경로 계획을 독립적인 모듈로 분리하고 표준 인터페이스(Standard Interface)를 이용하여 연결한다. ROS(Robot Operating System)와 같은 미들웨어(Middleware)는 메시지 통신, 시간 동기화, 하드웨어 추상화(Hardware Abstraction), 분산 처리(Distributed Execution)를 지원한다.

테스트(Test)와 검증(Validation)은 실시간 비전 파이프라인 개발에서 필수적인 과정이다. 각 모듈은 단위 테스트(Unit Test)를 수행하고, 전체 시스템은 기록된 데이터셋과 시뮬레이터(Simulator), 실제 환경(Field Test)를 이용하여 검증된다. 지속적인 성능 모니터링을 통해 모델 업데이트, 센서 재보정, 성능 개선을 수행함으로써 장기간 안정적인 운용이 가능해진다.

미래의 실시간 비전 파이프라인은 멀티모달 센싱(Multimodal Sensing), 파운데이션 비전 모델(Foundation Vision Model), 월드 모델(World Model), 체화형 인공지능(Embodied Intelligence), 지속 학습(Continual Learning), 예측 기반 추론(Predictive Reasoning)을 하나의 통합 인식 구조로 결합하는 방향으로 발전하고 있다. 미래의 자율주행 이동로봇은 개별 알고리즘을 독립적으로 실행하는 것이 아니라 환경에 대한 지속적인 내부 표현(Persistent Internal Representation)을 유지하면서 관찰, 예측, 상호작용, 경험을 통해 지속적으로 환경을 이해하게 될 것이다. 이러한 통합 파이프라인은 더욱 안전한 자율주행, 높은 수준의 지능형 의사결정, 뛰어난 운용 효율성, 그리고 복잡한 실제 환경에서의 완전한 자율성을 실현하는 핵심 기술이 될 것이다.

## 02.8 Field Vision Failure Cases

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

현장 비전 실패(Field Vision Failure)란 실제 환경에서 컴퓨터 비전(Computer Vision) 시스템이 잘못되거나, 불완전하거나, 지연되거나, 신뢰할 수 없는 인식 결과를 생성하는 상황을 의미한다. 조명, 객체 배치, 환경 조건이 철저히 제어되는 실험실과 달리 자율주행 이동로봇(AMR, Autonomous Mobile Robot)은 예측하기 어려운 날씨, 조명 변화, 움직이는 장애물, 센서 성능 저하, 하드웨어 제약 속에서도 지속적으로 동작해야 한다. 이러한 실패 사례를 이해하는 것은 매우 중요하다. 인식 오류는 자율주행, 장애물 회피, 물체 조작, 임무 수행 성공률에 직접적인 영향을 미치기 때문이다. 따라서 신뢰성 있는 로봇 비전 시스템은 단순히 평균 정확도가 높은 것이 아니라 실패 상황에서도 안전하게 동작하도록 설계되어야 한다.

많은 비전 알고리즘은 벤치마크(Benchmark)에서는 매우 높은 성능을 보이지만 실제 현장에서는 예상하지 못한 문제를 경험한다. 공개 데이터셋은 비교적 균형 잡힌 환경에서 수집되고 정확하게 라벨링되어 있지만, 실제 현장에는 드문 사건(Rare Event), 손상된 시설, 임시 장애물, 특이한 객체 형태, 예상하지 못한 사람의 행동 등이 존재한다. 이러한 실험실과 실제 환경의 차이는 일반적으로 시뮬레이션-현실 간격(Sim-to-Real Gap) 또는 실험실-현장 간격(Lab-to-Field Gap)이라고 불린다. 이 차이를 줄이기 위해서는 벤치마크 성능만으로는 충분하지 않으며, 지속적인 현장 검증(Field Validation), 성능 모니터링(Monitoring), 적응형 인식(Adaptive Perception)이 필요하다.

조명 변화(Illumination Variation)는 가장 흔한 비전 실패 원인 가운데 하나이다. 카메라는 물체 자체가 아니라 물체에서 반사되는 빛을 관측하기 때문에 인식 성능은 조명 조건에 크게 영향을 받는다. 강한 햇빛, 깊은 그림자, 역광(Backlighting), 터널, 야간 환경, 깜빡이는 조명, 반사광, 급격한 노출 변화는 동일한 물체의 외형을 크게 변화시킨다. 실제 환경은 변하지 않았더라도 영상이 크게 달라질 수 있으며, 이는 객체 인식 정확도를 크게 저하시킨다.

과다 노출(Overexposure)은 너무 많은 빛이 카메라 센서에 입력될 때 발생한다. 밝은 영역은 센서의 최대 밝기 값을 초과하여 질감(Texture) 정보가 사라진다. 흰색 벽, 반사되는 차량, 금속 기계, 광택이 있는 바닥, 직사광선은 과다 노출을 쉽게 발생시킨다. 이 경우 객체의 경계가 사라지고 특징 추출이 어려워지며 중요한 장애물을 완전히 놓칠 수도 있다.

과소 노출(Underexposure)은 반대로 영상이 지나치게 어두운 경우이다. 조명이 부족하면 센서 노이즈(Sensor Noise)가 실제 영상 정보를 압도하게 된다. 야간 창고, 지하 시설, 어두운 복도, 해가 진 야외 환경에서는 중요한 시각 정보가 사라지고 객체 경계가 모호해진다. 이로 인해 객체 검출의 신뢰도와 정확도가 크게 감소한다.

고동적 범위(High Dynamic Range, HDR) 환경은 특히 어려운 인식 환경이다. 하나의 영상 안에 매우 밝은 영역과 매우 어두운 영역이 동시에 존재하여 카메라가 표현할 수 있는 밝기 범위를 초과하게 된다. 창고 출입구, 터널 입구, 실내 창문 주변, 한낮의 건설 현장은 대표적인 예이다. 일반 카메라는 밝은 영역과 어두운 영역을 동시에 정확하게 표현할 수 없기 때문에 어느 한쪽의 정보가 손실될 수밖에 없다.

모션 블러(Motion Blur)는 카메라와 환경 사이의 상대적인 움직임이 노출 시간보다 빠를 때 발생한다. 빠르게 이동하는 로봇, 진동하는 플랫폼, 빠르게 움직이는 객체, 긴 노출 시간은 모두 영상을 흐리게 만든다. 모션 블러는 특징 추출, 객체 검출, 광류(Optical Flow), 위치 추정(Localization)의 정확도를 크게 저하시킨다. 울퉁불퉁한 지형을 주행하는 산업용 로봇이나 고속 이동하는 자율주행 차량에서 자주 발생하는 문제이다.

렌즈 오염(Lens Contamination)은 매우 현실적인 실패 원인이다. 먼지(Dust), 진흙(Mud), 빗방울(Rain Droplet), 눈(Snow), 지문(Fingerprint), 벌레(Insect), 기름(Oil), 김 서림(Condensation)은 카메라 렌즈를 부분적으로 가린다. 이는 알고리즘 문제가 아니라 영상 자체가 제대로 생성되지 않는 물리적인 문제이다. 소수성 코팅(Hydrophobic Coating), 자동 렌즈 세척(Lens Cleaning System), 오염 감지 알고리즘은 장기적인 신뢰성을 향상시킨다.

비(Rain)는 여러 가지 문제를 동시에 발생시킨다. 렌즈 위의 물방울은 영상을 왜곡하고, 떨어지는 빗방울은 영상 전체에 움직이는 잡음을 생성한다. 젖은 도로와 웅덩이(Puddle)는 강한 반사를 발생시켜 인식을 더욱 어렵게 만든다. 사람은 이러한 환경에 쉽게 적응하지만, 컴퓨터 비전 시스템은 악천후 데이터로 충분히 학습되지 않았다면 성능이 크게 저하된다.

안개(Fog)는 공기 중의 작은 물방울이 빛을 산란시켜 영상 대비(Contrast)를 크게 감소시킨다. 먼 거리에 있는 객체는 점차 사라지고 전체 시야가 흐려진다. 거리가 멀수록 특징 추출이 어려워져 장애물 검출 거리와 위치 추정 정확도가 감소한다. 따라서 해안 지역, 산악 지역, 산업 단지에서 운용되는 야외 로봇은 다른 센서와의 융합이 반드시 필요하다.

눈(Snow)은 단순히 시야를 가리는 것 이상의 문제를 만든다. 떨어지는 눈송이는 지속적인 움직이는 잡음을 생성하고, 쌓인 눈은 환경의 외형 자체를 변화시킨다. 또한 눈은 빛을 강하게 반사하여 전체 밝기를 크게 변화시킨다. 이전에 학습했던 랜드마크(Landmark)가 눈에 가려질 수 있기 때문에 위치 추정이 실패할 수 있다. 따라서 강인한 자율주행은 단순한 외형이 아니라 의미 정보(Semantic Information)를 함께 이용해야 한다.

먼지(Dust)와 연기(Smoke)는 빛을 산란시키고 시야를 부분적으로 차단하여 영상 품질을 저하시킨다. 건설 현장, 광산, 농업 환경, 제조 공장, 재난 대응 환경에서는 이러한 상황이 자주 발생한다. 카메라 기반 인식은 이러한 환경에서 큰 영향을 받지만 레이더(Radar)는 상대적으로 안정적으로 동작한다. 따라서 멀티센서 융합(Multi-Sensor Fusion)은 이러한 환경에서 매우 중요한 역할을 한다.

반사 표면(Reflective Surface)은 비전 알고리즘을 혼란스럽게 만드는 대표적인 요소이다. 유리벽, 광택 바닥, 거울(Mirror), 금속 기계, 젖은 도로, 차량 유리는 실제 물체와 동일한 형태의 반사 영상을 생성한다. 특히 단안 비전(Monocular Vision)은 이러한 반사와 실제 물체를 구별하기 어렵다. 깊이 센서와 시간적인 일관성(Temporal Consistency)을 이용하면 이러한 문제를 크게 줄일 수 있다.

투명한 물체(Transparent Material) 역시 매우 어려운 인식 대상이다. 유리문, 아크릴(Acrylic) 벽, 투명 용기, 창문은 특정 조명 조건에서는 거의 보이지 않는다. 색상과 질감에 의존하는 카메라는 이러한 장애물을 쉽게 놓칠 수 있다. 라이다, 스테레오 비전, 멀티센서 융합은 탐지 성능을 향상시키지만, 매우 투명한 물체에서는 능동형 센서조차도 어려움을 겪을 수 있다.

가림(Occlusion)은 가장 흔한 인식 실패 원인 가운데 하나이다. 선반, 기계, 차량, 식물, 상자, 사람 등에 의해 객체의 일부가 가려질 수 있다. 사람은 경험과 문맥(Context)을 이용하여 일부만 보이는 객체도 쉽게 인식하지만, 컴퓨터 비전은 보이는 정보가 줄어들수록 신뢰도가 감소한다. 최근에는 객체 추적(Object Tracking), 트랜스포머(Transformer), 월드 모델(World Model)을 이용하여 이러한 문제를 해결하고 있다.

혼잡한 환경(Crowded Environment)은 또 다른 어려움을 만든다. 여러 사람이 가까이 걷거나, 창고 물품이 빽빽하게 쌓여 있거나, 건설 자재가 겹쳐 있는 환경에서는 객체를 개별적으로 분리하기 어려워진다. 객체 검출기는 여러 객체를 하나로 합치거나, 객체 추적은 ID를 잘못 변경하며, 의미론적 분할의 경계도 모호해질 수 있다.

작은 객체(Small Object)는 매우 쉽게 검출에 실패한다. 전기 커넥터(Electrical Connector), 검사 결함(Inspection Defect), 안전 표지(Safety Marker), 떨어진 공구, 멀리 있는 보행자, 경고 라벨은 영상에서 매우 적은 픽셀만 차지한다. 반복적인 다운샘플링(Downsampling)을 거치면서 이러한 정보는 쉽게 사라질 수 있다. 다중 스케일 특징 피라미드(Feature Pyramid), 초해상도(Super Resolution), 고해상도 센서, 특수한 검출 구조는 이러한 문제를 개선한다.

크기 변화(Scale Variation)는 동일한 객체가 거리마다 매우 다른 형태로 보이는 문제이다. 가까운 차량은 화면 대부분을 차지하지만 먼 차량은 몇 개의 픽셀만 차지할 수도 있다. 따라서 객체 검출기는 다양한 크기의 데이터를 충분히 학습해야 하며, 작은 특징과 큰 문맥 정보를 동시에 표현할 수 있는 계층적 특징 구조(Hierarchical Feature Structure)가 필요하다.

비정상적인 시점(Unusual Viewpoint) 역시 인식 성능을 저하시킨다. 대부분의 학습 데이터는 일반적인 시점에서 촬영되지만, 실제 로봇은 위에서 내려다보거나, 아래에서 올려다보거나, 기울어진 각도에서 객체를 관찰할 수 있다. 높은 선반에서 내려다본 지게차나 바닥에서 올려다본 기계는 학습 데이터와 크게 다를 수 있다. 다양한 시점 데이터 증강(Viewpoint Augmentation)은 이러한 일반화 성능을 향상시킨다.

도메인 변화(Domain Shift)는 실제 환경이 학습 환경과 크게 다른 경우 발생한다. 깨끗한 창고 영상으로 학습한 모델은 병원, 건설 현장, 농업 환경, 지하 시설에서 성능이 크게 저하될 수 있다. 조명, 객체 외형, 배경, 카메라 종류, 날씨, 작업 방식의 차이가 모두 성능 저하를 유발한다. 도메인 적응(Domain Adaptation), 전이 학습(Transfer Learning), 지속 학습(Continual Learning)은 이러한 문제를 해결하기 위한 대표적인 기술이다.

분포 밖 데이터(OOD, Out-of-Distribution) 입력은 최근 매우 중요한 실패 유형으로 주목받고 있다. 딥러닝 모델은 학습 데이터와 유사한 입력을 가정하고 동작한다. 그러나 처음 보는 기계, 파손된 시설, 특이한 차량, 드문 환경은 매우 높은 신뢰도로 잘못된 결과를 출력할 수도 있다. 따라서 OOD 탐지는 모델이 자신의 예측을 신뢰해서는 안 되는 상황을 스스로 판단하도록 하는 중요한 기술이다.

거짓 양성(False Positive)은 실제로 존재하지 않는 객체를 잘못 검출하는 경우이다. 그림자, 반사, 특이한 질감, 장비의 무늬, 식물 등이 객체로 잘못 인식될 수 있다. 너무 많은 거짓 양성은 불필요한 제동, 우회, 작업 실패를 유발하여 전체 운용 효율을 떨어뜨린다. 신뢰도 보정(Confidence Calibration), 시간적 일관성 검증, 센서 융합은 이러한 오검출을 줄이는 데 도움이 된다.

거짓 음성(False Negative)은 실제 객체를 전혀 검출하지 못하는 경우이다. 사람, 지게차, 공사 장벽, 동물, 예상하지 못한 장애물을 놓치면 안전에 직접적인 위험이 발생한다. 따라서 안전이 중요한 시스템에서는 거짓 음성을 최소화하는 것이 매우 중요하며, 이를 위해 다소 많은 거짓 양성을 허용하는 보수적인 인식 전략이 자주 사용된다.

분류 혼동(Classification Confusion)은 외형이 비슷한 객체를 잘못 구분하는 경우이다. 팔레트(Pallet)와 박스(Box), 작업자와 방문객, 건설 장비와 일반 차량, 임시 안전 시설과 영구 구조물은 쉽게 혼동될 수 있다. 더 다양한 데이터셋, 문맥 정보, 시간적 추론, 멀티센서 융합은 이러한 혼동을 줄이는 데 효과적이다.

위치 추정 오류(Localization Error)는 객체를 올바르게 인식하더라도 위치를 정확하게 계산하지 못하는 경우이다. 경계 상자의 크기가 부정확하거나, 의미론적 분할 경계가 어긋나거나, 깊이 측정이 불안정하면 경로 계획, 물체 조작, 충돌 회피에 직접적인 오류가 발생한다. 따라서 정확한 객체 분류만으로는 충분하지 않으며, 위치 정확도 역시 매우 중요하다.

센서 동기화 실패(Sensor Synchronization Failure)는 여러 센서가 서로 다른 시점의 데이터를 사용하는 경우 발생한다. 카메라, 라이다, IMU, 바퀴 오도메트리가 서로 다른 시간의 정보를 사용하면 움직이는 객체의 위치가 맞지 않게 되어 센서 융합 결과가 크게 왜곡된다. 정확한 타임스탬프 관리와 하드웨어 동기화는 이러한 문제를 줄이는 핵심 기술이다.

하드웨어 성능 저하(Hardware Degradation)는 장기 운용에서 점진적으로 발생한다. 카메라 센서는 노화되고, 렌즈는 오염되며, 진동으로 인해 보정이 틀어질 수 있다. 온도 변화는 전자 장치의 성능을 변화시키고, 통신 오류는 프레임 손실을 유발한다. 지속적인 상태 모니터링(Health Monitoring), 자동 진단(Self-Diagnostics), 예측 유지보수(Predictive Maintenance), 주기적인 재보정은 장기간 신뢰성을 유지하는 데 필수적이다.

계산 과부하(Computational Overload) 역시 실제 환경에서 자주 발생하는 문제이다. 높은 해상도, 여러 대의 카메라, 복잡한 딥러닝 모델, 동시에 수행되는 다양한 로봇 작업은 제한된 연산 자원을 경쟁적으로 사용한다. 처리 시간이 증가하면 오래된 정보를 기반으로 자율주행이 이루어질 수 있다. 효율적인 스케줄링(Scheduling), 하드웨어 가속(Hardware Acceleration), 모델 최적화(Model Optimization), 적응형 작업 관리(Adaptive Workload Management)는 이러한 문제를 해결한다.

적대적 환경(Adversarial Environment)은 예상하지 못한 인식 오류를 유발할 수 있다. 특이한 조명 패턴, 반복되는 질감, 위장(Camouflage), 강한 반사 재질, 변형된 표지판, 예외적인 환경은 학습된 특징 표현의 약점을 노출시킬 수 있다. 의도적인 적대적 공격(Adversarial Attack)은 산업 환경에서는 드물지만, 자연스럽게 발생하는 유사한 상황은 실제 현장에서 자주 나타난다.

최근의 로봇 비전은 불확실성 추정(Uncertainty Estimation)을 적극적으로 도입하고 있다. 단순히 하나의 결과만 출력하는 것이 아니라 객체 검출, 의미론적 분할, 깊이 추정, 위치 추정, 객체 추적 결과의 신뢰도를 함께 계산한다. 신뢰도가 낮을 경우 로봇은 속도를 줄이고, 추가 센서를 사용하거나, 사람의 개입을 요청하거나, 더욱 보수적인 자율주행 전략을 선택할 수 있다.

실패 복구(Failure Recovery)는 실제 시스템에서 매우 중요한 기능이다. 완벽한 인식을 가정하지 않고 지속적으로 인식 품질을 모니터링하며 센서 이상과 성능 저하를 감지하여 적절한 대응을 수행한다. 예를 들어 예비 센서로 전환하거나, 카메라를 재보정하거나, 로봇 속도를 낮추거나, 원격 운영자의 도움을 요청하거나, 안전하게 자율주행을 일시 중단하는 등의 방법이 사용된다.

충분한 현장 시험(Field Testing)은 상용화 이전에 비전 실패 사례를 발견하는 가장 효과적인 방법이다. 실험실 환경만으로는 수년간의 실제 운용에서 발생하는 모든 상황을 재현할 수 없다. 다양한 계절, 날씨, 조명, 시설, 작업 환경에서 장기간 현장 시험을 수행하면 벤치마크 데이터셋에는 거의 포함되지 않는 희귀한 코너 케이스(Corner Case)를 발견할 수 있다. 이러한 경험은 데이터셋 품질 향상, 모델의 강인성, 안전성 검증, 전체 시스템 신뢰성을 지속적으로 향상시키는 기반이 된다.

미래의 로봇 비전 시스템은 멀티모달 센싱(Multimodal Sensing), 파운데이션 비전 모델(Foundation Vision Model), 월드 모델(World Model), 지속 학습(Continual Learning), 불확실성 추론(Uncertainty Reasoning), 예측 기반 인식(Predictive Perception), 체화형 인공지능(Embodied Intelligence)을 통합하여 현장 실패를 최소화하는 방향으로 발전할 것이다. 미래의 시스템은 각 영상을 독립적으로 처리하는 것이 아니라 기하학, 의미 정보, 움직임, 시간적 일관성, 경험을 하나의 지속적인 세계 표현(Persistent World Representation)으로 통합하게 된다. 이를 통해 자율주행 이동로봇은 인식이 불확실한 상황을 스스로 판단하고, 추가 정보를 수집하며, 변화하는 환경에 적응하고, 실제 현장에서 발생하는 다양한 예측 불가능한 상황에서도 더욱 안전하고 신뢰성 있게 동작할 수 있을 것이다.
