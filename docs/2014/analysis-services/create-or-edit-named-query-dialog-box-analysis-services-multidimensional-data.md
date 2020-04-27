---
title: Boîte de dialogue créer ou modifier une requête nommée (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createnamedquery.f1
helpviewer_keywords:
- Create Named Query dialog box
ms.assetid: 8e192ad6-a0b1-4e21-bb3f-087c93e62941
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f01b0bbf3d1ddc54ea4db2b771723e12d168d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66086808"
---
# <a name="create-or-edit-named-query-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Créer/Modifier la requête nommée (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Créer/Modifier la requête nommée** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer ou modifier une requête nommée dans le **Concepteur de vue de source de données**. Une requête nommée peut être traitée sous la forme d'une table sur laquelle vous pouvez baser d'autres objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Vous pouvez afficher la boîte de dialogue **Créer/Modifier la requête nommée** en :  
  
-   cliquant sur **Nouvelle requête nommée** dans le volet **Barre d'outils** du **Concepteur de vue de source de données**;  
  
-   cliquant avec le bouton droit de la souris sur le volet **Diagramme** du **Concepteur de vue de source de données** et en sélectionnant **Nouvelle requête nommée**;  
  
-   cliquant avec le bouton droit de la souris sur une requête nommée dans le volet **Diagramme** ou **Tables** du **Concepteur de vue de source de données** et en sélectionnant **Modifier la requête nommée**.  
  
 La requête entrée doit être une commande de requête acceptée par le fournisseur sous-jacent. La requête est préparée pour validation au moyen du fournisseur sous-jacent et pour identifier les colonnes retournées. La boîte de dialogue peut présenter deux vues :  
  
-   Générateur de requête VDT (Outils Visual Database)  
  
     Pour tous les utilisateurs, la vue Générateur de requête VDT utilise un ensemble d'outils d'interface destinés à créer et à tester visuellement une requête SQL.  
  
-   Générateur de requêtes générique  
  
     Pour les utilisateurs avancés, la vue Générateur de requêtes générique fournit une interface utilisateur plus simple et plus directe pour créer et tester une requête SQL.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de la requête.  
  
 **Description**  
 Tapez la description facultative de la requête.  
  
 **Source de données**  
 Définit la source de données de la requête.  
  
 **Définition de la requête**  
 La définition de la requête propose une barre d'outils et des volets dans lesquels il est possible de définir et de tester la requête en fonction de la vue sélectionnée.  
  
 **Barre**  
 Utilisez la barre d'outils pour gérer les datasets, sélectionner les volets à afficher et contrôler diverses fonctions de requête.  
  
|Value|Description|  
|-----------|-----------------|  
|**Basculer vers le générateur de requêtes générique**|Sélectionnez cette option pour afficher uniquement les options disponibles dans la vue Générateur de requêtes générique. Seules les options suivantes sont affichées :<br />**Volet SQL**<br />**Volet résultats**<br />**Barre d'outils**qui contient uniquement les commandes **Basculer vers le générateur de requêtes VDT** et **Exécuter**<br /><br /> <br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Basculer vers le générateur de requêtes VDT**|Sélectionnez cette option pour afficher toutes les options disponibles dans la vue Générateur de requête Outils Visual Database (VDT).<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes générique** est sélectionné.|  
|**Afficher/Masquer le volet Diagramme**|Affiche ou masque le **volet Diagramme**.<br /><br /> **Remarque** Cette option s’affiche uniquement si l’option **basculer vers VDT générateur de requêtes** est sélectionnée.|  
|**Afficher/Masquer le volet Grille**|Affiche ou masque le **volet Grille**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Afficher/Masquer le volet SQL**|Affiche ou masque le **volet SQL**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
|**Afficher/Masquer le volet Résultats**|Affiche ou masque le **volet Résultats**.<br /><br /> Remarque : cette option s’affiche uniquement si **Basculer vers le générateur de requêtes VDT** est sélectionné.|  
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
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Définir des requêtes nommées dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)  
  
  
