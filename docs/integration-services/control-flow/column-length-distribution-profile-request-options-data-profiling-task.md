---
title: "Options de demande de profil colonne longueur Distribution (tâche de profilage des données) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5799a96f092b7277bdeb5e7e49ca998d17f12020
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a>Options Demande de profil de distribution de longueurs de colonne (tâche de profilage des données)
  Utilisez le volet **Propriétés de demandes** de la page **Demandes de profil** pour définir les options de la **Demande de profil de distribution de longueurs de colonne** sélectionnée dans le volet Demandes. Un profil de distribution de longueurs de colonne signale toutes les longueurs distinctes des valeurs de chaîne dans la colonne sélectionnée, et le pourcentage de lignes dans la table que chaque longueur représente. Ce profil peut vous aider à identifier les problèmes dans vos données, tels que les valeurs non valides. Par exemple, vous profilez une colonne de codes d'états des États-Unis à deux caractères et découvrez des valeurs excédant deux caractères.  
  
> [!NOTE]  
>  Les options décrites dans cette rubrique apparaissent sur la page **Demandes de profil** de l' **Éditeur de tâche de profilage de données**. Pour plus d’informations sur cette page de l’éditeur, consultez [Éditeur de tâche de profilage de données &#40;page Demandes de profil&#41;](../../integration-services/control-flow/data-profiling-task-editor-profile-requests-page.md).  
  
 Pour plus d’informations sur l’utilisation de la tâche de profilage des données, consultez [Configuration de la tâche de profilage des données](../../integration-services/control-flow/setup-of-the-data-profiling-task.md). Pour plus d’informations sur l’utilisation de la visionneuse du profil des données pour analyser le résultat de la tâche de profilage des données, consultez [Visionneuse du profil des données](../../integration-services/control-flow/data-profile-viewer.md).  
  
## <a name="request-properties-options"></a>Options Propriétés de la demande  
 Pour une **Demande de profil de distribution de longueurs de colonne**, le volet **Propriétés de la demande** affiche les groupes d’options suivants :  
  
-   **Données**, qui incluent les options **TableOrView** et **Column**  
  
-   **Général**  
  
-   **Options**  
  
### <a name="data-options"></a>Options de données  
 **ConnectionManager**  
 Sélectionnez le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] existant qui utilise le fournisseur de données .NET pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) pour se connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contient la table ou la vue à profiler.  
  
 **TableOrView**  
 Sélectionnez la table ou la vue existante qui contient la colonne à profiler.  
  
 Pour plus d'informations, consultez la section « Options TableorView » dans cette rubrique.  
  
 **Column**  
 Sélectionnez la colonne existante à profiler. Sélectionnez **(\*)** pour profiler toutes les colonnes.  
  
 Pour plus d'informations, consultez la section « Options de colonne » dans cette rubrique.  
  
#### <a name="tableorview-options"></a>Options TableOrView  
 **Schéma**  
 Spécifiez le schéma auquel la table sélectionnée appartient. Cette option est en lecture seule.  
  
 **Table**  
 Affiche le nom de la table sélectionnée. Cette option est en lecture seule.  
  
#### <a name="column-options"></a>Options de colonne  
 **IsWildCard**  
 Indique si le caractère générique **(\*)** a été sélectionné. Cette option a la valeur **True** si vous avez sélectionné **(\*)** pour générer le profil de toutes les colonnes. Sa valeur est **False** si vous avez sélectionné une colonne spécifique dont le profil doit être généré. Cette option est en lecture seule.  
  
 **ColumnName**  
 Affiche le nom de la colonne sélectionnée. Cette option est vide si vous avez sélectionné **(\*)** pour générer le profil de toutes les colonnes. Cette option est en lecture seule.  
  
 **StringCompareOptions**  
 Cette option ne s'applique pas au profil de distribution de longueurs de colonne.  
  
### <a name="general-options"></a>Options générales  
 **RequestID**  
 Tapez un nom descriptif pour identifier cette demande de profil. En règle générale, il n'est pas nécessaire de modifier la valeur générée automatiquement.  
  
### <a name="options"></a>Options  
 **IgnoreLeadingSpaces**  
 Indiquez si les espaces de début doivent être ignorés lorsque le profil compare des valeurs de chaîne. La valeur par défaut de cette option est **False**.  
  
 **IgnoreTrailingSpaces**  
 Indiquez si les espaces de fin doivent être ignorés lorsque le profil compare des valeurs de chaîne. La valeur par défaut de cette option est **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de tâche &#40; de profilage des données Page Général &#41;](../../integration-services/control-flow/data-profiling-task-editor-general-page.md)   
 [Formulaire de profil rapide de Table simple &#40; &#41; de la tâche de profilage des données](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)  
  
  

