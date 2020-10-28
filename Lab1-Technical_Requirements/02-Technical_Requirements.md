# Lab 1: Meeting the Technical Requirements

## Lab 1.1: Setting technology, environments and keys

This lab is meant for an Artificial Intelligence (AI) Engineer or an AI Developer on Azure. To ensure you have time to work through the exercises, there are certain requirements to meet before starting the labs for this course.

You should ideally have some previous exposure to Visual Studio. We will be using it for everything we are building in the labs, so you should be familiar with [how to use it](https://docs.microsoft.com/en-us/visualstudio/ide/visual-studio-ide) to create applications. Additionally, this is not a class where we teach code or development. We assume you have some familiarity with C# (intermediate level - you can learn [here](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169?l=Lvld4EQIC_2706218949) and [here](https://docs.microsoft.com/en-us/dotnet/csharp/quick-starts/)).

### Account Setup

> **Note** You can use different environments for completing this lab.  Your instructor will guide you through the necessary steps to get the environment up and running.   This could be as simple as using the computer you are logged into in the classroom or as complex as setting up a virtualized environment.  The labs were created and tested using the Azure Data Science Virtual Machine (DSVM) on Azure and as such, will require an Azure account to use.

#### Setup your Azure Account

You may activate an Azure free trial at [https://azure.microsoft.com/en-us/free/](https://azure.microsoft.com/en-us/free/).

If you have been given an Azure Pass to complete this lab, you may go to [http://www.microsoftazurepass.com/](http://www.microsoftazurepass.com/) to activate it.  Please follow the instructions at [https://www.microsoftazurepass.com/howto](https://www.microsoftazurepass.com/howto), which document the activation process.  A Microsoft account may have **one free trial** on Azure and one Azure Pass associated with it, so if you have already activated an Azure Pass on your Microsoft account, you will need to use the free trial or use another Microsoft account.

### Environment Setup

These labs are intended to be used with the .NET Framework using [Visual Studio 2019](https://www.visualstudio.com/downloads/) runnning on a Microsoft Windows operating system. While there is a version of Visual Studio for Mac OS, certain features in the sample code are not supported on the Mac OS platform.  As a result, there is a hosted lab option available using a virtual machine solution. Your instructor will have the details on using the VM solution.  The original workshop was designed to be used, and was tested with, the Azure Data Science Virtual Machine (DSVM).  Only premium Azure subscriptions can actually create a DSVM resource on Azure but the labs can be completed with a local computer running Visual Studio 2019 and the required software downloads listed throughout the lab steps.

### Urls and Keys Needed

Over the course of this lab, we will collect a variety of Cognitive Services keys and storage keys. You should save all of them in a text file so you can easily access them in future labs. Not all of these will be populated in this lab.

>_Keys_
>
>- Cognitive Services API Url:
>- Cognitive Services API key:
>- LUIS API Endpoint:
>- LUIS API Key:
>- LUIS API App ID:
>- Bot App Name:
>- Bot App ID:
>- Bot App Password:
>- Azure Storage Connection String:
>- Cosmos DB Url:
>- Cosmos DB Key:
>- DirectLine Key:

### Azure Setup

In the following steps, you will configure the Azure environment for the labs that follow.

#### Cognitive Services

While the first lab focuses on the [Computer Vision](https://www.microsoft.com/cognitive-services/en-us/computer-vision-api) Cognitive Service, Microsoft Azure allows you to create a cognitive service account that spans all services, or you can elect to create a cognitive service account for an individual service.  In the following steps, you will create a single Azure resource that contains all available cognitive services endpoints.

1. Open the [Azure Portal](https://portal.azure.com)

2. Select **+ Create a Resource** and then enter **cognitive services** in the search box

3. Choose **Cognitive Services** from the available options, then select **Create**

> **Note** Again to reiterate, you can create specific cognitive services resources or you can create a single resource that contains all the endpoints.

1. Type a name of your own choosing

1. Select your subscription and resource group

1. For the pricing tier, select **S0**

1. Check the confirmation checkbox

1. Select **Create**

1. Navigate to the new resource, under the **Resource Management** section in the left toolbar, select **Keys and Endpoints**

1. Copy the **API Key** and the **url of the endpoint** to your notepad

    ![Quick start and the Key1 and Endpoint values are highlighted](../images/lab01-cogskeys.png 'The service key and endpoint values are highlighted')

#### Azure Storage Account

1. In the Azure Portal, select **+ Create a Resource** and then enter **storage** in the search box

1. Choose **Storage account** from the available options, then select **Create**

1. Select your subscription and resource group

1. Type a unique name for your account

1. For the location, select the same as your resource group

1. Performance should be **Standard**

1. Account kind should be **StorageV2 (general purpose v2**)

1. For replication, select **Locally-redundant storage (LRS)**

    ![The values for a storage account are displayed](../images/lab01-storageaccount.png 'Create a storage account')

1. Select **Review + create**

1. Select**Create**

1. Navigate to the new resource, select **Access Keys**

1. Copy the **Connection string** to your notepad

    ![The Access Keys and Connection string value is highlighted](../images/lab01-storageaccountkeys.png 'Copy the connection string')

1. Select **Overview**, then select **Containers**

    ![The overview and containers links are highlighted](../images/lab01-storageaccountcontainers.png 'Open the storage account containers')

1. Select **+ Container**

1. For the name, type **images**

    ![The container button is highlighted and the container name is populated.  The OK button is also highlighted.](../images/lab01-storageaccountcontainercreate.png 'Create a container called images')

1. Select **OK**

#### Cosmos DB

1. Open the [Azure Portal](https://portal.azure.com)

1. Select **"+ Create a Resource"** and then enter **cosmos** in the search box

1. Choose **Azure Cosmos DB** from the available options.  

1. Select **Create**

1. Select your subscription and resource group

1. Type a unique account name

1. Select a location that matches your resource group

    ![The cosmosdb creation details are populated.](../images/lab01-cosmoscreate.png 'Create a cosmosdb resource')

1. Select **Review + create**

1. Select **Create**

1. Navigate to the new resource, under **Settings**, select **Keys**

1. Copy the **URI** and the **PRIMARY KEY** to your notepad

### Bot Builder SDK

We will use the Bot Builder template for C# to create bots in this course.

#### Download the Bot Builder SDK

1. Open a browser window to [Bot Builder SDK v4 Template for C# here](https://marketplace.visualstudio.com/items?itemName=BotBuilder.botbuilderv4)

1. Select **Download**

1. Navigate to the download folder location and double-click on the install

1. Ensure that all versions of Visual Studio are selected and select **Install**.  If prompted, select **End Tasks**.  

1. Select **Close**. You should now have the bot templates added to your Visual Studio templates.

### Bot Emulator

We will be developing a bot using the latest .NET SDK (v4).  In order to do local testing, we'll need to download the Bot Framework Emulator.

### Download the Bot Framework Emulator

You can download the v4 Bot Framework Emulator for testing your bot locally. The instructions for the rest of the labs will assume you've downloaded the v4 Emulator.

1. Download the emulator by going to [this page](https://github.com/Microsoft/BotFramework-Emulator/releases) and downloading the most recent version of the emulator that has the tag "4.6.0" or higher (select the "*-windows-setup.exe" file, if you are using windows).

> **Note** The emulator installs to
`"C:\Users\_your-username\AppData\Local\Programs\@bfemulatormain\Bot Framework Emulator.exe"`, but you can gain access to it through the start menu by searching for **bot framework**.

## Credits

Labs in this series were adapted from the [Cognitive Services Tutorial](https://github.com/noodlefrenzy/CognitiveServicesTutorial) and [Learn AI BootCamp](https://github.com/Azure/LearnAI-Bootcamp)

## Resources

To deepen your understanding of the architecture described here, and to involve your broader team in the development of AI solutions, we recommend reviewing the following resources:

- [Cognitive Services](https://www.microsoft.com/cognitive-services) - AI Engineer
- [Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/) - Data Engineer
- [Azure Cognitive Search](https://azure.microsoft.com/en-us/services/search/) - Search Engineer
- [Bot Developer Portal](http://dev.botframework.com) - AI Engineer

## Next Steps

- [Lab 02-01: Implement Computer Vision](../Lab2-Implement_Computer_Vision/01-Introduction.md)
