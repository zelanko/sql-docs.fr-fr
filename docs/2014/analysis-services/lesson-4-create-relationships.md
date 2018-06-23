---
title: 'Leçon 5 : Créer des relations | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: abac1a00-f827-4c3e-a473-6db5c8a3a66f
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: d9428908b712fcda9a016af0825602c62548a691
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140855"
---
# <a name="lesson-5-create-relationships"></a>Leçon 5 : Créer des relations
  Dans cette leçon, vous allez vérifier les relations qui ont été créées automatiquement lorsque vous avez importé des données, et vous allez ajouter de nouvelles relations entre les tables. Une relation est une connexion entre deux tables qui établit le mode de corrélation des données dans les deux tables. Par exemple, la table Product et la table Product Subcategory ont une relation basée sur le fait que chaque produit appartient à une sous-catégorie. Pour en savoir plus, consultez [Relations &#40;SSAS Tabulaire&#41;](tabular-models/relationships-ssas-tabular.md).  
  
 Durée estimée pour effectuer cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 3 : Renommer des colonnes](rename-columns.md).  
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Examiner les relations existantes et ajouter de nouvelles relations  
 Lorsque vous avez importé des données à l'aide de l'Assistant Importation de table, vous avez importé sept tables de la base de données AdventureWorksDW. En général, si vous importez des données d'une source relationnelle, les relations existantes sont importées automatiquement avec les données. Toutefois, avant de poursuivre la création de votre modèle, vous devez vérifier que les relations entre les tables ont été créées correctement. Pour ce didacticiel, vous allez également ajouter trois relations.  
  
#### <a name="to-review-existing-relationships"></a>Pour vérifier les relations existantes  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis pointez sur **Vue du modèle**et sur **Vue de diagramme**.  
  
     Le concepteur de modèles apparaît maintenant dans la vue de diagramme, c'est un format graphique affichant toutes les tables que vous avez importées et les lignes les reliant. Les lignes entre les tables indiquent les relations qui ont été créées automatiquement lorsque vous avez importé les données.  
  
     Utilisez les contrôles de la minicarte dans l'angle supérieur droit du concepteur de modèles pour ajuster la vue et inclure autant de tables que possible. Vous pouvez également cliquer et faire glisser des tables à différents emplacements, en rapprochant les tables autant que possible, ou en les plaçant dans un ordre précis. Le déplacement des tables n'affecte pas les relations qui existent déjà entre elles. Pour afficher toutes les colonnes d'une table donnée, cliquez et faites glisser le bord de la table pour l'agrandir ou la réduire.  
  
2.  Cliquez sur la ligne pleine entre la table **Customer** et la table **Geography** . La ligne pleine entre ces deux tables indique que cette relation est active, c.-à-d. qu'elle est utilisée par défaut lors du calcul des formules DAX.  
  
     Notez que la colonne **Geography Id** dans la table **Customer** et la colonne **Geography Id** dans la table **Geography** apparaissent maintenant chacune dans une zone. Cela indique qu'il s'agit des colonnes utilisées dans la relation. Les propriétés de la relation apparaissent maintenant aussi dans la fenêtre **Propriétés** .  
  
    > [!TIP]  
    >  Outre l’utilisation du concepteur de modèles dans la vue de diagramme, vous pouvez également utiliser la boîte de dialogue **Gérer les relations** pour afficher les relations entre toutes les tables dans un format tabulaire. Cliquez sur le menu **Table** , puis sur **Gérer les relations**. La boîte de dialogue **Gérer les relations** affiche les relations qui ont été créées automatiquement quand vous avez importé des données.  
  
3.  Utilisez le concepteur de modèles dans la vue de diagramme, ou la boîte de dialogue **Gérer les relations** , pour vérifier que les relations suivantes ont été créées quand chacune des tables a été importée à partir de la base de données AdventureWorksDW :  
  
    |Actif|Table de charge de travail|Table de recherche associée|  
    |------------|-----------|--------------------------|  
    |Oui|**Client [Geography Id]**|**Geography [Geography Id]**|  
    |Oui|**Produit [Id de sous-catégorie de produit]**|**Sous-catégorie de produit [Id de sous-catégorie de produit]**|  
    |Oui|**Sous-catégorie de produit [Id de catégorie de produit]**|**Catégorie de produit [Id de catégorie de produit]**|  
    |Oui|**Ventes sur Internet [Id de client]**|**Client [Id de client]**|  
    |Oui|**Ventes sur Internet [Id de produit]**|**Produit [Id de produit]**|  
  
 Si l'une des relations dans la table ci-dessus est manquante, vérifiez que votre modèle inclut les tables suivantes : Customer, Date, Geography, Product, Product Category, Product Subcategory et Internet Sales. Si des tables provenant de la même connexion de source de données sont importées à des moments différents, aucune relation entre ces tables ne sera créée et les relations devront être créées manuellement.  
  
 Dans certains cas, vous devrez peut-être créer des relations supplémentaires entre les tables dans votre modèle pour prendre en charge certaines logiques métiers. Pour ce didacticiel, vous devez créer trois relations supplémentaires entre la table Internet sales et la table Date.  
  
#### <a name="to-add-new-relationships-between-tables"></a>Pour ajouter de nouvelles relations entre des tables  
  
1.  Dans le concepteur de modèles, dans la table **Internet Sales** , cliquez et maintenez le bouton enfoncé sur la colonne **Order Date** , faites glisser le curseur sur la colonne **Date** dans la table **Date** , puis relâchez la souris.  
  
     Une ligne pleine apparaît et indique que vous avez créé une relation active entre la colonne **Order Date** dans la table **Internet Sales** et la colonne **Date** dans la table **Date** .  
  
    > [!NOTE]  
    >  Lorsque vous créez des relations, l'ordre entre la table primaire et la table de recherche associée est automatiquement classifié correctement.  
  
2.  Dans la table **Internet Sales** , cliquez et maintenez le bouton enfoncé sur la colonne **Due Date** , faites glisser le curseur sur la colonne **Date** dans la table **Date** , puis relâchez la souris.  
  
     Une ligne en pointillés apparaît et indique que vous avez créé une relation inactive entre la colonne **Due Date** dans la table **Internet Sales** et la colonne **Date** dans la table **Date** . Vous pouvez avoir plusieurs relations entre les tables, mais une seule relation peut être active à la fois.  
  
3.  Enfin, créez une relation supplémentaire : dans la table **Internet Sales** , cliquez et maintenez le bouton enfoncé sur la colonne **Ship Date** , faites glisser le curseur sur la colonne **Date** dans la table **Date** , puis relâchez la souris.  
  
     Une ligne en pointillés apparaît et indique que vous avez créé une relation inactive entre la colonne **Ship Date** dans la table **Internet Sales** et la colonne **Date** dans la table **Date** .  
  
## <a name="next-step"></a>Étape suivante  
 Pour continuer cette leçon, passez à la [Leçon 6 : Créer des colonnes calculées](lesson-5-create-calculated-columns.md).  
  
  