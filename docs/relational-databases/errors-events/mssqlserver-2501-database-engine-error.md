---
title: MSSQLSERVER_2501 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: b1562b89d5e627035d3800a036b769ceccdfde83
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver2501"></a>MSSQLSERVER_2501
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2501|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_NO_SUCH_TABLE_NAME|  
|Texte du message|Table ou objet avec le nom 'NAME' introuvable. Vérifiez le catalogue système.|  
  
## <a name="explanation"></a>Explication  
L'objet spécifié reste introuvable.  
  
### <a name="possible-causes"></a>Causes possibles  
Cette erreur peut être causée par l'un des problèmes suivants :  
  
-   L'objet n'est pas correctement spécifié.  
  
-   L'objet n'existe pas ou il a été supprimé avant qu'une instruction n'essaie de l'utiliser.  
  
-   L'objet existe probablement mais n'a pas pu être exposé à l'utilisateur. Il se peut par exemple que l'utilisateur ne dispose pas d'autorisations sur l'objet ou que l'objet soit une table interne qui ne peut pas être vue par l'utilisateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Vérifiez que le contexte de base de données est correct. Pour plus d’informations, consultez [USE &#40;Transact-SQL&#41;](~/t-sql/language-elements/use-transact-sql.md).  
  
-   Vérifiez que le nom de la table ou de l'objet est correctement orthographié.  
  
-   Vérifiez le nom de schéma que contient l'objet. Si l’objet appartient à un schéma autre que le schéma par défaut (**dbo**), vous devez spécifier le nom de la table ou de l’objet à l’aide du format en deux parties *nom_schéma.nom_objet*.  
  
-   Vérifiez que l'objet existe dans les tables système. Pour vérifier s’il existe une table ou un autre objet étendu aux schémas, interrogez la vue de catalogue [sys.objects](~/relational-databases/system-catalog-views/sys-objects-transact-sql.md). Si l'objet ne se trouve pas dans les tables système, cela signifie qu'il a été supprimé ou que l'utilisateur ne dispose pas d'autorisations pour afficher les métadonnées de l'objet. Pour plus d’informations sur l’affichage des métadonnées d’objet, consultez [Configuration de la visibilité des métadonnées](~/relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
[Vues catalogue &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
