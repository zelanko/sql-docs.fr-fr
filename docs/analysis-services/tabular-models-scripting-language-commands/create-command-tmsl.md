---
title: "Créer une commande (TMSL) | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e3024f89-ebfa-47e4-9893-708f379fd9b8
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae07d8b17fc659bb8a8bc2bef1cdcb6421606c29
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="create-command-tmsl"></a>Créer une commande (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Crée l’objet spécifié et tous les objets descendants qui sont spécifiés. Si l’objet existe déjà, la commande génère une erreur.  
  
## <a name="request"></a>Demande  
 La structure de la requête varie en fonction de l’objet. Un objet qui est le parent doit inclure tous ses enfants, même si les définitions d’objet complet des frères ou des parents ne sont pas requises.  
  
 [Objet de base de données &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md) Ajouter une base de données à un serveur.  
  
```  
{   
  "create": {   
    "database": {   
      "name": "AdventureworksDW2016",   
      "description": "<description>",   
      "tables": [   
        { },   
        { },   
        { }   
      ],   
      "relationships": [   
        { },   
        { }   
      ]   
    }   
  }   
}  
```  
  
 [Objet de sources de données &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)  
  
```  
{  
  "create": {  
    "parentObject": {  
      "database": "AdventureworksDW2016"  
    },  
    "dataSource": {  
      "name": "SqlServer localhost AdventureworksDW2016",  
      "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
      "impersonationMode": "impersonateAccount",  
      "account": "<account name>",  
      "annotations": [  
        {  
          "name": "ConnectionEditUISource",  
          "value": "SqlServer"  
        }  
      ]  
    }  
  }  
}  
```  
  
 [Objet tables &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) Ajouter des colonnes à une table.  
  
```  
{   
  "create": {   
    "parentObject": {   
      "database": "AdventureworksDW2016",   
      "table": "DimSales"  
    },   
    "columns": {   
      "type": ["calculated"  | "data" ]  
      "name": "\<column-name>",   
       "expression":  "<DAX expression>"  
    }   
  }   
}   
```  
  
 [Objet de partitions &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md) Ajouter une partition à un objet de table parent.  
  
```  
{  
  "create": {  
    "parentObject": {  
      "database": "AdventureWorksTabular1200",  
      "table": "Date"  
    },  
    "partition": {  
      "name": "Date 2",  
      "source": {  
        "query": "SELECT [dbo].[DimDate].* FROM [dbo].[DimDate]",  
        "dataSource": "SqlServer localhost AdventureworksDW2016"  
      }  
    }  
  }  
}  
```  
  
 [Objet rôles &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) Ajouter au minimum un rôle à une base de données, mais sans l’appartenance ou des filtres.  
  
```  
{  
  "create": {  
    "parentObject": {  
      "database": "AdventureWorksDW2016"  
    },  
    "role": {  
      "name": "DataReader",  
      "modelPermission": "read"  
    }  
  }  
}  
```  
  
 À l’exception de la **base de données** de l’objet, l’objet créé est l’enfant d’un **parentObject**. Le parent de la **base de données** objet est toujours le **Server** objet.  
  
 Server est considéré à partir du contexte. Par exemple, si vous exécutez le script à partir de Management Studio ou PowerShell AMO, la connexion au serveur est spécifiée dans la session ou en tant que paramètre.  
  
## <a name="response"></a>Réponse  
 Retourne un résultat vide lorsque la commande aboutit. Sinon, une exception XMLA est retournée.  
  
## <a name="examples"></a>Exemples  
 **Exemple 1** -ajouter un rôle qui spécifie l’appartenance et un filtre.  
  
```  
{   
   "create":{   
      "parentObject":{   
         "database":"AdventureWorksTabular1200"  
      },  
      "role":{  
         "name":"DataReader",  
         "modelPermission":"read",  
         "members":[   
            {  
               "memberName": "account-01",  
               "memberId":"S-1-5-21-1111111111-2222222222-33333333-444444"  
            },  
            {   
               "memberName": "account-02",  
               "memberId":"S-2-5-21-1111111111-2222222222-33333333-444444"  
            }  
         ],  
         "tablePermissions":[   
            {   
               "name":"Date",  
               "filterExpression":"CalendarYear('2011')"  
            }  
         ]  
      }  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>Utilisation (points de terminaison)  
 Cet élément de commande est utilisé dans une instruction de la [méthode Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) appel via un point de terminaison XMLA exposée comme suit :  
  
-   Comme une fenêtre XMLA dans SQL Server Management Studio (SSMS)  
  
-   En tant que fichier d’entrée dans le **invoke-ascmd** applet de commande PowerShell  
  
-   En tant qu’entrée pour un travail de l’Agent SQL Server ou de tâche SSIS  
  
 Vous pouvez générer un script prêts à l’emploi pour cette commande à partir de SSMS.  Par exemple, vous pouvez cliquer sur une base de données > **Script** > **base de données de Script en tant que** > **CREATE To**.  
  
 Le [ \[MS-SSAS-T\]: QL Server tabulaires Analysis Services (SQL Server technique Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) document inclut section 3.1.5.2.2 qui décrit la structure des objets et les commandes de métadonnées sous forme de tableau JSON. Actuellement, ce document traite des commandes et fonctions non encore implémentées dans un script TMSL. Reportez-vous à la rubrique ([langage de script de modèle tabulaire &#40; TMSL &#41; Référence](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) pour obtenir des éclaircissements sur ce qui est pris en charge.  

## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
