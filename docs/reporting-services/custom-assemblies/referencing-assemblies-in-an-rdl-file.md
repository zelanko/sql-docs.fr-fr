---
title: "Référencement d’assemblys dans un fichier RDL | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
caps.latest.revision: "36"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: fb34fd3f73b8b7451d52c9794697e4a6c3f8b82e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Référencement d'assemblys dans un Fichier RDL
  Pour prendre en charge l’utilisation d’assemblys de code personnalisés dans les fichiers de définition de rapport, deux éléments RDL (Report Definition Language) sont inclus dans la spécification RDL : l’élément **CodeModules** et l’élément **Classes**.  
  
 L’élément **CodeModules** vous permet de faire référence aux assemblys de code managé dans les expressions de rapport. **CodeModules** est un élément de niveau supérieur qui contient la référence à l’assembly que vous utilisez dans vos fichiers de définition de rapport pour appeler des fonctions spécialisées. Une entrée dans une définition de rapport qui prend en charge l'utilisation d'un assembly personnalisé peut ressembler aux éléments suivants :  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Au lieu d’appeler <xref:System.Reflection.Assembly.Load%2A> de votre code personnalisé, enregistrez vos assemblys personnalisés en ajoutant manuellement des éléments **CodeModule** à votre fichier RDL ou en utilisant l’onglet **Références** de la boîte de dialogue **Propriétés de rapport**. Pour plus d’informations, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 L’élément **Classes** prend en charge l’utilisation de membres d’instance dans une définition de rapport. L’élément **Classes** est un élément de niveau supérieur qui contient une référence au nom de classe et un nom d’instance. Une entrée dans une définition de rapport qui prend en charge l'utilisation de membres d'instance peut ressembler aux éléments suivants :  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Pour plus d’informations, consultez [Accès aux assemblys personnalisés par le biais d’expressions](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblages personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
