---
title: "Création d’une bibliothèque d’Extension de traitement de données | Documents Microsoft"
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
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
caps.latest.revision: 39
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2832e65cb5cad2effa4c551a9842e37244d99c28
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="creating-a-data-processing-extension-library"></a>Création d'une bibliothèque d'extensions pour le traitement des données
  Chaque extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] que vous créez doit être affectée à un espace de noms unique et intégrée dans un fichier bibliothèque ou d'assembly. Le nom exact de l'espace de noms n'est pas important, mais il doit être unique et ne pas être partagé avec une autre extension. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] utilise l'espace de noms <xref:Microsoft.ReportingServices.DataProcessing> pour les extensions pour le traitement des données fournies avec [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Vous devez créer vos propres espaces de noms uniques pour les extensions pour le traitement des données de votre entreprise.  
  
 L'exemple suivant indique le code pour commencer une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] qui utilise les espaces de noms qui contiennent les interfaces de traitement des données et les classes d'utilitaires.  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 Lors de la compilation d'une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vous devez fournir au compilateur une référence à Microsoft.ReportingServices.Interfaces.dll, parce que les interfaces d'extension pour le traitement des données sont contenues dans ce fichier. L'espace de noms <xref:Microsoft.ReportingServices.DataProcessing> est nécessaire pour implémenter les interfaces d'extension pour le traitement des données, et l'espace de noms <xref:Microsoft.ReportingServices.Interfaces> est nécessaire pour implémenter l'interface <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Par exemple, si tous les fichiers qui contiennent le code pour implémenter une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] écrit en C# sont dans un répertoire unique avec l'extension .cs, la commande suivante est issue de ce répertoire pour compiler les fichiers stockés dans CompanyName.ExtensionName.dll.  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 L’exemple de code suivant montre la commande qui serait utilisée pour [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] fichiers portant l’extension. vb.  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  Vous pouvez aussi concevoir, développer et générer votre extension pour le traitement des données à l'aide de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Pour plus d'informations sur le développement des assemblys dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], consultez votre documentation [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
