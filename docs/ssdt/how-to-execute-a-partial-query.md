---
title: 'Procédure : exécuter une requête partielle | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c6ed1362f7001a55b74538c165b373364b93df3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087471"
---
# <a name="how-to-execute-a-partial-query"></a>Procédure : exécuter une requête partielle
L'éditeur Transact\-SQL permet de mettre en surbrillance un segment spécifique du script et de l'exécuter en tant que requête unique. Ainsi, il est plus facile pour vous de déboguer des sections de requêtes complexes.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes des sections [Développement de base de données connectée](../ssdt/connected-database-development.md) et [Développement de base de données hors connexion orientée projet](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-partially-execute-a-query"></a>Pour exécuter partiellement une requête  
  
1.  Dans l’**Explorateur d’objets SQL Server**, double-cliquez sur **PerishableFruits** sous **Vues** pour l’ouvrir dans l’éditeur Transact\-SQL.  
  
2.  Sélectionnez le segment `SELECT p.Id, p.Name FROM dbo.Product p` dans le code, cliquez avec le bouton droit, puis sélectionnez **Exécuter la requête**.  
  
3.  Notez que toutes les lignes avec les champs spécifiés dans la table `Products` sont retournées dans le volet de **résultats**.  
  
