---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 119ff7b3bb46e0ea05f1e3cbe87f497132468713
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064249"
---
# <a name="mssqlserver1904"></a>MSSQLSERVER_1904
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1904|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|KEYCOUNT|  
|Texte du message|Le %S_MSG '%.*ls' sur la table '%.\*ls' a %d noms de colonnes dans la liste de clés %S_MSG. La limite maximale pour la liste des colonnes de clés d'index ou de statistiques est %d.|  
  
## <a name="explanation"></a>Explication  
 La liste des colonnes de clés pour l'index ou les statistiques spécifiés dépasse le nombre maximal autorisé de colonnes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez la liste des colonnes de clés de sorte qu'elle n'inclue pas plus de colonnes que le nombre maximal spécifié.  
  
 Pour les index non cluster, pensez à utiliser la clause INCLUDE dans l'instruction CREATE INDEX pour ajouter des colonnes à l'index en tant que colonnes non clés. Cette méthode évite de dépasser la limite actuelle de taille d'index fixée à un maximum de 16 colonnes clés. Pour plus d’informations, consultez [Créer des index avec colonnes incluses](../indexes/create-indexes-with-included-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
