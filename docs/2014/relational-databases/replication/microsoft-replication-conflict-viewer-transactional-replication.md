---
title: Outil de résolution des conflits de réplication de Microsoft (réplication transactionnelle) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvqueued.f1
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a098bdec4b7ad5e7f213d4cb34f93a7b624b9c7e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296529"
---
# <a name="microsoft-replication-conflict-viewer-transactional-replication"></a>Outil de résolution des conflits de réplication de Microsoft (réplication transactionnelle)
  L'Outil de résolution des conflits de réplication vous permet d'examiner les conflits qui se sont produits lors de la synchronisation pour la réplication transactionnelle d'égal à égal et la réplication transactionnelle avec des abonnements de mise à jour en attente. Pour plus d’informations, consultez [Afficher les conflits de données pour les publications transactionnelles &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).  
  
> [!NOTE]  
>  L'outil de résolution des conflits de réplication affiche les conflits qui se produisent dans une réplication de fusion et dans une réplication transactionnelle. Pour la réplication transactionnelle, vous pouvez utiliser l'outil de résolution des conflits de réplication pour examiner les données de conflit, mais vous ne pouvez pas choisir une résolution différente du conflit.  
  
## <a name="options"></a>Options  
 L'Outil de résolution des conflits comporte deux parties. La partie supérieure de la boîte de dialogue affiche la liste des conflits de la table sélectionnée. Lorsque vous cliquez sur un élément de cette liste, les informations sur le conflit s'affichent dans la partie inférieure de la boîte de dialogue.  
  
 Les données en conflit de la partie inférieure sont affichées dans les deux colonnes correspondantes (**Gagnant du conflit** et **Perdant du conflit**). Si le conflit existe entre des données mises à jour et des données supprimées, il est possible qu'aucune donnée ne soit affichée pour le côté supprimé du conflit. Dans ce cas, l'outil de résolution des conflits de réplication affiche un message dans l'une des colonnes qui indique que la ligne a été supprimée à un emplacement et mise à jour à un autre. Il indique également la résolution suggérée.  
  
 **Sauvegarde de la base de données**  
 Choisissez une base de données qui comporte des publications faisant l'objet de conflits.  
  
 **Publication**  
 Choisissez une publication qui comporte des tables faisant l'objet de conflits.  
  
 **Table**  
 Choisissez une table qui comporte des conflits.  
  
 **Définir le filtre**  
 Cliquez sur ce bouton pour ouvrir la boîte de dialogue **Définir les filtres** .  
  
 **Appliquer ou supprimer le filtre**  
 Applique ou supprime un filtre défini dans la boîte de dialogue **Définir les filtres** .  
  
 **Tout sélectionner**  
 Sélectionne tous les conflits de la grille.  
  
 **Aucune sélection**  
 Désélectionne tous les conflits de la grille.  
  
 **Supprimer**  
 Supprime les conflits sélectionnés et leurs métadonnées associées des tables système de réplication.  
  
 **Afficher toutes les colonnes**  
 Sélectionnez cette option pour afficher toutes les colonnes de la table.  
  
 **Afficher les cinq premières colonnes et les autres colonnes qui contiennent des données conflictuelles**  
 Sélectionnez cette option pour afficher les cinq premières colonnes et toute colonne qui comporte des conflits. Cette option est utile lorsque la table comporte de nombreuses colonnes si vous voulez afficher uniquement les colonnes les plus pertinentes pour la résolution du conflit. Les cinq premières colonnes figurent toujours dans cette vue du fait que les champs qui identifient une ligne (par exemple la clé primaire ou les noms des champs) se trouvent souvent parmi les premières colonnes de la table.  
  
 **Informations sur la colonne** (**…**)  
 Affiche les informations sur la colonne : **Nom de la table**, **Nom de la colonne**, **Type de données**et **Valeur de la colonne**.  
  
 **Consigner les détails de ce conflit**  
 Activez cette case pour enregistrer les détails du conflit dans un fichier. Pour spécifier l'emplacement du fichier, pointez sur le menu **Affichage** et cliquez sur **Options**. Entrez une valeur ou cliquez sur le bouton d'exploration (**...**) et allez au fichier voulu. Cliquez sur **OK** pour fermer la boîte de dialogue **Options** .  
  
## <a name="see-also"></a>Voir aussi  
 [Détection de conflit dans la réplication d’égal à égal](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Afficher les conflits de données pour les publications transactionnelles &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  
