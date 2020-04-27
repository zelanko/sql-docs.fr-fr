---
title: Créer et gérer des catalogues de texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d90ba7f8e183beeeeefe25ea20834b07d7a1bf80
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011468"
---
# <a name="create-and-manage-full-text-catalogs"></a>Créer et gérer des catalogues de texte intégral
  Un catalogue de texte intégral est un objet virtuel qui n'appartient à aucun groupe de fichiers ; c'est un concept logique qui renvoie à un groupe d'index de recherche en texte intégral.  
  
##  <a name="creating-a-full-text-catalog"></a><a name="creating"></a>Création d’un catalogue de texte intégral  
  
#### <a name="to-create-a-full-text-catalog"></a>Pour créer un catalogue de texte intégral  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, le nœud **Bases de données**, puis la base de données contenant le catalogue de texte intégral à créer.  
  
2.  Développez **Stockage**, puis cliquez avec le bouton droit sur **Catalogues de texte intégral**.  
  
3.  Sélectionnez **Nouveau catalogue de recherche en texte intégral**.  
  
4.  Dans la boîte de dialogue **Nouveau catalogue de recherche en texte intégral** , précisez les informations relatives au catalogue que vous recréez. Pour plus d’informations, consultez [Recherche en texte intégral &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
    > [!NOTE]  
    >  Les ID de catalogues de texte intégral commencent à 00005 et sont incrémentés d'une unité à chaque fois qu'un catalogue est créé.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="viewing-the-properties-of-a-full-text-catalog"></a><a name="props"></a>Affichage des propriétés d’un catalogue de texte intégral  
 Vous pouvez faire appel à plusieurs fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)], telles que FULLTEXTCATALOGPROPERTY, pour obtenir la valeur de diverses propriétés relatives à l'indexation de texte intégral. Ces informations sont utiles pour administrer la recherche en texte intégral et résoudre les problèmes qui la concernent.  
  
 Le tableau suivant répertorie les propriétés liées aux catalogues de texte intégral.  
  
|Propriété|Description|Fonction|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|Respect des accents.|[FULLTEXTCATALOGPROPERTY](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|Indique si le catalogue de texte intégral est en cours d'importation.|FULLTEXTCATALOGPROPERTY|  
|`IndexSize`|Taille du catalogue de texte intégral en mégaoctets (Mo).|FULLTEXTCATALOGPROPERTY|  
|`ItemCount`|Nombre d'éléments indexés de texte intégral actuellement dans le catalogue de texte intégral.|FULLTEXTCATALOGPROPERTY|  
|`MergeStatus`|Indique si une fusion principale est en cours.|FULLTEXTCATALOGPROPERTY|  
|`PopulateCompletionAge`|Différence en secondes entre la fin du remplissage du dernier index de texte intégral et le 01/01/1990 00:00:00.|FULLTEXTCATALOGPROPERTY|  
|`PopulateStatus`|État de remplissage.<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|FULLTEXTCATALOGPROPERTY|  
|`UniqueKeyCount`|Nombre de clés uniques dans le catalogue de texte intégral.|FULLTEXTCATALOGPROPERTY|  
  
  
  
##  <a name="rebuilding-a-full-text-catalog"></a><a name="rebuildone"></a>Reconstruction d’un catalogue de texte intégral  
  
#### <a name="to-rebuild-a-full-text-catalog"></a>Pour reconstruire un catalogue de texte intégral  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données contenant le catalogue de texte intégral à reconstruire.  
  
2.  Développez **Stockage**, puis **Catalogues de texte intégral**.  
  
3.  Cliquez avec le bouton droit sur le nom du catalogue de texte intégral que vous souhaitez reconstruire, puis sélectionnez **Reconstruire**.  
  
4.  En réponse à la question **Voulez-vous supprimer le catalogue de texte intégral et le reconstruire ?**, cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Reconstruire le catalogue de texte intégral** , cliquez sur **Fermer**.  
  
  
  
##  <a name="rebuilding-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a>Reconstruction de tous les catalogues de texte intégral d’une base de données  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a>Pour reconstruire les catalogues de texte intégral pour une base de données  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données contenant les catalogues de texte intégral à reconstruire.  
  
2.  Développez **Stockage**, puis cliquez avec le bouton droit sur **Catalogues de texte intégral**.  
  
3.  Sélectionnez **Tout reconstruire**.  
  
4.  En réponse à la question **Voulez-vous supprimer tous les catalogues de texte intégral et les reconstruire ?**, cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Reconstruire tous les catalogues de texte intégral** , cliquez sur **Fermer**.  
  
  
  
##  <a name="removing-a-full-text-catalog-from-a-database"></a><a name="removing"></a>Suppression d’un catalogue de texte intégral d’une base de données  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a>Pour supprimer un catalogue de texte intégral d'une base de données  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données qui contient le catalogue de texte intégral à supprimer.  
  
2.  Développez **Stockage**, puis **Catalogues de texte intégral**.  
  
3.  Cliquez avec le bouton droit sur le catalogue de texte intégral à supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer les objets** , cliquez sur **OK**.  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
