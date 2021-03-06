<properties pageTitle="Use Mobile Services to upload images to blob storage (Windows Phone) | Mobile Services" metaKeywords="" description="Learn how to use Mobile Services to upload images to Azure Blob Storage." metaCanonical="" disqusComments="0" umbracoNaviHide="1" documentationCenter="Mobile" title="Upload images to Azure Storage by using Mobile Services" authors="wesmc" writer="wesmc" services="mobile-services,storage"  />

<tags ms.service="mobile-services" ms.workload="mobile" ms.tgt_pltfrm="mobile-windows-phone" ms.devlang="dotnet" ms.topic="article" ms.date="01/01/1900" ms.author="wesmc" />

# Upload images to Azure Storage by using Mobile Services
<div class="dev-center-tutorial-selector sublanding"><a href="/en-us/documentation/articles/mobile-services-windows-store-dotnet-upload-data-blob-storage" title="Windows Store C#">Windows Store C#</a><a href="/en-us/documentation/articles/mobile-services-windows-phone-upload-data-blob-storage" title="Windows Phone" class="current">Windows Phone</a></div>
<div class="dev-center-tutorial-subselector"><a href="/en-us/documentation/articles/mobile-services-dotnet-backend-windows-phone-upload-data-blob-storage" title=".NET backend" >.NET backend</a> | <a href="/en-us/documentation/articles/mobile-services-windows-phone-upload-data-blob-storage" title="JavaScript backend" class="current">JavaScript backend</a></div>

This topic shows you how to use Azure Mobile Services to enable your app to upload and store user-generated images in Azure Storage. Mobile Services uses a SQL Database to store data. However, binary large object (BLOB) data is more efficiently stored in Azure Blob storage service. 

You cannot securely distribute with the client app the credentials required to securely upload data to the Blob Storage service. Instead, you must store these credentials your mobile service and use them to generate a Shared Access Signature (SAS) that is used to upload a new image. The SAS, a credential with a short expiration--in this case 5 minutes, is returned securely by Mobile Services to the client app. The app then uses this temporary credential to upload the image. In this example, downloads from the Blob service are public.

In this tutorial you add functionality to the Mobile Services quickstart app to take pictures and upload the images to Azure by using an SAS generated by Mobile Services. This tutorial walks you through the following basic steps to update the Mobile Services quickstart to upload images to the Blob Storage service:

1. [Install the Storage Client library]
2. [Update the insert script to generate an SAS]
3. [Update the client app to capture images]
4. [Upload images to test the app]

This tutorial requires the following:

+ Microsoft Visual Studio 2012 Express for Windows 8, or a later version
+ [Windows Phone SDK 8.0] or higher
+ Nuget Package Manager installed for Microsoft Visual Studio.
+ [Azure Storage account][How To Create a Storage Account]

This tutorial is based on the Mobile Services quickstart. Before you start this tutorial, you must first complete [Get started with Mobile Services]. 

##<a name="install-storage-client"></a>Install the Storage client for Windows Phone apps

To be able to use an SAS to upload images to Blob storage, you must first add the NuGet package that installs Storage client library for Windows Phone apps.

1. In **Solution Explorer** in Visual Studio, right-click the project name, and then select **Manage NuGet Packages**.

2. In the left pane, select the **Online** category, select **Include Prerelease**, search for **WindowsAzure.Storage-Preview**, click **Install** on the **Azure Storage** package, then accept the license agreements. 

  	![][2]

  	This adds the client library for Azure storage services to the project.

Next, you will update the quickstart app to capture and upload images.

##<a name="update-scripts"></a>Update the registered insert script in the Management Portal


[WACOM.INCLUDE [mobile-services-configure-blob-storage](../includes/mobile-services-configure-blob-storage.md)]

>[WACOM.NOTE]To add new properties to the TodoItem object, you must have Dynamic Schema enabled in your mobile service. When Dynamic Schema is enabled, new columns are automatically added to the TodoItem table that map to these new properties.

[WACOM.INCLUDE [mobile-services-windows-phone-upload-to-blob-storage](../includes/mobile-services-windows-phone-upload-to-blob-storage.md)]


## <a name="next-steps"> </a>Next steps

Now that you have been able to securely upload images by integrating your mobile service with the Blob service, check out some of the other backend service and integration topics:

+ [Send email from Mobile Services with SendGrid]
 
  Learn how to add email functionality to your Mobile Service using the SendGrid email service. This topic demonstrates how to add server side scripts to send email using SendGrid.

+ [Schedule backend jobs in Mobile Services]

  Learn how to use the Mobile Services job scheduler functionality to define server script code that is executed on a schedule that you define.

+ [Mobile Services server script reference]

  Reference topics for using server scripts to perform server-side tasks and integration with other Azure components and external resources.
 
+ [Mobile Services .NET How-to Conceptual Reference]

  Learn more about how to use Mobile Services with .NET
  
 
<!-- Anchors. -->
[Install the Storage Client library]: #install-storage-client
[Update the client app to capture images]: #add-select-images
[Update the insert script to generate an SAS]: #update-scripts
[Upload images to test the app]: #test
[Next Steps]:#next-steps

<!-- Images. -->


[2]: ./media/mobile-services-windows-phone-upload-data-blob-storage/mobile-add-storage-nuget-package-dotnet.png


[5]: ./media/mobile-services-windows-phone-upload-data-blob-storage/mobile-upload-blob-app-WMAppmanifest-wp8.png
[6]: ./media/mobile-services-windows-phone-upload-data-blob-storage/mobile-upload-blob-app-view-wp8.png
[7]: ./media/mobile-services-windows-phone-upload-data-blob-storage/mobile-upload-blob-app-view-camera-wp8.png
[8]: ./media/mobile-services-windows-phone-upload-data-blob-storage/mobile-upload-blob-app-view-save-wp8.png
[9]: ./media/mobile-services-windows-phone-upload-data-blob-storage/mobile-upload-blob-app-view-final-wp8.png

[11]: ./media/mobile-services-windows-phone-upload-data-blob-storage/mobile-upload-blob-app-view-camera-accept-wp8.png

<!-- URLs. -->
[Send email from Mobile Services with SendGrid]: /en-us/develop/mobile/tutorials/send-email-with-sendgrid/
[Schedule backend jobs in Mobile Services]: /en-us/develop/mobile/tutorials/schedule-backend-tasks/
[Mobile Services server script reference]: http://go.microsoft.com/fwlink/p/?LinkId=262293
[Get started with Mobile Services]: /en-us/documentation/articles/mobile-services-windows-phone-get-started

[Azure Management Portal]: https://manage.windowsazure.com/
[How To Create a Storage Account]: /en-us/manage/services/storage/how-to-create-a-storage-account
[Azure Storage Client library for Store apps]: http://go.microsoft.com/fwlink/p/?LinkId=276866 
[Mobile Services .NET How-to Conceptual Reference]: /en-us/develop/mobile/how-to-guides/work-with-net-client-library
[Windows Phone SDK 8.0]: http://www.microsoft.com/en-us/download/details.aspx?id=35471


