---
title: MSSQLSERVER_2501 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1d6e9f16e00684f0a55682b69e4c2d89d0dd552e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140976"
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
  
-   Vérifiez que le contexte de base de données est correct. Pour plus d’informations, consultez [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   Vérifiez que le nom de la table ou de l'objet est correctement orthographié.  
  
-   Vérifiez le nom de schéma que contient l'objet. Si l’objet appartient à un schéma autre que le schéma par défaut (**dbo**), vous devez spécifier le nom de la table ou de l’objet à l’aide du format en deux parties *nom_schéma.nom_objet*.  
  
-   Vérifiez que l'objet existe dans les tables système. Pour vérifier s’il existe une table ou un autre objet étendu aux schémas, interrogez la vue de catalogue [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql). Si l'objet ne se trouve pas dans les tables système, cela signifie qu'il a été supprimé ou que l'utilisateur ne dispose pas d'autorisations pour afficher les métadonnées de l'objet. Pour plus d’informations sur l’affichage des métadonnées d’objet, consultez [Configuration de la visibilité des métadonnées](../security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues catalogue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
  
