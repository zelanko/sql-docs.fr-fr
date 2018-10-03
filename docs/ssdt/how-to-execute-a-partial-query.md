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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1c10ec2282e5e7870ec05de356b0d2f1461e95f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677311"
---
# <a name="how-to-execute-a-partial-query"></a>Procédure : exécuter une requête partielle
L'éditeur Transact\-SQL permet de mettre en surbrillance un segment spécifique du script et de l'exécuter en tant que requête unique. Ainsi, il est plus facile pour vous de déboguer des sections de requêtes complexes.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes des sections [Développement de base de données connectée](../ssdt/connected-database-development.md) et [Développement de base de données hors connexion orientée projet](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-partially-execute-a-query"></a>Pour exécuter partiellement une requête  
  
1.  Dans l’**Explorateur d’objets SQL Server**, double-cliquez sur **PerishableFruits** sous **Vues** pour l’ouvrir dans l’éditeur Transact\-SQL.  
  
2.  Sélectionnez le segment `SELECT p.Id, p.Name FROM dbo.Product p` dans le code, cliquez avec le bouton droit, puis sélectionnez **Exécuter la requête**.  
  
3.  Notez que toutes les lignes avec les champs spécifiés dans la table `Products` sont retournées dans le volet de **résultats**.  
  
