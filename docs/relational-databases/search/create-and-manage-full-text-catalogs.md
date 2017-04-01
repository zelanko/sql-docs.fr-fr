---
title: "Cr&#233;er et g&#233;rer des catalogues de texte int&#233;gral | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "catalogues de texte intégral [SQL Server], création"
  - "recherche en texte intégral [SQL Server], à l’aide de SQL Server Management Studio"
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Cr&#233;er et g&#233;rer des catalogues de texte int&#233;gral
  Un catalogue de texte intégral est un objet virtuel qui n'appartient à aucun groupe de fichiers ; c'est un concept logique qui renvoie à un groupe d'index de recherche en texte intégral.  
  
##  <a name="creating"></a> Création d'un catalogue de texte intégral  
  
#### Pour créer un catalogue de texte intégral  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, le nœud **Bases de données**, puis la base de données contenant le catalogue de texte intégral à créer.  
  
2.  Développez **Stockage**, puis cliquez avec le bouton droit sur **Catalogues de texte intégral**.  
  
3.  Sélectionnez **Nouveau catalogue de recherche en texte intégral**.  
  
4.  Dans la boîte de dialogue **Nouveau catalogue de recherche en texte intégral**, précisez les informations relatives au catalogue que vous recréez. Pour plus d’informations, consultez [Recherche en texte intégral &#40;page Général&#41;](../Topic/New%20Full-Text%20Catalog%20\(General%20Page\).md).  
  
    > [!NOTE]  
    >  Les ID de catalogues de texte intégral commencent à 00005 et sont incrémentés d'une unité à chaque fois qu'un catalogue est créé.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
   
  
##  <a name="props"></a> Affichage des propriétés d'un catalogue de texte intégral  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Vous pouvez faire appel à plusieurs fonctions, telles que FULLTEXTCATALOGPROPERTY, pour obtenir la valeur de diverses propriétés relatives à l’indexation de texte intégral. Ces informations sont utiles pour administrer la recherche en texte intégral et résoudre les problèmes qui la concernent.  
  
 Le tableau suivant répertorie les propriétés liées aux catalogues de texte intégral.  
  
|Propriété|Description|Fonction|  
|--------------|-----------------|--------------|  
|**AccentSensitivity**|Respect des accents.|[FULLTEXTCATALOGPROPERTY](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)|  
|**ImportStatus**|Indique si le catalogue de texte intégral est en cours d'importation.|FULLTEXTCATALOGPROPERTY|  
|**IndexSize**|Taille du catalogue de texte intégral en mégaoctets (Mo).|FULLTEXTCATALOGPROPERTY|  
|**ItemCount**|Nombre d'éléments indexés de texte intégral actuellement dans le catalogue de texte intégral.|FULLTEXTCATALOGPROPERTY|  
|**MergeStatus**|Indique si une fusion principale est en cours.|FULLTEXTCATALOGPROPERTY|  
|**PopulateCompletionAge**|Différence en secondes entre la fin du remplissage du dernier index de texte intégral et le 01/01/1990 00:00:00.|FULLTEXTCATALOGPROPERTY|  
|**PopulateStatus**|État de remplissage.<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|FULLTEXTCATALOGPROPERTY|  
|**UniqueKeyCount**|Nombre de clés uniques dans le catalogue de texte intégral.|FULLTEXTCATALOGPROPERTY|  
  
   
  
##  <a name="rebuildone"></a> Reconstruction d'un catalogue de texte intégral  
  
#### Pour reconstruire un catalogue de texte intégral  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données contenant le catalogue de texte intégral à reconstruire.  
  
2.  Développez **Stockage**, puis **Catalogues de texte intégral**.  
  
3.  Cliquez avec le bouton droit sur le nom du catalogue de texte intégral que vous souhaitez reconstruire, puis sélectionnez **Reconstruire**.  
  
4.  En réponse à la question **Voulez-vous supprimer le catalogue de texte intégral et le reconstruire ?**, cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Reconstruire le catalogue de texte intégral**, cliquez sur **Fermer**.  
  
   
  
##  <a name="rebuildall"></a> Reconstruction de tous les catalogues de texte intégral pour une base de données  
  
#### Pour reconstruire les catalogues de texte intégral pour une base de données  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données contenant les catalogues de texte intégral à reconstruire.  
  
2.  Développez **Stockage**, puis cliquez avec le bouton droit sur **Catalogues de texte intégral**.  
  
3.  Sélectionnez **Tout reconstruire**.  
  
4.  En réponse à la question **Voulez-vous supprimer tous les catalogues de texte intégral et les reconstruire ?**, cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Reconstruire tous les catalogues de texte intégral**, cliquez sur **Fermer**.  
  
  
  
##  <a name="removing"></a> Suppression d'un catalogue de texte intégral d'une base de données  
  
#### Pour supprimer un catalogue de texte intégral d'une base de données  
  
1.  Dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données qui contient le catalogue de texte intégral à supprimer.  
  
2.  Développez **Stockage**, puis **Catalogues de texte intégral**.  
  
3.  Cliquez avec le bouton droit sur le catalogue de texte intégral à supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer les objets**, cliquez sur **OK**.  
  
  
## Voir aussi  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)  
  
  