# Lab 03: Retrieving Azure Storage resources and metadata by using the Azure Storage SDK for .NET

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
- File Explorer

**Architecture**

![LAB03_Az204_00_Architecture](Evidencia/LAB03_Az204_00_Architecture.png)

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

3. On the **Storage accounts** blade, find your list of Storage instances.

   ![LAB03_Az204_01](Evidencia/LAB03_Az204_01.png)

4. On the **Storage accounts** blade, select **New**.

5. Find the tabs on the **Create storage account** blade, such as **Basics**.

   > **Note**: Each tab represents a step in the workflow to create a new storage account. You can select **Review + Create** at any time to skip the remaining tabs.

   ![LAB03_Az204_02](Evidencia/LAB03_Az204_02.png)

6. On the **Basics** tab, perform the following actions:

   1. Leave the **Subscription** text box set to its default value.
   2. In the **Resource group** section, select **Create new**, enter **StorageMedia**, and then select **OK**.
   3. In the **Storage account name** text box, enter **mediastor\*[yourname]\***.
   4. In the **Location** drop-down list, select the **(US) East US** region.
   5. In the **Performance** section, select **Standard**.
   6. In the **Redundancy** drop-down list, select **Locally-redundant storage (LRS)**.
   7. Select **Review + Create**.

   ![LAB03_Az204_03](Evidencia/LAB03_Az204_03.png)

7. On the **Review + Create** tab, review the options that you selected during the previous steps.

   ![LAB03_Az204_04](Evidencia/LAB03_Az204_04.png)

8. Select **Create** to create the storage account by using your specified configuration.

   > **Note**: Wait for the creation task to complete before you move forward with this lab.

   ![LAB03_Az204_05](Evidencia/LAB03_Az204_05.png)

   

9. In the Azure portal’s navigation pane, select **All services**.

10. On the **All services** blade, select **Storage Accounts**.

    ![LAB03_Az204_06](Evidencia/LAB03_Az204_06.png)

11. On the **Storage accounts** blade, select the **mediastor\*[yourname]\*** storage account instance.

12. On the **Storage account** blade, find the **Settings** section, and then select the **Endpoints** link.

    ![LAB03_Az204_07](Evidencia/LAB03_Az204_07.png)

13. In the **Endpoints** section, record the value of the **Blob Service** text box.

    > **Note**: You’ll use this endpoint value later in the lab.

    ![LAB03_Az204_08](Evidencia/LAB03_Az204_08.png)

14. Still on the **Storage account** blade, find the **Security + networking** section, and then select the **Access keys** link.

    ![LAB03_Az204_09](Evidencia/LAB03_Az204_09.png)

15. In the **Access keys** section, perform the following actions:

    1. Record the value in the **Storage account name** text box.
    2. Select any one of the keys, and then record the value in either of the **Key** boxes.

    > **Note**: All these values will be used later in this lab.

![LAB03_Az204_10](Evidencia/LAB03_Az204_10.png)

#### Review

In this exercise, you created a new Storage account to use throughout the remainder of the lab.

### Exercise 2: Upload a blob into a container

#### Task 1: Create storage account containers

1. In the Azure portal’s navigation pane, select the **Resource groups** link.

2. On the **Resource groups** blade, find and then select the **StorageMedia** resource group that you created earlier in this lab.

   ![LAB03_Az204_11](Evidencia/LAB03_Az204_11.png)

3. On the **StorageMedia** blade, select the **mediastor\*[yourname]\*** storage account that you created earlier in this lab.

4. On the **Storage account** blade, select the **Containers** link in the **Data storage** section.

   ![LAB03_Az204_12](Evidencia/LAB03_Az204_12.png)

5. In the **Containers** section, select **+ Container**.

6. In the **New container** pop-up window, perform the following actions:
   1. In the **Name** text box, enter **raster-graphics**.
   2. In the **Public access level** drop-down list, select **Private (no anonymous access)**, and then select **OK**.

7. Back in the **Containers** section, select **+ Container**.

   ![LAB03_Az204_13](Evidencia/LAB03_Az204_13.png)

8. In the **New container** pop-up window, perform the following actions:
   1. In the **Name** text box, enter **compressed-audio**.

   2. In the **Public access level** drop-down list, select **Private (no anonymous access)**, and then select **OK**.

      ![LAB03_Az204_14](Evidencia/LAB03_Az204_14.png)

9. Back in the **Containers** section, observe the updated list of containers.

   ![LAB03_Az204_15](Evidencia/LAB03_Az204_15.png)

#### Task 2: Upload a storage account blob

1. In the Azure portal’s navigation pane, select the **Resource groups** link.

2. On the **Resource groups** blade, find and then select the **StorageMedia** resource group that you created earlier in this lab.

3. On the **StorageMedia** blade, select the **mediastor\*[yourname]\*** storage account that you created earlier in this lab.

4. On the **Storage account** blade, select the **Containers** link in the **Data storage** section.

5. In the **Containers** section, select the recently created **raster-graphics** container.

   ![LAB03_Az204_16](Evidencia/LAB03_Az204_16.png)

6. On the **Container** blade, select **Upload**.

7. In the **Upload blob** window, perform the following actions:

   1. In the **Files** section, select the **Folder** icon.

   2. In the **File Explorer** window, browse to **Allfiles (F):\Allfiles\Labs\03\Starter\Images**, select the **graph.jpg** file, and then select **Open**.

      ![LAB03_Az204_17](Evidencia/LAB03_Az204_17.png)

   3. Ensure that the **Overwrite if files already exist** check box is selected, and then select **Upload**.

   > **Note**: Wait for the blob to upload before you continue with this lab.

![LAB03_Az204_18](Evidencia/LAB03_Az204_18.png)

![LAB03_Az204_19](Evidencia/LAB03_Az204_19.png)

#### Review

In this exercise, you created a couple of placeholder containers in the storage account and populated one of the containers with a blob.

### Exercise 3: Access containers by using the .NET SDK

#### Task 1: Create .NET project

1. On the **Start** screen, select the **Visual Studio Code** tile.

2. From the **File** menu, select **Open Folder**.

3. In the **File Explorer** window that opens, browse to **Allfiles (F):\Allfiles\Labs\03\Starter\BlobManager**, and then select **Select Folder**.

   ![LAB03_Az204_20](Evidencia/LAB03_Az204_20.png)

   ![LAB03_Az204_21](Evidencia/LAB03_Az204_21.png)

   

4. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

   ![LAB03_Az204_22](Evidencia/LAB03_Az204_22.png)

   ![LAB03_Az204_23](Evidencia/LAB03_Az204_23.png)

5. At the open command prompt, enter the following command, and then select Enter to create a new .NET project named **BlobManager** in the current folder:

   CodeCopy

   ```
   dotnet new console --name BlobManager --output .
   ```

   > **Note**: The **dotnet new** command will create a new **console** project in a folder with the same name as the project.

   ![LAB03_Az204_24](Evidencia/LAB03_Az204_24.png)

6. At the command prompt, enter the following command, and then select Enter to import version 12.0.0 of **Azure.Storage.Blobs** from NuGet:

   CodeCopy

   ```
   dotnet add package Azure.Storage.Blobs --version 12.0.0
   ```

   > **Note**: The **dotnet add package** command will add the **Azure.Storage.Blobs** package from NuGet. For more information, go to [Azure.Storage.Blobs](https://www.nuget.org/packages/Azure.Storage.Blobs/12.0.0).

   ![LAB03_Az204_25](Evidencia/LAB03_Az204_25.png)

7. At the command prompt, enter the following command, and then select Enter to build the .NET web application:

   CodeCopy

   ```
   dotnet build
   ```

   ![LAB03_Az204_26](Evidencia/LAB03_Az204_26.png)

8. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 2: Modify the Program class to access Storage

1. In the Explorer pane of the **Visual Studio Code** window, open the **Program.cs** file.

   ![LAB03_Az204_27](Evidencia/LAB03_Az204_27.png)

2. On the code editor tab for the **Program.cs** file, delete all the code in the existing file.

   ![LAB03_Az204_28](Evidencia/LAB03_Az204_28.png)

3. Add the following line of code to import the **Azure.Storage**, **Azure.Storage.Blobs**, and **Azure.Storage.Blobs.Models** namespaces from the **Azure.Storage.Blobs** package imported from NuGet:

   CodeCopy

   ```
   using Azure.Storage;
   using Azure.Storage.Blobs;
   using Azure.Storage.Blobs.Models;
   ```

   ![LAB03_Az204_29](Evidencia/LAB03_Az204_29.png)

4. Add the following lines of code to add **using** directives for the built-in namespaces that will be used in this file:

   CodeCopy

   ```
   using System;
   using System.Threading.Tasks;
   ```

   ![LAB03_Az204_30](Evidencia/LAB03_Az204_30.png)

5. Enter the following code to create a new **Program** class:

   CodeCopy

   ```
   public class Program
   {
   }
   ```

   ![LAB03_Az204_31](Evidencia/LAB03_Az204_31.png)

6. In the **Program** class, enter the following line of code to create a new string constant named **blobServiceEndpoint**:

   CodeCopy

   ```
   private const string blobServiceEndpoint = "";
   ```

   ![LAB03_Az204_32](Evidencia/LAB03_Az204_32.png)

7. Update the **blobServiceEndpoint** string constant by setting its value to the **Primary Blob Service Endpoint** of the Storage account that you recorded earlier in this lab.

   ![LAB03_Az204_33](Evidencia/LAB03_Az204_33.png)

   ![LAB03_Az204_34](Evidencia/LAB03_Az204_34.png)

8. In the **Program** class, enter the following line of code to create a new string constant named **storageAccountName**:

   CodeCopy

   ```
   private const string storageAccountName = "";
   ```

   ![LAB03_Az204_35](Evidencia/LAB03_Az204_35.png)

9. Update the **storageAccountName** string constant by setting its value to the **Storage account name** of the Storage account that you recorded earlier in this lab.

   ![LAB03_Az204_36](Evidencia/LAB03_Az204_36.png)

   ![LAB03_Az204_37](Evidencia/LAB03_Az204_37.png)

10. In the **Program** class, enter the following line of code to create a new string constant named **storageAccountKey**:

    CodeCopy

    ```
    private const string storageAccountKey = "";
    ```

    ![LAB03_Az204_38](Evidencia/LAB03_Az204_38.png)

11. Update the **storageAccountKey** string constant by setting its value to the **Key** of the Storage account that you recorded earlier in this lab.

    ![LAB03_Az204_39](Evidencia/LAB03_Az204_39.png)

    ![LAB03_Az204_40](Evidencia/LAB03_Az204_40.png)

12. In the **Program** class, enter the following code to create a new asynchronous **Main** method:

    CodeCopy

    ```
    public static async Task Main(string[] args)
    {
    }
    ```

    ![LAB03_Az204_41](Evidencia/LAB03_Az204_41.png)

13. Observe the **Program.cs** file, which should now include:

    CodeCopy

    ```
    using Azure.Storage;
    using Azure.Storage.Blobs;
    using Azure.Storage.Blobs.Models;
    using System;
    using System.Threading.Tasks;
    
    public class Program
    {
        private const string blobServiceEndpoint = "<primary-blob-service-endpoint>";
        private const string storageAccountName = "<storage-account-name>";
        private const string storageAccountKey = "<key>";
    
        public static async Task Main(string[] args)
        {
        }
    }
    ```

#### Task 3: Connect to the Azure Storage blob service endpoint

1. In the **Main** method, add the following line of code to create a new instance of the **StorageSharedKeyCredential** class by using the **storageAccountName** and **storageAccountKey** constants as constructor parameters:

   CodeCopy

   ```
   StorageSharedKeyCredential accountCredentials = new StorageSharedKeyCredential(storageAccountName, storageAccountKey);
   ```

   ![LAB03_Az204_42](Evidencia/LAB03_Az204_42.png)

2. In the **Main** method, add the following line of code to create a new instance of the **BlobServiceClient** class by using the **blobServiceEndpoint** constant and the *accountCredentials* variable as constructor parameters:

   CodeCopy

   ```
   BlobServiceClient serviceClient = new BlobServiceClient(new Uri(blobServiceEndpoint), accountCredentials);
   ```

   ![LAB03_Az204_43](Evidencia/LAB03_Az204_43.png)

3. In the **Main** method, add the following line of code to invoke the **GetAccountInfoAsync** method of the **BlobServiceClient** class to retrieve account metadata from the service:

   CodeCopy

   ```
   AccountInfo info = await serviceClient.GetAccountInfoAsync();
   ```

   ![LAB03_Az204_44](Evidencia/LAB03_Az204_44.png)

4. In the **Main** method, add the following line of code to render a welcome message:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Connected to Azure Storage Account");
   ```

   ![LAB03_Az204_45](Evidencia/LAB03_Az204_45.png)

5. In the **Main** method, add the following line of code to render the storage account’s name:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Account name:\t{storageAccountName}");
   ```

   ![LAB03_Az204_46](Evidencia/LAB03_Az204_46.png)

6. In the **Main** method, add the following line of code to render the type of storage account:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Account kind:\t{info?.AccountKind}");
   ```

   ![LAB03_Az204_47](Evidencia/LAB03_Az204_47.png)

7. In the **Main** method, add the following line of code to render the currently selected stock keeping unit (SKU) for the storage account:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Account sku:\t{info?.SkuName}");
   ```

   ![LAB03_Az204_48](Evidencia/LAB03_Az204_48.png)

8. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       StorageSharedKeyCredential accountCredentials = new StorageSharedKeyCredential(storageAccountName, storageAccountKey);	
   
       BlobServiceClient serviceClient = new BlobServiceClient(new Uri(blobServiceEndpoint), accountCredentials);
   
       AccountInfo info = await serviceClient.GetAccountInfoAsync();
   
       await Console.Out.WriteLineAsync($"Connected to Azure Storage Account");
       await Console.Out.WriteLineAsync($"Account name:\t{storageAccountName}");
       await Console.Out.WriteLineAsync($"Account kind:\t{info?.AccountKind}");
       await Console.Out.WriteLineAsync($"Account sku:\t{info?.SkuName}");
   }
   ```

   

9. Save the **Program.cs** file.

   ![LAB03_Az204_49](Evidencia/LAB03_Az204_49.png)

10. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

    ![LAB03_Az204_50](Evidencia/LAB03_Az204_50.png)

11. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

    CodeCopy

    ```
    dotnet run
    ```

    > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\03\Solution\BlobManager** folder.

    ![LAB03_Az204_51](Evidencia/LAB03_Az204_51.png)

    ![LAB03_Az204_52](Evidencia/LAB03_Az204_52.png)

12. Observe the output from the currently running console application. The output contains metadata for the Storage account that was retrieved from the service.

13. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 4: Enumerate the existing containers

1. In the **Program** class, enter the following code to create a new **private static** method named **EnumerateContainersAsync** that’s asynchronous and has a single **BlobServiceClient** parameter type:

   CodeCopy

   ```
   private static async Task EnumerateContainersAsync(BlobServiceClient client)
   {        
   }
   ```

   ![LAB03_Az204_53](Evidencia/LAB03_Az204_53.png)

2. In the **EnumerateContainersAsync** method, enter the following code to create an asynchronous **foreach** loop that iterates over the results of an invocation of the **GetBlobContainersAsync** method of the **BlobServiceClient** class:

   CodeCopy

   ```
   await foreach (BlobContainerItem container in client.GetBlobContainersAsync())
   {
   }
   ```

   ![LAB03_Az204_54](Evidencia/LAB03_Az204_54.png)

3. Within the **foreach** loop, enter the following code to print the name of each container:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Container:\t{container.Name}");
   ```

   ![LAB03_Az204_55](Evidencia/LAB03_Az204_55.png)

4. Observe the **EnumerateContainersAsync** method, which should now include:

   CodeCopy

   ```
   private static async Task EnumerateContainersAsync(BlobServiceClient client)
   {        
       await foreach (BlobContainerItem container in client.GetBlobContainersAsync())
       {
           await Console.Out.WriteLineAsync($"Container:\t{container.Name}");
       }
   }
   ```

   ![LAB03_Az204_56](Evidencia/LAB03_Az204_56.png)

5. In the **Main** method, enter the following code at the end of the method to invoke the **EnumerateContainersAsync** method, passing in the *serviceClient* variable as a parameter:

   CodeCopy

   ```
   await EnumerateContainersAsync(serviceClient);
   ```

   ![LAB03_Az204_57](Evidencia/LAB03_Az204_57.png)

6. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       // Existing code removed for brevity
           
       await EnumerateContainersAsync(serviceClient);
   }
   ```

   ![LAB03_Az204_58](Evidencia/LAB03_Az204_58.png)

7. Save the **Program.cs** file.

   ![LAB03_Az204_59](Evidencia/LAB03_Az204_59.png)

8. In the **Visual Studio Code** window, right-click or access the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

   ![LAB03_Az204_60](Evidencia/LAB03_Az204_60.png)

9. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

   CodeCopy

   ```
   dotnet run
   ```

   > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\03\Solution\BlobManager** folder.

   ![LAB03_Az204_61](Evidencia/LAB03_Az204_61.png)

   ![LAB03_Az204_62](Evidencia/LAB03_Az204_62.png)

10. Observe the output from the currently running console application. The updated output includes a list of every existing container in the account.

11. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Review

In this exercise, you accessed existing containers by using the Azure Storage SDK.

### Exercise 4: Retrieve blob Uniform Resource Identifiers (URIs) by using the .NET SDK

#### Task 1: Enumerate the blobs in an existing container by using the SDK

1. In the **Program** class, enter the following code to create a new **private static** method named **EnumerateBlobsAsync** that’s asynchronous and has two parameter types, **BlobServiceClient** and **string**:

   CodeCopy

   ```
   private static async Task EnumerateBlobsAsync(BlobServiceClient client, string containerName)
   {      
   }
   ```

   ![LAB03_Az204_63](Evidencia/LAB03_Az204_63.png)

2. In the **EnumerateBlobsAsync** method, enter the following code to get a new instance of the **BlobContainerClient** class by using the **GetBlobContainerClient** method of the **BlobServiceClient** class, passing in the **containerName** parameter:

   CodeCopy

   ```
   BlobContainerClient container = client.GetBlobContainerClient(containerName);
   ```

   ![LAB03_Az204_64](Evidencia/LAB03_Az204_64.png)

3. In the **EnumerateBlobsAsync** method, enter the following code to render the name of the container that will be enumerated:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Searching:\t{container.Name}");
   ```

   ![LAB03_Az204_65](Evidencia/LAB03_Az204_65.png)

   ![LAB03_Az204_65a](Evidencia/LAB03_Az204_65a.png)

4. In the **EnumerateBlobsAsync** method, enter the following code to create an asynchronous **foreach** loop that iterates over the results of an invocation of the **GetBlobsAsync** method of the **BlobContainerClient** class:

   CodeCopy

   ```
   await foreach (BlobItem blob in container.GetBlobsAsync())
   {        
   }
   ```

   ![LAB03_Az204_66](Evidencia/LAB03_Az204_66.png)

5. Within the **foreach** loop, enter the following code to print the name of each blob:

   CodeCopy

   ```
    await Console.Out.WriteLineAsync($"Existing Blob:\t{blob.Name}");
   ```

   ![LAB03_Az204_67](Evidencia/LAB03_Az204_67.png)

6. Observe the **EnumerateBlobsAsync** method, which should now include:

   CodeCopy

   ```
   private static async Task EnumerateBlobsAsync(BlobServiceClient client, string containerName)
   {      
       BlobContainerClient container = client.GetBlobContainerClient(containerName);
           
       await Console.Out.WriteLineAsync($"Searching:\t{container.Name}");
           
       await foreach (BlobItem blob in container.GetBlobsAsync())
       {        
            await Console.Out.WriteLineAsync($"Existing Blob:\t{blob.Name}");
       }
   }
   ```

   ![LAB03_Az204_68](Evidencia/LAB03_Az204_68.png)

7. In the **Main** method, enter the following code at the end of the method to create a variable named *existingContainerName* with a value of **raster-graphics**:

   CodeCopy

   ```
   string existingContainerName = "raster-graphics";
   ```

   ![LAB03_Az204_69](Evidencia/LAB03_Az204_69.png)

8. In the **Main** method, enter the following code at the end of the method to invoke the **EnumerateBlobsAsync** method, passing in the *serviceClient* and *existingContainerName* variables as parameters:

   CodeCopy

   ```
   await EnumerateBlobsAsync(serviceClient, existingContainerName);
   ```

   ![LAB03_Az204_70](Evidencia/LAB03_Az204_70.png)

9. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       // Existing code removed for brevity
           
       await EnumerateContainersAsync(serviceClient);
   
       string existingContainerName = "raster-graphics";
       await EnumerateBlobsAsync(serviceClient, existingContainerName);
   }
   ```

   ![LAB03_Az204_71](Evidencia/LAB03_Az204_71.png)

10. Save the **Program.cs** file.

    ![LAB03_Az204_72](Evidencia/LAB03_Az204_72.png)

11. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

    ![LAB03_Az204_73](Evidencia/LAB03_Az204_73.png)

12. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

    CodeCopy

    ```
    dotnet run
    ```

    > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\03\Solution\BlobManager** folder.

    ![LAB03_Az204_74](Evidencia/LAB03_Az204_74.png)

    ![LAB03_Az204_75](Evidencia/LAB03_Az204_75.png)

13. Observe the output from the currently running console application. The updated output includes metadata about the existing container and blobs.

14. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 2: Create a new container by using the SDK

1. In the **Program** class, enter the following code to create a new **private static** method named **GetContainerAsync** that’s asynchronous and has two parameter types, **BlobServiceClient** and **string**:

   CodeCopy

   ```
   private static async Task<BlobContainerClient> GetContainerAsync(BlobServiceClient client, string containerName)
   {      
   }
   ```

   ![LAB03_Az204_76](Evidencia/LAB03_Az204_76.png)

2. In the **GetContainerAsync** method, enter the following code to get a new instance of the **BlobContainerClient** class by using the **GetBlobContainerClient** method of the **BlobServiceClient** class, passing in the **containerName** parameter:

   CodeCopy

   ```
   BlobContainerClient container = client.GetBlobContainerClient(containerName);
   ```

   ![LAB03_Az204_77](Evidencia/LAB03_Az204_77.png)

3. In the **GetContainerAsync** method, enter the following code to invoke the **CreateIfNotExistsAsync** method of the **BlobContainerClient** class:

   CodeCopy

   ```
   await container.CreateIfNotExistsAsync(PublicAccessType.Blob);
   ```

   ![LAB03_Az204_78](Evidencia/LAB03_Az204_78.png)

4. In the **GetContainerAsync** method, enter the following code to render the name of the container that was potentially created:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"New Container:\t{container.Name}");
   ```

   ![LAB03_Az204_79](Evidencia/LAB03_Az204_79.png)

5. In the **GetContainerAsync** method, enter the following code to return the instance of the **BlobContainerClient** class named **container** as the result of the **GetContainerAsync** method:

   CodeCopy

   ```
   return container;
   ```

   ![LAB03_Az204_80](Evidencia/LAB03_Az204_80.png)

6. Observe the **GetContainerAsync** method, which should now include:

   CodeCopy

   ```
   private static async Task<BlobContainerClient> GetContainerAsync(BlobServiceClient client, string containerName)
   {      
       BlobContainerClient container = client.GetBlobContainerClient(containerName);
           
       await container.CreateIfNotExistsAsync(PublicAccessType.Blob);
           
       await Console.Out.WriteLineAsync($"New Container:\t{container.Name}");
           
       return container;
   }
   ```

   ![LAB03_Az204_81](Evidencia/LAB03_Az204_81.png)

7. In the **Main** method, enter the following code at the end of the method to create a variable named *newContainerName* with a value of **vector-graphics**:

   CodeCopy

   ```
   string newContainerName = "vector-graphics";
   ```

   ![LAB03_Az204_82](Evidencia/LAB03_Az204_82.png)

8. In the **Main** method, enter the following code at the end of the method to invoke the **GetContainerAsync** method, passing in the *serviceClient* and *newContainerName* variables as parameters, and to store the result in a variable named *containerClient* of type **BlobContainerClient**:

   CodeCopy

   ```
   BlobContainerClient containerClient = await GetContainerAsync(serviceClient, newContainerName);
   ```

   ![LAB03_Az204_83](Evidencia/LAB03_Az204_83.png)

9. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       // Existing code removed for brevity
           
       await EnumerateContainersAsync(serviceClient);
   
       string existingContainerName = "raster-graphics";
       await EnumerateBlobsAsync(serviceClient, existingContainerName);
           
       string newContainerName = "vector-graphics";
       BlobContainerClient containerClient = await GetContainerAsync(serviceClient, newContainerName);
   }
   ```

   ![LAB03_Az204_84](Evidencia/LAB03_Az204_84.png)

10. Save the **Program.cs** file.

    ![LAB03_Az204_85](Evidencia/LAB03_Az204_85.png)

11. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

    ![LAB03_Az204_86](Evidencia/LAB03_Az204_86.png)

12. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

    CodeCopy

    ```
    dotnet run
    ```

    > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\03\Solution\BlobManager** folder.

    ![LAB03_Az204_87](Evidencia/LAB03_Az204_87.png)

    ![LAB03_Az204_88](Evidencia/LAB03_Az204_88.png)

13. Observe the output from the currently running console application. The updated output includes metadata about the existing container and blobs.

14. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 3: Upload a new blob by using the portal

1. In the Azure portal’s navigation pane, select the **Resource groups** link.

2. On the **Resource groups** blade, find and then select the **StorageMedia** resource group that you created earlier in this lab.

   ![LAB03_Az204_89](Evidencia/LAB03_Az204_89.png)

3. On the **StorageMedia** blade, select the **mediastor\*[yourname]\*** storage account that you created earlier in this lab.

   ![LAB03_Az204_90](Evidencia/LAB03_Az204_90.png)

4. On the **Storage account** blade, select the **Containers** link in the **Data storage** section.

5. In the **Containers** section, select the newly created **vector-graphics** container.

   ![LAB03_Az204_91](Evidencia/LAB03_Az204_91.png)

6. On the **Container** blade, select **Upload**.

7. In the **Upload blob** window, perform the following actions:

   1. In the **Files** section, select the **Folder** icon.

   2. In the **File Explorer** window, browse to **Allfiles (F):\Allfiles\Labs\03\Starter\Images**, select the **graph.svg** file, and then select **Open**.

      ![LAB03_Az204_92](Evidencia/LAB03_Az204_92.png)

   3. Ensure that the **Overwrite if files already exist** check box is selected, and then select **Upload**.

   > **Note**: Wait for the blob to upload before you continue with this lab.

![LAB03_Az204_93](Evidencia/LAB03_Az204_93.png)

![LAB03_Az204_94](Evidencia/LAB03_Az204_94.png)

#### Task 4: Access blob URI by using the SDK

1. In the **Program** class, enter the following code to create a new **private static** method named **GetBlobAsync** that’s asynchronous and has two parameter types, **BlobContainerClient** and **string**:

   CodeCopy

   ```
   private static async Task<BlobClient> GetBlobAsync(BlobContainerClient client, string blobName)
   {      
   }
   ```

   ![LAB03_Az204_95](Evidencia/LAB03_Az204_95.png)

2. In the **GetBlobAsync** method, enter the following code to get a new instance of the **BlobClient** class by using the **GetBlobClient** method of the **BlobContainerClient** class, passing in the **blobName** parameter:

   CodeCopy

   ```
   BlobClient blob = client.GetBlobClient(blobName);
   ```

   ![LAB03_Az204_97](Evidencia/LAB03_Az204_97.png)

3. In the **GetBlobAsync** method, enter the following code to render the name of the blob that was referenced:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Blob Found:\t{blob.Name}");
   ```

   ![LAB03_Az204_98](Evidencia/LAB03_Az204_98.png)

4. In the **GetBlobAsync** method, enter the following code to return the instance of the **BlobClient** class named **blob** as the result of the **GetBlobAsync** method:

   CodeCopy

   ```
   return blob;
   ```

   ![LAB03_Az204_99](Evidencia/LAB03_Az204_99.png)

5. Observe the **GetBlobAsync** method, which should now include:

   CodeCopy

   ```
   private static async Task<BlobClient> GetBlobAsync(BlobContainerClient client, string blobName)
   {      
       BlobClient blob = client.GetBlobClient(blobName);
       await Console.Out.WriteLineAsync($"Blob Found:\t{blob.Name}");
       return blob;
   }
   ```

   ![LAB03_Az204_100](Evidencia/LAB03_Az204_100.png)

6. In the **Main** method, enter the following code at the end of the method to create a variable named *uploadedBlobName* with a value of **graph.svg**:

   CodeCopy

   ```
   string uploadedBlobName = "graph.svg";
   ```

   ![LAB03_Az204_101](Evidencia/LAB03_Az204_101.png)

7. In the **Main** method, enter the following code at the end of the method to invoke the **GetBlobAsync** method, passing in the *containerClient* and *uploadedBlobName* variables as parameters, and to store the result in a variable named *blobClient* of type **BlobClient**:

   CodeCopy

   ```
   BlobClient blobClient = await GetBlobAsync(containerClient, uploadedBlobName);
   ```

   ![LAB03_Az204_102](Evidencia/LAB03_Az204_102.png)

8. In the **Main** method, enter the following code at the end of the method to render the **Uri** property of the *blobClient* variable:

   CodeCopy

   ```
   await Console.Out.WriteLineAsync($"Blob Url:\t{blobClient.Uri}");
   ```

   ![LAB03_Az204_103](Evidencia/LAB03_Az204_103.png)

9. Observe the **Main** method, which should now include:

   CodeCopy

   ```
   public static async Task Main(string[] args)
   {
       // Existing code removed for brevity
           
       await EnumerateContainersAsync(serviceClient);
   
       string existingContainerName = "raster-graphics";
       await EnumerateBlobsAsync(serviceClient, existingContainerName);
           
       string newContainerName = "vector-graphics";
       BlobContainerClient containerClient = await GetContainerAsync(serviceClient, newContainerName);
           
       string uploadedBlobName = "graph.svg";
       BlobClient blobClient = await GetBlobAsync(containerClient, uploadedBlobName);
   
       await Console.Out.WriteLineAsync($"Blob Url:\t{blobClient.Uri}");
   }
   ```

   ![LAB03_Az204_104](Evidencia/LAB03_Az204_104.png)

10. Save the **Program.cs** file.

    ![LAB03_Az204_105](Evidencia/LAB03_Az204_105.png)

11. In the **Visual Studio Code** window, right-click or activate the shortcut menu for the Explorer pane, and then select **Open in Terminal**.

    ![LAB03_Az204_106](Evidencia/LAB03_Az204_106.png)

12. At the open command prompt, enter the following command, and then select Enter to run the .NET web application:

    CodeCopy

    ```
    dotnet run
    ```

    > **Note**: If there are any build errors, review the **Program.cs** file in the **Allfiles (F):\Allfiles\Labs\03\Solution\BlobManager** folder.

    ![LAB03_Az204_107](Evidencia/LAB03_Az204_107.png)

    ![LAB03_Az204_108](Evidencia/LAB03_Az204_108.png)

    

13. Observe the output from the currently running console application. The updated output includes the final URL to access the blob online. Record the value of this URL to use later in the lab.

    > **Note**: The URL will likely be similar to the following string: **https://mediastor\*[yourname]\*.blob.core.windows.net/vector-graphics/graph.svg**

    ![LAB03_Az204_109](Evidencia/LAB03_Az204_109.png)

    

    ![LAB03_Az204_109b](Evidencia/LAB03_Az204_109b.png)

14. Select **Kill Terminal** or the **Recycle Bin** icon to close the currently open terminal and any associated processes.

#### Task 5: Test the URI by using a browser

1. On the taskbar, right-click the **Microsoft Edge** icon or activate the shortcut menu, and then select **New window**.

2. In the new browser window, go to the URL that you copied for the blob earlier in this lab.

3. You should now notice the Scalable Vector Graphic (SVG) file in your browser window.

   ![LAB03_Az204_109d](Evidencia/LAB03_Az204_109d.png)

#### Review

In this exercise, you created containers and managed blobs by using the Storage SDK.

### Exercise 5: Clean up your subscription

#### Task 1: Open Azure Cloud Shell and list resource groups

1. In the Azure portal’s navigation pane, select the **Cloud Shell** icon to open a new shell instance.

   > **Note**: The **Cloud Shell** icon is represented by a greater than sign (>) and underscore character (_).

2. If this is your first time opening Cloud Shell using your subscription, you can use the **Welcome to Azure Cloud Shell Wizard** to configure Cloud Shell for first-time usage. Perform the following actions in the wizard:

   1. A dialog box prompts you to configure the shell. Select **Bash**, review the selected subscription, and then select **Create storage**.

   > **Note**: Wait for Cloud Shell to finish its initial setup procedures before moving forward with the lab. If you don’t notice Cloud Shell configuration options, this is most likely because you’re using an existing subscription with this course’s labs. The labs are written with the presumption that you’re using a new subscription.

#### Task 2: Delete a resource group

1. At the command prompt, enter the following command, and then select Enter to delete the **StorageMedia** resource group:

   CodeCopy

   ```
   az group delete --name StorageMedia --no-wait --yes
   ```

   ![LAB03_Az204_110](Evidencia/LAB03_Az204_110.png)

   ![LAB03_Az204_111](Evidencia/LAB03_Az204_111.png)

   ![LAB03_Az204_112](Evidencia/LAB03_Az204_112.png)

2. Close the Cloud Shell pane in the portal.

#### Task 3: Close the active application

1. the currently running Microsoft Edge application.

#### Review

In this exercise, you cleaned up your subscription by removing the resource group used in this lab.