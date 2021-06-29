# Lab 09: Publishing and subscribing to Event Grid events

## Microsoft Azure user interface

Given the dynamic nature of Microsoft cloud tools, you might experience Azure UI changes after the development of this training content. These changes might cause the lab instructions and lab steps to not match up.

Microsoft updates this training course when the community brings needed changes to our attention; however, because cloud updates occur frequently, you might encounter UI changes before this training content updates. **If this occurs, adapt to the changes, and then work through them in the labs as needed.**

## Instructions

### Before you start

#### Sign in to the lab virtual machine

Sign in to your Windows 10 virtual machine (VM) using the following credentials:

- Username: **Admin**
- Password: **Pa55w.rd**

> **Note**: Instructions to connect to the virtual lab environment will be provided by your instructor.

#### Review the installed applications

Find the taskbar on your Windows 10 desktop. The taskbar contains the icons for the applications that you’ll use in this lab:

- Microsoft Edge

- Microsoft Visual Studio Code

  

**Architecture**

![LAB09-Az204_00_Architecture](Evidencia/LAB09-Az204_00_Architecture.png)

### Exercise 1: Create Azure resources

#### Task 1: Open the Azure portal

1. On the taskbar, select the **Microsoft Edge** icon.

2. In the open browser window, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com/)).

3. Enter the email address for your Microsoft account, and then select **Next**.

4. Enter the password for your Microsoft account, and then select **Sign in**.

   > **Note**: If this is your first time signing in to the Azure portal, you’ll be offered a tour of the portal. Select **Get Started** to skip the tour and begin using the portal.

#### Task 2: Open Azure Cloud Shell

1. In the Azure portal, select the **Cloud Shell** icon to open a new shell instance.

   > **Note**: The **Cloud Shell** icon is represented by a greater than sign (>) and underscore character (_).

2. If this is your first time opening Cloud Shell using your subscription, you can use the **Welcome to Azure Cloud Shell Wizard** to configure Cloud Shell. Perform the following actions in the wizard:

   - When a dialog box prompts you to create a new storage account to begin using the shell, accept the default settings, and then select **Create storage**.

   > **Note**: Wait for Cloud Shell to finish its initial setup procedures before continuing with the lab. If you don’t notice the **Cloud Shell** configuration options, this is most likely because you’re using an existing subscription with this course’s labs. The labs are written with the presumption that you’re using a new subscription.

3. In Azure portal, at the **Cloud Shell** command prompt enter the following command, and then select Enter to get the version of the Azure Command-Line Interface (Azure CLI) tool:

   CodeCopy

   ```bash
    az --version
   ```

![LAB09-Az204_01](Evidencia/LAB09-Az204_01.png)

#### Task 3: View the Microsoft.EventGrid provider registration

1. At the **Cloud Shell** command prompt in the portal, perform the following actions:

   1. Enter the following command, and then select Enter to get a list of subgroups and commands at the root level of the Azure CLI:

      CodeCopy

      ```bash
       az --help
      ```

      ![LAB09-Az204_02](Evidencia/LAB09-Az204_02.png)

      ![LAB09-Az204_02a](Evidencia/LAB09-Az204_02a.png)

      ![LAB09-Az204_02b](Evidencia/LAB09-Az204_02b.png)

      ![LAB09-Az204_02c](Evidencia/LAB09-Az204_02c.png)

   2. Enter the following command, and then select Enter to get a list of the commands that are available for resource providers:

      CodeCopy

      ```bash
       az provider --help
      ```

      ![LAB09-Az204_03](Evidencia/LAB09-Az204_03.png)

   3. Enter the following command, and then select Enter to list all currently registered providers:

      CodeCopy

      ```bash
       az provider list
      ```

      ![LAB09-Az204_04h](Evidencia/LAB09-Az204_04h.png)

      ![LAB09-Az204_04](Evidencia/LAB09-Az204_04.png)

      ![LAB09-Az204_04a](Evidencia/LAB09-Az204_04a.png)

      ![LAB09-Az204_04b](Evidencia/LAB09-Az204_04b.png)

      ![LAB09-Az204_04c](Evidencia/LAB09-Az204_04c.png)

      ![LAB09-Az204_04d](Evidencia/LAB09-Az204_04d.png)

      ![LAB09-Az204_04d](Evidencia/LAB09-Az204_04d.png)

      ![LAB09-Az204_04e](Evidencia/LAB09-Az204_04e.png)

      ![LAB09-Az204_04f](Evidencia/LAB09-Az204_04f.png)

      ![LAB09-Az204_04g](Evidencia/LAB09-Az204_04g.png)

      ![LAB09-Az204_04h](Evidencia/LAB09-Az204_04h.png)

   4. Enter the following command, and then select Enter to list just the namespaces of the currently registered providers:

      CodeCopy

      ```bash
       az provider list --query "[].namespace"
      ```

      ![LAB09-Az204_05](Evidencia/LAB09-Az204_05.png)

      ![LAB09-Az204_05a](Evidencia/LAB09-Az204_05a.png)

      ![LAB09-Az204_05b](Evidencia/LAB09-Az204_05b.png)

      ![LAB09-Az204_05c](Evidencia/LAB09-Az204_05c.png)

      ![LAB09-Az204_05d](Evidencia/LAB09-Az204_05d.png)

   5. Review the list of currently registered providers. Notice that the **Microsoft.EventGrid** provider is currently included in the list of providers.

2. Close the Cloud Shell pane.

#### Task 4: Create a custom Event Grid topic

1. In the Azure portal’s navigation pane, select **Create a resource**.

2. On the **Create a resource** blade, find the **Search services and marketplace** text box.

3. In the search box, enter **Event Grid Topic**, and then select Enter.

4. On the **Everything** search results blade, select the **Event Grid Topic** result.

   ![LAB09-Az204_06](Evidencia/LAB09-Az204_06.png)

5. On the **Event Grid Topic** blade, select **Create**.

   ![LAB09-Az204_07](Evidencia/LAB09-Az204_07.png)

6. On the **Create Topic** blade, perform the following actions:

   1. In the **Name** text box, enter **hrtopic\*[yourname]\***.

   2. In the **Resource group** section, select **Create new**, enter **PubSubEvents**, and then select **OK**.

   3. From the **Location** drop-down list, select the **(US) East US** region.

      ![LAB09-Az204_08](Evidencia/LAB09-Az204_08.png)

   4. Select the **Advanced** tab.

   5. From the **Event Schema** drop-down list, select **Event Grid Schema**.

   6. Select **Review + Create**.

      ![LAB09-Az204_09](Evidencia/LAB09-Az204_09.png)

   7. **Create**.

      ![LAB09-Az204_10](Evidencia/LAB09-Az204_10.png)

      ![LAB09-Az204_11](Evidencia/LAB09-Az204_11.png)

   > **Note**: Wait for Azure to finish creating the topic before you continue with the lab. You’ll receive a notification when the topic is created.

![LAB09-Az204_12](Evidencia/LAB09-Az204_12.png)

#### Task 5: Deploy the Azure Event Grid viewer to a web app

1. In the Azure portal’s navigation pane, select **Create a resource**.

2. On the **Create a resource** blade, find the **Search services and marketplace** text box.

3. In the search box, enter **Web App**, and then select Enter.

4. On the **Everything** search results blade, select the **Web App** result.

   ![LAB09-Az204_13](Evidencia/LAB09-Az204_13.png)

5. On the **Web App** blade, select **Create**.

   ![LAB09-Az204_14](Evidencia/LAB09-Az204_14.png)

6. On the **Create Web App** blade, find the tabs on the blade, such as **Basics**.

   > **Note**: Each tab represents a step in the workflow to create a new web app. You can select **Review + Create** at any time to skip the remaining tabs.

7. On the **Basics** tab, perform the following actions:

   1. Leave the **Subscription** text box set to its default value.

   2. In the **Resource group** section, select **PubSubEvents**.

   3. In the **Name** text box, enter **eventviewer\*[yourname]\***.

   4. In the **Publish** section, select **Docker Container**.

   5. In the **Operating System** section, select **Linux**.

   6. From the **Region** drop-down list, select the **East US** region.

   7. In the **Linux Plan (East US)** section, select **Create new**.

   8. In the **Name** text box, enter the value **EventPlan**, and then select **OK**.

   9. Leave the **SKU and size** section set to its default value.

      ![LAB09-Az204_15](Evidencia/LAB09-Az204_15.png)

   10. Select **Next: Docker**.

8. On the **Docker** tab, perform the following actions:

   1. From the **Options** drop-down list, select **Single Container**.

   2. From the **Image Source** drop-down list, select **Docker Hub**.

   3. From the **Access Type** drop-down list, select **Public**.

   4. In the **Image and tag** text box, enter **microsoftlearning/azure-event-grid-viewer:latest**.

   5. Select **Review + Create**.

      ![LAB09-Az204_16](Evidencia/LAB09-Az204_16.png)

9. On the **Review + Create** tab, review the options that you selected during the previous steps.

10. Select **Create** to create the web app using your specified configuration.

    ![LAB09-Az204_17](Evidencia/LAB09-Az204_17.png)

    ![LAB09-Az204_18](Evidencia/LAB09-Az204_18.png)

    > **Note**: Wait for Azure to finish creating the web app before you continue with the lab. You’ll receive a notification when the app is created.

![LAB09-Az204_19](Evidencia/LAB09-Az204_19.png)

#### Review

In this exercise, you created the Event Grid topic and a web app that you will use throughout the remainder of the lab.

### Exercise 2: Create an Event Grid subscription

#### Task 1: Access the Event Grid Viewer web application

1. In the Azure portal’s navigation pane, select **Resource groups**.

2. On the **Resource groups** blade, select the **PubSubEvents** resource group that you created earlier in this lab.

   ![LAB09-Az204_20](Evidencia/LAB09-Az204_20.png)

3. On the **PubSubEvents** blade, select the **eventviewer\*[yourname]\*** web app that you created earlier in this lab.

   ![LAB09-Az204_21](Evidencia/LAB09-Az204_21.png)

4. On the **App Service** blade, in the **Settings** category, select the **Properties** link.

   ![LAB09-Az204_22](Evidencia/LAB09-Az204_22.png)

5. In the **Properties** section, record the value of the **URL** text box. You’ll use this value later in the lab.

   ![LAB09-Az204_23](Evidencia/LAB09-Az204_23.png)

6. Select **Overview**.

7. In the **Overview** section, select **Browse**.

   ![LAB09-Az204_24](Evidencia/LAB09-Az204_24.png)

8. Observe the currently running **Azure Event Grid viewer** web application. Leave this web application running for the remainder of the lab.

   ![LAB09-Az204_25](Evidencia/LAB09-Az204_25.png)

   > **Note**: This web application will update in real-time as events are sent to its endpoint. We will use this to monitor events throughout the lab.

9. Return to your currently open browser window that’s displaying the Azure portal.

#### Task 2: Create new subscription

1. In the Azure portal’s navigation pane, select **Resource groups**.

2. On the **Resource groups** blade, select the **PubSubEvents** resource group that you created earlier in this lab.

3. On the **PubSubEvents** blade, select the **hrtopic\*[yourname]\*** Event Grid topic that you created earlier in this lab.

   ![LAB09-Az204_26](Evidencia/LAB09-Az204_26.png)

4. On the **Event Grid Topic** blade, select **+ Event Subscription**.

   ![LAB09-Az204_27](Evidencia/LAB09-Az204_27.png)

5. On the **Create Event Subscription** blade, perform the following actions:

   1. In the **Name** text box, enter **basicsub**.

   2. In the **Event Schema** list, select **Event Grid Schema**.

   3. In the **Endpoint Type** list, select **Web Hook**.

   4. Select **Select an endpoint**.

      ![LAB09-Az204_28](Evidencia/LAB09-Az204_28.png)

   5. In the **Select Web Hook** dialog box, in the **Subscriber Endpoint** text box, enter the **Web App URL** value that you recorded earlier, ensure it uses an **https://** prefix, add the suffix **/api/updates**, and then select **Confirm Selection**.

      > **Note**: For example, if your **Web App URL** value is `http://eventviewerstudent.azurewebsites.net/`, then your **Subscriber Endpoint** would be `https://eventviewerstudent.azurewebsites.net/api/updates`.

      ![LAB09-Az204_29](Evidencia/LAB09-Az204_29.png)

   6. Select **Create**.

      ![LAB09-Az204_30](Evidencia/LAB09-Az204_30.png)

   > **Note**: Wait for Azure to finish creating the subscription before you continue with the lab. You’ll receive a notification when the subscription is created.

![LAB09-Az204_31](Evidencia/LAB09-Az204_31.png)

#### Task 3: Observe the subscription validation event

1. Return to the browser window displaying the **Azure Event Grid viewer** web application.

2. Review the **Microsoft.EventGrid.SubscriptionValidationEvent** event that was created as part of the subscription creation process.

   ![LAB09-Az204_33](Evidencia/LAB09-Az204_33.png)

3. Select the event and review its JSON content.

   ![LAB09-Az204_34](Evidencia/LAB09-Az204_34.png)

4. Return to your currently open browser window with the Azure portal.

#### Task 4: Record subscription credentials

1. In the Azure portal’s navigation pane, select **Resource groups**.

2. On the **Resource groups** blade, select the **PubSubEvents** resource group that you created earlier in this lab.

3. On the **PubSubEvents** blade, select the **hrtopic\*[yourname]\*** Event Grid topic that you created earlier in this lab.

   ![LAB09-Az204_35](Evidencia/LAB09-Az204_35.png)

4. On the **Event Grid Topic** blade, record the value of the **Topic Endpoint** field. You’ll use this value later in the lab.

   ![LAB09-Az204_36](Evidencia/LAB09-Az204_36.png)

5. In the **Settings** category, select the **Access keys** link.

6. In the **Access keys** section, record the value of the **Key 1** text box. You’ll use this value later in the lab.

   ![LAB09-Az204_37](Evidencia/LAB09-Az204_37.png)

#### Review

In this exercise, you created a new subscription, validated its registration, and then recorded the credentials required to publish a new event to the topic.

### Exercise 3: Publish Event Grid events from .NET

#### Task 1: Create a .NET project

1. On the **Start** screen, select the **Visual Studio Code** tile.

2. From the **File** menu, select **Open Folder**.

3. In the **File Explorer** window that opens, browse to **Allfiles (F):\Allfiles\Labs\09\Starter\EventPublisher**, and then select **Select Folder**.

4. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

5. At the open command prompt, enter the following command, and then select Enter to create a new .NET project named **EventPublisher** in the current folder:

   CodeCopy

   ```powershell
    dotnet new console --name EventPublisher --output .
   ```

   > **Note**: The **dotnet new** command will create a new **console** project in a folder with the same name as the project.

   ![LAB09-Az204_38](Evidencia/LAB09-Az204_38.png)

6. At the command prompt, enter the following command, and then select Enter to import version 4.1.0 of **Azure.Messaging.EventGrid** from NuGet:

   CodeCopy

   ```powershell
    dotnet add package Azure.Messaging.EventGrid --version 4.1.0
   ```

   > **Note**: The **dotnet add package** command will add the **Microsoft.Azure.EventGrid** package from NuGet. For more information, go to [Azure.Messaging.EventGrid](https://www.nuget.org/packages/Azure.Messaging.EventGrid/4.1.0).

   ![LAB09-Az204_39](Evidencia/LAB09-Az204_39.png)

7. At the command prompt, enter the following command, and then select Enter to build the .NET web application:

   CodeCopy

   ```powershell
    dotnet build
   ```

   ![LAB09-Az204_40](Evidencia/LAB09-Az204_40.png)

8. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 2: Modify the Program class to connect to Event Grid

1. In the Explorer pane of the **Visual Studio Code** window, open the **Program.cs** file.

   ![LAB09-Az204_41](Evidencia/LAB09-Az204_41.png)

2. On the code editor tab for the **Program.cs** file, delete all the code in the existing file.

   ![LAB09-Az204_42](Evidencia/LAB09-Az204_42.png)

   ![LAB09-Az204_43](Evidencia/LAB09-Az204_43.png)

   ![LAB09-Az204_44](Evidencia/LAB09-Az204_44.png)

3. Add the following line of code to import the **Azure**, and **Azure.Messaging.EventGrid** namespaces from the **Azure.Messaging.EventGrid** package imported from NuGet:

   C#Copy

   ```csharp
    using Azure;
    using Azure.Messaging.EventGrid;
   ```

   ![LAB09-Az204_45](Evidencia/LAB09-Az204_45.png)

4. Add the following lines of code to add **using** directives for the built-in namespaces that will be used in this file:

   C#Copy

   ```csharp
    using System;
    using System.Threading.Tasks;
   ```

   ![LAB09-Az204_46](Evidencia/LAB09-Az204_46.png)

5. Enter the following code to create a new **Program** class:

   C#Copy

   ```csharp
    public class Program
    {
    }
   ```

   ![LAB09-Az204_47](Evidencia/LAB09-Az204_47.png)

6. In the **Program** class, enter the following line of code to create a new string constant named **topicEndpoint**:

   C#Copy

   ```csharp
    private const string topicEndpoint = "";
   ```

   ![LAB09-Az204_48](Evidencia/LAB09-Az204_48.png)

7. Update the **topicEndpoint** string constant by setting its value to the **Topic Endpoint** of the Event Grid topic that you recorded earlier in this lab.

   ![LAB09-Az204_49](Evidencia/LAB09-Az204_49.png)

   ![LAB09-Az204_50](Evidencia/LAB09-Az204_50.png)

8. In the **Program** class, enter the following line of code to create a new string constant named **topicKey**:

   C#Copy

   ```csharp
    private const string topicKey = "";
   ```

   ![LAB09-Az204_51](Evidencia/LAB09-Az204_51.png)

   

9. Update the **topicKey** string constant by setting its value to the **Key** of the Event Grid topic that you recorded earlier in this lab.

   ![LAB09-Az204_52](Evidencia/LAB09-Az204_52.png)

10. In the **Program** class, enter the following code to create a new asynchronous **Main** method:

    C#Copy

    ```csharp
     public static async Task Main(string[] args)
     {
     }
    ```

    ![LAB09-Az204_53](Evidencia/LAB09-Az204_53.png)

11. Observe the **Program.cs** file, which should now include the following lines of code:

    C#Copy

    ```csharp
     using System;
     using System.Threading.Tasks;
     using Azure;
     using Azure.Messaging.EventGrid;
    
     public class Program
     {
         private const string topicEndpoint = "<topic-endpoint>";
         private const string topicKey = "<topic-key>";
            
         public static async Task Main(string[] args)
         {
         }
     }
    ```

![LAB09-Az204_54](Evidencia/LAB09-Az204_54.png)

#### Task 3: Publish new events

1. In the **Main** method, perform the following actions to publish a list of events to your topic endpoint:

   1. Add the following line of code to create a new variable named **endpoint** of type **Uri**, using the **topicEndpoint** string constant as a constructor parameter:

      C#Copy

      ```csharp
       Uri endpoint = new Uri(topicEndpoint); 
      ```

      ![LAB09-Az204_55](Evidencia/LAB09-Az204_55.png)

   2. Add the following line of code to create a new variable named **credential** of type **[AzureKeyCredential](https://docs.microsoft.com/dotnet/api/azure.azurekeycredential)**, using the **topicKey** string constant as a constructor parameter:

      C#Copy

      ```csharp
       AzureKeyCredential credential = new AzureKeyCredential(topicKey);
      ```

      ![LAB09-Az204_56](Evidencia/LAB09-Az204_56.png)

   3. Add the following line of code to create a new variable named **client** of type **[EventGridPublisherClient](https://docs.microsoft.com/dotnet/api/azure.messaging.eventgrid.eventgridpublisherclient)**, using the **endpoint** and **credential** variables as constructor parameters:

      C#Copy

      ```csharp
       EventGridPublisherClient client = new EventGridPublisherClient(endpoint, credential);
      ```

      ![LAB09-Az204_57](Evidencia/LAB09-Az204_57.png)

   4. Add the following block of code to create a new variable named **firstEvent** of type **[EventGridEvent](https://docs.microsoft.com/dotnet/api/azure.messaging.eventgrid.eventgridevent)** and populate that variable with sample data:

      C#Copy

      ```csharp
       EventGridEvent firstEvent = new EventGridEvent(
           subject: $"New Employee: Alba Sutton",
           eventType: "Employees.Registration.New",
           dataVersion: "1.0",
           data: new
           {
               FullName = "Alba Sutton",
               Address = "4567 Pine Avenue, Edison, WA 97202"
           }
       );
      ```

      ![LAB09-Az204_58](Evidencia/LAB09-Az204_58.png)

   5. Add the following block of code to create a new variable named **secondEvent** of type **[EventGridEvent](https://docs.microsoft.com/dotnet/api/azure.messaging.eventgrid.eventgridevent)** and populate that variable with sample data:

      C#Copy

      ```csharp
       EventGridEvent secondEvent = new EventGridEvent(
           subject: $"New Employee: Alexandre Doyon",
           eventType: "Employees.Registration.New",
           dataVersion: "1.0",
           data: new
           {
               FullName = "Alexandre Doyon",
               Address = "456 College Street, Bow, WA 98107"
           }
       );
      ```

      ![LAB09-Az204_59](Evidencia/LAB09-Az204_59.png)

   6. Add the following line of code to asynchronously invoke the **[EventGridPublisherClient.SendEventAsync](https://docs.microsoft.com/dotnet/api/azure.messaging.eventgrid.eventgridpublisherclient.sendeventasync)** method using the **firstEvent** variable as a parameter:

      C#Copy

      ```csharp
       await client.SendEventAsync(firstEvent);
      ```

      ![LAB09-Az204_60](Evidencia/LAB09-Az204_60.png)

   7. Add the following line of code to render the **“First event published”** message to the console:

      C#Copy

      ```csharp
       Console.WriteLine("First event published");
      ```

      ![LAB09-Az204_61](Evidencia/LAB09-Az204_61.png)

   8. Add the following line of code to asynchronously invoke the **[EventGridPublisherClient.SendEventAsync](https://docs.microsoft.com/dotnet/api/azure.messaging.eventgrid.eventgridpublisherclient.sendeventasync)** method using the **secondEvent** variable as a parameter:

      C#Copy

      ```csharp
       await client.SendEventAsync(secondEvent);
      ```

      ![LAB09-Az204_62](Evidencia/LAB09-Az204_62.png)

   9. Add the following line of code to render the **“Second event published”** message to the console:

      C#Copy

      ```csharp
       Console.WriteLine("Second event published");
      ```

   ![LAB09-Az204_63](Evidencia/LAB09-Az204_63.png)

2. Review the **Main** method, which should now include:

   C#Copy

   ```csharp
    public static async Task Main(string[] args)
    {
        Uri endpoint = new Uri(topicEndpoint);
        AzureKeyCredential credential = new AzureKeyCredential(topicKey);
        EventGridPublisherClient client = new EventGridPublisherClient(endpoint, credential);
           
        EventGridEvent firstEvent = new EventGridEvent(
            subject: $"New Employee: Alba Sutton",
            eventType: "Employees.Registration.New",
            dataVersion: "1.0",
            data: new
            {
                FullName = "Alba Sutton",
                Address = "4567 Pine Avenue, Edison, WA 97202"
            }
        );
   
        EventGridEvent secondEvent = new EventGridEvent(
            subject: $"New Employee: Alexandre Doyon",
            eventType: "Employees.Registration.New",
            dataVersion: "1.0",
            data: new
            {
                FullName = "Alexandre Doyon",
                Address = "456 College Street, Bow, WA 98107"
            }
        );
   
        await client.SendEventAsync(firstEvent);
        Console.WriteLine("First event published");
   
        await client.SendEventAsync(secondEvent);
        Console.WriteLine("Second event published");
    }
   ```

   ![LAB09-Az204_64](Evidencia/LAB09-Az204_64.png)

3. Save the **Program.cs** file.

   ![LAB09-Az204_65](Evidencia/LAB09-Az204_65.png)

4. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

5. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

   CodeCopy

   ```powershell
    dotnet run
   ```

   > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\09\Solution\EventPublisher** folder.

6. Observe the success message output from the currently running console application.

   ![LAB09-Az204_66](Evidencia/LAB09-Az204_66.png)

7. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 4: Observe published events

1. Return to the browser window with the **Azure Event Grid viewer** web application.

2. Review the **Employees.Registration.New** events that were created by your console application.

   ![LAB09-Az204_67](Evidencia/LAB09-Az204_67.png)

3. Select any of the events and review its JSON content.

   ![LAB09-Az204_68a](Evidencia/LAB09-Az204_68a.png)

4. Return to the Azure portal.

#### Review

In this exercise, you published new events to your Event Grid topic using a .NET console application.

### Exercise 4: Clean up your subscription

#### Task 1: Open Azure Cloud Shell

1. In Azure portal, select the **Cloud Shell** icon to open a new shell instance.

   > **Note**: The **Cloud Shell** icon is represented by a greater than sign (>) and underscore character (_).

2. If this is your first time opening Cloud Shell using your subscription, you can use the **Welcome to Azure Cloud Shell Wizard** to configure Cloud Shell for first-time usage. Perform the following actions in the wizard:

   1. A dialog box prompts you to configure the shell. Select **Bash**, review the selected subscription, and then select **Create storage**.

   > **Note**: Wait for Cloud Shell to finish its initial setup procedures before moving forward with the lab. If you don’t notice the Cloud Shell configuration options, this is most likely because you’re using an existing subscription with this course’s labs. The labs are written with the presumption that you’re using a new subscription.

#### Task 2: Delete resource groups

1. Enter the following command, and then select Enter to delete the **PubSubEvents** resource group:

   CodeCopy

   ```bash
    az group delete --name PubSubEvents --no-wait --yes
   ```

   ![LAB09-Az204_69](Evidencia/LAB09-Az204_69.png)

2. Close the Cloud Shell pane in the portal.

   ![LAB09-Az204_70](Evidencia/LAB09-Az204_70.png)

#### Task 3: Close the active applications

1. Close the currently running Microsoft Edge application.
2. Close the currently running Visual Studio Code application.

#### Review

In this exercise, you cleaned up your subscription by removing the resource groups used in this lab.