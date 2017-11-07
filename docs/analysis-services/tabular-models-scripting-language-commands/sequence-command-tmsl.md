---
title: "Séquence de commande (TMSL) | Documents Microsoft"
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
ms.assetid: 898d6ec2-9b40-441b-be2b-5728d1d2882e
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e7fc7f1541131ac6a8e7249940a31104e50f0b09
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sequence-command-tmsl"></a>Commande Sequence (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Utilisez le **séquence** commande à exécuter un ensemble consécutif d’opérations en mode batch sur une instance d’Analysis Services.  La commande entière et tous ses composants doivent être exécutée dans l’ordre de la transaction réussisse.  
  
 Les commandes suivantes peuvent être exécutées séquentiellement, à l’exception de la **Actualiser** commande qui s’exécute en parallèle de traiter plusieurs objets simultanément.  
  
-   [Créer une commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)  
  
-   [La commande CreateOrReplace &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)  
  
-   [Modifier la commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)  
  
-   [Supprimer la commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)  
  
-   [Actualiser les commandes &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)  
  
-   [Commande de sauvegarde &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)  
  
-   [Restaurer des commandes &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)  
  
-   [Attacher une commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)  
  
-   [Détacher la commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)  
  
## <a name="request"></a>Demande  
 **maxParallelism** est une propriété facultative qui détermine si **Actualiser** opérations s’exécutent dans l’ordre ou en parallèle.  
  
 Le comportement par défaut est à utiliser le parallélisme d’autant que possible. En incorporant **Actualiser** dans **séquence**, vous pouvez contrôler le nombre exact de threads utilisés au cours du traitement, y compris la limitation de l’opération pour qu’un seul thread.  
  
> [!NOTE]  
>  L’entier assigné à **maxParallelism** détermine le nombre maximal de threads utilisés au cours du traitement. Les valeurs valides sont un entier positif. Si la valeur 1 est égal à non parallèle (utilise un thread).  
  
 Uniquement **Actualiser** s’exécute en parallèle. Si vous modifiez **maxParallelism** pour utiliser un nombre fixe de threads, veillez à consulter les propriétés sur le [actualiser commande &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md) pour comprendre l’impact potentiel. Il est possible de définir les propriétés d’une manière qui amoindrissent parallélisme même lorsque vous avez effectué plusieurs threads disponibles. La séquence de types de l’actualisation suivante vous donne le meilleur degré de parallélisme :  
  
-   Spécifier tout d’abord, l’actualisation de tous les objets à l’aide de ClearValues  
  
-   Ensuite, spécifiez l’actualisation de tous les objets à l’aide de DataOnly  
  
-   Spécifier le dernière actualisation de tous les objets à l’aide complète, Calculate, automatique ou ajouter  
  
 Toute variation sur ce rompt le parallélisme.  
  
```  
{   
  "sequence":    
    {   
      "maxParallelism": 3,   
      "operations": [   
        {   
          "mergepartitions": {   
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
        },   
        {   
          "refresh": {   
            "type": "calculate",   
            "object": {   
             "database": "salesdatabase"   
            }   
          }   
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
  
 Impossible de générer un script prêts à l’emploi pour cette commande à partir de SSMS. Au lieu de cela, vous pouvez commencer par un exemple ou écrire votre propre.  
  
 Le [ \[MS-SSAS-T\]: tabulaire SQL Server Analysis Services (SQL Server technique Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) document inclut section 3.1.5.2.2 qui décrit la structure des objets et les commandes de métadonnées sous forme de tableau JSON. Actuellement, ce document traite des commandes et fonctions non encore implémentées dans un script TMSL. Reportez-vous à la rubrique ([langage de script de modèle tabulaire &#40; TMSL &#41; Référence](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) pour obtenir des éclaircissements sur ce qui est pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

