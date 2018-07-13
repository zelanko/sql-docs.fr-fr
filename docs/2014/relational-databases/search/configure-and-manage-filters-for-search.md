---
title: Configurer et gérer des filtres pour la recherche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7b19f9141df65be952551dbb899b6cb30544e9a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278925"
---
# <a name="configure-and-manage-filters-for-search"></a>Configurer et gérer des filtres pour la recherche
  Indexation de documents dans un `varbinary`, `varbinary(max)`, `image`, ou `xml` colonne de type de données nécessite un traitement supplémentaire. Ce traitement doit être effectué par un filtre. Le filtre extrait les informations textuelles du document (en supprimant la mise en forme). Le filtre envoie ensuite le texte au composant d'analyseur lexical pour la langue associée à la colonne de table.  
  
 Un filtre donné est spécifique à un type de document donné (.doc, .pdf, .xls, .xml, etc.). Ces filtres implémentent l'interface IFilter. Pour plus d’informations sur ces types de document, interrogez l’affichage catalogue [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) .  
  
 Des documents binaires peuvent être stockés dans une colonne `varbinary(max)` ou `image` unique. Pour chaque document, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] choisit le filtre correct en fonction de l'extension de fichier. Étant donné que l’extension de fichier n’est pas visible lorsque le fichier est stocké dans un `varbinary(max)` ou `image` colonne, l’extension de fichier (.doc, .xls, .pdf, etc.) doit être stockée dans une colonne distincte dans la table, appelée colonne de type. Cette colonne de type peut être composée de n'importe quel type de données de caractères ; par ailleurs, elle contient l'extension de fichier du document, par exemple « .doc » pour un document [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word. Dans le **Document** table [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], le **Document** colonne est de type `varbinary(max)`et la colonne de type **FileExtension**, est de type `nvarchar(8)`.  
  
> [!NOTE]  
>  Un filtre peut être en mesure de gérer des objets incorporés dans l'objet parent, selon son implémentation. Toutefois, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne configure pas de filtres pour suivre des liens vers d'autres objets.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe ses propres filtres XML et HTML. De plus, tous les filtres des formats propriétaires [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (.doc, .xdoc, .ppt, etc.) qui sont déjà installés sur le système d’exploitation sont également chargés par  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour identifier les filtres actuellement chargés sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], utilisez la procédure stockée [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) , comme suit :  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 Toutefois, avant de pouvoir utiliser des filtres pour des formats non [!INCLUDE[msCoName](../../../includes/msconame-md.md)] , vous devez les charger manuellement dans l’instance de serveur. Pour plus d’informations sur l’installation de filtres supplémentaires, consultez [Afficher ou modifier des filtres et des analyseurs lexicaux inscrits](view-or-change-registered-filters-and-word-breakers.md).  
  
 **Pour voir la colonne de type dans un index de recherche en texte intégral existant**  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)   
 [Compatibilité de FILESTREAM avec d'autres fonctionnalités SQL Server](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
