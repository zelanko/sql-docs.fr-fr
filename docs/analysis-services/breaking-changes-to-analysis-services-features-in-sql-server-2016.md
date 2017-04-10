---
title: "Modifications avec rupture dans les fonctionnalit&#233;s Analysis Services de SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifications avec rupture [Analysis Services]"
  - "mise à niveau d'Analysis Services"
ms.assetid: aeb02542-5a6c-458c-a110-13413dd3e9d9
caps.latest.revision: 55
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 53
---
# Modifications avec rupture dans les fonctionnalit&#233;s Analysis Services de SQL Server 2016
  Une *modification avec rupture* bloque le fonctionnement d’un modèle de données, d’un code d’application ou d’un script après la mise à niveau du modèle ou du serveur.  
  
> [!NOTE]  
>  En revanche, une *modification de comportement* correspond à une modification du code qui n’empêche pas un modèle ou une application de fonctionner, mais introduit un comportement différent de celui de la version précédente.  La modification d’une valeur par défaut ou l’interdiction (auparavant autorisée) de la configuration de propriétés ou d’options sont des exemples de modification de comportement. Pour en savoir plus sur les changements de comportement dans cette version, consultez [Behavior Changes to Analysis Services Features in SQL Server 2016](../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
## Mise à niveau du .NET 4.0  
 Les bibliothèques clientes AMO (Analysis Services Management Objects), ADOMD.NET et TOM (Tabular Object Model) dans [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] ciblent maintenant le runtime .NET 4.0. Il peut s’agir d’une modification majeure pour les applications qui ciblent le .NET 3.5. Les applications utilisant des versions plus récentes de ces assemblys doivent maintenant cibler .NET 4.0 ou ultérieur.  
  
## Mise à niveau de la version AMO  
 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] est une mise à niveau de la version pour [Analysis Services Management Objects &#40;AMO&#41;](../Topic/Analysis%20Services%20Management%20Objects%20\(AMO\).md) et est une modification majeure dans certaines circonstances.  Le code et les scripts qui appellent AMO continueront de s’exécuter comme avant, si vous mettez à niveau une version précédente. En revanche, si vous devez *recompiler* votre application et que vous ciblez une instance de [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] , vous devez ajouter l’espace de noms suivant pour rendre votre code ou votre script opérationnel :  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 L’espace de noms [Microsoft.AnalysisServices.Core](../Topic/Microsoft.AnalysisServices.Core.md) est maintenant nécessaire chaque fois que vous faites référence à l’assembly Microsoft.AnalysisServices dans votre code. Les objets qui auparavant ne figuraient que dans l’espace de noms **Microsoft.AnalysisServices** sont déplacés dans l’espace de noms principal dans cette version, si l’objet est utilisé de la même façon dans des scénarios multidimensionnels et tabulaires.  Par exemple, les API liées au serveur sont déplacées dans l’espace de noms principal.  
  
 Bien qu’il y ait plusieurs espaces de noms, deux coexistent dans le même assembly (Microsoft.AnalysisServices.dll).  
  
## Modifications de DISCOVER XEvent  
 Pour mieux prendre en charge le streaming DISCOVER XEvent dans SSMS pour [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], `DISCOVER_XEVENT_TRACE_DEFINITION` est remplacé par les traces XEvent suivantes :  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  
  
## Voir aussi  
 [Compatibilité descendante Analysis Services](../analysis-services/analysis-services-backward-compatibility.md)  
  
  