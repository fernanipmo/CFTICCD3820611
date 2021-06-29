# Lab 10: Asynchronously processing messages by using Azure Queue Storage

## Microsoft Azure user interface

Given the dynamic nature of Microsoft cloud tools, you might experience Azure UI changes after the development of this training content. These changes might cause the lab instructions and lab steps to not match up.

Microsoft updates this training course when the community brings needed changes to our attention; however, because cloud updates occur frequently, you might encounter UI changes before this training content updates. **If this occurs, adapt to the changes, and then work through them in the labs as needed.**

## Instructions

### Before you start

#### Sign in to the lab virtual machine

Sign in to your Windows 10 virtual machine (VM) by using the following credentials:

- Username: **Admin**
- Password: **Pa55w.rd**

> **Note**: Instructions to connect to the virtual lab environment will be provided by your instructor.

#### Review the installed applications

Find the taskbar on your Windows 10 desktop. The taskbar contains the icons for the applications that you’ll use in this lab:

- Microsoft Edge
- Visual Studio Code
- Azure Storage Explorer

**Architecture**

![LAB10_Az204_00_Architecture](Evidencia/LAB10_Az204_00_Architecture.png)

### Exercise 1: Create Azure resources

#### Task 1: Open the Azure portal

1. On the taskbar, select the **Microsoft Edge** icon.

2. In the open browser window, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com/)).

3. Enter the email address for your Microsoft account, and then select **Next**.

4. Enter the password for your Microsoft account, and then select **Sign in**.

   > **Note**: If this is your first time signing in to the Azure portal, you’ll be offered a tour of the portal. Select **Get Started** to skip the tour and begin using the portal.

#### Task 2: Create a Storage account

1. In the Azure portal’s navigation pane, select **All services**.

2. On the **All services** blade, select **Storage Accounts**.

   ![LAB10-Az204_01](Evidencia/LAB10-Az204_01.png)

3. On the **Storage accounts** blade, get your list of storage account instances.

4. On the **Storage accounts** blade, select **Create**.

   ![LAB10-Az204_02](Evidencia/LAB10-Az204_02.png)

5. On the **Create storage account** blade, observe the tabs on the blade, such as **Basics**, **Tags**, and **Review + Create**.

   > **Note**: Each tab represents a step in the workflow to create a new storage account. You can select **Review + Create** at any time to skip the remaining tabs.

6. Select the **Basics** tab, and then in the tab area, perform the following actions:

   1. Leave the **Subscription** text box set to its default value.

   2. In the **Resource group** section, select **Create new**, enter **AsyncProcessor**, and then select **OK**.

   3. In the **Storage account name** text box, enter **asyncstor\*[yourname]\***.

   4. In the **Location** list, select the **(US) East US** region.

   5. In the **Performance** section, select **Standard**.

   6. In the **Redundancy** list, select **Locally-redundant storage (LRS)**.

   7. Select **Review + Create**.

      ![LAB10-Az204_03](Evidencia/LAB10-Az204_03.png)

7. On the **Review + Create** tab, review the options that you specified in the previous steps.

8. Select **Create** to create the storage account by using your specified configuration.

   ![LAB10-Az204_04](Evidencia/LAB10-Az204_04.png)

   > **Note**: On the **Deployment** blade, wait for the creation task to complete before moving forward with this lab.

   ![LAB10-Az204_05](Evidencia/LAB10-Az204_05.png)

9. Select the **Go to resource** button on the **Deployment** blade to go to the newly created storage account.

   ![LAB10-Az204_06](Evidencia/LAB10-Az204_06.png)

10. On the **Storage account** blade, find the **Security + networking** section, and then select **Access keys**.

    ![LAB10-Az204_07](Evidencia/LAB10-Az204_07.png)

11. On the **Access keys** blade, select any one of the keys, and then record the value of either of the **Connection string** boxes. You’ll use this value later in this lab.

    > **Note**: It doesn’t matter which connection string you choose. They are interchangeable.

![LAB10-Az204_08](Evidencia/LAB10-Az204_08.png)

#### Review

In this exercise, you created a new Azure Storage account that you’ll use through the remainder of the lab.

### Exercise 2: Configure the Azure Storage SDK in a .NET project

#### Task 1: Create a .NET project

1. On the **Start** screen, select the **Visual Studio Code** tile.

2. On the **File** menu, select **Open Folder**.

3. In the **File Explorer** window that opens, browse to **Allfiles (F):\Allfiles\Labs\10\Starter\MessageProcessor**, and then select **Select Folder**.

4. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

5. At the open command prompt, enter the following command, and then select Enter to create a new .NET project named **MessageProcessor** in the current folder:

   CodeCopy

   ```
   dotnet new console --name MessageProcessor --output .
   ```

   > **Note**: The **dotnet new** command will create a new **console** project in a folder with the same name as the project.

   ![LAB10-Az204_09](Evidencia/LAB10-Az204_09.png)

6. At the command prompt, enter the following command, and then select Enter to import version 12.0.0 of **Azure.Storage.Queues** from NuGet:

   CodeCopy

   ```
   dotnet add package Azure.Storage.Queues --version 12.0.0
   ```

   > **Note**: The **dotnet add package** command will add the **Azure.Storage.Queues** package from NuGet. For more information, go to [Azure.Storage.Queues](https://www.nuget.org/packages/Azure.Storage.Queues/12.0.0).

   ![LAB10-Az204_10](Evidencia/LAB10-Az204_10.png)

7. At the command prompt, enter the following command, and then select Enter to build the .NET web application:

   CodeCopy

   ```
   dotnet build
   ```

   ![LAB10-Az204_11](Evidencia/LAB10-Az204_11.png)

8. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 2: Write code to access Azure Storage

1. In the Explorer pane of the **Visual Studio Code** window, open the **Program.cs** file.

   ![LAB10-Az204_12](Evidencia/LAB10-Az204_12.png)

2. On the code editor tab for the **Program.cs** file, delete all the code in the existing file.

   ![LAB10-Az204_13](Evidencia/LAB10-Az204_13.png)

   ![LAB10-Az204_14](Evidencia/LAB10-Az204_14.png)

3. Add the following line of code to import the **Azure**, **Azure.Storage.Queues**, and **Azure.Storage.Queues.Models** namespaces from the **Azure.Storage.Queues** package imported from NuGet:

   CodeCopy

   ```
   using Azure;
   using Azure.Storage.Queues;
   using Azure.Storage.Queues.Models;
   ```

   ![LAB10-Az204_15](Evidencia/LAB10-Az204_15.png)

   

4. Add the following lines of code to add **using** directives for the built-in namespaces that will be used in this file:

   CodeCopy

   ```
   using System;
   using System.Text;
   using System.Threading.Tasks;
   ```

   ![LAB10-Az204_16](Evidencia/LAB10-Az204_16.png)

5. Enter the following code to create a new **Program** class:

   CodeCopy

   ```
   public class Program
   {
   }
   ```

   ![LAB10-Az204_17](Evidencia/LAB10-Az204_17.png)

6. In the **Program** class, enter the following line of code to create a new string constant named **storageConnectionString**:

   CodeCopy

   ```
   private const string storageConnectionString = "";
   ```

   ![LAB10-Az204_18](Evidencia/LAB10-Az204_18.png)

7. Update the **storageConnectionString** string constant by setting its value to the **Connection string** of the Storage account that you recorded earlier in this lab.

   ![LAB10-Az204_19](Evidencia/LAB10-Az204_19.png)

   ![LAB10-Az204_20](Evidencia/LAB10-Az204_20.png)

8. In the **Program** class, enter the following line of code to create a new string constant named **queueName** with a value of **messagequeue**:

   CodeCopy

   ```
   private const string queueName = "messagequeue";
   ```

   ![LAB10-Az204_21](Evidencia/LAB10-Az204_21.png)

9. In the **Program** class, enter the following code to create a new asynchronous **Main** method:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
   }
   ```

   ![LAB10-Az204_22](Evidencia/LAB10-Az204_22.png)

10. Observe the **Program.cs** file, which should now include:

    CodeCopy

    ```
    using Azure;
    using Azure.Storage.Queues;
    using Azure.Storage.Queues.Models;
    using System;
    using System.Text;
    using System.Threading.Tasks;
    
    public class Program
    {
        private const string storageConnectionString = "<storage-connection-string>";
        private const string queueName = "messagequeue";
    
        public static async Task Main(string[] args)
        {
        }
    }
    ```

![LAB10-Az204_23](Evidencia/LAB10-Az204_23.png)

#### Task 3: Validate Azure Storage access

1. In the **Main** method, add the following line of code to connect to the storage account by creating a new variable named *client* of type **QueueClient**:

   CodeCopy

   ```
   QueueClient client = new QueueClient(storageConnectionString, queueName);  
   ```

   ![LAB10-Az204_24](Evidencia/LAB10-Az204_24.png)

2. In the **Main** method, add the following line of code to asynchronously create the queue if it doesn’t already exist:

   CodeCopy

   ```
   await client.CreateAsync();
   ```

   ![LAB10-Az204_25](Evidencia/LAB10-Az204_25.png)

3. In the **Main** method, add the following line of code to render a header for the “Account Metadata” section:

   CodeCopy

   ```
   Console.WriteLine($"---Account Metadata---");
   ```

   ![LAB10-Az204_26](Evidencia/LAB10-Az204_26.png)

4. In the **Main** method, add the following line of code to render the Uniform Resource Identifier (URI) of the queue endpoint:

   CodeCopy

   ```
   Console.WriteLine($"Account Uri:\t{client.Uri}");
   ```

   ![LAB10-Az204_27](Evidencia/LAB10-Az204_27.png)

5. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       QueueClient client = new QueueClient(storageConnectionString, queueName);        
       await client.CreateAsync();
   
       Console.WriteLine($"---Account Metadata---");
       Console.WriteLine($"Account Uri:\t{client.Uri}");
   }
   ```

   ![LAB10-Az204_28](Evidencia/LAB10-Az204_28.png)

6. Save the **Program.cs** file.

   ![LAB10-Az204_29](Evidencia/LAB10-Az204_29.png)

7. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

8. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

   CodeCopy

   ```
   dotnet run
   ```

   > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\10\Solution\MessageProcessor** folder.

9. Observe the output from the currently running console application. The output contains metadata for the queue endpoint.

   ![LAB10-Az204_30](Evidencia/LAB10-Az204_30.png)

10. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Review

In this exercise, you configured your .NET project to access the Storage service and manipulate a queue made available through the service.

### Exercise 3: Read messages from the queue

#### Task 1: Write code to access queue messages

1. In the **Main** method, add the following line of code to render a header for the “Existing Messages” section:

   CodeCopy

   ```
   Console.WriteLine($"---Existing Messages---");
   ```

   ![LAB10-Az204_31](Evidencia/LAB10-Az204_31.png)

2. Within the **Main** method, perform the following actions to create variables that will be used when retrieving queue messages:

   1. Add the following line of code to create a variable of type **int** named *batchSize* with a value of **10**:

      CodeCopy

      ```
      int batchSize = 10;
      ```

      ![LAB10-Az204_32](Evidencia/LAB10-Az204_32.png)

   2. Add the following line of code to create a variable of type **TimeSpan** named *visibilityTimeout* with a value of **2.5 seconds**:

      CodeCopy

      ```
      TimeSpan visibilityTimeout = TimeSpan.FromSeconds(2.5d);
      ```

   ![LAB10-Az204_33](Evidencia/LAB10-Az204_33.png)

3. Within the **Main** method, perform the following actions to retrieve a batch of messages asynchronously from the queue service:

   1. Add the following line of code to invoke the **ReceiveMessagesAsync** asynchronous method of the **QueueClient** class, passing in the *batchSize* and *visibilityTimeout* variables as parameters:

      CodeCopy

      ```
      client.ReceiveMessagesAsync(batchSize, visibilityTimeout);
      ```

      ![LAB10-Az204_34](Evidencia/LAB10-Az204_34.png)

   2. Update the previous line of code by adding more code to process the expression asynchronously by using the **await** keyword:

      CodeCopy

      ```
      await client.ReceiveMessagesAsync(batchSize, visibilityTimeout);
      ```

      ![LAB10-Az204_35](Evidencia/LAB10-Az204_35.png)

   3. Update the previous line of code by adding more code to store the result of the expression in a new variable named *messages* of type **[Response](https://docs.microsoft.com/dotnet/api/azure.response-1)**:

      CodeCopy

      ```
      Response<QueueMessage[]> messages = await client.ReceiveMessagesAsync(batchSize, visibilityTimeout);
      ```

   ![LAB10-Az204_36](Evidencia/LAB10-Az204_36.png)

4. Within the **Main** method, perform the following actions to iterate over and render the properties of each message:

   1. Add the following line of code to create a **foreach** loop that iterates over each message that’s stored in the **[Value](https://docs.microsoft.com/dotnet/api/azure.response-1.value)** property of the *messages* variable of type **[QueueMessage[\]](https://docs.microsoft.com/dotnet/api/azure.storage.queues.models.queuemessage)**:

      CodeCopy

      ```
      foreach(QueueMessage message in messages?.Value)
      {
      }
      ```

      ![LAB10-Az204_37](Evidencia/LAB10-Az204_37.png)

   2. Within the **foreach** loop, add another line of code to render the **MessageId** and **MessageText** properties of each **QueueMessage** instance:

      CodeCopy

      ```
      Console.WriteLine($"[{message.MessageId}]\t{message.MessageText}");
      ```

   ![LAB10-Az204_38](Evidencia/LAB10-Az204_38.png)

5. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       // Existing code removed for brevity
   
       Console.WriteLine($"---Existing Messages---");
       int batchSize = 10;
       TimeSpan visibilityTimeout = TimeSpan.FromSeconds(2.5d);
           
       Response<QueueMessage[]> messages = await client.ReceiveMessagesAsync(batchSize, visibilityTimeout);
   
       foreach(QueueMessage message in messages?.Value)
       {
           Console.WriteLine($"[{message.MessageId}]\t{message.MessageText}");
       }
   }
   ```

   ![LAB10-Az204_39](Evidencia/LAB10-Az204_39.png)

6. Save the **Program.cs** file.

   ![LAB10-Az204_40](Evidencia/LAB10-Az204_40.png)

7. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

8. At the open command prompt, enter the following command, and then select Enter to build the .NET web application:

   CodeCopy

   ```
   dotnet build
   ```

   > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\10\Solution\MessageProcessor** folder.

   ![LAB10-Az204_41](Evidencia/LAB10-Az204_41.png)

9. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 2: Test message queue access

1. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

2. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

   CodeCopy

   ```
   dotnet run
   ```

   > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\10\Solution\MessageProcessor** folder.

3. Observe the output from the currently running console application. The output indicates that no messages are in the queue.

   ![LAB10-Az204_42](Evidencia/LAB10-Az204_42.png)

4. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

5. In the Azure portal’s navigation pane, select the **Resource groups** link.

6. On the **Resource groups** blade, find and then select the **AsyncProcessor** resource group that you created earlier in this lab.

7. On the **AsyncProcessor** blade, select the **asyncstor\*[yourname]\*** storage account that you created earlier in this lab.

   ![LAB10-Az204_43](Evidencia/LAB10-Az204_43.png)

8. On the **Storage account** blade, select **Overview**.

9. In the **Overview** section, select **Open in Explorer**.

   ![LAB10-Az204_44](Evidencia/LAB10-Az204_44.png)

10. In the **Azure Storage Explorer** window, select **Open Azure Storage Explorer**.

    ![LAB10-Az204_45](Evidencia/LAB10-Az204_45.png)

    > **Note**: If this is your first time opening Storage Explorer by using the portal, you might be prompted to allow the portal to open these types of links in the future. You should accept the prompt.

    ![LAB10-Az204_46](Evidencia/LAB10-Az204_46.png)

    

    ![LAB10-Az204_46a](Evidencia/LAB10-Az204_46a.png)

    ![LAB10-Az204_46b](Evidencia/LAB10-Az204_46b.png)

    

11. In the **Azure Storage Explorer** application, you will notice a prompt to sign in to your Azure account. Sign in by performing the following actions:

    ![LAB10-Az204_47](Evidencia/LAB10-Az204_47.png)

    ![LAB10-Az204_48](Evidencia/LAB10-Az204_48.png)

    ![LAB10-Az204_49](Evidencia/LAB10-Az204_49.png)

    1. In the popup dialog, select **Sign in**.

       ![LAB10-Az204_50](Evidencia/LAB10-Az204_50.png)

    2. In the **Connect to Azure Storage** window, select **Add an Azure Account**, in the **Azure environment** list select **Azure**, and then select **Next**.

       ![LAB10-Az204_51](Evidencia/LAB10-Az204_51.png)

    3. In the **Sign in to your account** popup window, enter the email address for your Microsoft account, and then select **Next**.

       ![LAB10-Az204_52](Evidencia/LAB10-Az204_52.png)

    4. Still within the **Sign in to your account** popup window, enter the password for your Microsoft account, and then select **Sign in**.

       ![LAB10-Az204_53](Evidencia/LAB10-Az204_53.png)

       ![LAB10-Az204_54](Evidencia/LAB10-Az204_54.png)

    5. In the **ACCOUNT MANAGEMENT** pane, select **Apply**.

       ![LAB10-Az204_55](Evidencia/LAB10-Az204_55.png)

       ![LAB10-Az204_56](Evidencia/LAB10-Az204_56.png)

    6. Observe that you are returned back to the **EXPLORER** pane with your subscription information populated.

12. From the **Azure Storage Explorer** application, in the **EXPLORER** pane, find and expand the **asyncstor\*[yourname]\*** storage account that you created earlier in this lab.

13. Within the **asyncstor\*[yourname]\*** storage account, find and expand the **Queues** node.

    ![LAB10-Az204_57_](Evidencia/LAB10-Az204_57.png)

14. In the **Queues** node, open the **messagequeue** queue that you created earlier in this lab by using .NET code.

15. On the **messagequeue** tab, select **Add Message**.

16. In the **Add Message** pop-up window, perform the following actions:

    1. In the **Message text** text box, enter the value **Hello World**.

    2. In the **Expires in** text box, enter the value **12**.

    3. In the **Expires in** drop-down list, select **Hours**.

    4. In the **Encoding** section, select **UTF8**.

    5. Select **OK**.

       ![LAB10-Az204_58](Evidencia/LAB10-Az204_58.png)

       ![LAB10-Az204_59](Evidencia/LAB10-Az204_59.png)

17. Return to the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

18. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

    CodeCopy

    ```
    dotnet run
    ```

    > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\10\Solution\MessageProcessor** folder.

19. Observe the output from the currently running console application. The output includes the new message that you created.

    ![LAB10-Az204_60](Evidencia/LAB10-Az204_60.png)

20. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 3: Delete queued messages

1. In the Explorer pane of the **Visual Studio Code** window, open the **Program.cs** file.

2. On the code editor tab for the **Program.cs** file, find the existing **foreach** loop within the **Main** method:

   CodeCopy

   ```
   foreach(QueueMessage message in messages?.Value)
   {
       Console.WriteLine($"[{message.MessageId}]\t{message.MessageText}");
   }
   ```

   

3. Within the **foreach** loop, add a new line of code to invoke the **DeleteMessageAsync** method of the **QueueMessage** class, passing in the **MessageId** and **PopReceipt** properties of the *message* variable:

   CodeCopy

   ```
   await client.DeleteMessageAsync(message.MessageId, message.PopReceipt);
   ```

   ![LAB10-Az204_61](Evidencia/LAB10-Az204_61.png)

4. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       // Existing code removed for brevity
           
       foreach(QueueMessage message in messages?.Value)
       {
           Console.WriteLine($"[{message.MessageId}]\t{message.MessageText}");
           await client.DeleteMessageAsync(message.MessageId, message.PopReceipt);
       }
   }
   ```

5. **Save** the **Program.cs** file.

   ![LAB10-Az204_62](Evidencia/LAB10-Az204_62.png)

6. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

7. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

   CodeCopy

   ```
   dotnet run
   ```

   > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\10\Solution\MessageProcessor** folder.

8. Observe the output from the currently running console application. The message that you created earlier in the lab still exists because it hasn’t been deleted previously.

   ![LAB10-Az204_63](Evidencia/LAB10-Az204_63.png)

   ![LAB10-Az204_64](Evidencia/LAB10-Az204_64.png)

9. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

10. Return Storage Explorer, and then find and expand the **asyncstor\*[yourname]\*** storage account that you created earlier in this lab.

    ![LAB10-Az204_65](Evidencia/LAB10-Az204_65.png)

11. In the **asyncstor\*[yourname]\*** storage account, find and expand the **Queues** node.

12. In the **Queues** node, open the **messagequeue** queue that you created earlier in this lab by using .NET code.

13. Observe the empty list of messages in the queue.

    > **Note**: You might need to refresh the queue.

![LAB10-Az204_66](Evidencia/LAB10-Az204_66.png)

#### Review

In this exercise, you read and deleted existing messages from the Storage queue by using the .NET library.

### Exercise 4: Queue new messages by using .NET

#### Task 1: Write code to create queue messages

1. In the Explorer pane of the **Visual Studio Code** window, open the **Program.cs** file.

2. On the code editor tab for the **Program.cs** file, find the existing **Main** method.

3. Within the **Main** method, add a new line of code to render a header for the “New Messages” section:

   CodeCopy

   ```
   Console.WriteLine($"---New Messages---");
   ```

   ![LAB10-Az204_67](Evidencia/LAB10-Az204_67.png)

4. In the **Main** method, perform the following actions to create and send a message asynchronously:

   1. Add the following line of code to create a new string variable named *greeting* with a value of **Hi, Developer!**:

      CodeCopy

      ```
      string greeting = "Hi, Developer!";        
      ```

      ![LAB10-Az204_68](Evidencia/LAB10-Az204_68.png)

   2. Add the following line of code to invoke the **SendMessageAsync** method of the **QueueClient** class by using the *greeting* variable as a parameter

      CodeCopy

      ```
      await client.SendMessageAsync(Convert.ToBase64String(Encoding.UTF8.GetBytes(greeting)));        
      ```

      ![LAB10-Az204_69](Evidencia/LAB10-Az204_69.png)

   3. Add the following line of code to render the content of the message that you sent:

      CodeCopy

      ```
      Console.WriteLine($"Sent Message:\t{greeting}");        
      ```

   ![LAB10-Az204_70](Evidencia/LAB10-Az204_70.png)

5. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       // Existing code removed for brevity
           
       Console.WriteLine($"---New Messages---");
       string greeting = "Hi, Developer!";
       await client.SendMessageAsync(Convert.ToBase64String(Encoding.UTF8.GetBytes(greeting)));
           
       Console.WriteLine($"Sent Message:\t{greeting}");
   }
   ```

   ![LAB10-Az204_71](Evidencia/LAB10-Az204_71.png)

6. **Save** the **Program.cs** file.

   ![LAB10-Az204_72](Evidencia/LAB10-Az204_72.png)

7. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

8. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

   CodeCopy

   ```
   dotnet run
   ```

   > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\10\Solution\MessageProcessor** folder.

9. Observe the output from the currently running console application. The content of the new message that you sent should be in the output.

   ![LAB10-Az204_73](Evidencia/LAB10-Az204_73.png)

10. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 2: View queued messages by using Storage Explorer

1. Return to Storage Explorer, and then find and expand the **asyncstor\*[yourname]\*** storage account that you created earlier in this lab.

2. In the **asyncstor\*[yourname]\*** storage account, find and expand the **Queues** node.

3. In the **Queues** node, open the **messagequeue** queue that you created earlier in this lab by using .NET code.

   ![LAB10-Az204_74](Evidencia/LAB10-Az204_74.png)

4. Observe the single new message in the list of messages in the queue.

   > **Note**: You might need to refresh the queue.

![LAB10-Az204_75](Evidencia/LAB10-Az204_75.png)

#### Review

In this exercise, you created new messages in the queue by using the .NET library for Storage queues.

### Exercise 5: Clean up your subscription

#### Task 1: Open Azure Cloud Shell and list resource groups

1. In the Azure portal’s navigation pane, select the **Cloud Shell** icon to open a new shell instance.

   > **Note**: The **Cloud Shell** icon is represented by a greater than sign (>) and underscore character (_).

2. If this is your first time opening Cloud Shell using your subscription, you can use the **Welcome to Azure Cloud Shell Wizard** to configure Cloud Shell for first-time usage. Perform the following actions in the wizard:

   - A dialog box prompts you to configure the shell. Select **Bash**, review the selected subscription, and then select **Create storage**.

   > **Note**: Wait for Cloud Shell to finish its initial setup procedures before moving forward with the lab. If you don’t notice Cloud Shell configuration options, this is most likely because you’re using an existing subscription with this course’s labs. The labs are written with the presumption that you’re using a new subscription.

#### Task 2: Delete a resource group

1. At the command prompt, enter the following command, and then select Enter to delete the **AsyncProcessor** resource group:

   CodeCopy

   ```
   az group delete --name AsyncProcessor --no-wait --yes
   ```

   ![LAB10-Az204_76](Evidencia/LAB10-Az204_76.png)

2. Close the Cloud Shell pane in the portal.

   ![LAB10-Az204_77](Evidencia/LAB10-Az204_77.png)

#### Task 3: Close the active application

1. Close the currently running Microsoft Edge application.
2. Close the currently running Visual Studio Code application.
3. Close the currently running Azure Storage Explorer application.

#### Review

In this exercise, you cleaned up your subscription by removing the resource group that was used in this lab.