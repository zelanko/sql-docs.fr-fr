---
title: Créer d’interrogation de la boîte de dialogue requête (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.createpollingquerydialog.f1
ms.assetid: 0f2902b5-796a-4eb0-be03-01514dc01b9a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: faf96ad02005c0385ec56e1f8763da2e82f093ec
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66086830"
---
# <a name="create-polling-query-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Créer la requête d'interrogation (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Créer la requête d’interrogation** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer une requête d’interrogation sous l’onglet **Notifications** de la boîte de dialogue **Options de stockage**. En règle générale, une requête d'interrogation est une requête singleton qui retourne une valeur que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peut utiliser pour déterminer si les modifications ont été apportées à une table ou à un autre objet relationnel. Vous pouvez afficher la boîte de dialogue **Créer la requête d’interrogation** en cliquant sur le bouton de sélection (**...**) dans la colonne **Requête d’interrogation** de la grille de l’option **Interrogation planifiée** sous l’onglet **Notifications** de la boîte de dialogue **Options de stockage**. Pour plus d’informations sur l’onglet **Notifications**la boîte de dialogue **Options de stockage**, consultez [Notifications &#40;boîte de dialogue Options de stockage&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).  
  
 Le type de valeur qui doit être retourné par la requête d'interrogation dépend du type de mises à jour planifiées pour le cache MOLAP de l'objet selon la table interrogée :  
  
-   Si l’option **Activer les mises à jour incrémentielles** n’est pas sélectionnée sous l’onglet **Notifications**de la boîte de dialogue**Options de stockage[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)],**  procède à une mise à jour complète du cache MOLAP pour l’objet si une modification est identifiée lors de l’interrogation planifiée. La requête d'interrogation utilisée devrait déterminer si des enregistrements ont été ajoutés à la table depuis la dernière période d'interrogation.  
  
-   Si l’option **Activer les mises à jour incrémentielles** est sélectionnée sous l’onglet **Notifications** de la boîte de dialogue **Options de stockage** , [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] procède à une mise à jour incrémentielle du cache MOLAP pour l’objet si une modification est identifiée lors de l’interrogation planifiée. La requête d'interrogation utilisée devrait déterminer le dernier enregistrement dans la table.  
  
 Vous pouvez, par exemple, utiliser les requêtes d'interrogation suivantes pour fournir des mises à jour complètes ou incrémentielles pour la dimension Client dans l'exemple [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] de base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] :  
  
|Type de mise à jour|Requête d’interrogation|  
|-----------------|-------------------|  
|Mise à jour complète|`SELECT`<br /><br /> `COUNT(*) AS TotalCount`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
|Mise à jour incrémentielle|`SELECT`<br /><br /> `MAX([CustomerKey]) AS LastCustomerKey`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
  
 Pour plus d’informations sur les mises à jour complètes et incrémentielles pour des notifications d’interrogation planifiées, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
 La requête entrée doit être une commande de requête acceptée par le fournisseur sous-jacent. La requête est préparée pour validation au moyen du fournisseur sous-jacent et pour identifier les colonnes retournées. La boîte de dialogue peut présenter deux vues :  
  
-   Générateur de requête VDT (Outils Visual Database)  
  
     Pour tous les utilisateurs, la vue Générateur de requête VDT utilise un ensemble d'outils d'interface destinés à créer et à tester visuellement une requête SQL.  
  
-   Générateur de requêtes générique  
  
     Pour les utilisateurs avancés, la vue Générateur de requêtes générique fournit une interface utilisateur plus simple et plus directe pour créer et tester une requête SQL.  
  
## <a name="options"></a>Options  
 **Source de données**  
 Définit la source de données de la requête.  
  
 **Définition de la requête**  
 La définition de la requête propose une barre d'outils et des volets dans lesquels il est possible de définir et de tester la requête en fonction de la vue sélectionnée.  
  
 **Barre d'outils**  
 Utilisez la barre d'outils pour gérer les datasets, sélectionner les volets à afficher et contrôler diverses fonctions de requête.  
  
|Value|Description|  
|-----------|-----------------|  
|**Basculer vers le Générateur de requêtes générique**|Sélectionnez cette option pour afficher uniquement les options disponibles dans la vue Générateur de requêtes générique. Seules les options suivantes sont affichées :<br /><br /> **Volet SQL**<br /><br /> **Volet résultats**<br /><br /> **Barre d'outils**qui contient uniquement les commandes **Basculer vers le générateur de requêtes VDT** et **Exécuter**<br /><br /> <br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Basculer vers le Générateur de requêtes VDT**|Sélectionnez cette option pour afficher toutes les options disponibles dans la vue Générateur de requête Outils Visual Database (VDT).<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes générique** est sélectionné.|  
|**Afficher/Masquer le volet Diagramme**|Affiche ou masque le **volet Diagramme**.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Afficher/Masquer le volet Grille**|Affiche ou masque le **volet Grille**.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Afficher/Masquer le volet SQL**|Affiche ou masque le **volet SQL**.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Afficher/masquer le volet de résultats**|Affiche ou masque le **volet Résultats**.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Exécuter**|Exécute la requête. Les résultats s'affichent dans le **volet Résultats**.|  
|**Vérifier SQL**|Vérifie l'instruction SQL dans la requête.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Tri croissant**|Trie en ordre croissant les lignes de résultat de la colonne sélectionnée dans le **volet Grille**.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Tri décroissant**|Trie en ordre décroissant les lignes de résultat de la colonne sélectionnée dans le **volet Grille**.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Supprimer le filtre**|Supprime les critères de tri, le cas échéant, de la ligne sélectionnée dans le **volet Grille**.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Utiliser GROUP BY**|Ajoute la fonctionnalité de regroupement à la requête.<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
|**Ajouter une table**|Affiche la boîte de dialogue **Ajouter une table** pour ajouter une nouvelle table ou une nouvelle vue à la requête. Pour plus d’informations sur la boîte de dialogue **Ajouter une table**, consultez [Boîte de dialogue Ajouter une table &#40;Analysis Services - Données multidimensionnelles&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Remarque : Cette option s’affiche uniquement si **basculer vers le Générateur de requêtes VDT** est sélectionné.|  
  
 **Volet Schéma**  
 Affiche les objets référencés par la requête sous forme de diagramme. Le diagramme illustre les tables contenues dans la requête et leur mode de jointure. Activez ou désactivez la case à cocher correspondant à une colonne de la table pour l'ajouter ou la supprimer du résultat de la requête.  
  
 Lorsque vous ajoutez des tables à la requête, la boîte de dialogue crée des jointures entre les tables en fonction de leurs clés. Pour ajouter une jointure, faites glisser le champ d'une table vers un champ situé dans une autre table. Pour gérer une jointure, cliquez avec le bouton droit sur celle-ci.  
  
 Cliquez avec le bouton droit sur le **volet Diagramme** pour ajouter ou supprimer des tables, sélectionner toutes les tables, et afficher ou masquer des volets.  
  
> [!NOTE]  
>  Le contenu du **volet Diagramme**, du **volet Grille**et du **volet SQL** est synchronisé de sorte que les modifications apportées dans l’un d’eux soient répercutées dans les deux autres.  
  
> [!IMPORTANT]  
>  Cette boîte de dialogue ne prend pas en charge la modification des types de requêtes.  
  
 **Volet Grille**  
 Affiche sous forme de grille les objets référencés par la requête. Ce volet est utile pour ajouter ou supprimer des colonnes d'une requête et modifier les paramètres de chaque colonne.  
  
> [!NOTE]  
>  Le contenu du **volet Diagramme**, du **volet Grille**et du **volet SQL** est synchronisé de sorte que les modifications apportées dans l’un d’eux soient répercutées dans les deux autres.  
  
 **Volet SQL**  
 Affiche la requête sous forme d'instruction SQL. Utilisez le clavier pour modifier l'instruction SQL de la requête.  
  
> [!NOTE]  
>  Le contenu du **volet Diagramme**, du **volet Grille**et du **volet SQL** est synchronisé de sorte que les modifications apportées dans l’un d’eux soient répercutées dans les deux autres.  
  
 **Volet résultats**  
 Affiche les résultats de la requête quand vous cliquez sur **Exécuter** dans le volet **Barre d’outils** .  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
