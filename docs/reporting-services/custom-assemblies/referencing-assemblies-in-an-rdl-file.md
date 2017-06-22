---
title: "Référencement d’assemblys dans un fichier RDL | Documents Microsoft"
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 87609ab5b118eaa696f7152b25cf7e984e7f6e7f
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Référencement d'assemblys dans un Fichier RDL
  Pour prendre en charge l’utilisation d’assemblys de code personnalisé dans les fichiers de définition de rapport, les deux éléments de langage RDL (Report Definition) sont inclus dans la spécification RDL : le **CodeModules** élément et la **Classes** élément.  
  
 Le **CodeModules** élément vous permet de faire référence à des assemblys de code managé dans les expressions de rapport. **CodeModules** est un élément de niveau supérieur qui contient la référence à l’assembly que vous utilisez dans vos fichiers de définition de rapport pour appeler des fonctions spécialisées. Une entrée dans une définition de rapport qui prend en charge l'utilisation d'un assembly personnalisé peut ressembler aux éléments suivants :  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Au lieu d’appeler <xref:System.Reflection.Assembly.Load%2A> à partir de votre code personnalisé, enregistrez vos assemblys personnalisés en ajoutant manuellement **CodeModule** éléments à votre fichier RDL ou à l’aide de la **références** onglet de la **propriétés de rapport** boîte de dialogue. Pour plus d’informations, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Le **Classes** élément prend en charge l’utilisation de membres d’instance dans une définition de rapport. **Classes** est un élément de niveau supérieur qui contient une référence au nom de classe et un nom d’instance. Une entrée dans une définition de rapport qui prend en charge l'utilisation de membres d'instance peut ressembler aux éléments suivants :  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Pour plus d’informations, consultez [l’accès aux assemblys par le biais d’Expressions personnalisées](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’assemblys personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
