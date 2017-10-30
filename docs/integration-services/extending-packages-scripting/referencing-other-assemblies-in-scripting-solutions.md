---
title: "Référencer d’autres assemblys dans les Solutions de script | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3deb13c7e3aeb2e974ac6e6582555a617346a298
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>Référencement d'autres assemblys dans les solutions de script
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] bibliothèque de classes permet au développeur du script avec un ensemble d’outils puissants pour implémenter des fonctionnalités personnalisées dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages. La tâche de script et le composant Script peuvent également utiliser des assemblys managés personnalisés.  
  
> [!NOTE]  
>  Pour activer vos packages d’utiliser les objets et les méthodes d’un service Web, utilisez le **ajouter une référence Web** disponible dans la commande [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). Dans les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous deviez générer une classe proxy pour utiliser un service Web.  
  
## <a name="using-a-managed-assembly"></a>Utilisation d'un assembly managé  
 Pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour rechercher un assembly managé au moment du design, vous devez effectuer les étapes suivantes :  
  
1.  Stockez l'assembly managé dans un dossier sur votre ordinateur.  
  
    > [!NOTE]  
    >  Dans les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouviez uniquement ajouter une référence à un assembly managé qui était stocké dans le dossier %windir%\Microsoft.NET\Framework\vx.x.xxxxx ou le dossier %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies.  
  
2.  Ajoutez une référence à l'assembly managé.  
  
     Pour ajouter la référence, dans VSTA, dans le **ajouter une référence** boîte de dialogue le **Parcourir** onglet, recherchez et ajoutez l’assembly managé.  
  
 Pour que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] recherche l'assembly managé au moment de l'exécution, vous devez procéder comme suit :  
  
1.  Signez l'assembly managé avec un nom fort.  
  
2.  Installez l'assembly dans le Global Assembly Cache sur l'ordinateur sur lequel le package est exécuté.  
  
     Pour plus d’informations, consultez [génération, déploiement et débogage des objets personnalisés](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="using-the-microsoft-net-framework-class-library"></a>Utilisation de la bibliothèque de classes Microsoft .NET Framework  
 La tâche de script et le composant Script peuvent tirer parti de tous les autres objets et fonctionnalités exposés par la bibliothèque de classes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Par exemple, en utilisant [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez extraire des informations sur votre environnement et interagir avec l'ordinateur qui exécute le package.  
  
 Cette liste décrit plusieurs classes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] figurant parmi les plus fréquemment utilisées :  
  
-   **System.Data** contient l’architecture ADO.NET.  
  
-   **System.IO** fournit une interface pour le système de fichiers et les flux de données.  
  
-   **System.Windows.Forms** fournit la création de formulaires.  
  
-   **System.Text.RegularExpressions** fournit des classes pour travailler avec des expressions régulières.  
  
-   **System.Environment** retourne des informations sur l’ordinateur local, l’utilisateur actuel et l’ordinateur et les paramètres utilisateur.  
  
-   **System.Net** fournit une communication réseau.  
  
-   **System.DirectoryServices** expose Active Directory.  
  
-   **System.Drawing** fournit des bibliothèques de manipulation d’image complète.  
  
-   **System.Threading** permet la programmation multithread.  
  
 Pour plus d'informations sur le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], consultez MSDN Library.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Packages avec des scripts](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  

