---
title: Déploiement d’une extension de rendu | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 138fd2b43b214e16d960bec9daabb84b0f820c6d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63298601"
---
# <a name="deploying-a-rendering-extension"></a>Déploiement d'une extension de rendu
  Après avoir écrit et compilé votre extension de génération de rapport [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dans une bibliothèque [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vous devez la rendre détectable par le serveur de rapports et par le Concepteur de rapports. Pour cela, copiez l'extension dans le répertoire approprié et ajoutez des entrées aux fichiers de configuration [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] appropriés.  
  
## <a name="configuration-file-rendering-extension-element"></a>Élément Extension de rendu de fichier de configuration  
 Une fois qu'une extension de rendu est compilée dans une .DLL, vous devez ajouter une entrée dans le fichier rsreportserver.config. Par défaut, celui-ci se trouve dans le dossier %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<nom_instance>\Reporting Services\ReportServer. L’élément parent est \<Render>. Sous l'élément Render se trouve un élément Extension pour chaque extension de rendu. L'élément `Extension` contient deux attributs, Name et Type.  
  
 Le tableau suivant décrit les attributs de l' `Extension` élément pour les extensions de rendu :  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Nom**|Nom unique de l'extension. La longueur maximale de l'attribut **Name** est de 255 caractères. Le nom doit être unique parmi toutes les entrées de l'élément **Extensions** d'un fichier de configuration. Si un nom existe en double, le serveur de rapports retourne une erreur.|  
|**Type**|Liste séparée par des virgules qui inclut l'espace de noms complet, ainsi que le nom de l'assembly.|  
|**Visible**|La valeur `false` indique que l'extension de rendu ne doit pas être visible dans les interfaces utilisateur. Si cet attribut n'est pas défini, la valeur par défaut est `true`.|  
|**LogAllExecutionRequests**|La valeur `false` indique qu'une entrée est enregistrée pour la première exécution de rapport uniquement dans une session. Si cet attribut n'est pas défini, la valeur par défaut est `true`.<br /><br /> Par exemple, ce paramètre détermine s'il convient d'enregistrer une entrée pour la première page rendue dans un rapport uniquement (lorsque la valeur est `false`) ou une entrée pour chaque page rendue dans le rapport (lorsque la valeur est `true`).|  
  
 Pour plus d'informations, consultez [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Déploiement de l'extension sur le serveur de rapports  
 Le serveur de rapports utilise des extensions de rendu pour exporter des rapports dans d'autres formats. Vous devez déployer l'assembly d'extension de rendu sur le serveur de rapports sous la forme d'un assembly privé. Vous devez également créer une entrée dans le fichier de configuration du serveur de rapports (rsreportserver.config.)  
  
### <a name="to-deploy-the-assembly"></a>Pour déployer l'assembly  
  
1.  Copiez votre assembly depuis votre emplacement dans le répertoire bin du serveur de rapports sur lequel l'extension de rendu doit être utilisée. L’emplacement par défaut du répertoire Bin du serveur de rapports est le suivant : %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<nom_instance>\Reporting Services\ReportServer\Bin.  
  
2.  Une fois le fichier d'assembly copié, ouvrez le fichier rsreportserver.config. Ce fichier se trouve aussi dans le répertoire bin du serveur de rapports. Vous devez créer une entrée dans le fichier de configuration pour votre fichier d'assembly d'extension. Vous pouvez ouvrir le fichier avec [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou un éditeur de texte simple.  
  
     Pour plus d'informations, consultez [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).  
  
3.  Localisez l'élément **Render** dans le fichier Rsreportserver.config. Une entrée correspondant à votre nouvelle extension doit être créée à l'emplacement suivant :  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  Ajoutez une entrée pour votre extension de rendu. Celle-ci doit comporter un élément dont les valeurs **Name** et **Type**doivent être définies. Cette entrée peut se présenter comme suit :  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     La valeur définie pour **Name** correspond au nom unique de l'extension de rendu. La valeur définie pour **Type** est une liste séparée par des virgules comportant une entrée pour l’espace de noms complet de votre implémentation <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>, suivi du nom de votre assembly (l’extension de fichier .dll ne doit pas figurer dans cette entrée). Par défaut, les extensions de rendu sont visibles. Pour masquer une extension à partir des interfaces utilisateur, telles que Gestionnaire de rapports, **Visible** ajoutez un attribut visible `Extension` à l’élément et affectez `false`-lui la valeur.  
  
## <a name="verifying-the-deployment"></a>Vérification du déploiement  
 Vous pouvez également ouvrir le Gestionnaire de rapports et vérifier que votre extension est répertoriée dans la liste des types d'exportation pour un rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de rendu](implementing-a-rendering-extension.md)   
 [Vue d’ensemble des extensions de rendu](rendering-extensions-overview.md)   
 [Mise en œuvre de l’interface IRenderingExtension](implementing-the-irenderingextension-interface.md)   
 [Considérations sur la sécurité pour les extensions](../security-considerations-for-extensions.md)  
  
  
