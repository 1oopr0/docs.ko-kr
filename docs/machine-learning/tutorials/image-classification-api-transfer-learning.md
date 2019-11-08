---
title: '자습서: 전이 학습을 사용한 자동화된 시각적 개체 검사'
description: 이 자습서에서는 전이 학습을 사용하여 이미지 검색 API로 ML.NET의 TensorFlow 딥 러닝 모델을 학습함으로써 콘크리트 표면 이미지를 금이 갔는지 여부로 분류하는 방법을 설명합니다.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/25/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b8aec80134188811eb80ad1394e5a64d65a3c6f0
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961955"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="5e152-103">자습서: ML.NET 이미지 분류 API와 함께 전이 학습을 사용한 자동화된 시각적 개체 검사</span><span class="sxs-lookup"><span data-stu-id="5e152-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="5e152-104">전이 학습, 사전 학습된 TensorFlow 모델 및 ML.NET 이미지 분류 API를 통해 사용자 지정 딥 러닝 모델을 학습하여 콘크리트 표면 이미지를 금이 갔는지 여부로 분류하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

> [!NOTE]
> <span data-ttu-id="5e152-105">이 자습서에서는 ML.NET 이미지 분류 API의 미리 보기 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-105">This tutorial uses a preview version of the ML.NET Image Classification API.</span></span>

<span data-ttu-id="5e152-106">이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5e152-107">문제 이해</span><span class="sxs-lookup"><span data-stu-id="5e152-107">Understand the problem</span></span>
> - <span data-ttu-id="5e152-108">ML.NET 이미지 분류 API에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="5e152-108">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="5e152-109">사전 학습된 모델 이해</span><span class="sxs-lookup"><span data-stu-id="5e152-109">Understand the pretrained model</span></span>
> - <span data-ttu-id="5e152-110">전이 학습을 사용하여 사용자 지정 TensorFlow 이미지 분류 모델 학습</span><span class="sxs-lookup"><span data-stu-id="5e152-110">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="5e152-111">사용자 지정 모델을 사용하여 이미지 분류</span><span class="sxs-lookup"><span data-stu-id="5e152-111">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e152-112">전제 조건</span><span class="sxs-lookup"><span data-stu-id="5e152-112">Prerequisites</span></span>

- <span data-ttu-id="5e152-113">“.NET Core 플랫폼 간 개발” 워크로드가 설치된 [Visual Studio 2017 15.6 이상](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017).</span><span class="sxs-lookup"><span data-stu-id="5e152-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="5e152-114">이미지 분류 전이 학습 샘플 개요</span><span class="sxs-lookup"><span data-stu-id="5e152-114">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="5e152-115">이 샘플은 사전 학습된 딥 러닝 TensorFlow 모델을 사용하여 이미지를 분류하는 C# .NET Core 콘솔 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-115">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="5e152-116">이 샘플의 코드는 GitHub의 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-116">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="5e152-117">문제 이해</span><span class="sxs-lookup"><span data-stu-id="5e152-117">Understand the problem</span></span>

<span data-ttu-id="5e152-118">이미지 분류는 컴퓨터 비전 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-118">Image classification is a computer vision problem.</span></span> <span data-ttu-id="5e152-119">이미지 분류는 이미지를 입력으로 사용하고 규정된 클래스로 분류합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-119">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="5e152-120">이미지 분류를 유용하게 사용할 수 있는 몇 가지 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-120">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="5e152-121">얼굴 인식</span><span class="sxs-lookup"><span data-stu-id="5e152-121">Facial recognition</span></span>
- <span data-ttu-id="5e152-122">감정 감지</span><span class="sxs-lookup"><span data-stu-id="5e152-122">Emotion detection</span></span>
- <span data-ttu-id="5e152-123">의료 진단</span><span class="sxs-lookup"><span data-stu-id="5e152-123">Medical diagnosis</span></span>
- <span data-ttu-id="5e152-124">랜드마크 검색</span><span class="sxs-lookup"><span data-stu-id="5e152-124">Landmark detection</span></span>

<span data-ttu-id="5e152-125">이 자습서에서는 사용자 지정 이미지 분류 모델을 학습하여 교량 상판의 자동화된 시각적 개체 검사를 통해 금이 간 구조물을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-125">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="5e152-126">ML.NET 이미지 분류 API</span><span class="sxs-lookup"><span data-stu-id="5e152-126">ML.NET Image Classification API</span></span>

<span data-ttu-id="5e152-127">ML.NET은 이미지를 분류하는 다양한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-127">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="5e152-128">이 자습서에서는 이미지 분류 API를 사용하여 전이 학습을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-128">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="5e152-129">이미지 분류 API는 TensorFlow C++ API에 대한 C# 바인딩을 제공하는 하위 수준 라이브러리인 [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-129">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="5e152-130">전이 학습이란?</span><span class="sxs-lookup"><span data-stu-id="5e152-130">What is transfer learning?</span></span>

<span data-ttu-id="5e152-131">전이 학습은 한 가지 문제를 해결하면서 얻은 지식을 다른 관련 문제에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-131">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="5e152-132">딥 러닝 모델을 처음부터 학습하려면 여러 개의 매개 변수를 설정해야 하고 레이블이 지정된 대량 학습 데이터와 막대한 컴퓨팅 리소스(수백 시간의 GPU 시간)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-132">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="5e152-133">전이 학습과 함께 사전 학습된 모델을 사용하면 학습 프로세스를 단축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-133">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span> 

## <a name="training-process"></a><span data-ttu-id="5e152-134">학습 프로세스</span><span class="sxs-lookup"><span data-stu-id="5e152-134">Training process</span></span>

<span data-ttu-id="5e152-135">이미지 분류 API는 사전 학습된 TensorFlow 모델을 로드하여 학습 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-135">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="5e152-136">학습 프로세스는 다음 두 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-136">The training process consists of two steps:</span></span>

1. <span data-ttu-id="5e152-137">병목 상태 단계</span><span class="sxs-lookup"><span data-stu-id="5e152-137">Bottleneck phase</span></span>
2. <span data-ttu-id="5e152-138">학습 단계</span><span class="sxs-lookup"><span data-stu-id="5e152-138">Training phase</span></span>

![학습 단계](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="5e152-140">병목 상태 단계</span><span class="sxs-lookup"><span data-stu-id="5e152-140">Bottleneck phase</span></span>

<span data-ttu-id="5e152-141">병목 상태 단계에서는 학습 이미지 집합이 로드되고, 픽셀 값이 사전 학습된 모델의 고정 계층에 대한 입력 또는 기능으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-141">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="5e152-142">고정 계층에는 끝에서 두 번째 계층(비공식적으로 병목 상태 계층이라고 함)까지 신경망의 모든 계층이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-142">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="5e152-143">이 계층에서는 학습이 발생하지 않고 작업이 통과되기 때문에 고정 계층이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-143">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="5e152-144">모델에서 각 클래스를 구분하는 데 도움이 되는 하위 수준 패턴이 컴퓨팅되는 곳이 고정 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-144">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="5e152-145">계층 수가 많을수록 이 단계에서 사용되는 컴퓨팅이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-145">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="5e152-146">다행히 일회성 계산이므로 결과를 캐시했다가 후속 실행에서 다른 매개 변수로 실험할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-146">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="5e152-147">학습 단계</span><span class="sxs-lookup"><span data-stu-id="5e152-147">Training phase</span></span>

<span data-ttu-id="5e152-148">병목 상태 단계의 출력 값이 컴퓨팅되고 나면, 모델의 최종 계층을 다시 학습하기 위한 입력으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-148">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="5e152-149">이 프로세스는 반복되며 모델 매개 변수에 지정된 횟수만큼 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-149">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="5e152-150">실행할 때마다 손실과 정확도가 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-150">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="5e152-151">그런 다음, 손실 최소화 및 정확도 최대화를 목표로 해서 모델을 개선하기 위해 적절하게 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-151">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="5e152-152">학습이 완료되면 두 가지 모델 형식이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-152">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="5e152-153">하나는 모델의 `.pb` 버전이고, 다른 하나는 모델의 ML.NET 직렬화된 `.zip` 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-153">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="5e152-154">ML.NET이 지원하는 환경에서 작업하는 경우 모델의 `.zip` 버전을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-154">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="5e152-155">그러나 ML.NET이 지원되지 않는 환경에서는 `.pb` 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-155">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="5e152-156">사전 학습된 모델 이해</span><span class="sxs-lookup"><span data-stu-id="5e152-156">Understand the pretrained model</span></span>

<span data-ttu-id="5e152-157">이 자습서에서 사용되는 사전 학습 모델은 ResNet(Residual Network) v2 모델의 101 계층 변형입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-157">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="5e152-158">원본 모델은 이미지를 1000개 범주로 분류하도록 학습되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-158">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="5e152-159">모델은 224x224 크기의 이미지를 입력으로 사용하고, 모델이 학습된 각 클래스의 클래스 확률을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-159">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="5e152-160">이 모델의 일부는 두 클래스 간의 예측을 위해 사용자 지정 이미지를 사용하여 새 모델을 학습하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-160">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span> 

## <a name="create-console-application"></a><span data-ttu-id="5e152-161">콘솔 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="5e152-161">Create console application</span></span>

<span data-ttu-id="5e152-162">이제 전이 학습과 이미지 분류 API에 대한 일반적인 사항을 파악했으므로 애플리케이션을 빌드하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-162">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="5e152-163">“DeepLearning_ImageClassification_Binary”라는 **C# .NET Core 콘솔 애플리케이션**을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-163">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="5e152-164">**Microsoft.ML 1.4.0-preview2** NuGet 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-164">Install the **Microsoft.ML 1.4.0-preview2** NuGet Package:</span></span>
    1. <span data-ttu-id="5e152-165">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-165">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="5e152-166">패키지 원본으로 "nuget.org"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-166">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="5e152-167">**찾아보기** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-167">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="5e152-168">**시험판 포함** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-168">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="5e152-169">**Microsoft.ML**을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-169">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="5e152-170">**설치** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-170">Select the **Install** button.</span></span>
    1. <span data-ttu-id="5e152-171">**변경 내용 미리 보기** 대화 상자에서 **확인** 단추를 선택한 다음, 나열된 패키지의 사용 조건에 동의하는 경우 **라이선스 승인** 대화 상자에서 **동의함** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-171">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="5e152-172">**Microsoft.ML.Dnn 0.16.0-preview2** 및 **Microsoft.ML.ImageAnalytics 1.4.0-preview2**에 대해 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-172">Repeat these steps for **Microsoft.ML.Dnn 0.16.0-preview2** and **Microsoft.ML.ImageAnalytics 1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="5e152-173">데이터 준비 및 이해</span><span class="sxs-lookup"><span data-stu-id="5e152-173">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="5e152-174">이 자습서의 데이터 세트는 Maguire, Marc, Dorafshan, Sattar 및 Thomas, Robert J., “SDNET2018: A concrete crack image dataset for machine learning applications”(기계 학습 애플리케이션의 콘크리트 금 이미지 데이터 세트)(2018)에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-174">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="5e152-175">모든 데이터 세트를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-175">Browse all Datasets.</span></span> <span data-ttu-id="5e152-176">논문 48입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-176">Paper 48.</span></span> <span data-ttu-id="5e152-177">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="5e152-177">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="5e152-178">SDNET2018은 금이 간 콘크리트 구조물(교량 상판, 벽, 도로)과 금이 가지 않은 콘크리트 구조물에 대한 주석이 포함된 이미지 데이터 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-178">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span> 

![SDNET2018 데이터 세트 교량 상판 샘플](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="5e152-180">데이터는 다음 세 개의 하위 디렉터리로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-180">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="5e152-181">D에는 교량 상판 이미지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-181">D contains bridge deck images</span></span>
- <span data-ttu-id="5e152-182">P에는 도로 이미지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-182">P contains pavement images</span></span>
- <span data-ttu-id="5e152-183">W에 벽 이미지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-183">W contains wall images</span></span>

<span data-ttu-id="5e152-184">각 하위 디렉터리에는 접두사가 붙은 다음 두 개의 하위 디렉터리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-184">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="5e152-185">C는 금이 간 표면에 사용되는 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-185">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="5e152-186">U는 금이 가지 않은 표면에 사용되는 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-186">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="5e152-187">이 자습서에서는 교량 상판 이미지만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-187">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="5e152-188">[데이터 세트](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip)를 다운로드하여 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-188">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="5e152-189">프로젝트에서 데이터 세트 파일을 저장할 “assets”라는 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-189">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="5e152-190">최근에 압축을 푼 디렉터리의 *CD* 및 *UD* 하위 디렉터리를 *assets* 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-190">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="5e152-191">입력 및 출력 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="5e152-191">Create input and output classes</span></span>

1. <span data-ttu-id="5e152-192">*Program.cs* 파일을 열고 파일의 맨 위에 있는 기존 `using` 문을 다음 문으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-192">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="5e152-193">*Program.cs*의 `Program` 클래스 아래에 `ImageData`라는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-193">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="5e152-194">이 클래스는 처음에 로드된 데이터를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-194">This class is used to represent the initially loaded data.</span></span> 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    <span data-ttu-id="5e152-195">`ImageData`에는 다음 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-195">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="5e152-196">`ImagePath`는 이미지가 저장된 정규화된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-196">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="5e152-197">`Label`은 이미지가 속하는 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-197">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="5e152-198">예측할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-198">This is the value to predict.</span></span>

1. <span data-ttu-id="5e152-199">입력 및 출력 데이터의 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="5e152-199">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="5e152-200">`ImageData` 클래스 아래에 있는 `ModelInput`이라는 새 클래스에서 입력 데이터의 스키마를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-200">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        <span data-ttu-id="5e152-201">`ModelInput`에는 다음 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-201">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="5e152-202">`ImagePath`는 이미지가 저장된 정규화된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-202">`ImagePath` is the fully qualified path where the image is stored.</span></span> 
        - <span data-ttu-id="5e152-203">`Label`은 이미지가 속하는 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-203">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="5e152-204">예측할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-204">This is the value to predict.</span></span>
        - <span data-ttu-id="5e152-205">`Image`는 이미지의 `byte[]` 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-205">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="5e152-206">모델을 학습하려면 이미지 데이터가 이 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-206">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="5e152-207">`LabelAsKey`는 `Label`의 숫자 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-207">`LabelAsKey` is the numerical representation of the `Label`.</span></span> 

        <span data-ttu-id="5e152-208">`Image` 및 `LabelAsKey`만 모델을 학습하고 예측하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-208">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="5e152-209">`ImagePath` 및 `Label` 속성은 원본 이미지 파일 이름과 범주에 액세스하기 편리하도록 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-209">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="5e152-210">그런 다음, `ModelInput` 클래스 아래에 있는 `ModelOutput`이라는 새 클래스에서 출력 데이터의 스키마를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-210">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span> 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        <span data-ttu-id="5e152-211">`ModelOutput`에는 다음 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-211">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="5e152-212">`ImagePath`는 이미지가 저장된 정규화된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-212">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="5e152-213">`Label`은 이미지가 속하는 원래 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-213">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="5e152-214">예측할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-214">This is the value to predict.</span></span> 
        - <span data-ttu-id="5e152-215">`PredictedLabel`은 모델에서 예측된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-215">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="5e152-216">`ModelInput`과 마찬가지로, 예측 작업에는 모델의 예측이 포함된 `PredictedLabel`만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-216">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="5e152-217">`ImagePath` 및 `Label` 속성은 원본 이미지 파일 이름과 범주에 액세스하기 편리하도록 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-217">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="5e152-218">경로 정의 및 변수 초기화</span><span class="sxs-lookup"><span data-stu-id="5e152-218">Define paths and initialize variables</span></span>

1. <span data-ttu-id="5e152-219">`Main` 메서드 내에서 자산의 위치를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-219">Inside the `Main` method, define the location of your assets.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L16)]

1. <span data-ttu-id="5e152-220">그런 다음, [MLContext](xref:Microsoft.ML.MLContext)의 새 인스턴스를 사용하여 `mlContext` 변수를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-220">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

<span data-ttu-id="5e152-221">[MLContext](xref:Microsoft.ML.MLContext) 클래스는 모든 ML.NET 작업의 시작점이며, mlContext를 초기화하면 모델 생성 워크플로 개체 간에 공유할 수 있는 새 ML.NET 환경이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-221">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="5e152-222">개념적으로 Entity Framework의 `DBContext`와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-222">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="5e152-223">데이터 로드</span><span class="sxs-lookup"><span data-stu-id="5e152-223">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="5e152-224">데이터 로드 유틸리티 메서드 만들기</span><span class="sxs-lookup"><span data-stu-id="5e152-224">Create data loading utility method</span></span>

<span data-ttu-id="5e152-225">이미지는 두 개의 하위 디렉터리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-225">The images are stored in two subdirectories.</span></span> <span data-ttu-id="5e152-226">데이터를 로드하기 전에 `ImageData` 개체 목록으로 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-226">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="5e152-227">`Main` 메서드 아래에 `LoadImagesFromDirectory` 메서드를 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-227">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="5e152-228">`LoadImagesDirectory` 안에 다음 코드를 추가하여 하위 디렉터리에서 파일 경로를 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-228">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. <span data-ttu-id="5e152-229">`foreach` 문을 사용하여 각 파일을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-229">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="5e152-230">`foreach` 문 내에서 파일 확장명이 지원되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-230">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="5e152-231">이미지 분류 API는 JPEG 및 PNG 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-231">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. <span data-ttu-id="5e152-232">파일의 레이블을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-232">Then, get the label for the file.</span></span> <span data-ttu-id="5e152-233">`useFolderNameAsLabel` 매개 변수를 `true`로 설정하면 파일이 저장된 부모 디렉터리가 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-233">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="5e152-234">true로 설정하지 않으면 파일 이름의 접두사 또는 파일 이름 자체가 레이블이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-234">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. <span data-ttu-id="5e152-235">마지막으로, `ModelInput`의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-235">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a><span data-ttu-id="5e152-236">데이터 준비</span><span class="sxs-lookup"><span data-stu-id="5e152-236">Prepare the data</span></span>

1. <span data-ttu-id="5e152-237">`Main` 메서드로 돌아가서 `LoadFromDirectory` 유틸리티 메서드를 사용하여 학습에 사용할 이미지 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-237">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. <span data-ttu-id="5e152-238">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 메서드를 사용하여[`IDataView`](xref:Microsoft.ML.IDataView)에 이미지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-238">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. <span data-ttu-id="5e152-239">디렉터리에서 읽어온 순서대로 데이터가 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-239">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="5e152-240">데이터의 균형을 조정하려면 [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) 메서드를 사용하여 순서를 섞습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-240">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. <span data-ttu-id="5e152-241">기계 학습 모델에서는 입력이 숫자 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-241">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="5e152-242">따라서 학습 전에 데이터에서 몇 가지 전처리 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-242">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="5e152-243">[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) 및 [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) 변환으로 구성된 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-243">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transforms.</span></span> <span data-ttu-id="5e152-244">`MapValueToKey` 변환은 `Label` 열의 범주 값을 사용하여 숫자 `KeyType` 값으로 변환하고 `LabelAsKey`라는 새 열에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-244">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="5e152-245">`LoadImages`는 `ImagePath` 열의 값을 `imageFolder` 매개 변수와 함께 사용하여 학습에 사용할 이미지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-245">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span> <span data-ttu-id="5e152-246">`useImageType`을 `false`로 설정하면 이미지가 `byte[]`로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-246">Setting the `useImageType` to `false` converts the images into a `byte[]`.</span></span> 

    [!code-csharp [DefinePreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L26-L33)]

1. <span data-ttu-id="5e152-247">[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) 메서드를 사용하여 `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)에 데이터를 적용합니다. 그 다음에 오는 [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) 메서드가 전처리된 데이터를 포함하는 [`IDataView`](xref:Microsoft.ML.IDataView)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="5e152-248">모델을 학습하려면 유효성 검사 데이터 세트뿐만 아니라 학습 데이터 세트도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="5e152-249">학습 세트에서 모델이 학습됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-249">The model is trained on the training set.</span></span> <span data-ttu-id="5e152-250">보이지 않는 데이터의 예측 성능은 유효성 검사 세트에 대한 성능으로 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="5e152-251">성능 결과에 따라 모델이 배운 내용을 조정하여 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="5e152-252">유효성 검사 세트는 원본 데이터 세트를 분할해서 얻거나, 이 용도로 이미 설정된 다른 소스에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="5e152-253">이 예제에서는 전처리된 데이터 세트를 학습, 유효성 검사 및 테스트 세트로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="5e152-254">위의 코드 샘플은 두 가지 분할 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-254">The code sample above performs two splits.</span></span> <span data-ttu-id="5e152-255">먼저, 전처리된 데이터가 분할되어 70%는 학습에 사용되고 나머지 30%는 유효성 검사에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="5e152-256">그런 다음 30% 유효성 검사 세트가 유효성 검사 및 테스트 세트로 다시 분할됩니다. 여기서 90%는 유효성 검사에 사용되고 10%는 테스트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span> 

    <span data-ttu-id="5e152-257">시험 보기에 비유하면 이러한 데이터 파티션의 용도를 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="5e152-258">시험 공부를 할 때는 노트, 책 또는 기타 리소스를 검토하여 시험에 나오는 개념을 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="5e152-259">이때 학습 세트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-259">This is what the train set is for.</span></span> <span data-ttu-id="5e152-260">그 다음에는 지식을 검증하기 위해 모의 시험을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="5e152-261">이 용도에는 유효성 검사 세트가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="5e152-262">실제 시험을 보기 전에 개념을 잘 파악했는지 여부를 확인하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="5e152-263">결과에 따라 잘못 이해했거나 이해하지 못한 내용을 기록하고, 실제 시험을 위해 검토할 때 변경 내용을 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="5e152-264">최종 단계로, 시험을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-264">Finally, you take the exam.</span></span> <span data-ttu-id="5e152-265">이때 테스트 세트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-265">This is what the test set is used for.</span></span> <span data-ttu-id="5e152-266">시험에 나온 질문을 본 적이 없으며, 이제 학습 및 유효성 검사에서 배운 내용을 사용하여 해당 작업에 지식을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span> 

1. <span data-ttu-id="5e152-267">학습, 유효성 검사 및 테스트 데이터의 파티션에 해당 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="5e152-268">학습 파이프라인 정의</span><span class="sxs-lookup"><span data-stu-id="5e152-268">Define the training pipeline</span></span>

<span data-ttu-id="5e152-269">모델 학습은 몇 가지 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="5e152-270">먼저, 이미지 분류 API를 사용하여 모델을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="5e152-271">`MapKeyToValue` 변환을 사용하여 `PredictedLabel` 열의 인코드된 레이블이 원래 범주 값으로 다시 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span> 

1. <span data-ttu-id="5e152-272">`mapLabelEstimator` 및 `ImageClassification` 변환으로 구성된 학습 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 파이프라인을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-272">Define the training [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline that consists of both the `mapLabelEstimator` and the `ImageClassification` transforms.</span></span>

    [!code-csharp [DefineTrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L58)]    

    <span data-ttu-id="5e152-273">`ImageClassification` 예측은 여러 가지 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-273">The `ImageClassification` estimator takes in several parameters:</span></span>

    - <span data-ttu-id="5e152-274">`featuresColumnName`은 모델의 입력으로 사용되는 열입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-274">`featuresColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="5e152-275">`labelColumnName`은 예측할 값의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-275">`labelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="5e152-276">`arch`는 사용할 사전 학습 모델 아키텍처를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-276">`arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="5e152-277">이 자습서에서는 ResNetv2 모델의 101 계층 변형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-277">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="5e152-278">`epoch`는 학습 프로세스 전반에 걸쳐 전체 데이터 세트의 최대 반복 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-278">`epoch` specifies the maximum number of iterations over the entire dataset throughout the training process.</span></span> <span data-ttu-id="5e152-279">숫자가 클수록 모델의 학습 기간이 길어지고 생성되는 모델이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-279">The higher the number, the longer the model trains for and potentially the better model that is produced.</span></span>
    - <span data-ttu-id="5e152-280">`batchSize`는 학습을 위해 한 번에 사용할 샘플 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-280">`batchSize` is the number of samples to use at a time for training.</span></span> <span data-ttu-id="5e152-281">단일 Epoch에서 batchSize와 동일한 여러 개의 일괄 처리가 모델을 학습하고 업데이트하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-281">During one epoch, multiple batches equal to the batchSize are used to train and update the model.</span></span> <span data-ttu-id="5e152-282">숫자가 작을수록 각 일괄 처리에 필요한 메모리가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-282">The lower the number, the less memory required when each batch is processed.</span></span>
    - <span data-ttu-id="5e152-283">`testOnTrainSet`는 유효성 검사 세트가 없는 경우 학습 세트에서 성능을 측정하도록 모델에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-283">`testOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="5e152-284">`metricsCallback`은 학습 중에 진행 상황을 추적하기 위해 함수를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-284">`metricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="5e152-285">`validationSet`는 유효성 검사 데이터를 포함하는 [`IDataView`](xref:Microsoft.ML.IDataView)입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-285">`validationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="5e152-286">`reuseTrainSetBottleneckCachedValues`는 병목 상태 단계에서 캐시된 값을 후속 실행에 사용할지 여부를 모델에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-286">`reuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="5e152-287">병목 상태 단계는 일회성 통과 계산으로, 처음 수행할 때는 계산을 많이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-287">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="5e152-288">학습 데이터가 변경되지 않았으며 다른 Epoch 수나 일괄 처리 크기를 사용하여 실험하려는 경우 캐시된 값을 사용하면 모델을 학습하는 데 필요한 시간을 훨씬 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-288">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="5e152-289">`reuseValidationSetBottleneckCachedValues`는 `reuseTrainSetBottleneckCachedValues`와 비슷하지만, 이 경우에는 유효성 검사 데이터 세트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-289">`reuseValidationSetBottleneckCachedValues` is similar to `reuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="5e152-290">`disableEarlyStopping`은 ImageClassification 예측에 조기 중지 전략을 사용할지 여부를 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-290">`disableEarlyStopping` tells the ImageClassification estimator whether to employ an early stopping strategy.</span></span> <span data-ttu-id="5e152-291">학습 중에 모델이 정확한 예측에 도움이 되는 최적 값을 검색함에 따라 성능이 향상되거나 감소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-291">As the model searches for the optimal values that will help it make accurate predictions during training, performance may increase or decrease.</span></span> <span data-ttu-id="5e152-292">궁극적으로, 모델이 마지막 Epoch에 도달할 때 학습에서 배운 패턴이 최적이 아닌 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-292">Ultimately, if the model reaches the last epoch, it may be the case that the patterns it learned from training are suboptimal.</span></span> <span data-ttu-id="5e152-293">조기 중지는 학습에서 이러한 성능 저하를 모니터링하고 학습 프로세스를 중지하여 모델의 최적 버전을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-293">Early stopping monitors training for these drops in performance and stops the training process in an effort to preserve an optimal version of the model.</span></span>

1. <span data-ttu-id="5e152-294">[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) 메서드를 사용하여 모델을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-294">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a><span data-ttu-id="5e152-295">모델 사용</span><span class="sxs-lookup"><span data-stu-id="5e152-295">Use the model</span></span>

<span data-ttu-id="5e152-296">이제 모델을 학습했으므로, 모델을 사용하여 이미지를 분류해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-296">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="5e152-297">`Main` 메서드 아래에 예측 정보를 콘솔에 표시하는 `OutputPrediction`이라는 새 유틸리티 메서드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-297">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a><span data-ttu-id="5e152-298">단일 이미지 분류</span><span class="sxs-lookup"><span data-stu-id="5e152-298">Classify a single image</span></span>

1. <span data-ttu-id="5e152-299">`Main` 메서드 아래에 단일 이미지 예측을 수행하고 출력하는 `ClassifySingleImage`라는 새 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-299">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="5e152-300">`ClassifySingleImage` 메서드 안에 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-300">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="5e152-301">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)은 데이터의 단일 인스턴스를 전달하고 예측하는 데 사용할 수 있는 편리한 API입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-301">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. <span data-ttu-id="5e152-302">단일 `ModelInput` 인스턴스에 액세스하기 위해 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 메서드를 사용하여 `data` [`IDataView`](xref:Microsoft.ML.IDataView)를 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)로 변환하고 첫 번째 관찰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-302">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span> 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="5e152-303">[`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) 메서드를 사용하여 이미지를 분류합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-303">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="5e152-304">`OutputPrediction` 메서드를 사용하여 예측을 콘솔에 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-304">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. <span data-ttu-id="5e152-305">`Main` 메서드 내에서 테스트 이미지 세트를 사용하여 `ClassifySingleImage`를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-305">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a><span data-ttu-id="5e152-306">여러 이미지 분류</span><span class="sxs-lookup"><span data-stu-id="5e152-306">Classify multiple images</span></span>

1. <span data-ttu-id="5e152-307">`ClassifySingleImage` 메서드 아래에 여러 이미지 예측을 수행하고 출력하는 `ClassifyImages`라는 새 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-307">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="5e152-308">[`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 메서드를 사용하여 예측을 포함하는 [`IDataView`](xref:Microsoft.ML.IDataView)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-308">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="5e152-309">`ClassifyImages` 메서드 내에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-309">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. <span data-ttu-id="5e152-310">예측을 반복하기 위해 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 메서드를 사용하여 `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView)를 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)로 변환하고 처음 10개의 관찰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-310">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="5e152-311">예측을 반복하고 예측의 원래 레이블과 예측 레이블을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-311">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. <span data-ttu-id="5e152-312">최종 단계로, `Main` 메서드 내에서 테스트 이미지 세트를 사용하여 `ClassifyImages`를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-312">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a><span data-ttu-id="5e152-313">애플리케이션 실행</span><span class="sxs-lookup"><span data-stu-id="5e152-313">Run the application</span></span>

<span data-ttu-id="5e152-314">콘솔 앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-314">Run your console app.</span></span> <span data-ttu-id="5e152-315">아래와 유사하게 출력되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-315">The output should be similar to that below.</span></span> <span data-ttu-id="5e152-316">경고 또는 처리 메시지가 표시될 수 있지만, 이해하기 쉽도록 이러한 메시지는 다음 결과에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-316">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="5e152-317">간단히 표시하기 위해 출력이 압축되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-317">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="5e152-318">**병목 상태 단계**</span><span class="sxs-lookup"><span data-stu-id="5e152-318">**Bottleneck phase**</span></span>

<span data-ttu-id="5e152-319">이미지가 `byte[]`로 로드되어 표시할 이미지 이름이 없으므로 이미지 이름 값이 출력되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-319">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

<span data-ttu-id="5e152-320">**학습 단계**</span><span class="sxs-lookup"><span data-stu-id="5e152-320">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="5e152-321">**이미지 분류 출력**</span><span class="sxs-lookup"><span data-stu-id="5e152-321">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="5e152-322">*7001-220.jpg* 이미지를 살펴보면 실제로 금이 가지 않은 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-322">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span> 

![예측에 사용되는 SDNET2018 데이터 세트 이미지](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="5e152-324">지금까지</span><span class="sxs-lookup"><span data-stu-id="5e152-324">Congratulations!</span></span> <span data-ttu-id="5e152-325">이제 이미지 분류를 위한 딥 러닝 모델을 빌드했습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-325">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="5e152-326">모델 개선</span><span class="sxs-lookup"><span data-stu-id="5e152-326">Improve the model</span></span>

<span data-ttu-id="5e152-327">모델의 결과가 만족스럽지 않으면, 다음과 같은 방법을 사용하여 성능을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-327">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="5e152-328">**데이터 추가**: 모델이 더 많은 예제를 학습할수록 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-328">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="5e152-329">전체 [SDNET2018 데이터 세트](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional)를 다운로드하여 학습에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-329">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span> 
- <span data-ttu-id="5e152-330">**데이터 보강**: 데이터에 다양성을 추가하는 일반적인 방법은 이미지에 다양한 변환(회전, 대칭 이동, 이동, 자르기)을 적용하여 데이터를 보강하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-330">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="5e152-331">이렇게 하면 모델이 학습할 수 있는 다양한 예제가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-331">This adds more varied examples for the model to learn from.</span></span> 
- <span data-ttu-id="5e152-332">**학습 시간 연장**: 학습 시간이 길수록 모델이 더 튜닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-332">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="5e152-333">Epoch 수를 늘리면 모델의 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-333">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="5e152-334">**하이퍼 매개 변수로 실험**: 이 자습서에서 사용된 매개 변수 외에 다른 매개 변수를 튜닝하여 성능을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-334">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="5e152-335">각 Epoch 후의 모델 업데이트 크기를 결정하는 학습 속도를 변경하면 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-335">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="5e152-336">**다른 모델 아키텍처 사용**: 데이터 모양에 따라 기능 학습에 가장 적합한 모델이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-336">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="5e152-337">모델의 성능이 만족스럽지 않으면 아키텍처를 변경해 보세요.</span><span class="sxs-lookup"><span data-stu-id="5e152-337">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5e152-338">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="5e152-338">Additional Resources</span></span>

- <span data-ttu-id="5e152-339">[딥 러닝 및 기계 학습](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="5e152-339">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5e152-340">다음 단계</span><span class="sxs-lookup"><span data-stu-id="5e152-340">Next steps</span></span>

<span data-ttu-id="5e152-341">이 자습서에서는 전이 학습, 사전 학습된 이미지 분류 TensorFlow 모델 및 ML.NET 이미지 분류 API를 통해 사용자 지정 딥 러닝 모델을 작성하여 콘크리트 표면 이미지를 금이 갔는지 여부로 분류하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="5e152-341">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="5e152-342">다음 자습서로 이동하여 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="5e152-342">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e152-343">개체 감지</span><span class="sxs-lookup"><span data-stu-id="5e152-343">Object Detection</span></span>](object-detection-onnx.md)