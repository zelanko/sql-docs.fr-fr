---
title: Type de données ReportAction (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ReportAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportAction
helpviewer_keywords:
- ReportAction data type
ms.assetid: b22f0d52-ed3a-4239-840e-0eaf172d7276
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7c2c5140f3d2723f0456b007bc9228c5f87bbaa6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043936"
---
# <a name="reportaction-data-type-assl"></a>Type de données ReportAction (ASSL)
  Définit un type de données dérivé qui représente une action qui génère un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rapport.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReportAction>  
   <!-- The following elements extend Action -->  
   <ReportServer>...</ReportServer>  
   <Path>...</Path>  
   <ReportParameters>...</ReportParameters>  
   <ReportFormatParameters>...</ReportFormatParameters>  
</ReportAction>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Action](action-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Chemin d’accès](../properties/path-element-assl.md), [ReportFormatParameters](../collections/reportformatparameters-element-assl.md), [ReportParameters](../collections/reportparameters-element-assl.md), [ReportServer](../objects/server-element-assl.md)|  
|Éléments dérivés|[Action](../objects/action-element-assl.md) ([Actions](../collections/actions-element-assl.md) collection de [Cube](../objects/cube-element-assl.md) ou [Perspective](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le serveur de rapports répond aux demandes de rapports basées sur une URL. L'action de rapport est définie avec un type *Report*. Les ressources et les paramètres sont transmis au serveur lors de la création de l'action. Le serveur expose l'action en tant qu'action de type ensemble de lignes.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  