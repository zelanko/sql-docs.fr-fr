---
title: "Initialiser des objets de l’Assembly personnalisé | Documents Microsoft"
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
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ab05efc7baba58a34180faa038cb58c7f57f4af2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="initializing-custom-assembly-objects"></a>Initialisation d'objets Assembly personnalisés
  Dans certains cas, vous pouvez être amené à initialiser des valeurs de propriété et de champ dans vos classes d'assembly personnalisées lorsque vous les instanciez. Vous aurez vraisemblablement besoin d'initialiser vos classes personnalisées avec des valeurs disponibles à partir des collections d'objets globales du rapport. Pour cela, substituez le **OnInit** méthode de la **Code** l’objet d’un rapport. Pour accéder à **OnInit**, utilisez le **Code** élément de la définition de rapport. Il existe deux techniques pour l’initialisation de valeurs de propriété ou le champ des classes dans un assembly personnalisé que vous prévoyez d’utiliser dans votre rapport : vous pouvez déclarer et créer une nouvelle instance de votre classe à l’aide de **OnInit**, ou vous pouvez appeler une méthode publiquement disponible à l’aide de **OnInit**.  
  
## <a name="global-object-collections-and-initialization"></a>Collections d'objets globales et initialisation  
 Plusieurs collections sont disponibles pour initialiser vos variables de classe personnalisées. Vous pouvez utiliser la **Globals** et **utilisateur** collections. Le **paramètres**, **champs** et **ReportItems** collections ne sont pas disponibles au point dans le cycle de vie du rapport lors de la **OnInit** méthode est appelée. Pour utiliser les collections partagées, **Globals** ou **utilisateur**, vous devez inclure le **rapport** référence d’objet. Par exemple, pour initialiser votre classe personnalisée selon la langue actuelle de l’utilisateur d’accéder aux rapports, votre **Code** élément peut se présenter comme suit :  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 L'une des méthodes permettant d'initialiser les valeurs de propriété et de champ d'une classe comme montré précédemment consiste à déclarer votre classe et à créer une nouvelle instance de celle-ci en appelant un constructeur substitué.  
  
 Une autre pour initialiser les valeurs de propriété et champ des classes dans vos assemblys personnalisés consiste à appeler une méthode publiquement disponible que vous définissez à partir de la **OnInit** (méthode). Vous devez d'abord ajouter un nom d'instance pour votre classe dans le fichier de définition de rapport. Une fois que vous avez ajouté la référence d'assembly et le nom d'instance appropriés, vous pouvez appeler votre méthode d'initialisation pour initialiser les valeurs de propriété et de champ pour votre classe. Votre **OnInit** méthode peut se présenter comme suit :  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Pour plus d’informations sur l’ajout d’un nom de référence et l’instance de l’assembly pour votre classe personnalisée, consultez [ajouter une référence d’Assembly à un rapport &#40; SSRS &#41; ](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md).  
  
 Pour plus d’informations sur les collections d’objets globales, consultez [Collections intégrées dans les Expressions &#40; Le Générateur de rapports et SSRS &#41; ](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblages personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
