---
title: Déploiement d’une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
caps.latest.revision: 43
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 653369ef20b2febbf90c34e059c9105cdfeaafbf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194879"
---
# <a name="deploying-a-delivery-extension"></a>Déploiement d'une extension de remise
  Les extensions de remise fournissent leurs informations de configuration sous la forme d'un fichier de configuration XML. Le fichier XML est conforme au schéma XML défini pour les extensions de remise. Les extensions de remise fournissent l'infrastructure nécessaire pour définir et modifier le fichier de configuration.  
  
 Si une extension de remise est remplacée ou mise à niveau, tous les abonnements qui référencent cette extension restent valides.  
  
 Après avoir écrit et compilé votre extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dans une bibliothèque [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vous devez la copier dans le répertoire approprié et ajouter une entrée au fichier de configuration [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] approprié afin que le serveur de rapports puisse la trouver.  
  
## <a name="configuration-file-extension-element"></a>Élément Extension du fichier de configuration  
 Les extensions de remise que vous déployez sur le serveur de rapports doivent être entrées sous la forme d'éléments `Extension` dans le fichier de configuration. Le fichier de configuration du serveur de rapports est RSReportServer.config.  
  
 Le tableau suivant décrit les attributs de l'élément `Extension` pour les extensions de remise.  
  
|Attribute|Description|  
|---------------|-----------------|  
|`Name`|Nom unique de l'extension (par exemple, « Messagerie électronique du serveur de rapports » pour l'extension de remise par messagerie ou « Partage de fichiers du serveur de rapports » pour l'extension de remise par partage de fichiers). La longueur maximale de l'attribut `Name` s'élève à 255 caractères. Le nom doit être unique parmi toutes les entrées de la `Extension` élément d’un fichier de configuration. Si un nom existe en double, le serveur de rapports retourne une erreur.|  
|`Type`|Liste séparée par des virgules qui inclut l'espace de noms complet, ainsi que le nom de l'assembly.|  
|`Visible`|La valeur `false` indique que l'extension de remise ne doit pas être visible dans les interfaces utilisateur. Si l’attribut n’est pas inclus, la valeur par défaut est `true`.|  
  
 Pour plus d’informations sur le fichier RSReportServer.config, consultez [Fichiers de configuration de Reporting Services](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Déploiement de l'extension sur le serveur de rapports  
 Le serveur de rapports utilise des extensions de remise pour traiter et remettre des notifications ou des rapports. Vous devez déployer l'assembly d'extension de remise sur le serveur de rapports sous la forme d'un assembly privé. Vous devez également créer une entrée dans le fichier de configuration du serveur de rapports, à savoir dans le fichier dénommé RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Pour déployer un assembly d'extension de remise sur un serveur de rapports  
  
1.  Copiez l'assembly depuis son emplacement vers le répertoire bin du serveur de rapports sur lequel l'extension de remise doit être utilisée. L’emplacement par défaut du répertoire bin de serveur de rapports est %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \Reporting.  
  
    > [!IMPORTANT]  
    >  Si vous essayez de remplacer un assembly d'extension de remise existant, vous devez commencer par arrêter le service Report Server avant de copier l'assembly mis à jour. Redémarrez le service une fois l'assembly copié.  
  
2.  Une fois le fichier correspondant à l'assembly copié, ouvrez le fichier RSReportServer.config. Le fichier RSReportServer.config se trouve dans %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \Reporting Services\ReportServer. Vous devez créer une entrée pour le fichier d'assembly d'extension de remise dans le fichier de configuration. Vous pouvez ouvrir le fichier de configuration à l’aide de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou à l’aide d’un simple éditeur de texte, tel que le Bloc-notes.  
  
3.  Recherchez le `Delivery` élément dans le fichier RSReportServer.config. Une entrée correspondant à votre nouvelle extension de remise doit être créée à l'emplacement suivant :  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Ajoutez une entrée pour votre extension de remise. Celle-ci doit comporter un élément `Extension` dont les attributs `Name` et `Type` doivent être définis. Cette entrée peut se présenter comme suit :  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     La valeur définie pour `Name` correspond au nom unique de l'extension de remise. La valeur définie pour `Type` est une liste séparée par des virgules comportant une entrée pour l'espace de noms complet de la classe qui implémente l'interface <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>, suivie du nom de votre assembly (sans l'extension de fichier .dll). Par défaut, les extensions de remise sont visibles. Pour masquer ces extensions des interfaces utilisateur, telles que le Gestionnaires de rapports, et ne plus les afficher, ajoutez un attribut `Visible` à l'élément `Extension`, puis attribuez à cet élément la valeur `false`.  
  
5.  Enfin, ajoutez une groupe de codes pour votre assembly personnalisé qui octroie l'autorisation `FullTrust` à votre extension de remise. Pour cela, en ajoutant le groupe de codes au fichier rssrvpolicy.config qui se trouve par défaut dans %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \Reporting. Ce groupe de codes peut se présenter comme suit :  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     L'appartenance URL n'est qu'une des nombreuses conditions d'appartenance que vous pouvez sélectionner pour l'extension de remise. Pour plus d’informations sur la sécurité d’accès du code dans [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], consultez [Développement sécurisé &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).  
  
## <a name="deploying-the-extension-to-report-manager"></a>Déploiement de l'extension dans le Gestionnaire de rapports  
 Si votre extension de remise implémente l'interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, votre extension de remise peut être utilisée avec la page d'abonnement du Gestionnaire de rapports. Pour que l'interface utilisateur d'abonnement soit disponible, vous devez déployer votre extension dans le Gestionnaire de rapports.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a>Pour déployer un assembly d'extension de remise dans le Gestionnaire de rapports  
  
1.  Copiez l'assembly depuis son emplacement vers le répertoire bin du Gestionnaire de rapports. L’emplacement par défaut du répertoire bin du Gestionnaire de rapports est %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<Nom_instance > \Reporting Services\ReportManager\bin.  
  
2.  Une fois le fichier correspondant à l'assembly copié, ouvrez le fichier RSReportServer.config. Le fichier RSReportServer.config se trouve dans %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \Reporting Services\ReportServer. Vous devez créer une entrée pour le fichier d'assembly d'extension de remise dans le fichier de configuration. Vous pouvez ouvrir le fichier de configuration avec Visual Studio .NET ou un simple éditeur de texte, tel que le bloc-notes.  
  
3.  Recherchez le `DeliveryUI` élément dans le fichier RSReportServer.config. Une entrée correspondant à votre nouvelle extension de remise doit être créée à l'emplacement suivant :  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  Ajoutez une entrée pour votre extension de remise. Cette entrée doit comporter un élément `Extension` dont les valeurs `Name` et `Type` doivent être définies. Cette entrée peut se présenter comme suit :  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     La valeur définie pour `Name` correspond au nom unique de l'extension de remise. La valeur définie pour `Type` est une liste séparée par des virgules comportant une entrée pour l'espace de noms complet de la classe qui implémente l'interface <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, suivie du nom de votre assembly (sans l'extension de fichier .dll).  
  
    > [!IMPORTANT]  
    >  La valeur de l'attribut `Name` doit être identique pour les entrées du fichier de configuration du serveur de rapports et du Gestionnaire de rapports. Si ces valeurs ne sont pas identiques, la configuration de votre serveur n'est pas valide.  
  
     Enfin, ajoutez une groupe de codes pour votre assembly personnalisé qui octroie l'autorisation `FullTrust` à votre extension de remise. Pour cela, en ajoutant le groupe de codes au fichier RSmgrpolicy.config situé par défaut dans C:\Program Files\Microsoft SQL Server\MSRS10_50. \<Nom_instance > \Reporting Services\ReportManager. Ce groupe de codes peut se présenter comme suit :  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     L'appartenance URL n'est qu'une des nombreuses conditions d'appartenance que vous pouvez sélectionner pour l'extension de remise. Pour plus d’informations sur la sécurité d’accès du code dans [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], consultez [Développement sécurisé &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Vérification du déploiement  
 Vous pouvez vérifier que votre extension de remise a été correctement déployée sur le serveur de rapports en utilisant la méthode <xref:ReportService2010.ReportingService2010.ListExtensions%2A> du service Web. Vous pouvez également ouvrir le Gestionnaire de rapports et vérifier que votre extension est effectivement répertoriée dans la liste des extensions de remise disponibles pour un abonnement. Pour plus d’informations sur le Gestionnaire de rapports et abonnements, consultez [abonnements et remises &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
