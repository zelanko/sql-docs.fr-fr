---
title: "Déploiement d’une Extension de remise | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d072577828375a08c133bb1a68d93e652e5cf168
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="deploying-a-delivery-extension"></a>Déploiement d'une extension de remise
  Les extensions de remise fournissent leurs informations de configuration sous la forme d'un fichier de configuration XML. Le fichier XML est conforme au schéma XML défini pour les extensions de remise. Les extensions de remise fournissent l'infrastructure nécessaire pour définir et modifier le fichier de configuration.  
  
 Si une extension de remise est remplacée ou mise à niveau, tous les abonnements qui référencent cette extension restent valides.  
  
 Après avoir écrit et compilé votre [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension de remise dans un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] bibliothèque, vous devez copier l’extension dans le répertoire approprié et ajoutez une entrée approprié [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] fichier de configuration afin que le serveur de rapports peut le trouver.  
  
## <a name="configuration-file-extension-element"></a>Élément Extension du fichier de configuration  
 Extensions de remise que vous déployez sur le serveur de rapports doivent être entrées en tant que **Extension** éléments dans le fichier de configuration. Le fichier de configuration du serveur de rapports est RSReportServer.config.  
  
 Le tableau suivant décrit les attributs de la **Extension** , élément pour les extensions de remise.  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Nom**|Nom unique de l'extension (par exemple, « Messagerie électronique du serveur de rapports » pour l'extension de remise par messagerie ou « Partage de fichiers du serveur de rapports » pour l'extension de remise par partage de fichiers). La longueur maximale de l'attribut **Name** est de 255 caractères. Le nom doit être unique au sein de toutes les entrées de l’élément **Extension** d’un fichier de configuration. Si un nom existe en double, le serveur de rapports retourne une erreur.|  
|**Type**|Liste séparée par des virgules qui inclut l'espace de noms complet, ainsi que le nom de l'assembly.|  
|**Visible**|La valeur **false** indique que l’extension de remise ne doit pas être visible dans les interfaces utilisateur. Si cet attribut n'est pas défini, la valeur par défaut est **true**.|  
  
 Pour plus d’informations sur le fichier RSReportServer.config, consultez [fichiers de Configuration de Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Déploiement de l'extension sur le serveur de rapports  
 Le serveur de rapports utilise des extensions de remise pour traiter et remettre des notifications ou des rapports. Vous devez déployer l'assembly d'extension de remise sur le serveur de rapports sous la forme d'un assembly privé. Vous devez également créer une entrée dans le fichier de configuration du serveur de rapports, à savoir dans le fichier dénommé RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Pour déployer un assembly d'extension de remise sur un serveur de rapports  
  
1.  Copiez l'assembly depuis son emplacement vers le répertoire bin du serveur de rapports sur lequel l'extension de remise doit être utilisée. L’emplacement par défaut du répertoire bin de serveur de rapports est %ProgramFiles%\Microsoft SQL Server\MSRS13. \<InstanceName > \Reporting.  
  
    > [!IMPORTANT]  
    >  Si vous essayez de remplacer un assembly d'extension de remise existant, vous devez commencer par arrêter le service Report Server avant de copier l'assembly mis à jour. Redémarrez le service une fois l'assembly copié.  
  
2.  Une fois le fichier correspondant à l'assembly copié, ouvrez le fichier RSReportServer.config. Le fichier RSReportServer.config se trouve dans %ProgramFiles%\Microsoft SQL Server\MSRS13. \<InstanceName > \Reporting active. Vous devez créer une entrée pour le fichier d'assembly d'extension de remise dans le fichier de configuration. Vous pouvez ouvrir le fichier de configuration avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou un éditeur de texte simple, tel que le bloc-notes.  
  
3.  Recherchez le **remise** élément dans le fichier RSReportServer.config. Une entrée correspondant à votre nouvelle extension de remise doit être créée à l'emplacement suivant :  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Ajoutez une entrée pour votre extension de remise. Votre entrée doit contenir un **Extension** élément avec des valeurs pour **nom** et **Type**, peut se présenter comme suit :  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     La valeur de **nom** est le nom unique de l’extension de remise. La valeur de **Type** est une liste séparée par des virgules qui comporte une entrée pour l’espace de noms qualifié complet de la classe qui implémente le <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, suivi du nom de votre assembly (sans l’extension de fichier .dll). Par défaut, les extensions de remise sont visibles. Pour masquer des interfaces utilisateur, tels que le portail web, ajoutez un **Visible** d’attribut pour le **Extension** élément et affectez-lui la valeur **false**.  
  
5.  Enfin, ajoutez un groupe de codes pour votre assembly personnalisé octroyant **FullTrust** autorisation pour votre extension de remise. Pour cela, vous devez en ajoutant le groupe de codes au fichier rssrvpolicy.config qui se trouve par défaut dans %ProgramFiles%\Microsoft SQL Server\MSRS13. \<InstanceName > \Reporting. Ce groupe de codes peut se présenter comme suit :  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS13.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     L'appartenance URL n'est qu'une des nombreuses conditions d'appartenance que vous pouvez sélectionner pour l'extension de remise. Pour plus d’informations sur la sécurité d’accès du code dans [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], consultez.[ Sécuriser le développement &#40; Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
   
## <a name="verifying-the-deployment"></a>Vérification du déploiement  
 Vous pouvez vérifier que votre extension de remise a été correctement déployée sur le serveur de rapports en utilisant la méthode <xref:ReportService2010.ReportingService2010.ListExtensions%2A> du service Web. Vous pouvez également ouvrir le portail web et vérifiez que votre extension est incluse dans la liste des extensions de remise disponibles pour un abonnement. Pour plus d’informations sur le portail web et les abonnements, consultez [abonnements et remise &#40; Reporting Services &#41; ](../../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une Extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

