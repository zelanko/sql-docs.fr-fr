---
title: Interprétation des résultats des tests unitaires SQL Server| Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: fde3c95b-2f68-483d-a197-0f7161b72fa3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bcaea309d3399d7986ab793ecaf2085180a4c0a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119831"
---
# <a name="interpreting-sql-server-unit-test-results"></a>Interprétation des résultats des tests unitaires SQL Server
Lorsque vous exécutez un test unitaire SQL Server, le résultat du test est généré automatiquement, enregistré sur le disque et résumé dans la fenêtre **Résultats des tests**. Dès que vous démarrez une série de tests, la fenêtre **Résultats des tests** apparaît et affiche la progression de la série de tests. Cet affichage comprend les tests en cours d'exécution et les tests qui ont été finalisés.  
  
Pour afficher des informations détaillées sur un résultat de test, double-cliquez dessus dans la fenêtre **Résultats des tests** pour afficher la page **Détails des résultats des tests**. Pour plus d'informations sur un résultat de test, double-cliquez dessus.  
  
Pour plus d’informations sur la modification de l’affichage de la fenêtre **Résultats des tests**, consultez [Procédure : Ajouter ou supprimer des colonnes dans une fenêtre de test (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182508(VS.100).aspx) ou [Procédure : Ajouter ou supprimer des colonnes dans une fenêtre de test (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182508.aspx).  
  
## <a name="storing-test-results"></a>Stockage des résultats des tests  
Les résultats des tests unitaires sont automatiquement stockés sur votre disque dur dans des fichiers portant l'extension .trx. Un fichier .trx est un fichier XML qui contient les détails d'une série de tests. Chargez les fichiers .trx de séries de tests précédentes pour examiner les résultats de ces séries de tests ou réexécuter des tests antérieurs. Pour plus d’informations, consultez [Procédure : Réexécuter un Test (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182472(VS.100).aspx).  
  
> [!NOTE]  
> Vous ne pouvez pas exécuter des tests unitaires à distance.  
  
Si votre équipe utilise un projet d'équipe Visual Studio Team Foundation Server pour l'aider à gérer son travail, vous pouvez également publier vos données de test dans une base de données SQL Server appelée magasin opérationnel.  
  
Pour plus d’informations sur les méthodes pour enregistrer les résultats des tests, les réutiliser et les partager avec votre équipe, consultez [Procédure : Enregistrer et ouvrir des résultats des tests dans Visual Studio 2010](https://msdn.microsoft.com/library/ms404662(VS.100).aspx) ou [Procédure : Enregistrer et ouvrir des résultats des tests dans Visual Studio 2012](https://msdn.microsoft.com/library/ms404662.aspx).  
  
## <a name="see-also"></a>Voir aussi  
[Exécuter des tests unitaires SQL Server](../ssdt/running-sql-server-unit-tests.md)  
  
