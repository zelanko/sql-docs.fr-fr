---
title: Éditeur de tâche d’insertion en bloc (page Options) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1751d1e0ac01d5459a8c76e6a48626c2ad6deafd
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439176"
---
# <a name="bulk-insert-task-editor-options-page"></a>Éditeur de tâche d'insertion en bloc (page Options)
  Utilisez la page **Options** de la boîte de dialogue **Éditeur de tâche d'insertion en bloc** afin de définir les propriétés de l'opération d'insertion en bloc. La tâche d’insertion en bloc copie de grandes quantités de données dans une [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table ou une vue.  
  
 Pour en savoir plus sur l’utilisation des insertions en bloc, consultez [Tâche d’insertion en bloc](control-flow/bulk-insert-task.md) et [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
## <a name="options"></a>Options  
 **Courante**  
 Permet d'indiquer la page de codes des données dans le fichier de données.  
  
 **DataFileType**  
 Permet d'indiquer la valeur correspondant au type de données à utiliser lors d'une opération de chargement.  
  
 **BatchSize**  
 Permet d'indiquer le nombre de lignes contenues dans un traitement. La valeur par défaut correspond à la totalité du fichier de données. Si vous attribuez à **BatchSize** la valeur zéro, les données sont chargées dans un traitement unique.  
  
 **LastRow**  
 Permet de spécifier la dernière ligne à copier.  
  
 **FirstRow**  
 Permet de spécifier la première ligne à partir de laquelle la copie doit commencer.  
  
 **Options**  
 |Terme|Définition|  
|----------|----------------|  
|**Contraintes de validation**|Permet de vérifier les contraintes s'appliquant à la table et aux colonnes.|  
|**Conserver les valeurs NULL**|Permet de conserver les valeurs Null pendant l'opération d'insertion en bloc au lieu d'insérer des valeurs par défaut dans les colonnes vides.|  
|**Activer l’insertion d’identité**|Permet d'insérer des valeurs existantes dans une colonne d'identité.|  
|**Verrou de table**|Permet de verrouiller la table lors de l'opération d'insertion en bloc.|  
|**Exécuter les déclencheurs**|Lance tout déclencheur d'insertion, de mise à jour ou de suppression sur la table.|  
  
 **SortedData**  
 Implique l'ajout de la clause ORDER BY dans l'instruction d'insertion en bloc. Le nom de colonne que vous fournissez doit être celui d'une colonne valide pour la table de destination. Par défaut, il s’agit de `false`. En d'autres termes, les données ne sont pas triées par une clause ORDER BY.  
  
 **MaxErrors**  
 Permet de spécifier le nombre maximal d'erreurs tolérées avant l'annulation de l'opération d'insertion en bloc. La valeur 0 indique qu'un nombre illimité d'erreurs est autorisé.  
  
> [!NOTE]  
>  Chaque ligne ne pouvant pas être importée par l'opération de chargement en masse est comptée comme une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche d’insertion en bloc &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche d’insertion en bloc &#40;page connexion&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md)   
 [Page expressions](expressions/expressions-page.md)   
 [Workflow de contrôle](control-flow/control-flow.md)  
  
  
