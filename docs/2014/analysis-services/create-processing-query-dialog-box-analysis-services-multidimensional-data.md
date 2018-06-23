---
title: Créer le traitement de la boîte de dialogue requête (Analysis Services - données multidimensionnelles) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.createprocessingquerydialog.f1
ms.assetid: c133d624-f35e-486e-be9f-ceafd906f168
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 01633f8b8ce57d3b8953c1694a250cfdb9a64cc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141917"
---
# <a name="create-processing-query-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Créer la requête de traitement (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Créer la requête de traitement** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer une requête de traitement dans l'onglet **Notifications** de la boîte de dialogue **Options de stockage** . Une requête de traitement retourne un ensemble de lignes qui contient les modifications apportées à une table associée à un objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] depuis la dernière interrogation de la table de façon à effectuer une mise à jour incrémentielle de la mémoire cache OLAP multidimensionnelle (MOLAP) de l'objet. Analysis Services utilise une autre requête, baptisée requête d'interrogation, pour interroger une table associée à un objet et déterminer si la table a été modifiée. Les requêtes de traitement ne sont pas nécessaires lors de la mise à jour complète de la mémoire cache MOLAP de l'objet.  
  
 Généralement, la requête de traitement est paramétrable. Deux paramètres sont actuellement pris en charge :  
  
-   la valeur singleton retournée par la requête d'interrogation lors de la précédente interrogation planifiée ;  
  
-   la valeur singleton retournée par la requête d'interrogation lors de l'interrogation planifiée en cours.  
  
 Par exemple, les requêtes figurant dans le tableau ci-dessous permettent d'effectuer une mise à jour incrémentielle de la dimension Customer dans le projet spécimen Adventure Works DW [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
|Type de requête|Instruction de requête|  
|----------------|---------------------|  
|Requête d'interrogation|`SELECT`<br /><br /> `MAX([CustomerKey]) AS LastCustomerKey`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
|Traitement de la requête en cours|`SELECT`<br /><br /> `*`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`<br /><br /> `WHERE`<br /><br /> `(CustomerKey > COALESCE (@Param1, - 1))`<br /><br /> `AND (CustomerKey <= @Param2)`|  
  
 Pour plus d’informations sur les mises à jour incrémentielles des notifications d’interrogations planifiées, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
 Pour afficher la boîte de dialogue **Créer la requête de traitement** , cliquez sur **...** dans la colonne **Traitement de la requête en cours** de la grille de l'option **Interrogation planifiée** dans l'onglet **Notifications** de la boîte de dialogue **Options de stockage** . Pour plus d’informations sur l’onglet **Notifications** de la boîte de dialogue **Options de stockage**, consultez [Notifications &#40;boîte de dialogue Options de stockage&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).  
  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|**Basculer vers le Générateur de requêtes générique**|Sélectionnez cette option pour afficher uniquement les options disponibles dans la vue Générateur de requêtes générique. Seules les options suivantes sont affichées :<br /><br /> **Volet SQL**<br /><br /> **Volet résultats**<br /><br /> **Barre d'outils**qui contient uniquement les commandes **Basculer vers le générateur de requêtes VDT** et **Exécuter**<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Basculer vers le Générateur de requêtes VDT**|Sélectionnez cette option pour afficher toutes les options disponibles dans la vue Générateur de requête Outils Visual Database (VDT).<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes générique** est sélectionné.|  
|**Afficher/Masquer le volet Diagramme**|Affiche ou masque le **volet Diagramme**.<br /><br /> **Remarque** Cette option s'affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Afficher/Masquer le volet Grille**|Affiche ou masque le **volet Grille**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Afficher/Masquer le volet SQL**|Affiche ou masque le **volet SQL**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Afficher/masquer le volet de résultats**|Affiche ou masque le **volet Résultats**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Exécuter**|Exécute la requête. Les résultats s'affichent dans le **volet Résultats**.|  
|**Vérifier SQL**|Vérifie l'instruction SQL dans la requête.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Tri croissant**|Trie en ordre croissant les lignes de résultat de la colonne sélectionnée dans le **volet Grille**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Tri décroissant**|Trie en ordre décroissant les lignes de résultat de la colonne sélectionnée dans le **volet Grille**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Supprimer le filtre**|Supprime les critères de tri, le cas échéant, de la ligne sélectionnée dans le **volet Grille**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Utiliser GROUP BY**|Ajoute la fonctionnalité de regroupement à la requête.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Ajouter une table**|Affiche la boîte de dialogue **Ajouter une table** pour ajouter une nouvelle table ou une nouvelle vue à la requête. Pour plus d’informations sur la boîte de dialogue **Ajouter une table**, consultez [Boîte de dialogue Ajouter une table &#40;Analysis Services - Données multidimensionnelles&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
  
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
  
  