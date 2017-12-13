---
title: "Développement avec Analysis Services (ASSL) un langage de script | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 45b116586a0ce328815d8139b751547045fa85f8
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Développement avec le langage de script Analysis Services (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Analysis Services Scripting Language (ASSL) est une extension de XMLA qui ajoute un langage de définition d’objet et le langage de commande pour créer et gérer des structures Analysis Services directement sur le serveur. Vous pouvez utiliser ASSL dans l'application personnalisée pour communiquer avec Analysis Services sur le protocole XMLA. ASSL comprend deux parties :  
  
-   Un langage de définition de données (DDL), ou un langage de définition d’objet, définit et décrit une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ainsi que les bases de données et les objets de base de données que contient l’instance.  
  
-   Un langage de commande qui envoie des commandes d’action, tels que **créer**, **Alter**, ou **processus**, à une instance d’Analysis Services. Ce langage de commande est décrite dans le [XML for Analysis &#40; XMLA &#41; Référence](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md).  
  
 Pour afficher l'ASSL qui décrit une solution multidimensionnelle dans [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], vous pouvez utiliser la commande Afficher le code au niveau du projet. Vous pouvez également créer ou modifier le script ASSL dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] à l'aide de l'éditeur de requête XMLA. Les scripts que vous créez peuvent être utilisés pour gérer des objets ou pour exécuter des commandes sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets ASSL et caractéristiques des objets](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)   
 [Conventions ASSL XML](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-xml-conventions.md)   
 [Sources de données et liaisons &#40; SSAS multidimensionnel &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
