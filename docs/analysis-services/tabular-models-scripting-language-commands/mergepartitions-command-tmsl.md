---
title: Commande de MergePartitions (TMSL) | Documents Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dd568426-a415-41bf-b1e9-ea2261babf81
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 290e5e99219a37a1ff1f6793d640756ba21f7467
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mergepartitions-command-tmsl"></a>Commande de MergePartitions (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Fusionne les données d’une ou plusieurs partitions sources dans une partition cible et supprime la partition source. La requête SQL de la partition cible ne sera pas mis à jour dans le cadre de la fusion. Pour vous assurer que le traitement ultérieur de la partition récupère toutes les données, vous devez vérifier la requête de sorte qu’il sélectionne toutes les données dans la partition fusionnée.  
  
## <a name="request"></a>Demande  
 Vous devez spécifier la base de données, de table et les partitions source et cible. Vous ne pouvez fusionner des partitions à partir de la même table.  
  
```  
{   
  "mergePartitions": {   
    "object": {   
      "database": "salesdatabase",   
      "table": "sales",   
      "partition": "may2015"   
    },   
    "sources": [   
      {   
        "database": "salesdatabase",   
        "table": "Sales",   
        "partition": "partition1"   
      },   
      {   
        "database": "salesdatabase",   
        "table": "Sales",   
        "partition": "partition2"   
      }   
    ]   
  }   
}  
  
```  
  
## <a name="response"></a>Réponse  
 Retourne un résultat vide lorsque la commande aboutit. Sinon, une exception XMLA est retournée.  
  
## <a name="usage-endpoints"></a>Utilisation (points de terminaison)  
 Cet élément de commande est utilisé dans une instruction de la [méthode Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) appel via un point de terminaison XMLA exposée comme suit :  
  
-   Comme une fenêtre XMLA dans SQL Server Management Studio (SSMS)  
  
-   En tant que fichier d’entrée dans le **invoke-ascmd** applet de commande PowerShell  
  
-   En tant qu’entrée pour un travail de l’Agent SQL Server ou de tâche SSIS  
  
 Vous pouvez générer un script prêts à l’emploi pour cette commande à partir de SSMS.  Par exemple, vous pouvez cliquer sur le **Script** dans la boîte de dialogue Gestion des partitions.  
  
 Le [ \[MS-SSAS-T\]: QL Server tabulaires Analysis Services (SQL Server technique Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) document inclut section 3.1.5.2.2 qui décrit la structure des objets et les commandes de métadonnées sous forme de tableau JSON. Actuellement, ce document traite des commandes et fonctions non encore implémentées dans un script TMSL. Reportez-vous à la rubrique [langage de script de modèle tabulaire &#40; TMSL &#41; Référence](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) pour des explications sur ce qui est pris en charge  

## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference [Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;]](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  

