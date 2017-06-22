---
title: "Comment : déployer une Extension de traitement de données au Concepteur de rapports | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
caps.latest.revision: 41
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 42974101d21082568442d73d063de1d1b937c428
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="deploying-a-data-processing-extension-to-report-designer"></a>Déploiement d’une Extension de traitement des données pour le Concepteur de rapports
  Le Concepteur de rapports utilise des extensions pour le traitement des données afin de récupérer et traiter des données pendant que vous concevez des rapports. Vous devez déployer votre assembly d'extension pour le traitement des données sur le Concepteur de rapports en tant qu'assembly privé. Vous devez également créer une entrée dans le fichier de configuration du Concepteur de rapports (RSReportDesigner.config.)  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Pour déployer un assembly d'extension pour le traitement des données  
  
1.  Copiez votre assembly depuis son emplacement intermédiaire vers le répertoire du Concepteur de rapports. L'emplacement par défaut du répertoire du Concepteur de rapports est le suivant : C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
2.  Une fois le fichier d'assembly copié, ouvrez le fichier RSReportDesigner.config. Le fichier RSReportDesigner.config se trouve également dans le répertoire du Concepteur de rapports. Dans le fichier de configuration, créez une entrée correspondant au fichier d'assembly copié. Vous pouvez ouvrir le fichier de configuration avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou avec un simple éditeur de texte, tel que le bloc-notes.  
  
3.  Localisez l’élément **Data** dans le fichier RSReportDesigner.config. L'entrée correspondant à votre nouvelle extension pour le traitement des données doit être créée à l'emplacement suivant :  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Ajoutez une entrée pour votre extension pour le traitement de données qui inclut un **Extension** élément avec des valeurs pour le **nom**, **Type**, et **Visible** attributs. Votre entrée peut se présenter comme suit :  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     La valeur de **nom** est le nom unique de l’extension de traitement des données. La valeur de **Type** est une liste séparée par des virgules qui comporte une entrée pour l’espace de noms qualifié complet de la classe qui implémente le <xref:Microsoft.ReportingServices.Interfaces.IExtension> et <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, suivis du nom de votre assembly (sans l’extension de fichier .dll). Par défaut, les extensions utilisées pour le traitement des données sont visibles par les utilisateurs finaux. Pour masquer des interfaces utilisateur, tels que le Concepteur de rapports, ajoutez un **Visible** d’attribut pour le **Extension** élément et affectez-lui la valeur **false**.  
  
5.  Enfin, ajoutez un groupe de codes pour votre assembly personnalisé octroyant **FullTrust** autorisation pour votre extension. Pour cela, ajoutez le groupe de codes au fichier rspreviewpolicy.config qui se trouve par défaut à l'emplacement C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies. Ce groupe de codes peut se présenter comme suit :  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 L'appartenance URL n'est qu'une des nombreuses conditions d'appartenance que vous pouvez sélectionner pour l'extension permettant le traitement des données. Pour plus d’informations sur la sécurité d’accès du code dans [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)], consultez [sécurisé de développement &#40; Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
## <a name="generic-query-designer"></a>Concepteur de requêtes générique  
 Le Concepteur de rapports fournit un concepteur de requêtes générique que vous pouvez utiliser avec des extensions pour le traitement des données personnalisées. Ce concepteur comprend deux volets : un volet de requête et un volet de résultats. Vous pouvez utiliser le concepteur générique pour écrire des requêtes qui ne sont pas prises en charge par l'interface graphique. Contrairement au concepteur de requêtes graphique, le concepteur de requêtes générique ne restructure pas les requêtes et n'en vérifie pas la syntaxe.  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a>Pour activer le concepteur de requêtes générique pour une extension personnalisée  
  
-   Ajoutez l’entrée suivante au fichier RSReportDesigner.config sous le **concepteur** élément, en remplaçant le **nom** attribut avec le nom que vous avez fourni dans les entrées précédentes.  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a>Vérification du déploiement  
 Avant de vérifier le déploiement, vous devez fermer toutes les instances de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sur votre ordinateur local. Une fois que vous avez clôturé toutes les sessions en cours, vous pouvez vérifier si votre extension pour le traitement des données a été déployée correctement dans le Concepteur de rapports en créant un nouveau projet de rapport dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Votre extension doit être incluse dans la liste des types de source de données disponibles lorsque vous créez un nouveau jeu de données pour votre rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
