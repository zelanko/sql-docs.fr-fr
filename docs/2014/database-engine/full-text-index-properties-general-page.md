---
title: Propriétés de l’index de recherche en texte intégral (page général) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 187366d9f289804942ba6e7d331a47bfaae68232
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000939"
---
# <a name="full-text-index-properties-general-page"></a>Propriétés d'index de recherche en texte intégral (page Général)
  **Pour afficher ou changer les propriétés modifiables d'un index de recherche en texte intégral**  
  
-   [Gérer les index de recherche en texte intégral](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Catalogue de texte intégral**  
 Affiche le nom du catalogue de texte intégral auquel l'index de recherche en texte intégral est associé.  
  
 **Sauvegarde de la base de données**  
 Affiche le nom de la base de données dans laquelle réside l'index de recherche en texte intégral.  
  
 **Tableau**  
 Affiche le nom de la table dans laquelle est défini l'index de recherche en texte intégral.  
  
 **Clé d'index de recherche en texte intégral**  
 Affiche le nom de la clé d'index de recherche en texte intégral, qui est un index unique dans une colonne unique de la table.  
  
 **État de remplissage de la table de texte intégral**  
 Affiche l'état de remplissage de la table indexée de texte intégral.  
  
 Les valeurs possibles sont les suivantes :  
  
 0 = Inactif.  
  
 1 = Remplissage complet en cours.  
  
 2 = Remplissage incrémentiel en cours.  
  
 3 = Propagation des changements suivis en cours.  
  
 4 = Index de mise à jour en arrière-plan en cours (suivi des modifications automatique, par exemple).  
  
 5 = Indexation de texte intégral accélérée ou suspendue.  
  
 **Index de recherche en texte intégral actif**  
 Indique si la table possède un index de recherche en texte intégral actif.  
  
 1 = True  
  
 0 = False  
  
 **Groupe de fichiers d'un index de recherche en texte intégral**  
 Le groupe de fichiers auquel l'index de recherche en texte intégral appartient.  
  
 **Liste de mots vides de l’index de recherche en texte intégral**  
 La liste de mots vides actuellement associée à l'index de recherche en texte intégral. Une liste de mots vides est une liste de [mots vides](../relational-databases/search/full-text-search.md). La liste de mots vides associée à un index de recherche en texte intégral, s'applique aux requêtes de texte intégral sur cet index. Vous pouvez supprimer la liste de mots vides de l’index en sélectionnant ** \< dés>** dans la liste, ou vous pouvez sélectionner une autre liste de mots vides ; ** \<>système** indique la STOPLIST du système.  
  
 **Pour créer une liste de mots vides**  
  
-   [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../relational-databases/search/full-text-search.md)  
  
 **Liste de propriétés de recherche**  
 Liste de propriétés de recherche actuellement associée à l'index de recherche en texte intégral, le cas échéant. Une liste de propriétés de recherche spécifie un ensemble de propriétés du document incluses dans l'index de recherche en texte intégral associé, s'il est rempli. Pour plus d’informations, consultez [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 ** \< Off>** indique qu’il n’existe actuellement aucune liste de propriétés de recherche associée à l’index. Vous pouvez supprimer la liste de propriétés de recherche actuelle de l’index en sélectionnant ** \< dés>** dans la liste, ou vous pouvez sélectionner une autre liste de propriétés de recherche dans la liste. Seules les listes des propriétés de recherche de la base de données actuelle sont répertoriées ici.  
  
> [!NOTE]  
>  Vous pouvez associer une liste de propriétés de recherche donnée à plusieurs index de recherche en texte intégral dans la même base de données.  
  
 **Pour créer une liste de propriétés de recherche**  
  
-   [Rechercher les propriétés du document à l’aide des listes des propriétés de recherche](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 **Nombre d'éléments de la table de texte intégral**  
 Indique le nombre de lignes qui ont été correctement indexées en texte intégral.  
  
 Cette propriété correspond à la propriété `TableFulltextItemCount` retournée par la fonction OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
 **Documents traités de la table de texte intégral**  
 Affiche le nombre de lignes qui ont été traitées depuis le démarrage de l'indexation de texte intégral. Dans une table en cours d'indexation pour une recherche en texte intégral, toutes les colonnes d'une ligne sont considérées comme faisant partie d'un même document à indexer. Les lignes supprimées ne sont pas comptées.  
  
|||  
|-|-|  
|0|Indique que l'indexation de texte intégral est terminée et qu'aucun remplissage n'est actif.|  
|> 0|Dans le cas d'un remplissage actif, indique le nombre de documents traités par des opérations d'insertion ou de mise à jour depuis une opération de remplissage, d'activation d'un suivi de modification avec remplissage de l'index de mise à jour en arrière-plan (par exemple, suivi des modifications automatique), de modification du schéma d'index de recherche en texte intégral, de reconstruction du catalogue de texte intégral, de redémarrage de l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], etc.|  
  
 **Modifications en attente de la table de texte intégral**  
 Nombre d'entrées de suivi des modifications en attente de traitement.  
  
 0 = Le suivi des modifications n'est pas activé.  
  
 NULL = La table n'a pas d'index de recherche en texte intégral.  
  
 **Nombre d'erreurs de la table de texte intégral**  
 Nombre de lignes que la recherche en texte intégral n'a pas indexées.  
  
 0 = Le remplissage est terminé.  
  
 \>0 = l’un des éléments suivants :  
  
-   Nombre de documents qui n'ont pas été indexés depuis le début d'un remplissage de suivi des modifications intégral, incrémentiel ou manuel.  
  
-   Dans le cas d'un suivi des modifications avec index de mise à jour en arrière-plan, nombre de lignes qui n'ont pas été indexées depuis le début du remplissage, ou depuis le redémarrage du remplissage. Ceci peut être provoqué par une modification du schéma, une reconstruction du catalogue, un redémarrage du serveur, etc.  
  
 **Indexation de texte intégral activée**  
 Spécifie si l'indexation de texte intégral est activée.  
  
|||  
|-|-|  
|**:**|activé|  
|**Fausses**|Désactivé|  
  
 **Suivi des modifications**  
 Spécifie si le suivi des modifications de texte intégral est activé dans la table, et le cas échant, son type. Le suivi des modifications de texte intégral conserve un enregistrement des lignes qui ont été modifiées dans une table ou dans une vue indexée configurée pour l'indexation de texte intégral. Ces modifications peuvent être propagées à l'index de recherche en texte intégral.  
  
 Les valeurs pour **Suivi des modifications** sont les suivantes :  
  
|||  
|-|-|  
|**Désactivé**|L'index de recherche en texte intégral n'est pas mis à jour avec les modifications des données sous-jacentes.|  
|**Manuel**|L'index de recherche en texte intégral n'est pas mis à jour automatiquement au fur et à mesure des modifications des données sous-jacentes. Toutefois, les modifications apportées aux données sous-jacentes sont conservées et vous pouvez les propager à l'index de recherche en texte intégral soit de manière planifiée à l'aide de l'Agent SQL Server, soit de façon manuelle.|  
|**Automatique**|L'index de recherche en texte intégral est mis à jour automatiquement au fur et à mesure des modifications des données sous-jacentes dans la table de base.|  
  
 **Remplir à nouveau l'index**  
 Cliquez pour démarrer le remplissage de l'index de recherche en texte intégral lors de la sortie de la boîte de dialogue. Sélectionnez l'un des types de remplissage suivants :  
  
|||  
|-|-|  
|**Complète**|Au cours d'un remplissage complet d'une table, les entrées d'index sont créées pour toutes les lignes.|  
|**Incrémentielle**|Le remplissage incrémentiel permet de mettre à jour l'index de recherche en texte intégral pour les lignes ajoutées, supprimées ou modifiées après le dernier remplissage ou pendant l'exécution de ce dernier. Pour effectuer un remplissage incrémentiel, il est nécessaire que la table de base contienne une colonne du type de données `timestamp`.|  
|**Mettre à jour**|L'index de recherche en texte intégral est mis à jour chaque fois que les données de la table de base sont modifiées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Commencer à utiliser la recherche en texte intégral](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
