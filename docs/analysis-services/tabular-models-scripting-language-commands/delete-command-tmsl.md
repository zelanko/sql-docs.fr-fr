---
title: Supprimer la commande (TMSL) | Documents Microsoft
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
ms.assetid: 05d3fb14-ea03-4596-ac2e-9ae5bab27b4d
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6a4f8029d0d0cfb2ef9076347a791a04e03a540
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="delete-command-tmsl"></a>Supprimer la commande (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Supprime une base de données ou un objet dans la base de données actuelle.   
Il supprime l’objet spécifié et tous les objets enfants et les collections. Si l’objet n’existe pas, la commande génère une erreur.  
  
## <a name="request"></a>Demande  
 L’objet en cours de suppression est spécifié en utilisant le chemin d’accès de l’objet. Par exemple, la suppression d’une partition nécessite que vous spécifiez les objets de base de données et de table qui la précèdent.  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",   
      "partition": "may2011"   
    }   
  }   
}   
```  
  
 Vous pouvez supprimer les objets suivants :  
  
 [Objet de base de données &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016"  
    }   
  }   
}   
```  
  
 [Objet de sources de données &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureworksDW2016",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    }  
  }  
}  
```  
  
 [Objet tables &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",  
    }   
  }   
}   
```  
  
 [Objet de partitions &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",   
      "partition": "may2011"   
    }   
  }   
}   
```  
  
 [Objet rôles &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "role": "Data Reader"  
    }   
  }   
}   
```  
  
## <a name="response"></a>Réponse  
 Retourne un résultat vide lorsque la commande aboutit. Sinon, une exception XMLA est retournée.  
  
## <a name="examples"></a>Exemples  
 **Exemple 1** -supprimer une base de données.  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureWorksDW2016"  
    }  
  }  
}  
```  
  
 **Exemple 2** -supprimer une connexion.  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureWorksDW2016",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    }  
  }  
}  
```  
  
## <a name="usage-endpoints"></a>Utilisation (points de terminaison)  
 Cet élément de commande est utilisé dans une instruction de la [méthode Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) appel via un point de terminaison XMLA exposée comme suit :  
  
-   Comme une fenêtre XMLA dans SQL Server Management Studio (SSMS)  
  
-   En tant que fichier d’entrée dans le **invoke-ascmd** applet de commande PowerShell  
  
-   En tant qu’entrée pour un travail de l’Agent SQL Server ou de tâche SSIS  
  
 Vous pouvez générer un script prêts à l’emploi pour cette commande à partir de SSMS.  Par exemple, vous pouvez cliquer sur une base de données > **Script** > **base de données de Script en tant que** > **DELETE To**.  
  
 Le [ \[MS-SSAS-T\]: QL Server tabulaires Analysis Services (SQL Server technique Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) document inclut section 3.1.5.2.2 qui décrit la structure des objets et les commandes de métadonnées sous forme de tableau JSON. Actuellement, ce document traite des commandes et fonctions non encore implémentées dans un script TMSL. Reportez-vous à la rubrique [langage de script de modèle tabulaire &#40; TMSL &#41; Référence](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) pour des explications sur ce qui est pris en charge.  

## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

