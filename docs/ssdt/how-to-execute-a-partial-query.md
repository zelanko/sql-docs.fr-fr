---
title: 'Procédure : exécuter une requête partielle | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0dff2087286035b078f59ac1673a733fb3cc8358
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65090174"
---
# <a name="how-to-execute-a-partial-query"></a>Procédure : Exécuter une requête partielle
L'éditeur Transact\-SQL permet de mettre en surbrillance un segment spécifique du script et de l'exécuter en tant que requête unique. Ainsi, il est plus facile pour vous de déboguer des sections de requêtes complexes.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes des sections [Développement de base de données connectée](../ssdt/connected-database-development.md) et [Développement de base de données hors connexion orientée projet](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-partially-execute-a-query"></a>Pour exécuter partiellement une requête  
  
1.  Dans l’**Explorateur d’objets SQL Server**, double-cliquez sur **PerishableFruits** sous **Vues** pour l’ouvrir dans l’éditeur Transact\-SQL.  
  
2.  Sélectionnez le segment `SELECT p.Id, p.Name FROM dbo.Product p` dans le code, cliquez avec le bouton droit, puis sélectionnez **Exécuter la requête**.  
  
3.  Notez que toutes les lignes avec les champs spécifiés dans la table `Products` sont retournées dans le volet de **résultats**.  
  
