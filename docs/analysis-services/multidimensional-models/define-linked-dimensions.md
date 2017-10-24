---
title: "Définir des Dimensions liées | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: d5ad5eae-5dde-46a6-91c3-c8766d016dec
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d7830d5075da8ab4b741ecb31bbdefb3acdf6cb9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="define-linked-dimensions"></a>Définir des dimensions liées
  Une dimension liée est basée sur une dimension créée et enregistrée dans une autre base de données Analysis Services ayant la même version et le même niveau de compatibilité. En utilisant une dimension liée, vous pouvez créer, stocker et gérer une dimension dans une base de données, tout en rendant la dimension disponible pour les utilisateurs de plusieurs bases de données. Pour les utilisateurs, une dimension liée a la même apparence que n'importe quelle autre dimension.  
  
 Les dimensions liées sont en lecture seule. Si vous souhaitez modifier la dimension ou créer des relations, vous devez modifier la dimension source, puis supprimer et recréer la dimension liée et ses relations. Vous ne pouvez pas actualiser une dimension liée pour récupérer les modifications de l'objet source.  
  
 Les groupes de mesures et dimensions associés doivent provenir de la même base de données source. Vous ne pouvez pas créer de relations entre des groupes de mesures locaux et les dimensions liées que vous ajoutez à votre cube. Une fois que des dimensions et des groupes de mesures liés ont été ajoutés au cube actuel, les relations existant entre eux doivent être maintenues dans leur base de données source.  
  
> [!NOTE]  
>  Puisque l'actualisation n'est pas disponible, la plupart des développeurs Analysis Services copient les dimensions au lieu de les lier. Vous pouvez copier des dimensions entre les projets dans la même solution. Pour plus d’informations, consultez [Actualisation d’une dimension liée dans SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx).  
  
## <a name="prerequisites"></a>Conditions préalables  
 La base de données source qui fournit la dimension et la base de données active qui les utilise doivent être de la même version et avoir le même niveau de compatibilité. Pour plus d’informations, consultez [Niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
 La base de données source doit être déployée et en ligne. Les serveurs qui publient ou consomment des objets liés doivent être configurés pour autoriser l'opération (voir ci-dessous).  
  
 La dimension à utiliser ne peut pas être une dimension liée.  
  
## <a name="configure-server-to-allow-linked-objects"></a>Configurer le serveur pour autoriser les objets liés  
  
1.  Dans SQL Server Management Studio, connectez-vous à un serveur Analysis Services. Dans l’Explorateur d’objets, cliquez avec le bouton droit sur le nom du serveur, puis sélectionnez **Facettes**.  
  
2.  Affectez à **LinkedObjectsLinksFromOtherInstancesEnabled** la valeur **True** pour permettre au serveur d’émettre des demandes d’objets liés qui résident dans les bases de données exécutées sur d’autres instances.  
  
3.  Affectez à **LinkedObjectsLinksToOtherInstances** la valeur **True** pour permettre au serveur de demander des données pour les bases de données liées exécutées sur d’autres instances.  
  
## <a name="create-a-linked-dimension-in-sql-server-data-tools"></a>Créer une dimension liée dans les outils de données SQL Server  
  
1.  Démarrez l'Assistant. Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez avec le bouton droit sur le dossier **Dimensions** dans une base de données ou un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis cliquez sur **Nouvelle dimension liée**.  
  
2.  Connectez-vous à la base de données Analysis Services qui fournit la dimension. Dans la page **Sélectionner une source de données** de l’Assistant Objet lié, choisissez la source de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou créez-en une.  
  
3.  Dans la page **Sélectionner des objets** de l’Assistant, choisissez les dimensions vers lesquelles vous voulez créer un lien dans la base de données distante.  
  
4.  Dans la page **Fin de l’Assistant** , vous pouvez afficher un aperçu des objets liés. Si vous liez une dimension qui a le même nom qu'une dimension existante, un nombre ordinal (« 1 » pour le premier nom dupliqué, et ainsi de suite) est ajouté au nom. À la fin de l’Assistant, la dimension est ajoutée au dossier **Dimensions** .  
  
##  <a name="bkmk_CreateNew"></a> Créer une connexion de source de données à une base de données Analysis Services  
 Utilisez l'Assistant Nouvelle source de données pour ajouter à votre projet des informations de connexion relatives à la base de données Analysis Services qui fournit la dimension. Vous pouvez démarrer l’Assistant en cliquant sur **Nouvelle source de données** dans la page Sélectionner une source de données de l’Assistant Objets liés.  
  
1.  Dans l’Assistant Source de données, dans la page Sélectionner la méthode de définition de la connexion, cliquez sur **Nouvelle**.  
  
2.  Dans le Gestionnaire de connexions, vérifiez que le fournisseur a la valeur **OLE DB natif\Fournisseur Microsoft OLE DB pour Analysis Services 11.0**.  
  
3.  Entrez le nom du serveur (utilisez *nom_serveur*\\*nom_instance* pour une instance nommée), ou tapez **localhost** pour vous connecter à un serveur Analysis Services s’exécutant sur le même ordinateur.  
  
4.  Utilisez l'authentification Windows pour la connexion.  
  
5.  Dans **Catalogue initial**, cliquez sur la flèche bas pour sélectionner une base de données sur ce serveur.  
  
6.  Dans l’Assistant Source de données, cliquez sur **Suivant** pour continuer.  
  
7.  Dans la page Informations d’emprunt d’identité, cliquez sur **Utiliser le compte de service**. Cliquez sur **Suivant**, puis terminez l’Assistant. La connexion que vous venez de définie est sélectionnée dans l'Assistant Objets liés.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Comme vous ne pouvez pas modifier la structure d’une dimension liée, il est impossible de l’afficher à l’aide de l’onglet **Structure de dimension** du Concepteur de dimensions. Après avoir traité la dimension liée, vous pouvez l’afficher à l’aide de l’onglet **Navigateur** . Vous pouvez également modifier son nom et créer une traduction pour ce nom.  
  
## <a name="see-also"></a>Voir aussi  
 [Niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Groupes de mesures liés](../../analysis-services/multidimensional-models/linked-measure-groups.md)   
 [Relations de dimension](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  

