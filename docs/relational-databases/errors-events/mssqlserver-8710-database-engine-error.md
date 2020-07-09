---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 33bdc74ffee071d8a5f9e7d10543bad133066b32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637069"
---
# <a name="mssqlserver_8710"></a>MSSQLSERVER_8710
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|MSSQLSERVER|  
|ID de l’événement|8710|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|Texte du message|Les fonctions d'agrégation utilisées avec les requêtes CUBE, ROLLUP ou GROUPING SET doivent permettre la fusion des sous-agrégats. Pour résoudre ce problème, supprimez la fonction d'agrégation ou écrivez la requête en utilisant UNION ALL sur les clauses GROUP BY.|  
  
## <a name="explanation"></a>Explication  
Une fonction d'agrégation a été utilisée avec des requêtes CUBE, ROLLUP ou GROUPING SET qui ne fournit pas de méthode pour fusionner les sous-agrégats.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour résoudre ce problème, supprimez la fonction d'agrégation ou écrivez la requête en utilisant UNION ALL sur les clauses GROUP BY.  
  
